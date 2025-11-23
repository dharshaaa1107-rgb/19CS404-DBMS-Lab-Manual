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
Write a SQL query to Add a new column named "discount" with the data type
DECIMAL(5,2) to the "customer" table.
Sample table: customer
customer_id | cust_name | city | grade | salesman_id -------------+----------------+-------
-----+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad
Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002
```sql
ALTER TABLE customer
ADD COLUMN discount DECIMAL(5,2);
```

**Output:**

<img width="778" height="277" alt="image" src="https://github.com/user-attachments/assets/4a400ef3-fbd9-4bd6-a53f-f15b01858e1a" />

**Question 2**
---
Create a table named Events with the following columns: EventID as INTEGER
EventName as TEXT EventDate as DATE

```sql
CREATE TABLE Events (
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

<img width="771" height="288" alt="image" src="https://github.com/user-attachments/assets/e7844a8c-9ac9-44d2-b155-514bb7a2531e" />

**Question 3**
---
Create a table named ProjectAssignments with the following constraints: AssignmentID
as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key
referencing Employees(EmployeeID). ProjectID as INTEGER should be a foreign key
referencing Projects(ProjectID). AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments (
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="780" height="114" alt="image" src="https://github.com/user-attachments/assets/9faddc79-8a60-493e-bcca-7534fc5be88d" />

**Question 4**
---
Write a SQL query to Add a new column Mobilenumber as number in the
Student_details table.
Sample table: Student_details
cid name type notnu dflt_value pk
0 RollNo int 0 1 1 Name VARCHAR(100) 1 0 2 Gender TEXT 1 0 3 Subject VARCHAR(30)
0 0 4 MARKS INT (3) 0 0


```sql
ALTER TABLE Student_details
ADD COLUMN Mobilenumber number;
```

**Output:**

<img width="778" height="128" alt="image" src="https://github.com/user-attachments/assets/21c06121-e71b-4a63-84f6-380b7bbce063" />

**Question 5**
---
Create a table named Department with the following constraints: DepartmentID as
INTEGER should be the primary key. DepartmentName as TEXT should be unique and
not NULL. Location as TEXT
```sql
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
```

**Output:**

<img width="777" height="117" alt="image" src="https://github.com/user-attachments/assets/0739fd88-86ca-4112-be02-d4e90edf66e2" />

**Question 6**
---
create a table named jobs including columns job_id, job_title, min_salary and
max_salary, and make sure that, the default value for job_title is blank and min_salary is
8000 and max_salary is NULL will be entered automatically at the time of insertion if no
value assigned for the specified columns.

```sql
CREATE TABLE jobs (
job_id INTEGER PRIMARY KEY,
job_title TEXT DEFAULT '',
min_salary INTEGER DEFAULT 8000,
max_salary INTEGER DEFAULT NULL
);

```

**Output:**

<img width="779" height="132" alt="image" src="https://github.com/user-attachments/assets/bdbefe38-3172-4679-8dca-ecc137b2c3ea" />

**Question 7**
---
Create a table named Orders with the following constraints: OrderID as INTEGER should
be the primary key. OrderDate as DATE should be not NULL. CustomerID as INTEGER
should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders (
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="774" height="98" alt="image" src="https://github.com/user-attachments/assets/77620fdc-8fe6-4cd1-a3b1-b3724333501a" />

**Question 8**
---
Insert all customers from Old_customers into Customers
Table attributes are CustomerID, Name, Address, Email

```sql
INSERT INTO Customers (CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers;
```

**Output:**

<img width="775" height="130" alt="image" src="https://github.com/user-attachments/assets/7ee54d17-f4e1-4d4d-84e2-cc554f1d1119" />

**Question 9**
---
In the Student_details table, insert a student record where some fields are NULL,
another record where all fields are filled without any NULL values, and a third record
where some fields are filled, and others are left as NULL.
RollNo Name Gender Subject MARKS
205 Olivia Green F 207 Liam Smith M Mathematics 85 208 Sophia Johnson F Science

```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (205, 'Olivia Green', 'F');
INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (207, 'Liam Smith', 'M', 'Mathematics', 85);
INSERT INTO Student_details (RollNo, Name, Gender, Subject)
VALUES (208, 'Sophia Johnson', 'F', 'Science');
```

**Output:**

<img width="777" height="123" alt="image" src="https://github.com/user-attachments/assets/45fdd711-f3b7-40e1-b21e-8e4e8f6b058e" />

**Question 10**
---
Insert the below data into the Student_details table, allowing the Subject and MARKS
columns to take their default values.
RollNo Name Gender
204 Samuel Black M
Note: The Subject and MARKS columns will use their default values.
```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (204, 'Samuel Black', 'M');
```

**Output:**
<img width="782" height="150" alt="image" src="https://github.com/user-attachments/assets/71958f86-550b-4fa8-ab45-0c1b6502e77c" />

COMPELETION STATUS :
<img width="791" height="131" alt="image" src="https://github.com/user-attachments/assets/18cf5a7c-3bbf-44a1-886d-3db6635ef745" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
