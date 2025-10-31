# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

Sample table: customer

| customer_id | cust_name      | city       | grade | salesman_id |
| ----------- | -------------- | ---------- | ----- | ----------- |
| 3002        | Nick Rimando   | New York   | 100   | 5001        |
| 3007        | Brad Davis     | New York   | 200   | 5001        |
| 3005        | Graham Zusi    | California | 200   | 5002        |
| 3008        | Julian Green   | London     | 300   | 5002        |
| 3004        | Fabian Johnson | Paris      | 300   | 5006        |
| 3009        | Geoff Cameron  | Berlin     | 100   | 5003        |
| 3003        | Jozy Altidor   | Moscow     | 200   | 5007        |
| 3001        | Brad Guzan     | London     | —     | 5005        |

Sample table: salesman

| salesman_id | name       | city     | commission |
| ----------- | ---------- | -------- | ---------- |
| 5001        | James Hoog | New York | 0.15       |
| 5002        | Nail Knite | Paris    | 0.13       |
| 5005        | Pit Alex   | London   | 0.11       |
| 5006        | Mc Lyon    | Paris    | 0.14       |
| 5007        | Paul Adam  | Rome     | 0.13       |
| 5003        | Lauson Hen | San Jose | 0.12       |

```sql
SELECT 
    c.cust_name AS "cust_name",
    c.city AS "city",
    c.grade AS "grade",
    s.name AS "Salesman",
    s.city AS "city"
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="1268" height="676" alt="image" src="https://github.com/user-attachments/assets/77d63878-536b-4524-812b-07b8f21027d2" />


**Question 2**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

  Sample table: orders
  
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
| ------ | --------- | ---------- | ----------- | ----------- |
| 70001  | 150.50    | 2012-10-05 | 3005        | 5002        |
| 70009  | 270.65    | 2012-09-10 | 3001        | 5005        |
| 70002  | 65.26     | 2012-10-05 | 3002        | 5001        |
| 70004  | 110.50    | 2012-08-17 | 3009        | 5003        |
| 70007  | 948.50    | 2012-09-10 | 3005        | 5002        |
| 70005  | 2400.60   | 2012-07-27 | 3007        | 5001        |
| 70008  | 5760.00   | 2012-09-10 | 3002        | 5001        |
| 70010  | 1983.43   | 2012-10-10 | 3004        | 5006        |
| 70003  | 2480.40   | 2012-10-10 | 3009        | 5003        |
| 70012  | 250.45    | 2012-06-27 | 3008        | 5002        |
| 70011  | 75.29     | 2012-08-17 | 3003        | 5007        |
| 70013  | 3045.60   | 2012-04-25 | 3002        | 5001        |

  Sample table: customer
  
| customer_id | cust_name      | city       | grade | salesman_id |
| ----------- | -------------- | ---------- | ----- | ----------- |
| 3002        | Nick Rimando   | New York   | 100   | 5001        |
| 3007        | Brad Davis     | New York   | 200   | 5001        |
| 3005        | Graham Zusi    | California | 200   | 5002        |
| 3008        | Julian Green   | London     | 300   | 5002        |
| 3004        | Fabian Johnson | Paris      | 300   | 5006        |
| 3009        | Geoff Cameron  | Berlin     | 100   | 5003        |
| 3003        | Jozy Altidor   | Moscow     | 200   | 5007        |
| 3001        | Brad Guzan     | London     | —     | 5005        |

  Sample table : salesman
  
| salesman_id | name       | city     | commission |
| ----------- | ---------- | -------- | ---------- |
| 5001        | James Hoog | New York | 0.15       |
| 5002        | Nail Knite | Paris    | 0.13       |
| 5005        | Pit Alex   | London   | 0.11       |
| 5006        | Mc Lyon    | Paris    | 0.14       |
| 5007        | Paul Adam  | Rome     | 0.13       |
| 5003        | Lauson Hen | San Jose | 0.12       |


```sql
SELECT 
    o.ord_no AS "ord_no",
    o.purch_amt AS "purch_amt",
    o.ord_date AS "ord_date",
    c.cust_name AS "cust_name",
    c.city AS "customer_city",
    c.grade AS "grade",
    s.name AS "salesman_name",
    s.city AS "salesman_city",
    s.commission AS "commission"
FROM 
    orders o
INNER JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
INNER JOIN 
    salesman s
ON 
    o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1802" height="884" alt="image" src="https://github.com/user-attachments/assets/2642c593-05e5-43c7-8459-14c4fa15f775" />


**Question 3**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

Sample table: orders

| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
| ------ | --------- | ---------- | ----------- | ----------- |
| 70001  | 150.50    | 2012-10-05 | 3005        | 5002        |
| 70009  | 270.65    | 2012-09-10 | 3001        | 5005        |
| 70002  | 65.26     | 2012-10-05 | 3002        | 5001        |
| 70004  | 110.50    | 2012-08-17 | 3009        | 5003        |
| 70007  | 948.50    | 2012-09-10 | 3005        | 5002        |
| 70005  | 2400.60   | 2012-07-27 | 3007        | 5001        |
| 70008  | 5760.00   | 2012-09-10 | 3002        | 5001        |
| 70010  | 1983.43   | 2012-10-10 | 3004        | 5006        |
| 70003  | 2480.40   | 2012-10-10 | 3009        | 5003        |
| 70012  | 250.45    | 2012-06-27 | 3008        | 5002        |
| 70011  | 75.29     | 2012-08-17 | 3003        | 5007        |
| 70013  | 3045.60   | 2012-04-25 | 3002        | 5001        |

Sample table: customer
| customer_id | cust_name      | city       | grade | salesman_id |
| ----------- | -------------- | ---------- | ----- | ----------- |
| 3002        | Nick Rimando   | New York   | 100   | 5001        |
| 3007        | Brad Davis     | New York   | 200   | 5001        |
| 3005        | Graham Zusi    | California | 200   | 5002        |
| 3008        | Julian Green   | London     | 300   | 5002        |
| 3004        | Fabian Johnson | Paris      | 300   | 5006        |
| 3009        | Geoff Cameron  | Berlin     | 100   | 5003        |
| 3003        | Jozy Altidor   | Moscow     | 200   | 5007        |



```sql
| customer_id | cust_name      | city       | grade | salesman_id |
| ----------- | -------------- | ---------- | ----- | ----------- |
| 3002        | Nick Rimando   | New York   | 100   | 5001        |
| 3007        | Brad Davis     | New York   | 200   | 5001        |
| 3005        | Graham Zusi    | California | 200   | 5002        |
| 3008        | Julian Green   | London     | 300   | 5002        |
| 3004        | Fabian Johnson | Paris      | 300   | 5006        |
| 3009        | Geoff Cameron  | Berlin     | 100   | 5003        |
| 3003        | Jozy Altidor   | Moscow     | 200   | 5007        |

```

**Output:**

<img width="1077" height="854" alt="image" src="https://github.com/user-attachments/assets/9e8f76dc-cd77-498d-87eb-29c57e75d6cd" />


**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

<img width="1052" height="172" alt="unnamed" src="https://github.com/user-attachments/assets/c3985562-c132-422c-9b42-d55fdfde1c98" />


TEST_RESULT TABLES:

ATTRIBUTES - result_id, patient_id, test_name, result, test_date
<img width="1060" height="171" alt="unnamed" src="https://github.com/user-attachments/assets/1031ef2f-bc23-4d35-9c79-d99a81e62f47" />




```sql
SELECT 
    p.first_name AS patient_name,
    t.result_id,
    t.patient_id,
    t.test_name,
    t.result,
    t.test_date
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="1856" height="481" alt="image" src="https://github.com/user-attachments/assets/9c77b241-9231-4073-872f-1a620efc3ad7" />


**Question 5**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

| salesman_id | name       | city     | commission |
| ----------- | ---------- | -------- | ---------- |
| 5001        | James Hoog | New York | 0.15       |
| 5002        | Nail Knite | Paris    | 0.13       |
| 5005        | Pit Alex   | London   | 0.11       |
| 5006        | Mc Lyon    | Paris    | 0.14       |
| 5007        | Paul Adam  | Rome     | 0.13       |
| 5003        | Lauson Hen | San Jose | 0.12       |

Sample table: customer

| customer_id | cust_name      | city       | grade | salesman_id |
| ----------- | -------------- | ---------- | ----- | ----------- |
| 3002        | Nick Rimando   | New York   | 100   | 5001        |
| 3007        | Brad Davis     | New York   | 200   | 5001        |
| 3005        | Graham Zusi    | California | 200   | 5002        |
| 3008        | Julian Green   | London     | 300   | 5002        |
| 3004        | Fabian Johnson | Paris      | 300   | 5006        |
| 3009        | Geoff Cameron  | Berlin     | 100   | 5003        |
| 3003        | Jozy Altidor   | Moscow     | 200   | 5007        |
| 3001        | Brad Guzan     | London     | —     | 5005        |



```sql
SELECT
    s.name AS "Salesman",
    c.cust_name,
    c.city
FROM
    salesman s
JOIN
    customer c ON s.city = c.city;

