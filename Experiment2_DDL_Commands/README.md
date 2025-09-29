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
--
<img width="1115" height="469" alt="image" src="https://github.com/user-attachments/assets/848beb5c-2ba1-46e5-a3c6-485d5367c26c" />

```sql
create table item(
item_id varchar(50) primary key,
item_desc varchar(20) not null,
rate int(10) not null,
icom_id char(4),
foreign key (icom_id) references company(com_id) 
on update set null
on delete set null
);
```

**Output:**

<img width="1187" height="336" alt="image" src="https://github.com/user-attachments/assets/1a93369a-5146-40d5-804e-a340049b7d0a" />


**Question 2**
---
<img width="1236" height="443" alt="image" src="https://github.com/user-attachments/assets/e7489239-a77b-4ba5-bedb-ac252018d24f" />


```sql
create table orders(
ord_id TEXT(4) not null,
item_id TEXT not null,
ord_date date,
ord_qty integer,
cost integer,
primary key (item_id,ord_date)
);
```

**Output:**

<img width="1060" height="246" alt="image" src="https://github.com/user-attachments/assets/2b7a71d1-782e-4bf2-a1f0-cfc51f025467" />


**Question 3**
---
<img width="1211" height="434" alt="image" src="https://github.com/user-attachments/assets/374e81f6-498a-40d0-9cb9-cb69cd0a5591" />


```sql
Alter table Student_details 
add MobileNumber NUMBER;

alter table Student_details
add Address VARCHAR(100);
```

**Output:**

<img width="1181" height="369" alt="image" src="https://github.com/user-attachments/assets/cf29c58a-777b-491b-952b-d9997a3185e0" />


**Question 4**
---
<img width="1232" height="301" alt="image" src="https://github.com/user-attachments/assets/ccc45bfe-c8ea-444d-8270-e481dc1a9ae0" />


```sql
create table jobs(
job_id int,
job_title text default "",
min_salary int default 8000,
max_salary int default NULL
);
```

**Output:**

<img width="1185" height="318" alt="image" src="https://github.com/user-attachments/assets/f84b9f79-e542-4ac0-a03b-56d725dadfcb" />


**Question 5**
---
<img width="1028" height="344" alt="image" src="https://github.com/user-attachments/assets/11ef8f01-5682-4a0b-aaac-67d929711f61" />

```sql
alter table customers 
add email TEXT;
```

**Output:**

<img width="1177" height="273" alt="image" src="https://github.com/user-attachments/assets/13a5623d-a00d-4eab-990d-0af1931e5202" />


**Question 6**
---
<img width="1092" height="411" alt="image" src="https://github.com/user-attachments/assets/66d4b3b8-b2d3-4033-b453-d19a04da9ff1" />


```sql
insert into Products (Name,Category,Price,Stock) values ("Smartphone","Electronics",800,150);
insert into Products (Name,Category,Price,Stock) values ("Headphones","Accessories",200,300); 
```

**Output:**

<img width="1233" height="397" alt="image" src="https://github.com/user-attachments/assets/97d8d6fd-2509-48b9-94ff-96991b22f829" />


**Question 7**
---
<img width="1185" height="335" alt="image" src="https://github.com/user-attachments/assets/d6bd86cb-583d-4342-8417-41858c6c6900" />


```sql
Create table Employees(
EmployeeID INT primary key,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email text UNIQUE,
Salary int check (Salary>0),
DepartmentID int,
foreign key (DepartmentID) references Departments(DepartmentID)
);
```

**Output:**

<img width="1183" height="408" alt="image" src="https://github.com/user-attachments/assets/692cb126-8df9-49af-b2b3-23bb68c465ca" />

**Question 8**
---
<img width="1007" height="418" alt="image" src="https://github.com/user-attachments/assets/09ddae12-30d1-4329-9426-62e71de3f184" />


```sql
insert into customers (CustomerID,Name,Address) values (304,"Peter Parker","Spider St");
```

**Output:**

<img width="1181" height="293" alt="image" src="https://github.com/user-attachments/assets/2e756c55-00ba-409d-99e1-a7de129c31f4" />


**Question 9**
---
<img width="1132" height="444" alt="image" src="https://github.com/user-attachments/assets/0d99ce16-26ba-4399-949c-ceb1c6eedac9" />


```sql
create table Products(
ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);
```

**Output:**

<img width="1184" height="298" alt="image" src="https://github.com/user-attachments/assets/60270d20-ca21-42a4-928d-dafebf734f88" />


**Question 10**
---
<img width="842" height="363" alt="image" src="https://github.com/user-attachments/assets/6248df63-484d-4870-9f50-0bfcc8ee29fe" />

```sql
insert into Employee (EmployeeID,Name, Department, Salary) 
select EmployeeID, Name, Department, Salary from Former_employees;
```

**Output:**

<img width="1243" height="261" alt="image" src="https://github.com/user-attachments/assets/7120d218-c828-45cc-b80c-a36a3b13ffb6" />

## SCORE

<img width="1429" height="216" alt="image" src="https://github.com/user-attachments/assets/022d59f7-9eae-4aa6-8f1b-7e21503bd006" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
