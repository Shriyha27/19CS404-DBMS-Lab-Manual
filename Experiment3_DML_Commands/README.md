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
--
```
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

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
```
```sql
update Products 
set
quantity=(quantity*1.1);
```

**Output:**

<img width="1182" height="609" alt="image" src="https://github.com/user-attachments/assets/7f7fd885-707d-42eb-a3f7-26341540083f" />


**Question 2**
---
```
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT
```

```sql
update products set
category="Household"
where product_name like "%Detergent%";
```

**Output:**

<img width="1184" height="483" alt="image" src="https://github.com/user-attachments/assets/a29aa0c5-4c9c-4b5c-9319-675476a6c77a" />


**Question 3**
---
```
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

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
```

```sql
update Products set
sell_price=sell_price*1.1
where category = "Bakery";
```

**Output:**

<img width="1181" height="509" alt="image" src="https://github.com/user-attachments/assets/9e6f783d-f025-4bd0-a1d1-c22e5db6b7a4" />


**Question 4**
---
```
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

---------------
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
```

```sql
update Employees set
salary=salary+500 , email = "updated"
where job_id="SA_REP" and commission_pct>0.15;
```

**Output:**

<img width="1182" height="521" alt="image" src="https://github.com/user-attachments/assets/1e587966-c239-4859-a756-6da584da735e" />

**Question 5**
---
```
 Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)
```
```sql
update Sales set
total_sell_price = quantity*sell_price
where product_id = 10;
```

**Output:**

<img width="1184" height="486" alt="image" src="https://github.com/user-attachments/assets/75ddabe7-3705-478b-9fdb-b6ed3480c6a7" />


**Question 6**
---
```
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
```
```sql
delete from surgeries where surgery_date="2024-02-28";
```

**Output:**

<img width="1183" height="374" alt="image" src="https://github.com/user-attachments/assets/ea074a82-f03a-48e3-8b9f-aae020c8745d" />


**Question 7**
---
```
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```

```sql
delete from Doctors where specialization="Cardiology";
```

**Output:**

<img width="1190" height="374" alt="image" src="https://github.com/user-attachments/assets/b0984549-ffcd-49a2-b66b-b9955f29f680" />


**Question 8**
---
```
Write a SQL statement to Display the order number, orderdate and the purchase amount of
orders table which will be delivered by the salesman with ID 5001.

orders table

name                 type
---------------     ---------------
order_no            int
purch_amt         real
order_date        text
customer_id      int
salesman_id      int
```

```sql
select order_no,order_date,purch_amt from orders where salesman_id = 5001;
```

**Output:**

<img width="905" height="396" alt="image" src="https://github.com/user-attachments/assets/4399ddc9-ae52-43f5-bbab-1d64241fbac9" />


**Question 9**
---
```
write a SQL query to identify customers who do not belong to the city of 'New York' or have a grade value that exceeds 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```

```sql
select * from customer where city <> "New York" and grade = 100;
```

**Output:**

<img width="1186" height="392" alt="image" src="https://github.com/user-attachments/assets/586d242a-0230-4e74-a359-b00dbda4c342" />


**Question 10**
---
```
Write a SQL query to calculate the discounted price for products where the discount percentage is greater than 0, and order the results by discounted_price in ascending order. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage 

------------+----------------+--------------------- 

101 | 50.00 | 0.10 

102 | 75.00 | 0.00 

103 | 100.00 | 0.20
```

```sql
select product_id,original_price,discount_percentage,original_price-(original_price*discount_percentage) as discounted_price 
from Products
where discount_percentage > 0 order by discounted_price;
```

**Output:**

<img width="1186" height="276" alt="image" src="https://github.com/user-attachments/assets/4208d9e6-f671-4269-afef-e8b81b7bc79b" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
