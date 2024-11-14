.. list-table::
   :header-rows: 1
   :widths: 35 65

   * - Field

     - Value

   * - :guilabel:`Host`

     - The host IP or DNS name.

   * - :guilabel:`Port`

     - The port number.

   * - :guilabel:`Database`

     - The database name. Leave blank to load all databases.

   * - :guilabel:`Authentication`

     - By default, this is set to :guilabel:`SQL Server`. Set to
       :guilabel:`Windows` to enable :ref:`Windows Integrated Authentication
       <rm-sql-connection-string>`, using the credentials of the user who
       launched the Relational Migrator executable. This disables the
       :guilabel:`Username` and :guilabel:`Password` fields.

   * - :guilabel:`Username` and :guilabel:`Password`

     - The credentials to use for authentication. Disabled if
       :guilabel:`Authentication` is set to :guilabel:`Windows`.
     
       Checking :guilabel:`Save password` saves the password securely on 
       your machine. Relational Migrator automatically fills in the 
       :guilabel:`Password` field for the current project.
