.. short version of the steps under source/database-connections/save-mongodb-connection.txt, used within other procedures like migration job creation.

a. Enter your connection information.

   If you are using MongoDB Atlas, you can select your Atlas cluster 
   from the :guilabel:`Select a cluster` list, or you can enter the
   :ref:`MongoDB connection string <rm-mongodb-database-connection-strings>`.

   If you are using an on-premises deployment, you must use the MongoDB
   connection string.

   .. tabs::

      .. tab:: Select a cluster
         :tabid: select-atlas-cluster

         a. Select the cluster.

         #. If it isn't included in the connection string, enter the
            :guilabel:`Database` to connect to.
         
         #. If they aren't included in the connection string, enter the 
            :guilabel:`Username` and :guilabel:`Password` of your
            :ref:`Relational Migrator MongoDB user <rm-mongodb-service-user>`.

      .. tab:: Enter MongoDB URI
         :tabid: enter-mongodb-uri

         a. In the :guilabel:`MongoDB connection string (URI)` field, input
            your :manual:`MongoDB URI <mongodb-uri>`.

         #. If it isn't included in the connection string, enter the
            :guilabel:`Database` to connect to.
         
         #. If they aren't included in the connection string, enter the 
            :guilabel:`Username` and :guilabel:`Password` of your
            :ref:`Relational Migrator MongoDB user <rm-mongodb-service-user>`.

#. Specify a :guilabel:`Connection name` and optional :guilabel:`Environment tag`.

#. (Optional) Click :guilabel:`Test connection` to confirm that Relational Migrator can establish a connection.