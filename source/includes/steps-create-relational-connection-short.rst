.. short version of the steps under source/database-connections/save-relational-connection.txt, used within other procedures.

.. step:: To input a :ref:`connection string <rm-connection-strings>` directly, enable the :guilabel:`Enter URI manually` toggle and paste your connection string into the :guilabel:`JDBC URI` field.

.. step:: To create a connection string by entering database information, input the following:

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

.. step:: Enter the :guilabel:`Username` and :guilabel:`Password` to use for authentication.

.. step:: Optionally, if you are connecting to a SQL, MySQL, or PostgreSQL server, you can toggle from :guilabel:`General` to :guilabel:`SSL` to connect using SSL.

.. step:: Specify a :guilabel:`Connection name` and optionally an :guilabel:`Environment tag`.

.. step:: Optionally, click :guilabel:`Test connection` to confirm that Relational Migrator can establish a connection.
      
.. step:: Click :guilabel:`Save`.