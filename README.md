# SQL--COMMANDS

### 1. Show Commands;

SHOW DATABASES;

### 2. Create Database;

CREATE DATABASE COLLAGE;

### 3. Delete Database;

DROP DATABASE COLLAGE;

### 4. Create Table

CREATE TABLE student(
Roll int,
Name varchar(15),
Gender varchar(10),
Age int(5),
GPA double(3,2),
City varchar(15),
PRIMARY KEY(Roll)
);

### 5. Rename Table

RENAME TABLE student TO student_details;

### 6. Drop Table

DROP TABLE student_details;
