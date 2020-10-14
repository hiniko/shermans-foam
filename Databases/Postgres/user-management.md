# Postgres User Management

 - Watch out for quoting conventions!
    - `"foo"` is an identifier, a database, user, column, etc
    - `'bar'` is a contstant, a string or encoding type. e.g. `'UTF8'` 

- Create a user:
  - `CREATE USER "<username>" WITH PASSWORD '<password>';`

- Create a database:
    - `CREATE DATABASE "<database_name>" WITH OWNER "<username>" encoding 'UTF8';`

