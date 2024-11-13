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

         On the :guilabel:`Connect Destination DB` form, select an
         :guilabel:`Atlas Cluster` from the drop-down. 
         
         Clusters are displayed in a three-level hierarchy: 
         :guilabel:`Organization` > :guilabel:`Project` >
         :guilabel:`Cluster`, organized alphabetically. Only the first 100
         clusters you are authorized to access are shown.

         If you leave any of the form fields for :guilabel:`Database`,
         :guilabel:`Username`, or :guilabel:`Password` blank, Relational
         Migrator uses the values from the Atlas cluster metadata.

      .. tab:: Enter MongoDB URI
         :tabid: enter-mongodb-uri

         a. In the :guilabel:`MongoDB connection string (URI)` field, input
            your :manual:`MongoDB URI <mongodb-uri>`.

         #. (Optional) In the :guilabel:`Database` field, enter the name of
            the database to connect to.
         
         #. If they aren't included in the connection string, enter the 
            :guilabel:`Username` and :guilabel:`Password` to use for
            authentication.
            
            Checking :guilabel:`Save password` saves your password securely
            on your machine. Relational Migrator automatically fills in the 
            :guilabel:`Password` field on future uses.

#. Specify a :guilabel:`Connection name` and optional :guilabel:`Environment tag`.

#. (Optional) Click :guilabel:`Test connection` to confirm that Relational Migrator can establish a connection.
      
#. Click :guilabel:`Save`.