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
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

```sql
INSERT INTO student_details(RollNo,Name,Gender) VALUES (204,"Samuel Black","M");
```

**Output:**

<img width="1212" height="314" alt="Image" src="https://github.com/user-attachments/assets/a932abf6-6559-4077-8548-18412bb72c36" />

**Question 2**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```sql
CREATE TABLE Locations(
LocationID  INTEGER,
LocationName  TEXT,
Address  TEXT );
```

**Output:**

<img width="1195" height="377" alt="Image" src="https://github.com/user-attachments/assets/694cf865-6716-4261-89ea-969591ce1f59" />

**Question 3**
---
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
```
ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021
```
```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,year) 
VALUES('978-1234567890','Introduction to AI','John Doe',NULL,NULL),
('978-9876543210','Deep Learning','Jane Doe','TechPress',2022),
('978-1122334455','Cybersecurity Essentials','Alice Smith',NULL,2021);
```

**Output:**

<img width="1199" height="292" alt="Image" src="https://github.com/user-attachments/assets/fa2ce31a-0cd4-46c6-936e-4d572001417f" />

**Question 4**
---
Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE
```sql
create table Tasks
(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE 
);
```

**Output:**

<img width="1130" height="339" alt="Image" src="https://github.com/user-attachments/assets/1186937a-b92d-4417-a2a7-1e4d20557f43" />

**Question 5**
---
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE
```sql
create table Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE 
);
```

**Output:**

<img width="1192" height="334" alt="Image" src="https://github.com/user-attachments/assets/0d6834d0-356a-44b9-937a-20845faad117" />

**Question 6**
---
Write an SQL query to change the name of the column id to employee_id in the table employee.


```sql
alter table employee RENAME COLUMN id TO employee_id;
```

**Output:**

<img width="1001" height="196" alt="Image" src="https://github.com/user-attachments/assets/889a8bcd-9a85-4a0f-bb5d-6df48559c8a6" />

**Question 7**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock
```sql
insert into Products
select * from Discontinued_products
```

**Output:**

<img width="1185" height="267" alt="Image" src="https://github.com/user-attachments/assets/c11b083b-2fba-4f16-b749-f86a30b0eeb1" />

**Question 8**
---
Create a table named Products with the following columns:

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER
```sql
create table Products(
ProductID  INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);
```

**Output:**


<img width="1180" height="239" alt="Image" src="https://github.com/user-attachments/assets/c569a830-04c3-4d09-96d4-5e00f6f44f64" />

**Question 9**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
```sql
create table contacts
(
contact_id INTEGER primary key,
first_name TEXT not NULL,
last_name TEXT not NULL,
email TEXT,
phone TEXT NOT NULL CHECK(length(phone)>=10) 
);
```

**Output:**

<img width="1137" height="226" alt="Image" src="https://github.com/user-attachments/assets/a924011c-445b-479e-84f4-6ab13e379fb5" />

**Question 10**
---
Write a SQL Query  to add attribute Date_of_joining as Date and rename the attribute job_title as Designation in the table 'Employees'
```sql
ALTER TABLE Employees ADD Date_of_joining Date;
ALTER TABLE Employees RENAME COLUMN job_title TO Designation;
```

**Output:**

<img width="1182" height="234" alt="Image" src="https://github.com/user-attachments/assets/611b9996-a082-45a9-94b1-1a64434b2b37" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
