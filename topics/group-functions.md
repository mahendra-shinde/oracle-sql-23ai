
# Reporting Aggregated Data Using the Group Functions

Aggregate functions (also called group functions) in Oracle 23ai perform calculations on sets of rows and return a single result per group or for the entire result set. They are essential for summarizing, analyzing, and reporting data.

## Common Aggregate Functions

| Function   | Description                                 |
|------------|---------------------------------------------|
| `AVG`      | Returns the average value                   |
| `COUNT`    | Returns the number of rows                  |
| `MAX`      | Returns the maximum value                   |
| `MIN`      | Returns the minimum value                   |
| `SUM`      | Returns the total sum                       |
| `STDDEV`   | Returns the standard deviation              |
| `VARIANCE` | Returns the variance                        |

## Syntax

```sql
SELECT aggregate_function(column)
FROM table_name
[WHERE condition]
[GROUP BY column(s)]
[HAVING group_condition];
```

## Examples

### 1. Calculate the Average Salary
```sql
SELECT AVG(salary) AS avg_salary FROM employees;
```

### 2. Count the Number of Employees
```sql
SELECT COUNT(*) AS total_employees FROM employees;
```

### 3. Find the Maximum and Minimum Salary
```sql
SELECT MAX(salary) AS max_salary, MIN(salary) AS min_salary FROM employees;
```

### 4. Total Salary by Department
```sql
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id;
```

### 5. Departments with More Than 5 Employees
```sql
SELECT department_id, COUNT(*) AS emp_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

## Key Points

- Aggregate functions ignore NULL values (except `COUNT(*)`).
- Can be used with `GROUP BY` to aggregate data by groups.
- Use `HAVING` to filter groups after aggregation.
- Can be nested with other functions for advanced analysis.

## Practice Questions

1. Find the total number of departments in the `DEPARTMENTS` table.
2. Show the highest and lowest commission in the `EMPLOYEES` table.
3. List each job ID and the average salary for that job.
4. Display departments where the average salary is above 10,000.
5. Count the number of employees hired in each year.

---
Refer to the [Oracle 23ai SQL documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/index.html) for more details and advanced usage.
