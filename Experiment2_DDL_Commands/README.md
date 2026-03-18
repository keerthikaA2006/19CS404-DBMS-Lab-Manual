# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

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
```
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.
```

```sql
create table Bonuses(
 BonusID integer primary key,
 EmployeeID integer,
 BonusAmount real check(BonusAmount>0),
 BonusDate date,
 Reason text NOT NULL,
 foreign key(EmployeeID) references Employees(EmployeeID)
);
```

**Output:**

![Output1](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-1.png?raw=true)

**Question 2**
```
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE
```

```sql
CREATE TABLE Employees (
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE
);
```

**Output:**

![Output2](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-2.png?raw=true)

**Question 3**
```
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
```

```sql
ALTER TABLE Student_details
ADD mobilenumber number;
```

**Output:**

![Output3](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-3.png?raw=true)

**Question 4**
```
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email
```

```sql
INSERT INTO Customers(CustomerID,Name,Address,Email)
SELECT CustomerID,Name,Address,Email from Old_customers
```

**Output:**

![Output4](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-4.png?raw=true)

**Question 5**
```
Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.
```

```sql
ALTER TABLE employee
ADD COLUMN department_id INTEGER;
ALTER TABLE employee
ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**

![Output5](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-5.png?raw=true)

**Question 6**
```
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT
```

```sql
CREATE TABLE Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**

![Output6](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-6.png?raw=true)

**Question 7**
```
Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT
```

```sql
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**

![Output7](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-7.png?raw=true)

**Question 8**
```
Write a SQL Query for inserting the below values in the table Customers

ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000
```

```sql
INSERT INTO Customers(ID,NAME,AGE,ADDRESS,SALARY)
VALUES(1,"Ramesh",32,"Ahmedabad",2000),(2,"Khilan",25,"Delhi",1500),(3,"Kaushik",23,"Kota",2000);

```

**Output:**

![Output8](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-8.png?raw=true)

**Question 9**
```
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME
```

```sql
CREATE TABLE Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME
);
```

**Output:**

![Output9](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-9.png?raw=true)

**Question 10**
```
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.
```

```sql
INSERT INTO Employee(EmployeeID,Name,Position)
VALUES(4,"Emily White","Analyst");
```

**Output:**

![Output10](https://github.com/Sandhiya2517/19CS404-DBMS-Lab-Manual/blob/main/Experiment2_DDL_Commands/ex2-10.png?raw=true)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
