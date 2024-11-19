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

     - The database name. If blank, you will only see objects in the default
       ``dbo`` schema in all databases.

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

   * - :guilabel:`General / SSL` toggle

     - SSL settings for the connection. Use the :guilabel:`Use SSL` to enable
       or disable SSL. With SSL enabled, check :guilabel:`Trust server
       certificate` to trust the stored certificate.

   * - :guilabel:`General / SSL` toggle

     - View SSL settings for the connection. 
     
   * - SSL: :guilabel:`Use SSL`
   
     - Enable or disable SSL.
       
   * - SSL: :guilabel:`Trust server certificate`
   
     - With SSL enabled, check this to trust the stored certificate. Leave
       unchecked to verify the server certificate against a trusted
       Certificate Authority.
