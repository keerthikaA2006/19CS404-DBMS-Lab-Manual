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
Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

```sql
select name,city
from customer
where city IN(
          select city
          from customer
          where id in(3,7)
);
```

**Output:**

<img width="711" height="542" alt="image" src="https://github.com/user-attachments/assets/32b32efa-f825-4516-971a-9766659c53e5" />


**Question 2**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

salesman table

```sql
select s.salesman_id,s.name
from salesman s
join customer c
  on s.salesman_id=c.salesman_id
group by s.salesman_id,s.name
having COUNT(c.customer_id)>1;
```

**Output:**

<img width="652" height="541" alt="image" src="https://github.com/user-attachments/assets/79b4842d-98ae-452c-88f5-952612b53fa1" />


**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

```sql
select *
from CUSTOMERS
where salary>4500;
```

**Output:**

<img width="1234" height="496" alt="image" src="https://github.com/user-attachments/assets/7fbfdc38-76c7-4e5e-82ac-c3583ea82267" />


**Question 4**
---
Write a SQL query to List departments with names longer than the average length

Departments Table (attributes: department_id, department_name)

```sql
select department_id,department_name
from Departments
where LENGTH(department_name)>(
       select AVG(LENGTH(department_name))
       from Departments
);
```

**Output:**

<img width="657" height="462" alt="image" src="https://github.com/user-attachments/assets/e189e289-0b23-4139-8c86-b5b0c3357c7f" />


**Question 5**
---
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
select *
from GRADES g
where grade=(
    select MIN(grade)
    from GRADES
    where subject=g.subject
);
```

**Output:**

<img width="1249" height="513" alt="image" src="https://github.com/user-attachments/assets/bfb17f62-d12c-43e8-be38-ad988481f354" />


**Question 6**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

```sql
select *
from Employee
where age<(
    select AVG(age)
    from Employee
    where income>250000);
```

**Output:**

<img width="1136" height="454" alt="image" src="https://github.com/user-attachments/assets/68a9c84c-857d-4902-81c6-7871eb1576da" />


**Question 7**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

```sql
select *
from CUSTOMERS
WHERE SALARY<2500;
```

**Output:**

<img width="1075" height="466" alt="image" src="https://github.com/user-attachments/assets/e9bb2334-d1c0-4b28-97cc-79e22bb8e47c" />


**Question 8**
---
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
SELECT *
from Medications
where dosage=(
    select MAX(dosage)
    from Medications);
```

**Output:**

<img width="842" height="356" alt="image" src="https://github.com/user-attachments/assets/aefa6167-3d0f-42aa-a123-247df7e53e31" />


**Question 9**
---
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
select *
from Medications
where dosage=(
     select MIN(dosage)
     from Medications);
```

**Output:**

<img width="782" height="367" alt="image" src="https://github.com/user-attachments/assets/a99c9962-b6fe-45dc-96d4-e007fb3b04aa" />


**Question 10**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

```sql
select *
from customer
where customer_id=(
     select salesman_id-2001
     from salesman
     where name='Mc Lyon');

```

**Output:**

<img width="1122" height="263" alt="image" src="https://github.com/user-attachments/assets/4ece95f1-7d45-422c-b7e3-803a7c3cad19" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
