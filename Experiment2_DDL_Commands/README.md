# Experiment 2: DDL Commands
### YUVAN SUNDAR S
### 212223040250
## AIM
To study and implement DDL commands and different types of constraints.

## THEORY:
### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 

```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;
ALTER TABLE Companies ADD COLUMN mobilenumber number;
ALTER TABLE Companies ADD COLUMN DOB Date ;
```

**Output:**
<img width="1307" height="365" alt="image" src="https://github.com/user-attachments/assets/41e7288b-4f75-4256-a133-ec96840ba232" />


**Question 2**
---
Create a table named ProjectAssignments with the following constraints:
- AssignmentID as INTEGER should be the primary key.
- EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
- ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
- AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER, 
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**
<img width="1807" height="297" alt="image" src="https://github.com/user-attachments/assets/7e909ad3-d3b5-4b62-83f8-aefa4989034d" />


**Question 3**
---
Create a table named Events with the following columns:
- EventID as INTEGER
- EventName as TEXT
- EventDate as DATE

```sql
CREATE TABLE Events (
    EventID INTEGER,
    EventName TEXT,
    EventDate DATE
);
```

**Output:**
<img width="1774" height="399" alt="image" src="https://github.com/user-attachments/assets/86674f68-67cc-42e5-9bb1-71ef34cd7649" />


**Question 4**
---
Create a new table named item with the following specifications and constraints:
- item_id as TEXT and as primary key.
- item_desc as TEXT.
- rate as INTEGER.
- icom_id as TEXT with a length of 4.
- icom_id is a foreign key referencing com_id in the company table.
- The foreign key should set NULL on updates and deletes.
- item_desc and rate should not accept NULL.

```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT,
    rate INTEGER,
    icom_id TEXT(4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE SET NULL ON DELETE SET NULL
);
```

**Output:**
<img width="1238" height="300" alt="image" src="https://github.com/user-attachments/assets/3787dde2-486d-4504-a073-267d8b6ca820" />


**Question 5**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

| RollNo | Name           | Gender | Subject     | MARKS |
| ------ | -------------- | ------ | ----------- | ----- |
| 205    | Olivia Green   | F      |             |       |
| 207    | Liam Smith     | M      | Mathematics | 85    |
| 208    | Sophia Johnson | F      | Science     |       |


```sql
INSERT INTO Student_details(RollNo, Name, Gender ) VALUES(205,'Olivia Green','F');
INSERT INTO Student_details(RollNo, Name,Gender ,Subject, MARKS) VALUES(207,'Liam Smith','M','Mathematics',85);
INSERT INTO Student_details(RollNo, Name,Gender ,Subject) VALUES(208,'Sophia Johnson','F','Science');
```

**Output:**
<img width="1260" height="271" alt="image" src="https://github.com/user-attachments/assets/f459449f-4e39-4ea0-a068-e31b60cb1cb5" />


**Question 6**
---
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary) VALUES(001,'Sarah Parker','Manager','HR',60000);
```

**Output:**
<img width="1281" height="219" alt="image" src="https://github.com/user-attachments/assets/c309af4d-2fa6-412e-9a84-c686786287c4" />

**Question 7**
---
Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.


```sql
ALTER TABLE Employees ADD COLUMN salary INTEGER CHECK(salary>0);
```

**Output:**
<img width="1283" height="161" alt="image" src="https://github.com/user-attachments/assets/ceac1e0a-5d44-4ca0-96cc-17ad8b2203fa" />


**Question 8**
---
Create a table named Products with the following constraints:

- ProductID should be the primary key.
- ProductName should be NOT NULL.
- Price is of real datatype and should be greater than 0.
- Stock is of integer datatype and should be greater than or equal to 0.e

```sql
CREATE TABLE Products(
    productID INTEGER PRIMARY KEY,
    ProductName TEXT NOT NULL,
    Price REAL CHECK(Price>0),
    Stock INTEGER CHECK(Stock>=0)
);
```
**Output:**
<img width="1023" height="128" alt="image" src="https://github.com/user-attachments/assets/be362edf-e00a-441f-abac-bac65f00f490" />


**Question 9**
---
Create a table named Products with the following constraints:
- ProductID as INTEGER should be the primary key.
- ProductName as TEXT should be unique and not NULL.
- Price as REAL should be greater than 0.
- StockQuantity as INTEGER should be non-negative.

```sql
CREATE TABLE Products(
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT NOT NULL UNIQUE,
    Price REAL CHECK(Price>0),
    StockQuantity INTEGER CHECK(StockQuantity>=0)
);

```

**Output:**
<img width="1873" height="270" alt="image" src="https://github.com/user-attachments/assets/31882f5c-f4aa-4eb1-91ad-5db64207fb5f" />


**Question 10**
---
Insert all students from Archived_students table into the Student_details table.

| cid | name    | type         | notnull | dflt_value | pk |
| --- | ------- | ------------ | ------- | ---------- | -- |
| 0   | RollNo  | INT          | 0       |            | 1  |
| 1   | Name    | VARCHAR(100) | 0       |            | 0  |
| 2   | Gender  | VARCHAR(10)  | 0       |            | 0  |
| 3   | Subject | VARCHAR(50)  | 0       |            | 0  |
| 4   | MARKS   | INT          | 0       |            | 0  |


```sql

INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
SELECT RollNo,Name,Gender,Subject,MARKS
FROM Archived_students;
```

**Output:**

<img width="1289" height="277" alt="image" src="https://github.com/user-attachments/assets/da86073a-dbb3-439c-a402-6fd9fd9bd495" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
