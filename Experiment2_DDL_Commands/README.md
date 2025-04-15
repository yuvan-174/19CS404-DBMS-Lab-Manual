# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
Aim
To study and implement DDL commands and different types of constraints.
Theory
DDL Commands

CREATE

Used to create a new relation (table)
Syntax: CREATE TABLE table_name (field_1 data_type(size), field_2 data_type(size), ...);


ALTER

Used to modify an existing table structure
Types:

ALTER TABLE...ADD...: Adds new columns
ALTER TABLE...MODIFY...: Changes data type/size
ALTER TABLE...DROP...: Removes columns
ALTER TABLE...RENAME...: Renames columns




DROP TABLE

Permanently deletes the structure and records of a relation
Syntax: DROP TABLE relation_name;


RENAME

Modifies the name of an existing database object
Syntax: RENAME TABLE old_relation_name TO new_relation_name;



Constraints

NOT NULL

Makes a column mandatory
Syntax: CREATE TABLE Table_Name (column_name data_type(size) NOT NULL, ...);


UNIQUE

Ensures values in the column are unique
Syntax: CREATE TABLE Table_Name (column_name data_type(size) UNIQUE, ...);


CHECK

Specifies a condition each row must satisfy
Syntax: CREATE TABLE Table_Name (column_name data_type(size) CHECK(logical expression), ...);


PRIMARY KEY

Identifies records uniquely
Cannot be null and must contain unique values
Syntax: CREATE TABLE Table_Name (column_name data_type(size) PRIMARY KEY, ...);


FOREIGN KEY

References a primary key from another table
Creates relationships between tables
Syntax: CREATE TABLE Table_Name (column_name data_type(size) FOREIGN KEY(column_name) REFERENCES table_name);


DEFAULT

Inserts a default value into a column when no value is specified
Syntax: CREATE TABLE Table_Name (col_name1, col_name2, col_name3 DEFAULT '');

RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
