# Retrieving Data Using the SQL SELECT Statement

## Introduction
The `SELECT` statement is used to retrieve data from one or more tables in an Oracle 23ai database. It is the most fundamental SQL command for querying data.

## Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name;
```

## Selecting All Columns
```sql
SELECT * FROM employees;
```
This retrieves all columns from the `employees` table.

## Using WHERE Clause
The `WHERE` clause filters rows based on specified conditions.
```sql
SELECT first_name, last_name FROM employees WHERE department_id = 10;
```

## Sorting Results with ORDER BY
```sql
SELECT first_name, salary FROM employees ORDER BY salary DESC;
```

## Limiting Rows with FETCH FIRST
Oracle 23ai supports limiting rows using `FETCH FIRST`:
```sql
SELECT * FROM employees FETCH FIRST 5 ROWS ONLY;
```

## Using Aliases
Aliases make column names more readable:
```sql
SELECT first_name AS "First Name", salary AS "Monthly Salary" FROM employees;
```

## DISTINCT Keyword
Removes duplicate values:
```sql
SELECT DISTINCT department_id FROM employees;
```

## Combining Conditions with AND/OR
```sql
SELECT * FROM employees WHERE department_id = 10 AND salary > 5000;
```

## Using IN, BETWEEN, LIKE
```sql
SELECT * FROM employees WHERE department_id IN (10, 20);
SELECT * FROM employees WHERE salary BETWEEN 4000 AND 7000;
SELECT * FROM employees WHERE first_name LIKE 'A%';
```

## NULL Checks
```sql
SELECT * FROM employees WHERE manager_id IS NULL;
```

## Practice Exercise
1. Retrieve all employees in department 20, sorted by last name.
2. List unique job titles from the jobs table.
3. Find employees whose salary is between 6000 and 9000.

