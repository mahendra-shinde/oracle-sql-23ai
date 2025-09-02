# Generating Reports by Grouping Related Data

Grouping data is essential for generating summary reports and analyzing trends in your data. Oracle SQL provides several powerful features for grouping and aggregating data.

## 1. Basic GROUP BY

The `GROUP BY` clause groups rows that have the same values in specified columns into summary rows.

```sql
-- Total salary by department
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id;
```

## 2. GROUP BY with Multiple Columns

You can group by more than one column to get more granular reports.

```sql
-- Total salary by department and job
SELECT department_id, job_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id, job_id;
```

## 3. GROUPING SETS

`GROUPING SETS` allows you to define multiple groupings in a single query, producing multiple levels of aggregation.

```sql
SELECT department_id, job_id, SUM(salary) AS total_salary
FROM employees
GROUP BY GROUPING SETS ((department_id, job_id), (department_id), ());
```

## 4. ROLLUP

`ROLLUP` generates subtotals and a grand total.

```sql
SELECT department_id, job_id, SUM(salary) AS total_salary
FROM employees
GROUP BY ROLLUP (department_id, job_id);
```

## 5. CUBE

`CUBE` generates subtotals for all combinations of the specified columns.

```sql
SELECT department_id, job_id, SUM(salary) AS total_salary
FROM employees
GROUP BY CUBE (department_id, job_id);
```

## 6. HAVING Clause

Use `HAVING` to filter groups after aggregation.

```sql
-- Departments with total salary above 1,000,000
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id
HAVING SUM(salary) > 1000000;
```

---

These techniques help you generate detailed and summary reports for business analysis and decision-making.
