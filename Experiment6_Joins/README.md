
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
From the following tables write a SQL query to find the salesperson(s) and the
customer(s) he represents. Return Customer Name, city, Salesman, commission.
Sample table: customer
customer_id | cust_name | city | grade | salesman_id -------------+----------------+-------
-----+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad
Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002 3008 | Julian
Green | London | 300 | 5002 3004 | Fabian Johnson | Paris | 300 | 5006 3009 | Geoff
Cameron | Berlin | 100 | 5003 3003 | Jozy Altidor | Moscow | 200 | 5007 3001 | Brad
Guzan | London | | 5005 Sample table: salesman
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
3. RIGHT JOIN
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
4. FULL OUTER JOIN
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
Question 1
salesman_id | name | city | commission -------------+------------+----------+------------
5001 | James Hoog | New York | 0.15 5002 | Nail Knite | Paris | 0.13 5005 | Pit Alex |
London | 0.11 5006 | Mc Lyon | Paris | 0.14 5007 | Paul Adam | Rome | 0.13 5003 | Lauson
Hen | San Jose | 0.12

```sql
SELECT
T1.cust_name AS "Customer Name",
T1.city AS "city",
T2.name AS "Salesman",
T2.commission AS "commission"
FROM
customer AS T1
INNER JOIN
salesman AS T2
ON
T1.salesman_id = T2.salesman_id;
```

**Output:**

<img width="738" height="487" alt="image" src="https://github.com/user-attachments/assets/6d6432d2-22ec-4cf1-ae7a-a2e8dd4d71a9" />

**Question 2**
---
From the following tables write a SQL query to display the customer name, customer
city, grade, salesman, salesman city. The results should be sorted by ascending
customer_id.
Sample table: customer
SELECT
T1.cust_name AS "Customer Name",
T1.city AS "city",
T2.name AS "Salesman",
T2.commission AS "commission"
FROM
customer AS T1
INNER JOIN
salesman AS T2
ON
T1.salesman_id = T2.salesman_id;
Question 2
customer_id | cust_name | city | grade | salesman_id -------------+----------------+-------
-----+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad
Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002 3008 | Julian
Green | London | 300 | 5002 3004 | Fabian Johnson | Paris | 300 | 5006 3009 | Geoff
Cameron | Berlin | 100 | 5003 3003 | Jozy Altidor | Moscow | 200 | 5007 3001 | Brad
Guzan | London | | 5005 Sample table: salesman
salesman_id | name | city | commission -------------+------------+----------+------------
5001 | James Hoog | New York | 0.15 5002 | Nail Knite | Paris | 0.13 5005 | Pit Alex |
London | 0.11 5006 | Mc Lyon | Paris | 0.14 5007 | Paul Adam | Rome | 0.13 5003 | Lauson
Hen | San Jose | 0.12
```sql
SELECT
T1.cust_name,
T1.city,
T1.grade,
T2.name AS Salesman,
T2.city AS "city"
FROM
customer AS T1
INNER JOIN
salesman AS T2
ON
T1.salesman_id = T2.salesman_id
ORDER BY
T1.customer_id ASC;
```

**Output:**

<img width="783" height="463" alt="image" src="https://github.com/user-attachments/assets/5fddcc01-22ea-4efd-881f-7daf51686514" />

**Question 3**
---
Write the SQL query that achieves the selection of the first name from the "patients"
table, with an inner join on the "patient_id" column and a condition filtering for
surgeries with a surgery date of '2024-01-15'.:
PATIENTS TABLE:
name type
patient_id INT first_name VARCHAR(50) last_name VARCHAR(50) date_of_birth DATE
admission_date DATE discharge_date DATE doctor_id INT
SURGERIES TABLE:
name type
surgery_id INT patient_id INT surgeon_id INT surgery_date DATE

```sql
SELECT
T1.first_name
FROM
patients AS T1
INNER JOIN
surgeries AS T2
ON
T1.patient_id = T2.patient_id
WHERE
T2.surgery_date = '2024-01-15';
```

**Output:**

<img width="780" height="290" alt="image" src="https://github.com/user-attachments/assets/a8bffddc-aac5-4d28-b4fb-36031415f458" />