```

**Output:**

<img width="1067" height="772" alt="image" src="https://github.com/user-attachments/assets/f320973c-f449-45ba-9634-4b7d560c395c" />


**Question 6**
---
Write the SQL query that achieves the selection of the date of birth from the "patients" table (aliased as "p") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

<img width="1052" height="172" alt="unnamed" src="https://github.com/user-attachments/assets/0da876ab-82c7-4e7b-a437-82a60a6a3f1b" />


APPOINTMENTS TABLE:

ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date

<img width="1039" height="169" alt="unnamed" src="https://github.com/user-attachments/assets/766c86e9-9f34-4bda-a585-2ce87ac931dd" />


```sql
SELECT 
    p.date_of_birth,
    a.appointment_id,
    a.patient_id,
    a.doctor_id,
    a.appointment_date
FROM 
    patients p
INNER JOIN 
    appointments a
ON 
    p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';

```

**Output:**

<img width="1829" height="491" alt="image" src="https://github.com/user-attachments/assets/d7e310a6-ff76-4c1e-af90-a593cd7c71c0" />


**Question 7**
---
Write an SQL query to select all columns from the 'customer' table (aliased as 'c') by performing a LEFT JOIN with the 'orders' table on the 'customer_id' column, including only those orders where the order date falls between '2012-08-01' and '2012-08-30'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
SELECT 
    c.customer_id,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';

```

**Output:**

<img width="1203" height="400" alt="image" src="https://github.com/user-attachments/assets/20c31b17-6dd4-4ba6-a211-7715c5fb4e3a" />


**Question 8**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer

| customer_id | cust_name      | city       | grade | salesman_id |
| ----------- | -------------- | ---------- | ----- | ----------- |
| 3002        | Nick Rimando   | New York   | 100   | 5001        |
| 3007        | Brad Davis     | New York   | 200   | 5001        |
| 3005        | Graham Zusi    | California | 200   | 5002        |
| 3008        | Julian Green   | London     | 300   | 5002        |
| 3004        | Fabian Johnson | Paris      | 300   | 5006        |
| 3009        | Geoff Cameron  | Berlin     | 100   | 5003        |
| 3003        | Jozy Altidor   | Moscow     | 200   | 5007        |
| 3001        | Brad Guzan     | London     | —     | 5005        |

Sample table: orders

| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
| ------ | --------- | ---------- | ----------- | ----------- |
| 70001  | 150.50    | 2012-10-05 | 3005        | 5002        |
| 70009  | 270.65    | 2012-09-10 | 3001        | 5005        |
| 70002  | 65.26     | 2012-10-05 | 3002        | 5001        |
| 70004  | 110.50    | 2012-08-17 | 3009        | 5003        |
| 70007  | 948.50    | 2012-09-10 | 3005        | 5002        |
| 70005  | 2400.60   | 2012-07-27 | 3007        | 5001        |
| 70008  | 5760.00   | 2012-09-10 | 3002        | 5001        |
| 70010  | 1983.43   | 2012-10-10 | 3004        | 5006        |
| 70003  | 2480.40   | 2012-10-10 | 3009        | 5003        |
| 70012  | 250.45    | 2012-06-27 | 3008        | 5002        |
| 70011  | 75.29     | 2012-08-17 | 3003        | 5007        |
| 70013  | 3045.60   | 2012-04-25 | 3002        | 5001        |


```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM 
    orders o
JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
WHERE 
    o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

<img width="1588" height="636" alt="image" src="https://github.com/user-attachments/assets/14d6f1d0-f1bc-4fe5-8672-f7393b83d3f3" />


**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test names 'Blood Test' or 'Blood Pressure' and results not containing the substring 'Normal'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

<img width="1052" height="172" alt="unnamed" src="https://github.com/user-attachments/assets/819d591c-7292-4556-8320-7b6eed138dd2" />


TEST_RESULT TABLES:

ATTRIBUTES - result_id, patient_id, test_name, result, test_date

<img width="1060" height="171" alt="unnamed" src="https://github.com/user-attachments/assets/311fdcbd-88b5-475e-b35d-00226ec0a7e1" />


```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id
WHERE 
    (t.test_name = 'Blood Test' OR t.test_name = 'Blood Pressure')
    AND t.result NOT LIKE '%Normal%';

```

**Output:**

<img width="1365" height="405" alt="image" src="https://github.com/user-attachments/assets/19d7d78a-1a03-422f-8ad7-d2a8c1224433" />


**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman with the name 'Mc Lyon'.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.name = 'Mc Lyon';

```

**Output:**

<img width="1281" height="374" alt="image" src="https://github.com/user-attachments/assets/5d98c74b-21a6-437f-a618-329cd97efe48" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
