# SQL--COMMANDS

### 1. Show Commands;

```sql
SHOW DATABASES;
```

### 2. Create Database;

```sql
CREATE DATABASE COLLAGE;
```

### 3. Delete Database;

```sql
DROP DATABASE COLLAGE;
```

### 4. Create Table

```sql
CREATE TABLE student(
Roll int,
Name varchar(15),
Gender varchar(10),
Age int(5),
GPA double(3,2),
City varchar(15),
PRIMARY KEY(Roll)
);
```

### 5. Rename Table

```sql
RENAME TABLE student TO student_details;
```

### 6. Drop Table

```sql
DROP TABLE student_details;
```

### 7. Insert Table

For multiple insertion

```sql
INSERT INTO student_details
VALUES
(103, 'Rahim', 'Male', 18, 3.44, 'Sylhet'),
(104, 'Hasina', 'Female', 10, 4.44, 'Dhaka');
```

For single insertion

```sql
INSERT INTO student_details
VALUES
(103, 'Rahim', 'Male', 18, 3.44, 'Sylhet');
```

### 8. Select Columns

One column select

```sql
SELECT NAME
FROM student_details
```

Multi column select

```sql
SELECT Roll,NAME
FROM student_details
```

All column select

```sql
SELECT*
FROM student_details
```

### 9. DISTINCT and LIMIT keyword

Soupose you want to see student are come from how many city. If we use select the all columnt we get and there might be duplicate. But you want if there have duplicate of data then it will show one data then you can use `DISTINC` keyword.

```sql
SELECT DISTINCT *
FROM student_details;
```

Then if we want to limit the number the returning data then we can use `LIMIT` keyword.

```sql
SELECT *
FROM student_details
LIMIT 5;
```

### 10. Sort

We can sort in ascending order and descending order. For Ascending order we haven't add asc keyword but for descending order we have to add `DESC` keyword.

`For Ascending order`:

```sql
SELECT Name, GPA
FROM student_details
ORDER BY GPA;
```

`For Descending order`:

```sql
SELECT Name, GPA
FROM student_details
ORDER BY GPA DESC;
```

### 11. WHERE

```sql
SELECT *
FROM student_details
WHERE NAME='MANSINA';
```

```sql
SELECT *
FROM student_details
WHERE Roll BETWEEN 100 AND 110;
```

```sql
SELECT *
FROM student_details
WHERE Gender="Male" OR GPA>= 3.50;
```

```sql
SELECT *
FROM student_details
WHERE Gender="Male" AND GPA>= 3.50;
```

We can use `IN` keyword instead of multiple `OR` operator.

```sql
SELECT *
FROM student_details
WHERE City IN ('Sylhet', 'Dhaka', 'Barisal');
```

```sql
SELECT *
FROM student_details
WHERE City NOT IN ('Sylhet', 'Dhaka', 'Barisal');
```

### 12. `LIKE` keyword

Using `LIKE` keyword we can we can define a pattern and match the pattern with our database data. And Example are given below:

```sql
SELECT *
FROM student_details
WHERE Name LIKE '%S';
```

Here we say that the data will return which string has `s` at last. No matter at first the string which character have there.

In the given below example we can see that how can we find which string are start with character `s`

```sql
SELECT *
FROM student_details
WHERE Name LIKE 'S%';
```

We can also skip the character fist and last but match in the middle of the string like below

```sql
SELECT *
FROM student_details
WHERE Name LIKE '%hi%'
```

Here we get that data where `hi` string are available inside the string.

We can skip checking the pattern of first character using `_` this underscore. If we have to skip multiple character then we can use multiple underscore.

```sql
SELECT *
FROM student_details
WHERE Name LIKE '__u';
```

Here we checking the 3rd character are `u` or not.

### 13. `AS` Keyword

If we change the column name of generated data then we can use `AS` keyword. The syntax are given below:

```sql
SELECT Roll as ID, Name AS First_Name
FROM student_details;
```

### 14. SQL Constraints

