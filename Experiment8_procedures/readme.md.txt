# Experiment 8: PL/SQL Cursor Programs

## AIM
To understand the concept of cursors in PL/SQL and implement different types of cursors.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. There are two types of cursors:

Implicit Cursors: Automatically created by PL/SQL for single-row queries.

Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:

DECLARE: Section to declare variables and constants.

BEGIN: The execution section that contains PL/SQL statements.

EXCEPTION: Handles errors or exceptions that occur in the program.

END: Marks the end of the PL/SQL block.

## Program 1: Write a PL/SQL program using a simple cursor to display all employee names and their designations from the employees table.

```sql
--paste your answer
```

Expected Output


## Program 2: Create a parameterized cursor to display employees whose salary is between a given minimum and maximum. Use parameters to pass the salary range.


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
