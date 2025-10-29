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
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
select avg(length(name)) as avg_name_length
from customer
where city="Chennai";
```

**Output:**

<img width="627" height="288" alt="image" src="https://github.com/user-attachments/assets/52c13f2b-106d-40fe-9004-0a221bff5747" />


**Question 2**
---
<img width="976" height="232" alt="image" src="https://github.com/user-attachments/assets/73f9a2fa-276a-4c21-b48d-0517c83ebfac" />


```sql
select Address, count(*) as TotalPatients
from Patients
group by Address;
```

**Output:**

<img width="700" height="397" alt="image" src="https://github.com/user-attachments/assets/9fc3614d-3ae3-4ae4-9c40-55176b089515" />


**Question 3**
---
<img width="1036" height="239" alt="image" src="https://github.com/user-attachments/assets/a1625e56-d394-4754-82f2-7f0d64ab297a" />


```sql
select Gender, count(*) as TotalPatients
from Patients
group by Gender;
```

**Output:**

<img width="636" height="348" alt="image" src="https://github.com/user-attachments/assets/e2f884bc-12c6-40f6-bd41-39ce1210b523" />


**Question 4**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL

```sql
select cast(total(inventory) as int) as total
from fruits
where unit="LB";
```

**Output:**

<img width="381" height="300" alt="image" src="https://github.com/user-attachments/assets/09431116-2928-4c7d-b769-a458cbc1f836" />

**Question 5**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001


```sql
select max(purch_amt) as MAXIMUM
from orders;
```

**Output:**

<img width="375" height="298" alt="image" src="https://github.com/user-attachments/assets/68055a3b-db06-46bd-8a94-d3b13eb63125" />


**Question 6**
---
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
select avg(length(email)) as avg_email_length_below_30
from customer
where city="Mumbai" and length(email)<30;
```

**Output:**

<img width="817" height="299" alt="image" src="https://github.com/user-attachments/assets/075a2cab-085d-4737-9616-1730c79067ee" />


**Question 7**
---
<img width="1129" height="263" alt="image" src="https://github.com/user-attachments/assets/d1d99652-e8ba-4ac6-97e4-bb6de3dd840e" />


```sql
select address, SUM(salary)
from customer1
group by address having sum(salary)>2000;
```

**Output:**

<img width="581" height="474" alt="image" src="https://github.com/user-attachments/assets/24b2b388-c2b6-4688-ab14-89658a5cd8d8" />

**Question 8**
---
<img width="1215" height="256" alt="image" src="https://github.com/user-attachments/assets/7aa49abf-3f8c-4bf1-a8b4-4ac28e40ba3c" />


```sql
select (age/5)*5 as age_group, MIN(age)
from customer1
group by age_group having MIN(age)<25;
```

**Output:**

<img width="633" height="302" alt="image" src="https://github.com/user-attachments/assets/a7be8dde-6970-4362-8dd4-94439ae7141c" />

**Question 9**
---
Write the SQL query to find how many patients have more than 3 medical records?.

Sample table: MedicalRecords

name        type
----------  ----------
RecordID    INTEGER
PatientID   INTEGER
DoctorID    INTEGER
Date        DATE
Diagnosis   TEXT
Treatment   TEXT
Medication  TEXT

```sql
select PatientID, count(*) as TotalRecords
from MedicalRecords
group by PatientID having TotalRecords>3;
```

**Output:**

<img width="622" height="327" alt="image" src="https://github.com/user-attachments/assets/934004be-3922-47ab-9f7c-a27ee1bc3a0f" />

**Question 10**
---
<img width="1001" height="238" alt="image" src="https://github.com/user-attachments/assets/9d7aca48-9908-4766-b812-49e28b91b9e1" />

```sql
select STRFTIME('%Y-%m',Date) as Month,count(*) as TotalRecords
from MedicalRecords
group by Month;
```

**Output:**

<img width="625" height="416" alt="image" src="https://github.com/user-attachments/assets/a7fa8bda-adf0-4748-81e8-acf6cd052d42" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
