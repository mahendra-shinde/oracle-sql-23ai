# Retrieving/Manipulation Data by Using Subqueries

## What is a Subquery?
A **subquery** (or inner query or nested query) is a query embedded within another SQL query. Subqueries can be used in SELECT, INSERT, UPDATE, or DELETE statements to perform operations based on the results of another query.

Subqueries are enclosed in parentheses and can return a single value (scalar), a single row, or multiple rows and columns.

## Types of Subqueries

1. **Single-row subquery**: Returns only one row.
2. **Multiple-row subquery**: Returns more than one row.
3. **Multiple-column subquery**: Returns more than one column.
4. **Correlated subquery**: References columns from the outer query.

## Using Subqueries to Fetch Data

### Example 1: Subquery in WHERE Clause
Find employees who earn more than the average salary:

```sql
SELECT employee_id, first_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### Example 2: Subquery in FROM Clause
List departments with their average salary:

```sql
SELECT department_id, avg_salary
FROM (
	SELECT department_id, AVG(salary) AS avg_salary
	FROM employees
	GROUP BY department_id
);
```

### Example 3: Subquery in SELECT Clause
Show each employee and the average salary in their department:

```sql
SELECT first_name, salary,
	(SELECT AVG(salary) FROM employees e2 WHERE e2.department_id = e1.department_id) AS dept_avg_salary
FROM employees e1;
```

## Using Subqueries to Manipulate Data

### Example 4: Subquery in UPDATE Statement
Increase salary by 10% for employees in departments with an average salary below 5000:

```sql
UPDATE employees
SET salary = salary * 1.10
WHERE department_id IN (
	SELECT department_id
	FROM employees
	GROUP BY department_id
	HAVING AVG(salary) < 5000
);
```

### Example 5: Subquery in DELETE Statement
Delete employees who have the lowest salary in the company:

```sql
DELETE FROM employees
WHERE salary = (SELECT MIN(salary) FROM employees);
```

## Correlated Subqueries
A correlated subquery references columns from the outer query and is evaluated once for each row processed by the outer query.

**Example:** List employees who earn more than the average salary in their department:

```sql
SELECT employee_id, first_name, salary, department_id
FROM employees e1
WHERE salary > (
	SELECT AVG(salary)
	FROM employees e2
	WHERE e2.department_id = e1.department_id
);
```

## Key Points
- Subqueries can be used in SELECT, INSERT, UPDATE, and DELETE statements.
- Always enclose subqueries in parentheses.
- Use single-row operators (=, <, >) with single-row subqueries and multi-row operators (IN, ANY, ALL) with multi-row subqueries.
- Correlated subqueries are evaluated for each row of the outer query.

## Practice Exercises
1. Write a query to find employees who work in the same department as 'John Doe'.
2. Update the salary of employees who earn less than the average salary in their department to the average salary.
3. Delete all employees who do not belong to any department listed in the departments table.

---
Subqueries are a powerful tool in SQL for writing flexible and efficient queries. Practice using them in different clauses to master their use!
