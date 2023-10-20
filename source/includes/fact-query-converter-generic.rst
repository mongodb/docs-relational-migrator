- Consider SQL complexity when using query converter. The AI 
  model cannot convert highly complex SQL syntax. If your SQL 
  code isn't converting accurately, refactor it and try again.

- Query converter utilizes metadata from your relational and MongoDB 
  connections for syntax conversion. For optimal results, use queries 
  aligned with your project's relational database schema.

- Converted queries, views, and stored procedures are saved in your 
  project and persist through project import and exports.

- Conversions are limited to 10,000 text characters.