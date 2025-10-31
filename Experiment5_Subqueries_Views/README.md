# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)
<img width="602" height="233" alt="image (3)" src="https://github.com/user-attachments/assets/b5cd2610-d91e-4a4c-8f89-c1df6ce29800" />



```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

**Output:**

<img width="725" height="491" alt="image" src="https://github.com/user-attachments/assets/c532ee18-d2e9-49b4-b6c0-069feaaa8f55" />


**Question 2**
---
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

<img width="741" height="170" alt="image (6)" src="https://github.com/user-attachments/assets/520f8888-6f26-4708-b6b0-a1234af77246" />




```sql
SELECT medication_id AS medic, medication_name, dosage
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage)
    FROM Medications
);
```

**Output:**

<img width="851" height="468" alt="image" src="https://github.com/user-attachments/assets/db0518be-a6f7-4800-853c-376d64f78a18" />


**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS

| ID | NAME     | AGE | ADDRESS   | SALARY |
| -- | -------- | --- | --------- | ------ |
| 1  | Ramesh   | 32  | Ahmedabad | 2000   |
| 2  | Khilan   | 25  | Delhi     | 1500   |
| 3  | Kaushik  | 23  | Kota      | 2000   |
| 4  | Chaitali | 25  | Mumbai    | 6500   |
| 5  | Hardik   | 27  | Bhopal    | 8500   |
| 6  | Komal    | 22  | Hyderabad | 4500   |
| 7  | Muffy    | 24  | Indore    | 10000  |


```sql
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;
```

**Output:**

<img width="1217" height="640" alt="image" src="https://github.com/user-attachments/assets/8db1798e-5f07-49db-90af-755dcc9be5c6" />


**Question 4**
---
Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

SAMPLE TABLE: customer

| name  | type    |
| ----- | ------- |
| id    | INTEGER |
| name  | TEXT    |
| city  | TEXT    |
| email | TEXT    |
| phone | INTEGER |


```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);
```

**Output:**

<img width="549" height="528" alt="image" src="https://github.com/user-attachments/assets/84d1051a-380b-4b23-8f17-8d27210cdef0" />


**Question 5**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS

| ID | NAME     | AGE | ADDRESS   | SALARY |
| -- | -------- | --- | --------- | ------ |
| 1  | Ramesh   | 32  | Ahmedabad | 2000   |
| 2  | Khilan   | 25  | Delhi     | 1500   |
| 3  | Kaushik  | 23  | Kota      | 2000   |
| 4  | Chaitali | 25  | Mumbai    | 6500   |
| 5  | Hardik   | 27  | Bhopal    | 8500   |
| 6  | Komal    | 22  | Hyderabad | 4500   |
| 7  | Muffy    | 24  | Indore    | 10000  |


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;
```

**Output:**

<img width="1212" height="495" alt="image" src="https://github.com/user-attachments/assets/7f8447f8-aebd-4f79-9f44-fb7ede3e8b19" />


**Question 6**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
SALESMAN TABLE

| name        | type         |
| ----------- | ------------ |
| salesman_id | numeric(5)   |
| name        | varchar(30)  |
| city        | varchar(15)  |
| commission  | decimal(5,2) |

ORDERS TABLE

| name        | type |
| ----------- | ---- |
| ord_no      | int  |
| purch_amt   | real |
| ord_date    | text |
| customer_id | int  |
| salesman_id | int  |


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM ORDERS o
JOIN SALESMAN s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```

**Output:**

<img width="1235" height="548" alt="image" src="https://github.com/user-attachments/assets/1c2de7da-1bd6-4b68-ae4f-a82f30f4ed96" />


**Question 7**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

| name   | type    |
| ------ | ------- |
| id     | INTEGER |
| name   | TEXT    |
| age    | INTEGER |
| city   | TEXT    |
| income | INTEGER |


```sql
SELECT id, name, age, city, income
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);

```

**Output:**

<img width="1245" height="503" alt="image" src="https://github.com/user-attachments/assets/054814a6-ee14-4fb3-a640-2a9326852728" />


**Question 8**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS

| ID | NAME     | AGE | ADDRESS   | SALARY |
| -- | -------- | --- | --------- | ------ |
| 1  | Ramesh   | 32  | Ahmedabad | 2000   |
| 2  | Khilan   | 25  | Delhi     | 1500   |
| 3  | Kaushik  | 23  | Kota      | 2000   |
| 4  | Chaitali | 25  | Mumbai    | 6500   |
| 5  | Hardik   | 27  | Bhopal    | 8500   |
| 6  | Komal    | 22  | Hyderabad | 4500   |
| 7  | Muffy    | 24  | Indore    | 10000  |


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

<img width="1205" height="669" alt="image" src="https://github.com/user-attachments/assets/48ca9725-8dd6-453e-8181-54a052fa5c80" />


**Question 9**
---
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

salesman table

| name        | type         |
| ----------- | ------------ |
| salesman_id | numeric(5)   |
| name        | varchar(30)  |
| city        | varchar(15)  |
| commission  | decimal(5,2) |


orders table

| name        | type |
| ----------- | ---- |
| order_no    | int  |
| purch_amt   | real |
| order_date  | text |
| customer_id | int  |
| salesman_id | int  |

```sql
SELECT o.ord_no AS ord_no,o.purch_amt,o.ord_date AS ord_date,o.customer_id,o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.name = 'Paul Adam';

```

**Output:**

<img width="1246" height="439" alt="image" src="https://github.com/user-attachments/assets/1f2056e2-f20d-4524-bc60-58dfca3b24a2" />


**Question 10**
---
Write a SQL query to Retrieve the names of customers who have a phone number that is not shared with any other customer.

SAMPLE TABLE: customer

| name  | type    |
| ----- | ------- |
| id    | INTEGER |
| name  | TEXT    |
| city  | TEXT    |
| email | TEXT    |
| phone | INTEGER |


```sql
SELECT name
FROM customer
WHERE phone IN (
    SELECT phone
    FROM customer
    GROUP BY phone
    HAVING COUNT(phone) = 1
);
```

**Output:**

<img width="482" height="524" alt="image" src="https://github.com/user-attachments/assets/7812d08a-b194-4849-bc2a-c1e2bfa57680" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
