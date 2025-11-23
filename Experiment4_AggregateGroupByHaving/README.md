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
How many medical records does each doctor have?
Sample table:MedicalRecords Table
For example:
Result DoctorID TotalRecords
3 4 5 1 6 1 7 1 8 3
```sql
SELECT DoctorID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```

**Output:**

<img width="776" height="353" alt="image" src="https://github.com/user-attachments/assets/8e421862-b6c2-44dc-8d33-9df88aa7bb2e" />

**Question 2**
---
What is the most common diagnosis among patients?
Sample table:MedicalRecords Table
For example:
Result Diagnosis DiagnosisCount
Childhood vaccination 3

```sql
SELECT DoctorID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```

**Output:**

<img width="775" height="238" alt="image" src="https://github.com/user-attachments/assets/5cddd573-2216-4d7f-a5ea-e5337bf2debe" />

**Question 3**
---
How many patients have expired insurance coverage for each insurance company?
Sample table:Insurance Table
For example:
Result InsuranceCompany TotalExpiredPatients
ABC Insurance 1 DEF Insurance 1 GHI Insurance 1 JKL Insurance 1 MNO Insurance 1
PQR Insurance 1 STU Insurance 1 VWX Insurance 1 XYZ Insurance 1 YZA Insurance 1
```sql
SELECT InsuranceCompany,
       COUNT(*) AS TotalExpiredPatients
FROM Insurance
WHERE ExpiryDate < CURRENT_DATE
GROUP BY InsuranceCompany;
```

**Output:**

<img width="774" height="626" alt="image" src="https://github.com/user-attachments/assets/2acfbb86-5911-40e2-ba5b-bf5f6501ca96" />

**Question 4**
---
Write a SQL query to calculate the average purchase amount of all orders. Return
average purchase amount.
Sample table: orders
ord_no purch_amt ord_date customer_id salesman_id
70001 150.5 2012-10-05 3005 5002
70009 270.65 2012-09-10 3001 5005
70002 65.26 2012-10-05 3002 5001
For example:
1461.765
```sql
select avg(purch_amt) as AVERAGE from orders
```

**Output:**

<img width="699" height="433" alt="image" src="https://github.com/user-attachments/assets/238f2df1-31a1-4374-bd5f-cb09090d957d" />

**Question 5**
---
Write a SQL query to find the total income of employees aged 40 or above.
Table: employee
name type
id INTEGER name TEXT age INTEGER city TEXT income INTEGER For example:
1800000

```sql
select sum(income) as total_income from employee where age>=40
```

**Output:**

<img width="780" height="431" alt="image" src="https://github.com/user-attachments/assets/127846f3-2392-44c3-8801-bff49ab1f992" />

**Question 6**
---
Write a SQL query to calculate total purchase amount of all orders. Return total
purchase amount.
Sample table: orders
ord_no purch_amt ord_date customer_id salesman_id
Question 5
Result total_income
select sum(income) as total_income from employee where age>=40
Question 6
70001 150.5 2012-10-05 3005 5002
70009 270.65 2012-09-10 3001 5005
70002 65.26 2012-10-05 3002 5001
For example:
17541.18
```sql
select sum(purch_amt) as TOTAL from orders
```

**Output:**

<img width="692" height="433" alt="image" src="https://github.com/user-attachments/assets/c1d07f19-94f3-4085-8540-014964e27976" />

**Question 7**
---
Write a SQL query to find the total number of unique cities in the customer table?
Table: customer
name type
id INTEGER name TEXT city TEXT email TEXT phone INTEGER For example:
10
```sql
select count(DISTINCT city) as unique_cities from customer;
```

**Output:**

<img width="762" height="430" alt="image" src="https://github.com/user-attachments/assets/2c798815-b6ba-459c-be4b-cf255ef355d1" />

**Question 8**
---
Write a SQL query to identify the cities (addresses) where the average salary is greater
than Rs. 5000, as per the "customer1" table.
Sample table: customer1
For example:
Result address AVG(salary)
Bhopal 8500.0 Indore 10000.0 Mumbai 6500.0
```sql
SELECT address,
       AVG(salary) AS avg_salary
FROM customer1
GROUP BY address
HAVING AVG(salary) > 5000;
```

**Output:**

<img width="774" height="501" alt="image" src="https://github.com/user-attachments/assets/2be1e017-278d-4ae4-bde4-326b5c44e189" />

**Question 9**
---
Write the SQL query that performs grouping by age groups and displays the maximum
salary for each group, excluding groups where the maximum salary is not greater than
8000.
Note: Calculate the age group as multiples of 5.
Eg., 20,22,23 comes in age group 20.
25,27,29 comes in age group 25.
Sample table: customer1
For example:
Result age_group MAX(salary)
20 10000 25 8500

```sql
SELECT 
    (age - (age % 5)) AS age_group,
    MAX(salary) AS max_salary
FROM customer1
GROUP BY (age - (age % 5))
HAVING MAX(salary) > 8000;
```

**Output:**

<img width="772" height="409" alt="image" src="https://github.com/user-attachments/assets/0888dba6-4a3a-4e88-9b94-38340b33861d" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by age intervals using the
expression (age/5)5, calculates the total salary sum for each group, and excludes groups
where the total salary sum is not greater than 5000.
Sample table: customer1
For example:
Result age_group SUM(salary)
20 16500 25 16500
```sql
SELECT 
    (age / 5) * 5 AS age_group,
    SUM(salary) AS total_salary
FROM customer1
GROUP BY (age / 5) * 5
HAVING SUM(salary) > 5000;
```

**Output:**

<img width="777" height="412" alt="image" src="https://github.com/user-attachments/assets/efa36edc-2c67-45ba-a544-d1947e22674d" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
