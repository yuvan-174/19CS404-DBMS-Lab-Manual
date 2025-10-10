# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
----------
**Question 1**
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

| name         | type            |
| ------------ | --------------- |
| product_id   | INT PRIMARY KEY |
| product_name | VARCHAR(10)     |
| category     | VARCHAR(50)     |
| cost_price   | DECIMAL(10)     |
| sell_price   | DECIMAL(10)     |
| reorder_lv   | INT             |
| quantity     | INT             |
| supplier_id  | INT             |


```sql
UPDATE Products
SET sell_price = sell_price * 1.15
WHERE quantity < 50 AND supplier_id =10;
```

**Output:**

<img width="1748" height="392" alt="image" src="https://github.com/user-attachments/assets/0e9cba11-3c95-4a00-b86d-4502922b2896" />

---------------
**Question 2**
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 
| name           | type         |
| -------------- | ------------ |
| supplier_id    | INT          |
| supplier_name  | VARCHAR(100) |
| contact_person | VARCHAR(100) |
| phone_number   | VARCHAR(20)  |
| email          | VARCHAR(100) |
| address        | VARCHAR(250) |


```sql
UPDATE Suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id= 5;
```

**Output:**
<img width="1699" height="424" alt="image" src="https://github.com/user-attachments/assets/83419dd1-1fad-46b0-8f7d-4866c5010d15" />

------------
**Question 3**
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

Employees table
|--------------|
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE Employees
SET email = 'not available' , commission_pct = 0.55
WHERE department_id = 110;
```

**Output:**
<img width="1560" height="489" alt="image" src="https://github.com/user-attachments/assets/9ae73002-8225-40e0-b14d-fc5c72f8e2d6" />

------------
**Question 4**
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table
|-------------|
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE Products 
SET quantity = quantity*1.10;
```

**Output:**
<img width="1560" height="489" alt="Screenshot 2025-10-10 112419" src="https://github.com/user-attachments/assets/a9f13e62-6a36-474d-bf76-00547c8fac74" />

-----------
**Question 5**
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

Sample table: Customer

| CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT | OUTSTANDING_AMT | PHONE_NO | AGENT_CODE |
| --------- | --------- | --------- | ------------ | ------------ | ----- | ----------- | ----------- | ----------- | --------------- | -------- | ---------- |
| C00013    | Holmes    | London    | London       | UK           | 2     | 6000.00     | 5000.00     | 7000.00     | 4000.00         | BBBBBBB  | A003       |
| C00001    | Micheal   | New York  | New York     | USA          | 2     | 3000.00     | 5000.00     | 2000.00     | 6000.00         | CCCCCCC  | A008       |
| C00020    | Albert    | New York  | New York     | USA          | 3     | 5000.00     | 7000.00     | 6000.00     | 6000.00         | BBBBSBB  | A008       |




```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN ('India','USA');
```

**Output:**
<img width="1364" height="245" alt="image" src="https://github.com/user-attachments/assets/cfdf4687-2e0f-429c-aa82-7525e5dfb2cf" />

--------
**Question 6**
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors
WHERE doctor_id = 1;
```

**Output:**
<img width="1419" height="344" alt="image" src="https://github.com/user-attachments/assets/9eeccd0a-1c7d-4aba-8e70-77536a12a8bf" />

--------
**Question 7**
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

Sample table: Customer

| **CUST_CODE** | **CUST_NAME** | **CUST_CITY** | **WORKING_AREA** | **CUST_COUNTRY** | **GRADE** | **OPENING_AMT** | **RECEIVE_AMT** | **PAYMENT_AMT** | **OUTSTANDING_AMT** | **PHONE_NO** | **AGENT_CODE** |
| ------------- | ------------- | ------------- | ---------------- | ---------------- | --------- | --------------- | --------------- | --------------- | ------------------- | ------------ | -------------- |
| C00013        | Holmes        | London        | London           | UK               | 2         | 6000.00         | 5000.00         | 7000.00         | 4000.00             | BBBBBBB      | A003           |
| C00001        | Micheal       | New York      | New York         | USA              | 2         | 3000.00         | 5000.00         | 2000.00         | 6000.00             | CCCCCCC      | A008           |
| C00020        | Albert        | New York      | New York         | USA              | 3         | 5000.00         | 7000.00         | 6000.00         | 6000.00             | BBBBSBB      | A008           |




```sql
DELETE FROM Customer 
WHERE GRADE = 3 AND CUST_NAME LIKE '%BBB%' AND PAYMENT_AMT>2000;
```

**Output:**
<img width="1878" height="303" alt="image" src="https://github.com/user-attachments/assets/74613f4e-3839-48eb-98a7-36191f22a77e" />

----
**Question 8**
   Write a SQL query to locate the details of customers with grade values above 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

| **customer_id** | **cust_name** | **city**   | **grade** | **salesman_id** |
| --------------- | ------------- | ---------- | --------- | --------------- |
| 3002            | Nick Rimando  | New York   | 100       | 5001            |
| 3007            | Brad Davis    | New York   | 200       | 5001            |
| 3005            | Graham Zusi   | California | 200       | 5002            |


```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer 
WHERE grade >100;

```

**Output:**

<img width="928" height="342" alt="image" src="https://github.com/user-attachments/assets/6cff9fda-adbb-4717-861e-b412235ecafe" />

------
**Question 9**
Write a SQL query to Select all patients whose name starts with A.

Table: Patients
| **name**       | **type**    |
| -------------- | ----------- |
| patient_id     | INT         |
| first_name     | VARCHAR(50) |
| last_name      | VARCHAR(50) |
| date_of_birth  | DATE        |
| admission_date | DATE        |
| discharge_date | DATE        |
| doctor_id      | INT         |


```sql
SELECT * FROM Patients
WHERE first_name LIKE 'A%';
```

**Output:**
<img width="1737" height="384" alt="image" src="https://github.com/user-attachments/assets/ee49d81d-ac0c-49d8-85bf-8ee5cb5b64c0" />

-----
**Question 10**
Write a SQL query to label rows in the Calculations table as 'Even' if value1 is even, otherwise 'Odd'.

| **cid** | **name** | **type** | **notnull** | **dflt_value** | **pk** |
| ------- | -------- | -------- | ----------- | -------------- | ------ |
| 0       | id       | INTEGER  | 0           |                | 1      |
| 1       | value1   | REAL     | 0           |                | 0      |
| 2       | value2   | REAL     | 0           |                | 0      |
| 3       | base     | INTEGER  | 0           |                | 0      |
| 4       | exponent | INTEGER  | 0           |                | 0      |
| 5       | number   | REAL     | 0           |                | 0      |
| 6       | decimal  | REAL     | 0           |                | 0      |


```sql
SELECT 
    id,
    value1,
    CASE 
        WHEN CAST(value1 AS INTEGER)%2=0 THEN 'Even'
        ELSE 'Odd'
    END AS parity
FROM Calculations;
```

**Output:**
<img width="814" height="521" alt="image" src="https://github.com/user-attachments/assets/f0478b4e-29aa-42f1-bd6e-84e975f6a0fa" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
