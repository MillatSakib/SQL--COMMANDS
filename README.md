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
