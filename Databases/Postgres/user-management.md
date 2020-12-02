#   Postgres User Management

 - Watch out for quoting conventions!
    - `"foo"` is an identifier, a database, user, column, etc
    - `'bar'` is a contstant, a string or encoding type. e.g. `'UTF8'` 

- Create a user in `psql`:
  - `CREATE USER "<username>" WITH PASSWORD '<password>';`

- Create user in shell:
  - https://www.postgresql.org/docs/13/app-createuser.html 
  -  `createuser <username> -P -e`
     -  `-P` password prompt
     -  `-e` echo server commands
     -  `-s` superuser

- Create a database in `psql`:
  - `CREATE DATABASE "<database_name>" WITH OWNER "<username>" encoding 'UTF8';`

- Grant all to user 
  - `grant all privileges on database simpletag to simpletag`

- List all tables in `psql`
  - `\dt`