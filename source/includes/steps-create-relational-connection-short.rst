.. This is a streamlined version of the content in database-connections/save-relational-connection.txt, for use as an include in larger procedures.

.. tabs::

   .. tab:: Oracle
      :tabid: db-oracle

      .. procedure::

         .. step:: To use a saved :ref:`connection string <rm-connection-strings>` or input one directly:
   
            a. Above the :guilabel:`JDBC URI` field, enable the
               :guilabel:`Enter URI manually` toggle.

            #. Paste your connection string into the ``JDBC URI`` field.

         .. step:: If you don't have a connection string, create it by entering the following information:

            .. include:: /includes/table-oracle-connection-fields.rst

         .. step:: Enter connection credentials.
            
            Enter the :guilabel:`Username` and :guilabel:`Password` to use for 
            authentication, and optionally check :guilabel:`Save password`.

         .. step:: Specify a :guilabel:`Connection name` and optionally an :guilabel:`Environment tag`.
               
         .. step:: Click :guilabel:`Save`.


   .. tab:: SQL Server
      :tabid: db-sql

      .. procedure::

         .. step:: To use a saved connection string, enable the :guilabel:`Enter URI manually` toggle and paste the string into the :guilabel:`JDBC URI` field.

         .. step:: If you don't have a connection string, create it by entering the following information:

            .. include:: /includes/table-sql-connection-fields.rst

         .. step:: Enter connection credentials.
            
            Enter the :guilabel:`Username` and :guilabel:`Password` to use for 
            authentication, and optionally check :guilabel:`Save password`.

         .. step:: To connect using SSL:
            
            a. Toggle from :guilabel:`General` to :guilabel:`SSL`.
            
            #. Select an SSL mode.

         .. step:: Specify a :guilabel:`Connection name` and optionally an :guilabel:`Environment tag`.
               
         .. step:: Click :guilabel:`Save`.

   .. tab:: MySQL
      :tabid: db-mysql

      .. procedure::

         .. step:: To use a saved connection string, enable the :guilabel:`Enter URI manually` toggle and paste the string into the :guilabel:`JDBC URI` field.

         .. step:: If you don't have a connection string, create it by entering the following information:

            .. include:: /includes/table-mysql-connection-fields.rst

         .. step:: Enter connection credentials.
            
            Enter the :guilabel:`Username` and :guilabel:`Password` to use for 
            authentication, and optionally check :guilabel:`Save password`.

         .. step:: To connect using SSL:
            
            a. Toggle from :guilabel:`General` to :guilabel:`SSL`.
            
            #. Select an SSL mode.

         .. step:: Specify a :guilabel:`Connection name` and optionally an :guilabel:`Environment tag`.
               
         .. step:: Click :guilabel:`Save`.

   .. tab:: PostgreSQL
      :tabid: db-postgresql

      .. procedure::

         .. step:: To use a saved connection string, enable the :guilabel:`Enter URI manually` toggle and paste the string into the :guilabel:`JDBC URI` field.

         .. step:: If you don't have a connection string, create it by entering the following information:

            .. include:: /includes/table-postgresql-connection-fields.rst

         .. step:: Enter connection credentials.
            
            Enter the :guilabel:`Username` and :guilabel:`Password` to use for 
            authentication, and optionally check :guilabel:`Save password`.

         .. step:: To connect using SSL:
            
            a. Toggle from :guilabel:`General` to :guilabel:`SSL`.
            
            #. Select an SSL mode.

         .. step:: Specify a :guilabel:`Connection name` and optionally an :guilabel:`Environment tag`.
               
         .. step:: Click :guilabel:`Save`.

   .. tab:: Db2
      :tabid: db-db2

      .. procedure::

         .. step:: To use a saved connection string, enable the :guilabel:`Enter URI manually` toggle and paste the string into the :guilabel:`JDBC URI` field.

         .. step:: If you don't have a connection string, create it by entering the following information:

            .. include:: /includes/table-db2-connection-fields.rst

         .. step:: Enter connection credentials.
            
            Enter the :guilabel:`Username` and :guilabel:`Password` to use for 
            authentication, and optionally check :guilabel:`Save password`.

         .. step:: Specify a :guilabel:`Connection name` and optionally an :guilabel:`Environment tag`.
               
         .. step:: Click :guilabel:`Save`.

   .. tab:: Sybase
      :tabid: db-sybase

      .. procedure::

         .. step:: To use a saved connection string, enable the :guilabel:`Enter URI manually` toggle and paste the string into the :guilabel:`JDBC URI` field.

         .. step:: If you don't have a connection string, create it by entering the following information:

            .. include:: /includes/table-sybase-connection-fields.rst

         .. step:: Enter connection credentials.
            
            Enter the :guilabel:`Username` and :guilabel:`Password` to use for 
            authentication, and optionally check :guilabel:`Save password`.

         .. step:: Specify a :guilabel:`Connection name` and optionally an :guilabel:`Environment tag`.
               
         .. step:: Click :guilabel:`Save`.