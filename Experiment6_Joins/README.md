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

```sql
select c.cust_name,c.city as city,c.grade,s.name as Salesman,s.city as city
from customer c
join salesman s on 
c.salesman_id=s.salesman_id
where c.grade<300
order by c.customer_id ASC;
```

**Output:**

<img width="1281" height="613" alt="image" src="https://github.com/user-attachments/assets/9f0d6bb9-7069-448d-9abc-dbca2be2b8c0" />


**Question 2**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```sql
select s.name 
from Salesman s
join Customer c
on s.salesman_id=c.salesman_id
where c.city="London";
```

**Output:**

<img width="383" height="372" alt="image" src="https://github.com/user-attachments/assets/e48fe31d-3d2d-4582-9b68-7b72d5901859" />


**Question 3**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.
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

<img width="1072" height="364" alt="image" src="https://github.com/user-attachments/assets/1f94cca3-193f-4252-94e3-d63a25c6e4e1" />


**Question 4**
---
Write an SQL query to select all columns from the 'customer' table (aliased as 'c') by performing a LEFT JOIN with the 'orders' table on the 'customer_id' column, including only those orders where the order date falls between '2012-08-01' and '2012-08-30'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
select c.*
from customer c
left join orders o
on c.customer_id=o.customer_id
where o.ord_date between '2012-08-01' AND '2012-08-30';
```

**Output:**

<img width="1265" height="366" alt="image" src="https://github.com/user-attachments/assets/168e6874-19aa-4c16-9096-0c3b5329c732" />


**Question 5**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
JOIN 
    salesman s
ON 
    o.salesman_id = s.salesman_id;

```

**Output:**
<img width="1307" height="279" alt="image" src="https://github.com/user-attachments/assets/b4b72158-71c2-447a-9389-fbdf86291483" />



**Question 6**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```sql
select c.cust_name as 'Customer Name',c.city as city,s.name as Salesman ,s.commission
from customer c
join salesman s
on c.salesman_id=s.salesman_id
where s.commission >0.12;
```

**Output:**

<img width="1105" height="598" alt="image" src="https://github.com/user-attachments/assets/b9c28ecf-20fc-4408-b0a8-98e223b9b86e" />


**Question 7**
---
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.

```sql
SELECT 
    n.nurse_id,
    d.department_name
FROM 
    nurses n
INNER JOIN 
    departments d
ON 
    n.department_id = d.department_id
WHERE 
    n.first_name = 'David'
    AND n.last_name = 'Moore';

```

**Output:**

<img width="630" height="311" alt="image" src="https://github.com/user-attachments/assets/0b1698e0-271d-4f1d-b51e-5f02d716b1a0" />


**Question 8**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```sql
select p.first_name as patient_name,t.*
from PATIENTS p
inner join TEST_RESULTS t
on p.patient_id=t.patient_id
where p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="1287" height="265" alt="image" src="https://github.com/user-attachments/assets/7919b495-3df1-4224-a5bf-d047c63695be" />


**Question 9**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

```sql
SELECT 
    p.first_name AS patient_name
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id
WHERE 
    t.test_name = 'Blood Pressure';

```

**Output:**

<img width="371" height="306" alt="image" src="https://github.com/user-attachments/assets/40ab577a-6b5c-4091-b7bf-d2c2793a36e2" />


**Question 10**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  
```sql
select c.cust_name as 'Customer Name',c.city,s.name as Salesman,s.city,s.commission
from customer c
join salesman s
on c.salesman_id=s.salesman_id
where c.city!=s.city
     and s.commission>0.12;

```

**Output:**

<img width="1240" height="470" alt="image" src="https://github.com/user-attachments/assets/2dddfb3b-8773-404b-82f2-6e91dfef8d9a" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
