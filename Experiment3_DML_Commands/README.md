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
-- Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

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

```sql
update Employees set EMAIL='not available',COMMISSION_PCT=0.55 where DEPARTMENT_ID==110;
```

**Output:**

<img width="1802" height="345" alt="image" src="https://github.com/user-attachments/assets/f1753581-c421-4470-b790-908c083579e4" />


**Question 2**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

```sql
update suppliers set supplier_name='A1 Suppliers' where supplier_id=8;
```

**Output:**

<img width="1853" height="301" alt="image" src="https://github.com/user-attachments/assets/965a6307-d28c-4e3a-b0df-3acde9fc762b" />


**Question 3**
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
update products set  product_name='Premium Bread'  where product_id==5;
```

**Output:**
<img width="1869" height="307" alt="image" src="https://github.com/user-attachments/assets/9911ece5-c588-48c9-886a-7700c39788f4" />


**Question 4**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

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

```sql
update Employees set hire_date='2024-01-24' where department_id==50; 
```

**Output:**

<img width="1762" height="343" alt="image" src="https://github.com/user-attachments/assets/ce0e7b40-a075-4efc-a571-1d4b2255de01" />


**Question 5**
---
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

```sql
update Employees set salary=salary+500,email='updated' where job_id=='SA_REP' and commission_pct>0.15;
```

**Output:**

<img width="1823" height="492" alt="image" src="https://github.com/user-attachments/assets/b867dcd1-c4ef-45ad-a6ce-701a7c2da38e" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

```sql
delete from customer where OPENING_AMT>=4000 and OPENING_AMT<=6000;
```

**Output:**

<img width="1870" height="344" alt="image" src="https://github.com/user-attachments/assets/69f0f320-ad9d-47e3-ad63-e3707f59c515" />


**Question 7**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

```sql
delete from Doctors where last_name is null;
```

**Output:**

<img width="1284" height="667" alt="image" src="https://github.com/user-attachments/assets/dec39900-cc4a-4d83-b714-569c30df3ddb" />


**Question 8**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

```sql
delete from Customer where CUST_COUNTRY=='UK' and WORKING_AREA=='London' and GRADE<3;
```

**Output:**

<img width="1872" height="279" alt="image" src="https://github.com/user-attachments/assets/ffa056ef-17a6-4533-abbb-a833dcc990e0" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```sql
delete from customer where GRADE!=3;
```

**Output:**

<img width="1350" height="755" alt="image" src="https://github.com/user-attachments/assets/cb703030-f1df-49a3-9d5a-6e59fc69d844" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

```sql
delete from customer where GRADE<2; 
```

**Output:**

<img width="691" height="540" alt="image" src="https://github.com/user-attachments/assets/89b9ebd4-2539-4370-a9ce-90968873c5b9" />

**Module 2 SEB grades**
---
<img width="1422" height="777" alt="image" src="https://github.com/user-attachments/assets/4801f132-6307-4c3d-8ad1-e6bbbae64d88" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
