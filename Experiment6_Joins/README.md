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
Write an SQL query to select the 'cust_name' column from the 'customer' table (aliased as 'c'), using a LEFT JOIN with the 'orders' table based on the 'customer_id' column.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
SELECT c.cust_name
FROM customer AS c
LEFT JOIN orders AS o ON c.customer_id = o.customer_id;

```

**Output:**

<img width="355" height="909" alt="image" src="https://github.com/user-attachments/assets/d67b7795-6f6a-443e-854e-1a00c7e78ff4" />


**Question 2**
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
    customer c ON o.customer_id = c.customer_id
WHERE 
    o.purch_amt BETWEEN 500 AND 2000;

```

**Output:**

<img width="1216" height="399" alt="image" src="https://github.com/user-attachments/assets/1eef1b24-49ca-41b2-91c7-25682fdecf66" />


**Question 3**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS city,
    s.name AS Salesman,
    s.commission AS commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id;

```

**Output:**

<img width="1222" height="799" alt="image" src="https://github.com/user-attachments/assets/3a66c2ba-eece-4e8d-9f30-8ed718929211" />


**Question 4**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

```sql
SELECT s.name AS Salesman, c.cust_name, s.city
FROM salesman s
JOIN customer c ON s.city = c.city;

```

**Output:**

<img width="961" height="606" alt="image" src="https://github.com/user-attachments/assets/1dd5b0a1-e828-405f-9b12-5839622845a9" />


**Question 5**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1848" height="861" alt="image" src="https://github.com/user-attachments/assets/83b44ce1-3728-4f6f-8b2e-718b0ff66b1b" />


**Question 6**
---
Write an SQL query that retrieves all columns from the 'customer' table (using the alias 'c'), performs a LEFT JOIN with the 'orders' table on the 'customer_id' column, and includes only those orders with an order date after '2012-08-17'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
SELECT c.*
FROM customer AS c
LEFT JOIN orders AS o ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';

```

**Output:**

<img width="1681" height="881" alt="image" src="https://github.com/user-attachments/assets/ff4c9d61-e10c-4d81-a442-685ea4f78d73" />


**Question 7**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

```sql
SELECT 
    c.cust_name AS "Customer Name", 
    c.city AS city, 
    s.name AS Salesman, 
    s.city AS city, 
    s.commission 
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city 
    AND s.commission > 0.12;

```

**Output:**

<img width="1246" height="478" alt="image" src="https://github.com/user-attachments/assets/37568f18-ae2c-4b30-8d05-31018406b6d7" />


**Question 8**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.  

```sql
SELECT 
    p.first_name AS patient_name, 
    d.first_name AS doctor_name 
FROM 
    patients p 
INNER JOIN 
    doctors d 
ON 
    p.doctor_id = d.doctor_id 
WHERE 
    p.date_of_birth > '1990-01-01';

```

**Output:**

<img width="776" height="377" alt="image" src="https://github.com/user-attachments/assets/e68c1d7c-9465-44fd-9b28-076806f12ea5" />


**Question 9**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

```sql
SELECT p.first_name AS patient_name, t.test_name
FROM patients AS p
INNER JOIN test_results AS t ON p.patient_id = t.patient_id;

```

**Output:**

<img width="760" height="519" alt="image" src="https://github.com/user-attachments/assets/be65a78a-6eac-4fd8-8767-c6e53cfaba28" />


**Question 10**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```sql
SELECT 
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM 
    patients p
INNER JOIN 
    doctors d ON p.doctor_id = d.doctor_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="722" height="367" alt="image" src="https://github.com/user-attachments/assets/2a90f3d7-d410-4f30-a91e-9f97cfbe9355" />

**Module 5 SEB grades**
---
<img width="1850" height="849" alt="image" src="https://github.com/user-attachments/assets/93fcf979-61d5-4c3f-81bb-8be1b220840d" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
