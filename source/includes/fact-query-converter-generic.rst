- Consider SQL complexity when using the query converter. The query 
  converter cannot convert highly complex SQL syntax. If your SQL 
  code isn't converting accurately, refactor it and try again.

- The query converter uses the relational schema, the MongoDB schema,  
  and the mapping rules in your current project to determine how the 
  queries should be converted. Conversions may fail or be incorrect if 
  the queries reference tables that are not in your relational schema
  or if they are not mapped to MongoDB collections.

- Converted queries, views, and stored procedures are saved in your 
  project and persist through project import and exports.

- SQL queries are limited to 10,000 text characters.