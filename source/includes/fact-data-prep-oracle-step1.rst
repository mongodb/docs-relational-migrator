The following code creates a new Oracle service account 
for Relational Migrator to connect to the Oracle 
instance. Alternatively, you can use an existing Oracle 
service account to connect to Relational Migrator with 
the appropriate permissions.

a. Create a service account:

   .. code-block:: sql
      :copyable: true

      CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';

#. Grant the required permissions to the service account:

   .. code-block:: sql
      :copyable: true

      GRANT CREATE SESSION TO user;
      GRANT SELECT_CATALOG_ROLE TO user;
      GRANT SELECT ANY TABLE TO user;
      GRANT SELECT ON V$DATABASE TO user;