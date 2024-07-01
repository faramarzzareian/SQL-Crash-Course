#   SQL Fundamentals Crash Course

## A comprehensive guide to   fundamentals for beginners and intermediate users.
### Table of Contents

    1.Introduction
    2.Database Basics
    3.Table Operations
    4.Querying Data
    5.Data Manipulation
    6.Joins and Subqueries
    7.Advanced Topics
    8.Contributing
 

## 1.Introduction

  (Structured Query Language) is a standardized programming language used for managing relational databases and performing various operations on the data stored in them. This crash course will cover the fundamentals of  , providing examples and explanations to help beginners and intermediate users understand and use   effectively.
## 2.Database Basics
### What is a Database?

A database is an organized collection of structured information, or data, typically stored electronically in a computer system. A database is usually controlled by a Database Management System (DBMS).
Key Concepts

    Database Management System (DBMS): Software that interacts with the user, applications, and the database itself to capture and analyze data.
    Tables: Structured format to store data in rows and columns. Each table in a database represents an entity and contains records (rows) and fields (columns).
    Schema: The structure that defines the organization of data in a database, including tables, columns, and their relationships.
    Primary Key: A unique identifier for each record in a table, ensuring that no two rows have the same primary key.
    Foreign Key: A field in one table that uniquely identifies a row in another table, creating a relationship between the two tables.

## 3.Table Operations
### Creating a Table

The CREATE TABLE statement is used to create a new table in the database.

 

    CREATE TABLE employees (
        employee_id INT PRIMARY KEY,
        first_name VARCHAR(50),
        last_name VARCHAR(50),
        hire_date DATE,
        salary DECIMAL(10, 2)
    );

Explanation: This   command creates a table named employees with the following columns:

    employee_id: an integer that serves as the primary key.
    first_name: a string of up to 50 characters.
    last_name: a string of up to 50 characters.
    hire_date: a date.
    salary: a decimal number with up to 10 digits, 2 of which can be after the decimal point.

### Dropping a Table

The DROP TABLE statement is used to delete an existing table and all its data from the database.

 

    DROP TABLE employees;

Explanation: This command deletes the employees table from the database. Use this command with caution as it permanently removes the table and its data.
### Altering a Table

The ALTER TABLE statement is used to add, delete, or modify columns in an existing table.

### Add a column:

 

    ALTER TABLE employees ADD COLUMN email VARCHAR(100);

Explanation: This command adds a new column email of type VARCHAR (string) with a maximum length of 100 characters to the employees table.

### Remove a column:

 

    ALTER TABLE employees DROP COLUMN email;

Explanation: This command removes the email column from the employees table.
## 4.Querying Data
### Selecting Data

The SELECT statement is used to retrieve data from a database.

### Select all columns:

 

    SELECT * FROM employees;

Explanation: This command retrieves all columns from the employees table.

### Select specific columns:

 

    SELECT first_name, last_name FROM employees;

Explanation: This command retrieves only the first_name and last_name columns from the employees table.
### Filtering Data

The WHERE clause is used to filter records based on specified conditions.

 

    SELECT * FROM employees WHERE salary > 50000;

Explanation: This command retrieves all records from the employees table where the salary is greater than 50,000.
### Sorting Data

The ORDER BY clause is used to sort the result set in either ascending or descending order.

 

    SELECT * FROM employees ORDER BY last_name ASC;

Explanation: This command retrieves all records from the employees table and sorts them by the last_name column in ascending order. Use DESC for descending order.
Limiting Results

The LIMIT clause is used to specify the number of records to return.

 

    SELECT * FROM employees LIMIT 5;

Explanation: This command retrieves the first 5 records from the employees table.
## 5.Data Manipulation
### Inserting Data

The INSERT INTO statement is used to add new rows to a table.

 

    INSERT INTO employees (employee_id, first_name, last_name, hire_date, salary)
    VALUES (1, 'John', 'Doe', '2020-01-15', 60000.00);

Explanation: This command inserts a new record into the employees table with the specified values for employee_id, first_name, last_name, hire_date, and salary.
### Updating Data

The UPDATE statement is used to modify existing records in a table.

 

    UPDATE employees
    SET salary = 65000.00
    WHERE employee_id = 1;

Explanation: This command updates the salary of the employee with employee_id 1 to 65,000.00.
### Deleting Data

The DELETE statement is used to remove existing records from a table.

 

    DELETE FROM employees
    WHERE employee_id = 1;

Explanation: This command deletes the record from the employees table where the employee_id is 1.
## 6.Joins and Subqueries
### Joins

Joins are used to combine rows from two or more tables based on a related column between them.

### Inner Join:

 

    SELECT employees.first_name, departments.department_name
    FROM employees
    INNER JOIN departments ON employees.department_id = departments.department_id;

Explanation: This command retrieves the first_name from the employees table and the department_name from the departments table for records where the department_id matches in both tables.

### Left Join:

 

    SELECT employees.first_name, departments.department_name
    FROM employees
    LEFT JOIN departments ON employees.department_id = departments.department_id;

Explanation: This command retrieves all records from the employees table and the matching records from the departments table. If there is no match, the result is NULL on the side of the departments table.
Subqueries

Subqueries are nested queries used to perform operations on the result of another query.

### Simple Subquery:

 

    SELECT first_name, last_name
    FROM employees
    WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Sales');

Explanation: This command retrieves the first_name and last_name of employees who belong to the department named 'Sales'. The subquery finds the department_id for 'Sales', and the main query uses this department_id to filter employees.
## 7.Advanced Topics
### Aggregate Functions

Aggregate functions perform a calculation on a set of values and return a single value.

### COUNT:

     

    SELECT COUNT(*) FROM employees;

Explanation: This command returns the total number of records in the employees table.

### SUM:

 

    SELECT SUM(salary) FROM employees;

Explanation: This command returns the sum of all salaries in the employees table.

### AVG:

 

    SELECT AVG(salary) FROM employees;

Explanation: This command returns the average salary of all employees in the employees table.

### MAX:

 

    SELECT MAX(salary) FROM employees;

Explanation: This command returns the highest salary in the employees table.

### MIN:

 

    SELECT MIN(salary) FROM employees;

Explanation: This command returns the lowest salary in the employees table.

### Grouping Data

The GROUP BY clause is used to arrange identical data into groups.

 

    SELECT department_id, COUNT(*)
    FROM employees
    GROUP BY department_id;

Explanation: This command groups the records in the employees table by department_id and returns the count of records in each group.

### Having Clause

The HAVING clause is used to filter groups based on specified conditions, similar to the WHERE clause but for grouped data.

 

    SELECT department_id, COUNT(*)
    FROM employees
    GROUP BY department_id
    HAVING COUNT(*) > 5;

Explanation: This command groups the records in the employees table by department_id and returns only the groups with more than 5 records.
