.. short version of the steps under source/database-connections/save-mongodb-connection.txt, used within other procedures like migration job creation.

a. Enter the MongoDB connection string.

   a. In the :guilabel:`MongoDB connection string (URI)` field, input
      your :manual:`MongoDB URI <mongodb-uri>`.

   #. If it isn't included in the connection string, enter the
      :guilabel:`Database` to connect to.
   
   #. If they aren't included in the connection string, enter the 
      :guilabel:`Username` and :guilabel:`Password` of your
      :ref:`Relational Migrator MongoDB user <rm-mongodb-service-user>`.

#. Specify a :guilabel:`Connection name` and optional :guilabel:`Environment tag`.

#. (Optional) Click :guilabel:`Test connection` to confirm that Relational
   Migrator can establish a connection.

#. Click :guilabel:`Connect`.
      
   The saved connection becomes available for use in all jobs and projects.