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
\dt # shows just the tables

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

### Create a table with constraints

```sql
CREATE TABLE person (
	id BIGSERIAL NOT NULL PRIMARY KEY, 
	first_name VARCHAR(50) NOT NULL,
	last_name VARCHAR(50) NOT NULL,
	gender VARCHAR(6) NOT NULL,
	date_of_birth DATE NOT NULL,
);

Table "public.person"
    Column     |          Type          | Collation | Nullable |              Default
---------------+------------------------+-----------+----------+------------------------------------
 id            | bigint                 |           | not null | nextval('person_id_seq'::regclass)
 first_name    | character varying(50)  |           | not null |
 last_name     | character varying(50)  |           | not null |
 gender        | character varying(7)   |           | not null |
 date_of_birth | date                   |           | not null |
 email         | character varying(150) |           |          |
Indexes:
    "person_pkey" PRIMARY KEY, btree (id)
```

### Insert data

```sql
INSERT INTO person (
first_name,
last_name,
gender,
date_of_birth)
VALUES ('Anne', 'Smith', 'FEMALE', DATE '1988-01-09');
```

### Importing data

```sql
\i filename # this will import all the data from an sql file
```
### Reading data from the table

```sql
SELECT * FROM person;
SELECT first_name FROM person;
SELECT first_name, last_name FROM person;
```

### Order the data that's returned

```sql
SELECT * FROM person ORDER BY last_name ASC;
SELECT country_of_birth FROM person ORDER BY country_of_birth DESC;
```
### Unique Values using DISTINCT

```sql
SELECT DISTINCT country_of_birth FROM person ORDER BY country_of_birth;
```

### Using the WHERE clause

```sql
SELECT * FROM person WHERE gender = 'Female';
SELECT * FROM person WHERE gender = 'Male' AND country_of_birth = 'China';
```

### Comparison Operators

```sql
> greater than
< less than
>= greater than or equal
<= less than or equal
= equal 
<> not equal
```

### Limit, Offset & Fetch

```sql
SELECT * FROM person LIMIT 10; # Limit the number of records returned
SELECT * FROM person OFFSET 10 LIMIT 10; # Offset the first 10 rows
SELECT * FROM person OFFSET 10 FETCH FIRST 10 ROW ONLY; # Using FETCH
```



## Resources
[PostgreSQL offical site](https://www.postgresql.org/)

[Learn PostgreSQL Tutorial - Full Course for Beginners](https://www.youtube.com/watch?v=qw--VYLpxG4)

### Tools
[SQLECTRON](https://sqlectron.github.io/)