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
Write a SQL statement to Update the product_name to 'Premium Bread' whose product
ID is 5 in the products table. Products table
```sql
update products set product_name ='Premium Bread' where product_id=5;
```

**Output:**

<img width="758" height="299" alt="image" src="https://github.com/user-attachments/assets/451cc67e-500e-40c2-afec-bad4d4d2b371" />

**Question 2**
---
Write a SQL statement to Update the grade of all customers in Chennai city as 5.
Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
update Customer set grade=5 where city='Chennai';
```

**Output:**

<img width="766" height="343" alt="image" src="https://github.com/user-attachments/assets/5a593e2c-4b7a-400a-a062-36652a2ab306" />

**Question 3**
---
Salary will be increased by 25% for the department 40, 15% for department 90 and 10%
for the department 110 and the rest of the departments will remain same. Employees
table

```sql
update Employees set salary=salary+salary*0.25 where department_id=40;
update Employees set salary=salary+salary*0.15 where department_id=90;
update Employees set salary=salary+salary*0.1 where department_id=110;
```

**Output:**

<img width="781" height="334" alt="image" src="https://github.com/user-attachments/assets/fc80ab51-ae47-4d3b-b99e-e18c0dfecaac" />

**Question 4**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or
'Cardiology' and Last Name is Brown. Sample table: Doctors attributes : doctor_id,
first_name, last_name, specialization
```sql
DELETE FROM Doctors
WHERE last_name = 'Brown'
  AND specialization IN ('Pediatrics', 'Cardiology');
```

**Output:**

<img width="774" height="612" alt="image" src="https://github.com/user-attachments/assets/10d16cf0-1bdd-458a-b75b-3022b3ed80c8" />

**Question 5**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not
'New York' and 'OUTSTANDING_AMT' is greater than 5000. Sample table: Customer
```sql
delete from Customer where CUST_CITY!='New York' and OUTSTANDING_AMT>5000;
```

**Output:**

<img width="777" height="431" alt="image" src="https://github.com/user-attachments/assets/f04211df-d0dc-4158-9248-f76c7d77096d" />

**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose
'OUTSTANDING_AMT' is less than 5000 Sample table: Customer
```sql
DELETE FROM Customer
WHERE (grade = 3 OR agent_code = 'A008')
  AND outstanding_amt < 5000;
```

**Output:**

<img width="773" height="303" alt="image" src="https://github.com/user-attachments/assets/3247b3e9-1e3b-4606-9042-fd35c16b3c81" />

**Question 7**
---
Write a query to fetch last 5 rows in EmployeeInfo table.

```sql
select*from Employeeinfo order by EmpID desc limit 5;
```

**Output:**

<img width="776" height="252" alt="image" src="https://github.com/user-attachments/assets/d533e8d9-7008-467d-a87e-18a3a74ec704" />

**Question 8**
---
Write a query to get all the records from EmployeePosition table who have joined in the
year 2020.
```sql
SELECT *
FROM EmployeePosition
WHERE YEAR(JoinDate) = 2020;
```

**Output:**

<img width="778" height="240" alt="image" src="https://github.com/user-attachments/assets/35d30f07-5ca4-4b9f-8de4-8eddd38a8aaf" />

**Question 9**
---
Write a SQL query to label rows in the Calculations table as 'Even' if value1 is even,
otherwise 'Odd'.

```sql
SELECT id,
value1,
case
when value1%2=0 then 'Even'
ELSE 'Odd'
end as parity
from Calculations;
```

**Output:**

<img width="793" height="396" alt="image" src="https://github.com/user-attachments/assets/bbc73e19-54ea-40bc-874e-d072b086d2ba" />

**Question 10**
---
Write a query to calculate the discounted_price and discounted_price_percentage for
each product from the products table. Return product_id, original_price,
discount_percentage, discounted_price, and discounted_price_percentage. Discounted
Price: Calculate the price of the product after applying the discount. Discounted Price
Percentage: Calculate the percentage that the discounted price represents relative to
the original price.

```sql
select product_id,original_price,discount_percentage,(original_price-(origi
cast(round(((original_price-(original_price*discount_percentage))/original_
from products;
```

**Output:**

<img width="773" height="250" alt="image" src="https://github.com/user-attachments/assets/9337d310-4dd4-4f22-99a2-a89ed1cf2c28" />
<img width="767" height="111" alt="image" src="https://github.com/user-attachments/assets/030ef92e-4adf-4e7e-84bc-feefa265d819" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
