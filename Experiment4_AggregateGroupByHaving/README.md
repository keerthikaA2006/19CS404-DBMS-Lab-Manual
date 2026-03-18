# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many medical records were created in each month?

Sample table:MedicalRecords Table

```sql
SELECT 
    strftime('%Y-%m', Date) AS Month,
    COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY strftime('%Y-%m', Date)
ORDER BY Month;
```

**Output:**

<img width="785" height="504" alt="image" src="https://github.com/user-attachments/assets/ea5eca81-8c13-4676-988e-49c52b508358" />


**Question 2**
---
How many patients are covered by each insurance company?

Sample table:Insurance Table

```sql
SELECT 
    InsuranceCompany,
    COUNT(DISTINCT PatientID) AS TotalPatients
FROM Insurance
GROUP BY InsuranceCompany
ORDER BY InsuranceCompany;
```

**Output:**

<img width="824" height="754" alt="image" src="https://github.com/user-attachments/assets/ee7050f8-92c4-4e0a-9d82-1f6e1903c636" />


**Question 3**
---
How many prescriptions were written for each medication?

Sample tablePrescriptions Table


```sql
SELECT 
    Medication,
    COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication
ORDER BY Medication;
```

**Output:**

<img width="849" height="739" alt="image" src="https://github.com/user-attachments/assets/42359077-f61d-40a0-9912-3d6fa03aa340" />


**Question 4**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

```sql
SELECT 
    COUNT(*) AS employees_count
FROM employee
WHERE income > 50000;
```

**Output:**

<img width="596" height="381" alt="image" src="https://github.com/user-attachments/assets/4195bf7a-5b5b-4754-ad1c-2a5af72b3687" />



**Question 5**
---
Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 

Note: Inventory attribute contains amount of fruits

Table: fruits

```sql
SELECT 
    SUM(inventory) AS total_available_amount
FROM fruits
WHERE price > 0.5;
```

**Output:**

<img width="714" height="381" alt="image" src="https://github.com/user-attachments/assets/0eb3173d-a887-41d8-a6a4-07f28c48173a" />


**Question 6**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

```sql
SELECT 
    COUNT(*) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

<img width="503" height="402" alt="image" src="https://github.com/user-attachments/assets/75303e5a-2e7b-449a-8c74-1bd1704e57aa" />

**Question 7**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer

```sql
SELECT 
    COUNT(*) AS COUNT
FROM customer
WHERE city = 'Noida';
```

**Output:**

<img width="389" height="371" alt="image" src="https://github.com/user-attachments/assets/5b793e25-f7e1-4f7c-a9ac-d0354ec32888" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

Sample table: employee1

```sql
SELECT 
    jdate, 
    AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour) < 10;
```

**Output:**

<img width="650" height="418" alt="image" src="https://github.com/user-attachments/assets/ab400566-303c-4a7e-aa91-13a23fbf1ee0" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

Sample table: employee



```sql
SELECT 
    age, 
    SUM(income) AS "SUM(income)"
FROM employee
GROUP BY age
HAVING SUM(income) > 1000000;
```

**Output:**

<img width="716" height="475" alt="image" src="https://github.com/user-attachments/assets/c906b935-d685-4a36-8c0f-0b4248ff2cb8" />



**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1

```sql
SELECT 
    occupation, 
    SUM(workhour) AS "SUM(workhour)"
FROM employee1
GROUP BY occupation
HAVING SUM(workhour) > 20;
```

**Output:**

<img width="626" height="452" alt="image" src="https://github.com/user-attachments/assets/ed593055-ba3f-461f-bf82-1ad3a5cead64" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
