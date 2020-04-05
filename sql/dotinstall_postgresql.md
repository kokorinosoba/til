# PostgreSQL
## About
- Database system
- Open source
- High functioning

## Terms
- Database
  - Table
    - Column(Field)
    - Row(Record, Tuple)


# PostgreSQL Installation Message

```
==> postgresql
To migrate existing data from a previous major version of PostgreSQL run:
  brew postgresql-upgrade-database

To have launchd start postgresql now and restart at login:
  brew services start postgresql
Or, if you don't want/need a background service you can just run:
  pg_ctl -D /usr/local/var/postgres start
```

# PostgreSQL Starting / Stopping

```sh
pg_ctl -D /usr/local/var/postgres start
pg_ctl -D /usr/local/var/postgres stop
```

# Database Operation

```sh
psql
psql -l # List of Database
createdb [DB name] # Create DB
dropdb [DB name] # Remove DB
psql [DB name] # Connect to DB
```

```SQL
help # Display help
\? # List of commands
\l # List of DB
\q # Quit
```

SQL Sentence separator: ;(semi-colon)

# Table Operation

```SQL
create table [Table name] (title [Data type], body [Data type])
create table posts (title varchar(255), body text);

\dt # Show Data Table
\d [table name] # Show column names

alter table posts rename to myposts; # rename table
drop table myposts; # remove table

\i [file name] # Read external sql file
```
