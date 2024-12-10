.. code-block:: javascript
   :copyable: false
   
   class TicketManagement {
     constructor() {
       this.g_max_person_id = null;
       this.g_min_person_id = null;
     }
   
   async function sellTickets(person_id, event_id, quantity = 1) {
     const session = await db.startSession();
     session.startTransaction();
     try {
       const eventRec = await getEventDetails(event_id);
       const availableSeats = await db.collection('sportingEventTicket').aggregate([
         { $match: { sportingEventId: event_id, ticketholderId: null } },
         { $group: { _id: { seatLevel: "$seatLevel", seatSection: "$seatSection", seatRow: "$seatRow" }, count: { $sum: 1 } } },
         { $match: { count: { $gte: quantity } } },
         { $limit: 1 }
       ]).toArray();
   
       if (availableSeats.length === 0) {
         throw new Error('not_enough_seats');
       }
   
       const { seatLevel, seatSection, seatRow } = availableSeats[0]._id;
       const adjacentSeatsCursor = db.collection('sportingEventTicket').find({
         sportingEventId: event_id,
         seatLevel,
         seatSection,
         seatRow,
         ticketholderId: null
       }).sort({ seatLevel: 1, seatSection: 1, seatRow: 1 }).limit(quantity).session(session);
   
       for (let i = 0; i < quantity; i++) {
         const curTicket = await adjacentSeatsCursor.next();
         if (!curTicket) {
           throw new Error('not_enough_seats');
         }
         await db.collection('sportingEventTicket').updateOne(
           { _id: curTicket._id },
           { $set: { ticketholderId: person_id } },
           { session }
         );
         await db.collection('ticketPurchaseHist').insertOne({
           sportingEventTicketId: curTicket.id,
           purchasedById: person_id,
           transactionDateTime: new Date(),
           purchasePrice: curTicket.ticketPrice
         }, { session });
       }
   
       await session.commitTransaction();
     } catch (error) {
       await session.abortTransaction();
       if (error.message === 'not_enough_seats') {
         console.log(`Sorry, there aren't ${quantity} adjacent seats for event:`);
         console.log(`   ${eventRec.home_team_name} VS ${eventRec.away_team_name}   (${eventRec.sport_name})`);
         console.log(`   ${eventRec.home_field}:  ${eventRec.date_time.toLocaleString('en-US', { timeZone: 'UTC', month: 'short', day: 'numeric', year: 'numeric', hour: 'numeric', minute: 'numeric' })}`);
       } else {
         throw error;
       }
     } finally {
       session.endSession();
     }
   }
   
   async function transferTicket(ticket_id, new_ticketholder_id, transfer_all = false, price = null) {
     const session = await db.startSession();
     session.startTransaction();
     try {
       const sportingEventTicketCollection = db.collection('sportingEventTicket');
       const ticketPurchaseHistCollection = db.collection('ticketPurchaseHist');
   
       const ticket = await sportingEventTicketCollection.findOne({ id: ticket_id });
       if (!ticket) throw new Error('Ticket not found');
   
       const lastTransaction = await ticketPurchaseHistCollection.aggregate([
         { $match: { sportingEventTicketId: ticket_id, purchasedById: ticket.ticketholderId } },
         { $group: { _id: null, lastTransactionDate: { $max: "$transactionDateTime" } } }
       ]).toArray();
   
       if (lastTransaction.length === 0) throw new Error('No transaction history found');
   
       const lastTransactionDate = lastTransaction[0].lastTransactionDate;
       const oldTicketholderId = ticket.ticketholderId;
   
       const transactions = await ticketPurchaseHistCollection.find({
         purchasedById: oldTicketholderId,
         transactionDateTime: lastTransactionDate
       }).toArray();
   
       for (const txn of transactions) {
         await sportingEventTicketCollection.updateOne(
           { id: txn.sportingEventTicketId },
           { $set: { ticketholderId: new_ticketholder_id } }
         );
   
         await ticketPurchaseHistCollection.insertOne({
           sportingEventTicketId: txn.sportingEventTicketId,
           purchasedById: new_ticketholder_id,
           transferredFromId: oldTicketholderId,
           transactionDateTime: new Date(),
           purchasePrice: price !== null ? price : txn.purchasePrice
         });
       }
   
       await session.commitTransaction();
     } catch (error) {
       await session.abortTransaction();
       throw error;
     } finally {
       session.endSession();
     }
   }
   
   async function generateTicketActivity(transaction_delay, max_transactions = 1000) {
     let txn_count = 0;
   
     while (txn_count < max_transactions) {
       await sellRandomTickets();
       txn_count += 1;
       await new Promise(resolve => setTimeout(resolve, transaction_delay * 1000));
     }
   }
   
   async function generateTransferActivity(transaction_delay = 5, max_transactions = 100) {
     let txn_count = 0;
     let min_tik_id, max_tik_id, tik_id, new_ticketholder, xfer_all, chg_price, new_price;
   
     while (txn_count < max_transactions) {
       const minMaxResult = await db.collection('ticketPurchaseHist').aggregate([
         {
           $group: {
             _id: null,
             min_tik_id: { $min: "$sportingEventTicketId" },
             max_tik_id: { $max: "$sportingEventTicketId" }
           }
         }
       ]).toArray();
   
       if (minMaxResult.length === 0) {
         console.log('No tickets available to transfer.');
         return;
       }
   
       min_tik_id = minMaxResult[0].min_tik_id;
       max_tik_id = minMaxResult[0].max_tik_id;
   
       const tikResult = await db.collection('ticketPurchaseHist').aggregate([
         {
           $match: {
             sportingEventTicketId: { $lte: Math.floor(Math.random() * (max_tik_id - min_tik_id + 1)) + min_tik_id }
           }
         },
         {
           $group: {
             _id: null,
             tik_id: { $max: "$sportingEventTicketId" }
           }
         }
       ]).toArray();
   
       if (tikResult.length === 0) {
         console.log('No tickets available to transfer.');
         return;
       }
   
       tik_id = tikResult[0].tik_id;
   
       const personResult = await db.collection('person').aggregate([
         {
           $group: {
             _id: null,
             min_id: { $min: "$id" },
             max_id: { $max: "$id" }
           }
         }
       ]).toArray();
   
       if (personResult.length === 0) {
         console.log('No persons available.');
         return;
       }
   
       const g_min_person_id = personResult[0].min_id;
       const g_max_person_id = personResult[0].max_id;
   
       new_ticketholder = Math.floor(Math.random() * (g_max_person_id - g_min_person_id + 1)) + g_min_person_id;
   
       xfer_all = Math.round(Math.random() * 4) < 4;
   
       chg_price = Math.round(Math.random() * 2) === 0;
       if (chg_price) {
         const priceResult = await db.collection('sportingEventTicket').findOne({ id: tik_id });
         if (priceResult) {
           new_price = Math.random() * (1.2 - 0.8) + 0.8 * priceResult.ticketPrice;
         }
       }
   
       await transferTicket(tik_id, new_ticketholder, xfer_all, new_price);
   
       txn_count++;
       await new Promise(resolve => setTimeout(resolve, transaction_delay * 1000));
     }
   }
   
   async function get_event_details(event_id) {
     const event = await db.collection('sportingEvent').aggregate([
       { $match: { id: event_id } },
       {
         $lookup: {
           from: 'sportTeam',
           localField: 'homeTeamId',
           foreignField: 'id',
           as: 'homeTeam'
         }
       },
       { $unwind: '$homeTeam' },
       {
         $lookup: {
           from: 'sportTeam',
           localField: 'awayTeamId',
           foreignField: 'id',
           as: 'awayTeam'
         }
       },
       { $unwind: '$awayTeam' },
       {
         $lookup: {
           from: 'sportLocation',
           localField: 'locationId',
           foreignField: 'id',
           as: 'location'
         }
       },
       { $unwind: '$location' },
       {
         $project: {
           sport_name: '$sportTypeName',
           home_team_name: '$homeTeam.name',
           away_team_name: '$awayTeam.name',
           home_field: '$location.name',
           date_time: '$startDateTime'
         }
       }
     ]).toArray();
   
     if (event.length === 0) {
       throw new Error('Event not found');
     }
   
     return event[0];
   }
   
   async function sellRandomTickets() {
     const eventTab = await getOpenEvents();
     const rowCt = eventTab.length;
     const eventIdx = Math.floor(Math.random() * rowCt);
     const eventId = eventTab[eventIdx].id;
     const ticketHolder = Math.floor(Math.random() * (g_max_person_id - g_min_person_id + 1)) + g_min_person_id;
     const quantity = Math.floor(Math.random() * 6) + 1;
     await sellTickets(ticketHolder, eventId, quantity);
   }
   
   async function getOpenEvents() {
     const openEvents = await db.collection('sportingEvent').find({ soldOut: 0 }).sort({ startDateTime: 1 }).toArray();
     return openEvents;
   }
   
   async function get_open_events() {
     const openEvents = await db.collection('sportingEvent').find({ soldOut: 0 }).sort({ startDateTime: 1 }).toArray();
     return openEvents;
   }
   }