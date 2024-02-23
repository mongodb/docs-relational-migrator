The following code creates a new Oracle service account 
for Relational Migrator to connect to the Oracle 
instance. Alternatively, you can use an existing Oracle 
service account to connect to Relational Migrator with 
the appropriate permissions.

a. Create a service account:

   .. code-block:: sql
      :copyable: true

      CREATE USER '<user>'@'localhost' IDENTIFIED BY '<password>';

#. Grant select permissions to the service account:

   If the service account *is* the table owner:

   .. code-block:: sql
      :copyable: true

      GRANT CREATE SESSION TO <user>;
      GRANT SELECT ON V_$DATABASE TO <user>;
      GRANT FLASHBACK ON <table> TO user;

   .. note:

      The service account only needs these permissions *if it is 
      not* the table owner. To check table ownership you can run the 
      following query:

      .. code-block:: sql
         :copyable: true

         SELECT TABLE_NAME, OWNER 
         FROM ALL_TABLES 
         WHERE TABLE_NAME ='<table_name>'
         ORDER BY OWNER, TABLE_NAME;

   If the service account *is not* the table owner:

   .. code-block:: sql
      :copyable: true

      GRANT CREATE SESSION TO <user>;
      GRANT SELECT_CATALOG_ROLE TO <user>;
      GRANT SELECT ANY TABLE TO <user>;
      GRANT SELECT ON V_$DATABASE TO <user>;
      GRANT FLASHBACK ON <table> TO user;
      