**Question 4**
---
Write the SQL query that achieves the selection of the "cust_name" column from the
"customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt"
columns from the "orders" table (aliased as "o"), with a left join on the "customer_id"
column and a condition filtering for orders with a purchase amount greater than 1000.
'customer' Table: (customer_id, cust_name, city, grade, salesman_id)
'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
SELECT
c.cust_name,
o.ord_no,
o.ord_date,
o.purch_amt
FROM
customer AS c
LEFT JOIN
orders AS o
ON
c.customer_id = o.customer_id
WHERE
o.purch_amt > 1000;
```

**Output:**

<img width="772" height="404" alt="image" src="https://github.com/user-attachments/assets/b498abfc-9881-4a76-a183-883989505dd8" />

**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients"
table (aliased as "patient_name") and all columns from the "appointments" table
(aliased as "a"), with an inner join on the "patient_id" column.
PATIENTS TABLE:
ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date,
discharge_date, doctor_id
APPOINTMENTS TABLE:
ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date
```sql
SELECT
T1.first_name AS patient_name,
T2.*
FROM
PATIENTS AS T1
INNER JOIN
APPOINTMENTS AS T2
ON
T1.patient_id = T2.patient_id;
```

**Output:**

<img width="778" height="281" alt="image" src="https://github.com/user-attachments/assets/2e311292-76cb-4d4c-8b3c-a0f60c19159f" />

**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "patients" table
(aliased as "p"), with an inner join on the "patient_id" column and a condition filtering
for appointments with an appointment date between '2024-02-01' and '2024-02-28'.
PATIENTS TABLE:
Question 5
SELECT
T1.first_name AS patient_name,
T2.*
FROM
PATIENTS AS T1
INNER JOIN
APPOINTMENTS AS T2
ON
T1.patient_id = T2.patient_id;
Question 6
ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date,
discharge_date, doctor_id
APPOINTMENTS TABLE:
ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date
```sql
SELECT
p.*
FROM
PATIENTS AS p
INNER JOIN
APPOINTMENTS AS a
ON
p.patient_id = a.patient_id
WHERE
a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28'
GROUP BY
p.patient_id;
```

**Output:**

<img width="787" height="194" alt="image" src="https://github.com/user-attachments/assets/4b2340ab-ff10-4ce9-b5fc-08fe059e2752" />

**Question 7**
---
write a SQL query to find the salesperson and customer who reside in the same city.
Return Salesman, cust_name and city.
Sample table: salesman
salesman_id | name | city | commission -------------+------------+----------+------------
5001 | James Hoog | New York | 0.15 5002 | Nail Knite | Paris | 0.13 5005 | Pit Alex |
London | 0.11 5006 | Mc Lyon | Paris | 0.14 5007 | Paul Adam | Rome | 0.13 5003 | Lauson
Hen | San Jose | 0.12 Sample table: customer
SELECT
p.*
FROM
PATIENTS AS p
INNER JOIN
APPOINTMENTS AS a
ON
p.patient_id = a.patient_id
WHERE
a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28'
GROUP BY
p.patient_id;
Question 7
customer_id | cust_name | city | grade | salesman_id -------------+----------------+-------
-----+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad
Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002 3008 | Julian
Green | London | 300 | 5002 3004 | Fabian Johnson | Paris | 300 | 5006 3009 | Geoff
Cameron | Berlin | 100 | 5003 3003 | Jozy Altidor | Moscow | 200 | 5007 3001 | Brad
Guzan | London | | 5005
```sql
SELECT
s.name AS Salesman,
c.cust_name,
s.city
FROM
salesman s
INNER JOIN
customer c
ON
s.city = c.city;
```

**Output:**

<img width="780" height="553" alt="image" src="https://github.com/user-attachments/assets/143f3d5c-8dbe-412a-a386-0e2d54ee5acf" />

**Question 8**
---
Write an SQL query to select the 'cust_name' column from the 'customer' table (aliased
as 'c'), using a LEFT JOIN with the 'orders' table based on the 'customer_id' column.
'customer' Table: (customer_id, cust_name, city, grade, salesman_id)
'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)
```sql
SELECT
c.cust_name
FROM
customer AS c
LEFT JOIN
orders AS o
ON
c.customer_id = o.customer_id;
```

**Output:**

<img width="774" height="500" alt="image" src="https://github.com/user-attachments/assets/30bdddfd-9b74-4bfc-b0b1-d3c08cc2c872" />

**Question 9**
---
SQL statement to generate a report with customer name, city, order number, order
date, order amount, salesperson name, and commission to determine if any of the
existing customers have not placed orders or if they have placed orders through their
salesman or by themselves.
Sample table: customer
customer_id | cust_name | city | grade | salesman_id -------------+----------------+-------
-----+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad
Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002 3008 | Julian
Green | London | 300 | 5002 3004 | Fabian Johnson | Paris | 300 | 5006 3009 | Geoff
Cameron | Berlin | 100 | 5003 3003 | Jozy Altidor | Moscow | 200 | 5007 3001 | Brad
Guzan | London | | 5005 Sample table: orders
ord_no purch_amt ord_date customer_id salesman_id
customer AS c
LEFT JOIN
orders AS o
ON
c.customer_id = o.customer_id;
Question 9
70001 150.5 2012-10-05 3005 5002 70009 270.65 2012-09-10 3001 5005 70002 65.26
2012-10-05 3002 5001 70004 110.5 2012-08-17 3009 5003 70007 948.5 2012-09-10
3005 5002 70005 2400.6 2012-07-27 3007 5001 70008 5760 2012-09-10 3002 5001
70010 1983.43 2012-10-10 3004 5006 70003 2480.4 2012-10-10 3009 5003 70012
250.45 2012-06-27 3008 5002 70011 75.29 2012-08-17 3003 5007 70013 3045.6 2012-
04-25 3002 5001 Sample table: salesman
salesman_id | name | city | commission -------------+------------+----------+------------
5001 | James Hoog | New York | 0.15 5002 | Nail Knite | Paris | 0.13 5005 | Pit Alex |
London | 0.11 5006 | Mc Lyon | Paris | 0.14 5007 | Paul Adam | Rome | 0.13 5003 | Lauson
Hen | San Jose | 0.12

```sql
SELECT
T1.cust_name,
T1.city,
T2.ord_no,
T2.ord_date,
T2.purch_amt AS "Order Amount",
T3.name AS name,
T3.commission
FROM
customer AS T1
LEFT JOIN
orders AS T2
ON
T1.customer_id = T2.customer_id
LEFT JOIN
salesman AS T3
ON
T1.salesman_id = T3.salesman_id;
```

**Output:**

<img width="774" height="500" alt="image" src="https://github.com/user-attachments/assets/33a2d856-206c-43e6-a03c-9358a5aae68e" />

**Question 10**
---
From the following tables write a SQL query to find salespeople who received
commissions of more than 12 percent from the company. Return Customer Name,
customer city, Salesman, commission.
Sample table: customer
customer_id | cust_name | city | grade | salesman_id -------------+----------------+-------
-----+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad
Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002 3008 | Julian
Green | London | 300 | 5002 3004 | Fabian Johnson | Paris | 300 | 5006 3009 | Geoff
Cameron | Berlin | 100 | 5003 3003 | Jozy Altidor | Moscow | 200 | 5007 3001 | Brad
Guzan | London | | 5005 Sample table: salesman
salesman_id | name | city | commission -------------+------------+----------+------------
5001 | James Hoog | New York | 0.15 5002 | Nail Knite | Paris | 0.13 5005 | Pit Alex |
London | 0.11 5006 | Mc Lyon | Paris | 0.14 5007 | Paul Adam | Rome | 0.13 5003 | Lauson
Hen | San Jose | 0.12
```sql
SELECT
T1.cust_name AS "Customer Name",
T1.city AS "city",
T2.name AS Salesman,
T2.commission AS commission
FROM
customer AS T1
INNER JOIN
salesman AS T2
ON
T1.salesman_id = T2.salesman_id
WHERE
T2.commission > 0.12;
```

**Output:**

<img width="781" height="731" alt="image" src="https://github.com/user-attachments/assets/16cabfb5-af7d-4f7f-851d-f87315cdf46a" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
