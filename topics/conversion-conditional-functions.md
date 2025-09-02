## Conversion and Conditional Functions in Oracle SQL Database 23ai

Conversion and conditional functions are essential for data manipulation and transformation in Oracle SQL Database 23ai.

### Conversion Functions
- **TO_CHAR()**: Converts dates/numbers to strings.
- **TO_DATE()**: Converts strings to date values.
- **TO_NUMBER()**: Converts strings to numbers.
- **CAST()**: Converts one data type to another.

### Example: TO_CHAR()
```sql
SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD') AS today FROM dual;
```

### Conditional Functions
- **NVL()**: Replaces NULL with a specified value.
- **COALESCE()**: Returns the first non-NULL value in a list.
- **CASE**: Conditional logic in SQL statements.
- **DECODE()**: Performs IF-THEN-ELSE logic.


### Example: COALESCE
Returns the first non-NULL value from the list of columns/expressions.
```sql
SELECT employee_id, COALESCE(commission_pct, 0) AS commission
FROM employees;
```

### Example: DECODE
Performs IF-THEN-ELSE logic in a compact form.
```sql
SELECT employee_id, job_id,
	   DECODE(job_id,
			  'IT_PROG', 'Programmer',
			  'SA_REP', 'Sales Rep',
			  'AD_VP', 'Admin VP',
			  'Other') AS job_title
FROM employees;
```

### Example: CASE
```sql
SELECT employee_id, salary,
	   CASE WHEN salary > 5000 THEN 'High' ELSE 'Low' END AS salary_level
FROM employees;
```

### Tips
- Use conversion functions to ensure data consistency.
- Conditional functions simplify complex logic in queries.
