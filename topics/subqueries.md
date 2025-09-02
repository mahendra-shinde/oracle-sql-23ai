
# Using Subqueries to Solve Queries

Subqueries (also called nested queries or inner queries) are queries embedded within another SQL query. They are powerful tools for breaking complex problems into simpler steps and are widely used in Oracle 23ai.

## What is a Subquery?

A subquery is a SELECT statement placed inside another SQL statement, such as SELECT, INSERT, UPDATE, or DELETE. The outer query uses the result of the subquery to complete its operation.

## Types of Subqueries

1. **Single-Row Subquery**: Returns only one row.
2. **Multiple-Row Subquery**: Returns more than one row.
3. **Multiple-Column Subquery**: Returns more than one column.
4. **Correlated Subquery**: References columns from the outer query.
5. **Scalar Subquery**: Returns a single value (one row, one column).

## Subquery Placement

- In the SELECT list
- In the FROM clause (inline views)
- In the WHERE or HAVING clause
- In DML statements (INSERT, UPDATE, DELETE)

## Examples

### 1. Single-Row Subquery
```sql
SELECT last_name, salary
FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees);
```

### 2. Multiple-Row Subquery
```sql
SELECT employee_id, last_name
FROM employees
WHERE department_id IN (SELECT department_id FROM departments WHERE location_id = 1700);
```

### 3. Multiple-Column Subquery
```sql
SELECT employee_id, last_name
FROM employees
WHERE (department_id, job_id) IN (SELECT department_id, job_id FROM job_history);
```

### 4. Correlated Subquery
```sql
SELECT e1.last_name, e1.salary
FROM employees e1
WHERE salary > (SELECT AVG(salary) FROM employees e2 WHERE e1.department_id = e2.department_id);
```

### 5. Scalar Subquery in SELECT
```sql
SELECT last_name,
	   (SELECT department_name FROM departments d WHERE d.department_id = e.department_id) AS dept_name
FROM employees e;
```

## Key Points

- Subqueries can be nested to multiple levels.
- Use `IN`, `ANY`, `ALL`, `EXISTS`, or comparison operators with subqueries.
- Correlated subqueries are evaluated once per row of the outer query.
- Scalar subqueries can be used in SELECT, WHERE, and ORDER BY clauses.
- Inline views (subqueries in FROM) can simplify complex joins and aggregations.

## Practice Questions

1. Find employees who earn more than the average salary of their department.
2. List departments that have no employees.
3. Show employees who work in the same job as 'Smith'.
4. Display the highest paid employee in each department.
5. List employees whose salary is higher than any employee in department 50.

---
Refer to the [Oracle 23ai SQL documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/index.html) for more details and advanced usage.
