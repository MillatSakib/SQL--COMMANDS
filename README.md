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

### 8.
