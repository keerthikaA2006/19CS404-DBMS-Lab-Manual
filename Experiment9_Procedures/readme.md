# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

### program:
```sql
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE find_square(n NUMBER) AS
    sq NUMBER;
BEGIN
    sq := n * n;
    DBMS_OUTPUT.PUT_LINE('Square of ' || n || ' is ' || sq);
END;
/

BEGIN
    find_square(6);
END;
/

```
**Output:**  

<img width="218" height="45" alt="image" src="https://github.com/user-attachments/assets/59f4020f-f681-49d7-b8fc-31267cb29977" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

### program:
```sql
SET SERVEROUTPUT ON;

CREATE OR REPLACE FUNCTION get_factorial(n NUMBER)
RETURN NUMBER AS
    f NUMBER := 1;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        f := f * i;
        i := i + 1;
    END LOOP;
    RETURN f;
END;
/

DECLARE
    x NUMBER := 5;
    r NUMBER;
BEGIN
    r := get_factorial(x);
    DBMS_OUTPUT.PUT_LINE('Factorial of ' || x || ' is ' || r);
END;
/

```
**Output:**  
<img width="277" height="60" alt="image" src="https://github.com/user-attachments/assets/3c87ff2f-c0f5-48fc-94c5-e572eb677f2e" />


---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

### program:
```sql
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE check_even_odd(n NUMBER) AS
BEGIN
    IF MOD(n, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(n || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(n || ' is Odd');
    END IF;
END;
/

BEGIN
    check_even_odd(12);
END;
/

```
**Output:**  
<img width="169" height="71" alt="image" src="https://github.com/user-attachments/assets/49f69f0c-903d-4d29-8f4a-cc42030b08a6" />


---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

### program:
```sql
SET SERVEROUTPUT ON;

CREATE OR REPLACE FUNCTION reverse_number(n NUMBER)
RETURN NUMBER
AS
    rev NUMBER := 0;
    temp NUMBER := n;
BEGIN
    WHILE temp > 0 LOOP
        rev := rev * 10 + MOD(temp, 10);
        temp := FLOOR(temp / 10);
    END LOOP;
    RETURN rev;
END;
/

DECLARE
    num NUMBER := 1234;
    result NUMBER;
BEGIN
    result := reverse_number(num);
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || num || ' is ' || result);
END;
/

```
**Output:**  
<img width="429" height="58" alt="image" src="https://github.com/user-attachments/assets/2c0cc099-6347-4d68-83fd-ef56156d8885" />


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

### program:
```sql
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE print_table(n NUMBER)
AS
BEGIN
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(n || ' x ' || i || ' = ' || (n * i));
    END LOOP;
END;
/

BEGIN
    print_table(5);
END;
/

```
**Output:**  
<img width="154" height="280" alt="image" src="https://github.com/user-attachments/assets/42d93f50-91a0-40cd-ae41-8d74eb50b402" />



## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
