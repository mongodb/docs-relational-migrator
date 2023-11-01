- Consider SQL complexity when using the query converter. The query 
  converter cannot convert highly complex SQL syntax. If your SQL 
  code isn't converting accurately, refactor it and try again.

- The query converter uses metadata from both your relational and 
  MongoDB connections for syntax conversion. For best results, 
  use SQL queries referencing your project's relational database 
  schema, tables, and columns.

- Converted queries, views, and stored procedures are saved in your 
  project and persist through project import and exports.

- SQL queries are limited to 10,000 text characters.