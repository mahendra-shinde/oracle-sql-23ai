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

### Tips
- Use `PARTITION BY` to group data within analytical functions.
- Analytical functions do not collapse rows like GROUP BY.
- Combine multiple analytical functions for advanced reporting.

