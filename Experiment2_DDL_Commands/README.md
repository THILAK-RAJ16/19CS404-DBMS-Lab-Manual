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
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER references Suppliers(SupplierID),
OrderID INTEGER  references Orders(OrderID)
);
```

**Output:**

<img width="1247" height="134" alt="image" src="https://github.com/user-attachments/assets/3e91768d-6b61-4843-b5a5-bf01fe9907fd" />


**Question 2**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

| EmployeeID | Name        | Position |
|-------------|-------------|-----------|
| 4           | Emily White | Analyst   |


Note: The Department and Salary columns will use their default values. 

```sql
insert into Employee("EmployeeID","Name","Position") values(4,"Emily White","Analyst");
```

**Output:**

<img width="1092" height="279" alt="image" src="https://github.com/user-attachments/assets/b39141b9-77b0-4f7f-966f-46c52fb3730c" />


**Question 3**
---
Write an SQL command can to add a column named email of type TEXT to the customers table

```sql
alter table customers add email TEXT;
```

**Output:**

<img width="1179" height="177" alt="image" src="https://github.com/user-attachments/assets/304d1f40-ceb5-4e07-8738-07605dbd167c" />


**Question 4**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```sql
create table products(
product_id INTEGER primary key,
product_name TEXT not NULL,
list_price  DECIMAL (10, 2)  not NULL,
discount DECIMAL (10, 2)  default 0 not NULL,
check(list_price >=discount ),
check(discount >=0 ) ,
check(list_price >=0)

);
```

**Output:**

<img width="1740" height="221" alt="image" src="https://github.com/user-attachments/assets/85d1d7bc-8de0-4f67-8104-8481a6238e95" />


**Question 5**
---
Insert all students from Archived_students table into the Student_details table.

| cid | name    | type          | notnull | dflt_value | pk |
|-----|----------|---------------|----------|-------------|----|
| 0   | RollNo  | INT           | 0        |             | 1  |
| 1   | Name    | VARCHAR(100)  | 0        |             | 0  |
| 2   | Gender  | VARCHAR(10)   | 0        |             | 0  |
| 3   | Subject | VARCHAR(50)   | 0        |             | 0  |
| 4   | MARKS   | INT           | 0        |             | 0  |


```sql
Insert into Student_details select * from Archived_students ;
```

**Output:**

<img width="1784" height="297" alt="image" src="https://github.com/user-attachments/assets/2dccf6e9-e774-476e-9a28-af193784bd5e" />


**Question 6**
---
Create a table named Orders with the following columns:

OrderID as INTEGER,
OrderDate as TEXT,
CustomerID as INTEGER.

```sql
create table orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);
```

**Output:**

<img width="1772" height="336" alt="image" src="https://github.com/user-attachments/assets/3b682a45-6d19-49fb-97d6-222169a8bf0e" />


**Question 7**
---
Create a new table named contacts with the following specifications:

  contact_id as INTEGER and primary key.
  first_name as TEXT and not NULL.
  last_name as TEXT and not NULL.
  email as TEXT.
  phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
create table contacts (
contact_id INTEGER primary key,
first_name TEXT not NULL,
last_name TEXT not NULL,
email TEXT,
phone TEXT not NULL check(length(phone) >= 10)
);
```

**Output:**

<img width="1860" height="212" alt="image" src="https://github.com/user-attachments/assets/28dbe8cf-8707-4e29-8362-38e3ac4623ec" />


**Question 8**
---
Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 

```sql
alter table customer add "email" VARCHAR(100);
```

**Output:**

<img width="1837" height="285" alt="image" src="https://github.com/user-attachments/assets/cfd4016b-f256-4f8f-baf0-9f56eddb2bb3" />


**Question 9**
---
In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
insert into Products values(106,"Fitness Tracker","Wearables",NULL,NULL);
insert into Products values(107,"Laptop","Electronics",999.99,50);
insert into Products values(108,"Wireless Earbuds","Accessories",NULL,100); 
```

**Output:**

<img width="1783" height="295" alt="image" src="https://github.com/user-attachments/assets/6140da9d-dd7d-4bb0-8e50-24d609700330" />


**Question 10**
---
Create a table named Orders with the following constraints:

OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
create table Orders (
OrderID INTEGER primary key,
OrderDate DATE not NULL,
CustomerID INTEGER references Customers(CustomerID) 

);
```
**Output:**

<img width="1787" height="222" alt="image" src="https://github.com/user-attachments/assets/352c759a-26d0-4f2d-bb01-3b54215a0671" />



**Module 1 SEB grades:**
---
<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/84d61cd8-c744-41bb-b2b5-d4f08062c1b7" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
