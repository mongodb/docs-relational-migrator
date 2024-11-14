.. short version of the steps under source/database-connections/save-relational-connection.txt, used within other procedures like migration job creation.

a. In the :guilabel:`Database type` drop-down, select the database type.

#. To input a :ref:`connection string <rm-connection-strings>` directly, enable the :guilabel:`Enter URI manually` toggle and paste your connection string into the :guilabel:`JDBC URI` field.

#. To create a connection string by entering database information: 

   a. Input the following:

      .. tabs::

         .. tab:: Oracle
            :tabid: db-oracle

            .. include:: /includes/table-oracle-connection-fields.rst

         .. tab:: SQL Server
            :tabid: db-sql

            .. include:: /includes/table-sql-connection-fields.rst

         .. tab:: MySQL
            :tabid: db-mysql

            .. include:: /includes/table-mysql-connection-fields.rst
            
         .. tab:: PostgreSQL
            :tabid: db-postgresql

            .. include:: /includes/table-postgresql-connection-fields.rst

         .. tab:: Db2
            :tabid: db-db2

            .. include:: /includes/table-db2-connection-fields.rst

         .. tab:: Sybase
            :tabid: db-sybase

            .. include:: /includes/table-sybase-connection-fields.rst

   #. Enter the :guilabel:`Username` and :guilabel:`Password` to use for authentication.

#. (Optional) If you are connecting to a SQL, MySQL, or PostgreSQL server, you can toggle from :guilabel:`General` to :guilabel:`SSL` to connect using SSL.

#. Specify a :guilabel:`Connection name` and optional :guilabel:`Environment tag`.

#. (Optional) Click :guilabel:`Test connection` to confirm that Relational Migrator can establish a connection.
      
#. Click :guilabel:`Save`.