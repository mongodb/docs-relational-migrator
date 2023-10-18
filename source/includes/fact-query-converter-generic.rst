- There are complexity limits to consider when using query converter. 
  The AI model cannot handle overly complex SQL syntax. If your SQL syntax
  is not being converted accurately, consider refactoring the SQL code.

- Relational Migrator uses metadata from your relational and MongoDB 
  connections to help convert syntax. For best results, use queries that 
  are based on the schema of your project's relational database 
  connection.

- Converted queries, views, and stored procedures are saved in your 
  project and persist through project import and exports.

- Conversions are limited to 10,000 characters.