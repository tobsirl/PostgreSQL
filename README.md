# PostgreSQL
PostgreSQL  Tutorial 

## Useful Commands

```bash
psql -U postgres
```

### Create Database

```bash
CREATE DATABASE <database name>;
```

### Connect to a database

```bash
psql -h localhost -p 5432 -U postgres <database name>

\l # list the databases
\c # connect to the database
```
### Delete a database

```bash
# Danger this will detele everything about the database transactions and data
DROP DATABASE database_name;
```

### How to create a table with Postgres

```bash
CREATE TABLE table_name (
	column name + data type + constraints if any
)
```

```sql
CREATE TABLE person {
	id int,
	first_name VARCHAR(50),
	last_name VARCHAR(50),
	gender VARCHAR(6),
	date_of_birth TIMESTAMP,
}
```

### How to view a table

```sql
\d # describe
List of relations
 Schema |  Name  | Type  |  Owner
--------+--------+-------+----------
 public | person | table | postgres
(1 row)

\d person # describe with the table name
Table "public.person"
    Column     |         Type          | Collation | Nullable | Default
---------------+-----------------------+-----------+----------+---------
 id            | integer               |           |          |
 first_name    | character varying(50) |           |          |
 last_name     | character varying(50) |           |          |
 gender        | character varying(7)  |           |          |
 date_of_birth | date                  |           |          |
```
## Resources
[PostgreSQL offical site](https://www.postgresql.org/)

[Learn PostgreSQL Tutorial - Full Course for Beginners](https://www.youtube.com/watch?v=qw--VYLpxG4)

### Tools
[SQLECTRON](https://sqlectron.github.io/)