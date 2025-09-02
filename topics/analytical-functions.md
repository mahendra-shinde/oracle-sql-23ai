# Using Analytical Functions (LAG, LEAD, RANK, FIRST_VALUE, LAST_VALUE, NTILE, etc)

## Analytical Functions in Oracle SQL Database 23ai

Analytical functions in Oracle SQL Database 23ai provide advanced calculations across sets of rows, making them invaluable for reporting and data analysis.

### Key Analytical Functions
- **ROW_NUMBER()**: Assigns a unique number to each row based on a specified order.
- **RANK() / DENSE_RANK()**: Assigns a rank to each row within a partition.
- **LEAD() / LAG()**: Accesses data from subsequent or preceding rows.
- **NTILE()**: Divides rows into a specified number of buckets.
- **FIRST_VALUE() / LAST_VALUE()**: Returns the first or last value in an ordered set.
- **SUM(), AVG(), MIN(), MAX() OVER()**: Aggregate functions with windowing capability.

### Example: ROW_NUMBER()
```sql
SELECT employee_id, salary,
	ROW_NUMBER() OVER (ORDER BY salary DESC) AS rank
FROM employees;
```

### Example: LEAD() and LAG()
```sql
SELECT employee_id, hire_date,
	LAG(hire_date, 1) OVER (ORDER BY hire_date) AS prev_hire_date
FROM employees;
```
#### Explanation

The above SQL code demonstrates the use of the `LAG()` analytical function. In this example, for each employee, the query retrieves their `employee_id` and `hire_date`, and also fetches the `hire_date` of the previous employee (based on the order of `hire_date`). The `LAG(hire_date, 1)` function looks one row back from the current row, allowing you to compare each employee's hire date with that of the previous employee in the result set.

### Example: LEAD()
```sql
SELECT employee_id, hire_date,
	LEAD(hire_date, 1) OVER (ORDER BY hire_date) AS next_hire_date
FROM employees;
```
#### Explanation

This SQL example uses the `LEAD()` analytical function. For each employee, it retrieves their `employee_id` and `hire_date`, and also fetches the `hire_date` of the next employee (according to the order of `hire_date`). The `LEAD(hire_date, 1)` function looks one row ahead from the current row, making it easy to compare each employee's hire date with that of the following employee in the result set.

### Example: LEAD() with SALARY

```sql
SELECT employee_id, department_id, salary,
	LEAD(salary, 1) OVER (PARTITION BY department_id ORDER BY salary DESC) AS next_salary,
	salary - LAG(salary, 1) OVER (PARTITION BY department_id ORDER BY salary DESC) AS salary_diff_prev
FROM employees
WHERE department_id = 50;
```

#### Explanation

This query retrieves each employee's `employee_id`, `department_id`, and `salary` for department 50. It uses `LEAD(salary, 1)` to get the next highest salary within the same department and `LAG(salary, 1)` to get the previous salary. The `salary_diff_prev` column shows the difference between the current salary and the previous one in descending order.

### Tips
- Use `PARTITION BY` to group data within analytical functions.
- Analytical functions do not collapse rows like GROUP BY.
- Combine multiple analytical functions for advanced reporting.