SQL constraints are used to specify rules for table data. Some times we don't drop any data for a field. But we don't want that field would be be blank. Or we want to the value of that field will be unique. We can achive that using `SQL Constrain`. A constraint in SQL is a rule applied to columns in a table to control the type of data that can go into a table. Constraints help maintain the accuracy, integrity, and reliability of your data. There are 7 type of SQL Constrain. That are:

1. NOT NULL
2. UNIQUE
3. PRIMARY KEY -> NOT NULL + UNIQUE
4. Composite Key.
5. Foreign Key.
4. CHECK -> Determines whether the value is valid or not from a logical expression.
5. DEFAULT -> While inserting data into a table, if no value is supplied to a column, then the column gets the value set as DEFAULT.

**NOT NULL:** Some value we want never be `NULL`. Like we want the value of `name` attribute will never be null. For this we will have to define like below:

```sql
CREATE TABLE student_details
(
    Name varchar(15) NOT NULL
);
```

**Unique:** Some value we want to make it alawys unique. Like in our database we want that all the email will be unique. Then we can use `UNIQUE` constraints. Like below:

```sql
CREATE TABLE student_details
(
   email VARCHAR(100) UNIQUE
);
```
**PRIMARY KEY:** In each and every table there must have primary key. Primary key alawys be `NULL` and `UNIQUE`. We can define primary key in two ways. Like the easiest way is write primary key beside the attributes. Like below:
```sql
CREATE TABLE student_details
(
   id INT PRIMARY KEY AUTO_INCREMENT
);
```
We can also define primary key like below:
```sql
CREATE TABLE student_details
(
   id INT AUTO_INCREMENT,
   PRIMARY KEY(id)
);
```
We can also define primary key like below:

```sql
CREATE TABLE student_details
(
    ID int NOT NULL AUTO_INCREMENT,
    Name varchar(15) NOT NULL,
    Salary double(10,2),
    PRIMARY KEY(ID)
);
```
**COMPOSITE KEY:** Some time there have no primary key in the relation by which we can identify a record. On that time we can use `COMPOSITE KEY` to identify a record uniquely. The sql syntax of `COMPOSITE KEY` are given below:

```sql
CREATE TABLE diplomas(
	student_name VARCHAR(50) NOT NULL,
	course INT NOT NULL,
	d_date DATE,
	successful CHAR(1),
    location VARCHAR(50),
    PRIMARY KEY(student_name(50), course,d_date)
);
```

**FOREIGN KEY:** We can conncet two table using foreign key. When there have any relationship within two relation then we can maintain the relationship using foreign key. Let say we have two table name team1 and players. On players table the `Primary key` is `player_no`. If we want to use it as primary key then it will be like below:

```sql
CREATE TABLE team2(
	team_no INT NOT NULL,
	player_no int NOT NULL,
    division CHAR(15),
    PRIMARY KEY(team_no),
    FOREIGN KEY(player_no) REFERENCES players(player_no)
);
```

**CHECK Constraints:** The CHECK constraint is used to limit the values that can be stored in a column. It ensures that all values in a column satisfy a specific condition.

```sql
CREATE TABLE students (
    id INT,
    age INT CHECK (age >= 18)
);

```
Or using ALTER TABLE:

```sql
ALTER TABLE students
ADD CHECK (age >= 18);
```
**DEFAULT Constraint:** The DEFAULT constraint is used to assign a default value to a column when no value is specified during an insert.
```sql
CREATE TABLE users (
    id INT,
    status VARCHAR(10) DEFAULT 'active'
);

```
Or using ALTER TABLE:
```sql
ALTER TABLE users
ALTER COLUMN status SET DEFAULT 'active';
```

### 15. Upate SQL

```sql
UPDATE student_details
SET Name='Md. Sohan Millat Sakib', salary=520000
WHERE ID = 1002;
```

### 16. DELETE SQL

```sql
DELETE FROM STUDENT
WHERE ID=1002;
```

### 17. AGGREGATION:

```sql
SELECT COUNT(*),
MAX(Salary), MIN(Salary), SUM(Salary), AVG(Salary)
FROM teacher;
```

### 18. Sub Query in SQL

```sql
SELECT *
FROM teacher
WHERE Salary > SELECT AVG(Salary)FROM teacher;
```


