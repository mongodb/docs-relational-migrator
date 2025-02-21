To perform a migration with Relational Migrator, you must connect using a service 
account with the appropriate permissions. The required permissions
depend on the migration type:

- Snapshot migration jobs migrate all data once, and then stop.
- Continuous migration jobs run a snapshot migration and then enter a CDC stage, 
  which continuously replicates data changes.

For more information on supported migration types for |db-type|, see :ref:`<rm-db-migration-compatibility>`.