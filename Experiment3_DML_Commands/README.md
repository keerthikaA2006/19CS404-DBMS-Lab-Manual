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
**Question 1**

Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
Update PRODUCTS
SET Sell_price=ROUND(sell_price*1.10,2)
WHERE supplier_id=6;
```

**Output:**

<img width="1252" height="267" alt="image" src="https://github.com/user-attachments/assets/dd7df3c9-642a-486f-957b-b93e326f3ee7" />


**Question 2**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
update Products
set product_name='Premium Bread'
where product_id=5;
```

**Output:**

<img width="1468" height="279" alt="image" src="https://github.com/user-attachments/assets/703f5cb6-387a-4de0-aa83-484615afd2bd" />


**Question 3**
---
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

```sql
UPDATE products
SET availability =availability * 2
WHERE product_id=1;
```

**Output:**

<img width="1626" height="266" alt="image" src="https://github.com/user-attachments/assets/1186ba53-c3f1-406d-b656-1c8f0be8cedf" />


**Question 4**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE PRODUCTS
SET reorder_lvl=40 
WHERE category='Grocery';
```

**Output:**

<img width="1876" height="293" alt="image" src="https://github.com/user-attachments/assets/fb0a8302-e791-4880-8396-62730b47e86a" />


**Question 5**
---
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
UPDATE sales
SET sell_price=sell_price*1.05
WHERE product_id=15 AND sale_date='2023-01-31';
```

**Output:**

<img width="1529" height="333" alt="image" src="https://github.com/user-attachments/assets/194cefbb-efbd-4684-9716-94225c4bca62" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```sql
DELETE FROM customer
WHERE GRADE!=3;
```

**Output:**

<img width="798" height="567" alt="image" src="https://github.com/user-attachments/assets/474a47c1-7b26-48b0-889d-b63dd3aa62ca" />


**Question 7**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L'

```sql
DELETE FROM Customer
WHERE CUST_CITY LIKE 'L%';
```

**Output:**

<img width="1574" height="199" alt="image" src="https://github.com/user-attachments/assets/1352499e-8d33-4494-8d52-2439ff025a41" />


**Question 8**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```sql
DELETE FROM Surgeries
WHERE surgery_date='2024-02-28';
```

**Output:**

<img width="1177" height="321" alt="image" src="https://github.com/user-attachments/assets/d0f8a694-2e73-4204-9ef5-a1d044baf626" />


**Question 9**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

Sample table: Customer

```sql
DELETE FROM customer
WHERE GRADE =3 AND CUST_NAME LIKE '%BBB%' AND PAYMENT_AMT>2000;
```

**Output:**

<img width="1909" height="435" alt="image" src="https://github.com/user-attachments/assets/18836f01-d66c-4305-a0db-f87a5138f1d5" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

 
Sample table: Customer

```sql
DELETE FROM customer
WHERE GRADE=2;
```

**Output:**

<img width="697" height="526" alt="image" src="https://github.com/user-attachments/assets/3b3f0207-e16e-4c86-ab51-8f74fee90752" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
