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
How many patients have insurance coverage valid in each year?

Sample table:Insurance Table

```sql
select substr(ValidityPeriod,1,4) as ValidityYear ,count(ValidityPeriod) as TotalPatients from Insurance group by ValidityYear order by ValidityYear ;
```

**Output:**

<img width="672" height="374" alt="image" src="https://github.com/user-attachments/assets/8d9f61d1-9aff-40c3-b111-879033541613" />


**Question 2**
---
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

```sql
select PatientID,count(PatientID) as AvgMedications from MedicalRecords group by PatientID order by PatientID;
```

**Output:**

<img width="622" height="583" alt="image" src="https://github.com/user-attachments/assets/3a3b0c78-0ea4-4d45-ad21-59bcb8da448a" />


**Question 3**
---
How many appointments are scheduled for each patient?

Sample table: Appointments Table

```sql
select PatientID,count(PatientID) as TotalAppointments from Appointments group by PatientID order by PatientID; 
```

**Output:**

<img width="691" height="615" alt="image" src="https://github.com/user-attachments/assets/12e059b3-5893-4ef8-8c83-e4969d4a4ec3" />


**Question 4**
---
Write a SQL query to find the average length of email addresses (in characters):

Table: customer

```sql
Select avg(length(email)) as avg_email_length from customer;
```

**Output:**

<img width="483" height="284" alt="image" src="https://github.com/user-attachments/assets/5f65cffd-058f-42bc-a211-4dd2fa69264f" />


**Question 5**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

Sample table: customer1

```sql
select address,SUM(salary) from customer1 group by address having sum(salary)>2000 ;  
```

**Output:**

<img width="611" height="453" alt="image" src="https://github.com/user-attachments/assets/5d467060-b8a7-45d9-abe7-2e3dfdf57396" />


**Question 6**
---
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee

```sql
Select count(distinct age) as COUNT from employee;
```

**Output:**

<img width="381" height="296" alt="image" src="https://github.com/user-attachments/assets/bdbcce07-1b24-42a5-9b62-fccca898cbe2" />


**Question 7**
---
Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee

```sql
Select count(age) as COUNT from employee where age>32; 
```

**Output:**

<img width="383" height="289" alt="image" src="https://github.com/user-attachments/assets/d4545591-e191-4957-a03d-c04e85e2a30b" />


**Question 8**
---
Write a SQL query to count the number of customers. Return number of customers.

Sample table: customer

```sql
select count(customer_id) as COUNT from customer;
```

**Output:**

<img width="348" height="284" alt="image" src="https://github.com/user-attachments/assets/375131c0-5fa0-45d3-8237-3bb6b0768590" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1

```sql
select occupation,MIN(workhour) from employee1 where workhour>8 group by occupation ;
```

**Output:**

<img width="636" height="436" alt="image" src="https://github.com/user-attachments/assets/65e048cf-8cf4-4fa2-9292-af5bd5f7d756" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1

```sql
select occupation,SUM(workhour) from employee1 group by occupation having sum(workhour)>20; 
```

**Output:**

<img width="592" height="393" alt="image" src="https://github.com/user-attachments/assets/e84b2ed7-e65e-4170-b7fc-e858c2dc9458" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