## 19.Alter
### What is `ALTER` in SQL?

The `ALTER` statement is used to **modify the structure of an existing table** in a database without deleting or recreating it. It can be used to:

- Add, modify, or delete columns
- Rename columns or tables
- Add or remove constraints

---

### Commands

#### 1. Add New Column

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

**Example:**
```sql
ALTER TABLE student
ADD email VARCHAR(100);
```

---

#### 2. Modify Existing Column Type or Size

```sql
ALTER TABLE table_name
MODIFY column_name new_datatype;
```

**Example:**
```sql
ALTER TABLE student
MODIFY name VARCHAR(100);
```

---

#### 3. Rename a Column

```sql
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;
```

**Example:**
```sql
ALTER TABLE student
RENAME COLUMN name TO full_name;
```

---

#### 4. Rename a Table

```sql
RENAME TABLE old_table_name TO new_table_name;
```

**Example:**
```sql
RENAME TABLE student TO learners;
```

---

#### 5. Drop a Column

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

**Example:**
```sql
ALTER TABLE student
DROP COLUMN email;
```

---

#### 6. Add a Primary Key

```sql
ALTER TABLE table_name
ADD PRIMARY KEY (column_name);
```

**Example:**
```sql
ALTER TABLE student
ADD PRIMARY KEY (student_id);
```

---

#### 7. Add a Foreign Key

```sql
ALTER TABLE table_name
ADD CONSTRAINT fk_name
FOREIGN KEY (column_name)
REFERENCES other_table (column_name);
```

**Example:**
```sql
ALTER TABLE enrollment
ADD CONSTRAINT fk_student
FOREIGN KEY (student_id)
REFERENCES student (student_id);
```

---

#### 8. Drop Primary Key

```sql
ALTER TABLE table_name
DROP PRIMARY KEY;
```

**Example:**
```sql
ALTER TABLE student
DROP PRIMARY KEY;
```

---

#### 9. Drop Foreign Key

```sql
ALTER TABLE table_name
DROP FOREIGN KEY fk_name;
```

**Example:**
```sql
ALTER TABLE enrollment
DROP FOREIGN KEY fk_student;
```

---

#### 10. Add Unique Constraint

```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name UNIQUE (column_name);
```

**Example:**
```sql
ALTER TABLE student
ADD CONSTRAINT unique_email UNIQUE (email);
```

---

#### 11. Drop Unique Constraint

```sql
ALTER TABLE table_name
DROP INDEX constraint_name;
```

**Example:**
```sql
ALTER TABLE student
DROP INDEX unique_email;
```

---

#### 12. Change Column Name and Type (MySQL syntax)

```sql
ALTER TABLE table_name
CHANGE old_column_name new_column_name datatype;
```

**Example:**
```sql
ALTER TABLE student
CHANGE full_name name VARCHAR(50);
```


### 20.Group By Clause:

We can divide rows in a table into smaller groups by using the GROUP BY clause. Let I have a table below:
| ID | Name | Salary | Department |
|------|------------------|----------|------------|
| 1000 | Alak kanti shar | 35000.00 | CSE |
| 1001 | Rumel M S PIR | 45000.00 | EEE |
| 1002 | Saiful Ambia | 32000.00 | CSE |
| 1003 | Rubel | 9000.00 | EEE |
| 1006 | Selina | 32000.00 | CSE |
| 1007 | Asad | 38000.00 | EEE |
| 1008 | Sohid | 33500.00 | BBA |
| 1009 | Alin | 33000.00 | BBA |
| 1010 | Dola Barua | 32000.00 | CSE |

Now I want to find out the total salary of CSE, EEE, BBA faculty. How can I do it? We can do it using `Group By Clause`.

The syntax of create Group By clause are given below:

```
SELECT column, group_function(column)
FROM table
[WHERE condition]
[GROUP BY group_by_expression]
[ORDER BY column];
```

But we have to remember that If we use where, group and order with together then we have to write Group after where and before order.

```sql
SELECT Department, SUM(Salary)
FROM teacher
GROUP BY Department
ORDER BY SUM(Salary) DESC;
```
