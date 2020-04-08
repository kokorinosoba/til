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

# SQL Statements
## Data Types

```
/* Comment
  Data Types
  Integer: integer(int), real, serial(continuous number)
  Character:  char(5), varchar(255), text
  Boolean: boolean TRUE FALSE t f
  Date: date, time, timestamp
*/
```

## Create Table Statement

```SQL
create table posts (
  id serial primary key,
  title varchar(255) not null,
  body text check(length(body) > 5),
  is_draft boolean default TRUE,
  created timestamp default 'now'
);
```

## Data Restriction

```SQL
not null # Error if null
unique # not allowed
check # check content
default
primary key # (not null, unique)
```

## Insert Statement

```SQL
insert into posts (title, body) values ('title1', 'body1');
select * from posts; # Show all records
insert into posts (title, body) values ('title2', 'body2');
insert into posts (title, body) values ('title2', 'b3'); # Error
```

## Select Statement

Table Preparation
```SQL
create table users (
  id serial primary key,
  name varchar(255),
  score real,
  team varchar(255)
);

insert into users (name, score, team) values
  ('taguchi', 5.5, 'red'),
  ('fkoji', 8.3, 'blue'),
  ('dotinstall', 2.2, 'blue'),
  ('sakaki', 5.0, 'green'),
  ('sakaki', 4.6, 'red'),
  ('kimura', 4.7, 'green');
```

### Select Statement with Columns

```SQL
select * from users;
\x # Turn on expanded Display
select name, score from users; # indicate column
```

### Conditional Select Statement

```SQL
select * from users where score > 4.0; # Show field by condition
select * from users where score = 5.0;
select * from users where score != 5.0;
```

### Character Treatment in Select Statement

```SQL
# like operator
# %: Arbitary characters
# _: An arbitary character
select * from users where name like '%i';
select * from users where name like 'sa_aki';
```

### Record Sorting by Select Statement

```SQL
select * from users order by score; # ascend
select * from users order by score desc; # descend
select * from users order by team; # Avairable for string
select * from users order by team, score desc;
```

### Limit Number of Records

```SQL
select * from users limit 3;
select * from users limit 3 offset 3;
select * from users order by score desc limit 3;
```

### Count / Sum up Records

```SQL
select count(*) from users; # Number of records
select distinct team from users; # uniq
select sum(score) from users;
select max(score)
select min()
select avg()
select team, sum(score) from users group by team; # Grouping with team
select team, sum(score) from users group by team having sum(score) > 10.0; # Condition specification after selecting
```

### PostgreSQL Functions

Homepage > docs > Functions and Operators

```SQL
select name, length(name) from users;
select concat(name, ' (', team, ')') from users;
select concat(name, ' (', team, ')') as namelabel from users; # Change name label
select substring(team, 1, 1) as teaminitial from users;
select random();
select * from users order by random() limit 1;
```

## Records Update / Delete

```SQL
update users set score = 5.8 where name = 'taguchi';
select * from users;
update users set score = score + 1 where team = 'red';
update users set score = score + 1 where team = 'red' or team = 'green';

delete from users where score < 3.0;
```

## Change Table Structure

```SQL
\d users
alter table users add fullname varchar(255);
alter table users drop fullname

alter table users rename rename name to myname;
alter table users alter myname type varchar(32);

create index team_index on users(team);
drop index team_index;
```

## Concat Multiple Tables

Table Creation
```SQL
create table users (
  id serial primary key,
  name varchar(255),
  score real,
  team varchar(255)
);

insert into users (name, score, team) values
  ('taguchi', 5.5, 'red'),
  ('fkoji', 8.3, 'blue'),
  ('dotinstall', 2.2, 'blue'),
  ('sakaki', 5.0, 'green'),
  ('sakaki', 4.6, 'red'),
  ('kimura', 4.7, 'green');

create table posts (
  id serial primary key,
  user_id int not null,
  title varchar(255) not null,
  body text not null
);

insert into posts (user_id, title, body) values
  (1, 'title1', 'body1'),
  (1, 'title2', 'body2'),
  (2, 'title3', 'body3'),
  (5, 'title4', 'body4'),
  (4, 'title5', 'body5');
```

```SQL
select users.name, posts.title from users, posts where users.id = posts.user_id; # Concat tables
select u.name, p.title from users u, posts p where u.id = p.user_id;
select u.name, p.title from users u, posts p where u.id = p.user_id and u.id = 1;
```

## View

```SQL
create view taguchi_posts as # View making
select u.name, p.title from users u, posts p where u.id = p.user_id and u.id = 1;
\dv

select * from taguchi_posts;
drop view taguchi_posts;
```

## Transaction

```SQL
begin;
update users set score = score - 1.0 where name = 'taguchi';
update users set score = score + 1.0 where name = 'fkoji';
commit;

rollback; # Undo transaction
```
