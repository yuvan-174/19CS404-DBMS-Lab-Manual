# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

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
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

### Program:

```sql
DECLARE
    a NUMBER := 50;
    b NUMBER := 80;
BEGIN
    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
    END IF;
END;
/

```

### Output:  

<img width="475" height="287" alt="image" src="https://github.com/user-attachments/assets/173e5aa4-1900-4463-a2d4-fcf8776e3736" />


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

### Program:
```sql
DECLARE
    n   NUMBER := 10;
    i   NUMBER := 1;
    sum NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```

### Output: 

<img width="394" height="277" alt="image" src="https://github.com/user-attachments/assets/7051e4d7-1f00-4ed1-9229-cb1e822103a4" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

### Program:
```sql
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    result VARCHAR2(200) := '';
BEGIN

    IF n >= 1 THEN
        result := result || a;
    END IF;
    

    IF n >= 2 THEN
        result := result || ', ' || b;
    END IF;

   
    FOR i IN 3..n LOOP
        c := a + b;
        result := result || ', ' || c;
        a := b;
        b := c;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || result);
END;
/
```

### Output:

<img width="466" height="284" alt="image" src="https://github.com/user-attachments/assets/32664d1b-79c1-4321-8687-a08c6ffd4388" />


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

### Program:
```sql
DECLARE
    n NUMBER := 1535;
    temp NUMBER := n;
    rev NUMBER := 0;
    digit NUMBER;
BEGIN
    WHILE temp > 0 LOOP
        digit := temp MOD 10;       
        rev := rev * 10 + digit;     
        temp := FLOOR(temp / 10);    
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/
```


### Output:  

<img width="380" height="268" alt="image" src="https://github.com/user-attachments/assets/e4ca52b9-2cca-40ba-a928-4d0a8692a492" />


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

### Program:
```sql
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    largest NUMBER;
BEGIN
    IF a >= b AND a >= c THEN
        largest := a;
    ELSIF b >= a AND b >= c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('Largest of three numbers is ' || largest);
END;
/

```

### Output:

<img width="353" height="269" alt="image" src="https://github.com/user-attachments/assets/99bb0558-ccc2-4c47-97a1-f0cf162f877c" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

