# Displaying Data from Multiple Tables Using Joins

Joins are used in SQL to retrieve data from two or more tables based on related columns. Oracle 23ai supports both traditional (pre-ANSI SQL:1999) and ANSI-standard join syntax.

## 1. Pre-ANSI SQL:1999 Joins (Oracle Proprietary Syntax)

> Oracle Proprietary Joins are given only for reference ! Focus on Standard Joins.

### a. Equijoins
Join rows from two or more tables where there is a matching value in a common column.

```sql
SELECT e.employee_id, e.last_name, d.department_name
FROM employees e, departments d
WHERE e.department_id = d.department_id;
```

### b. Non-Equijoins
Join tables based on a condition other than equality.

```sql
SELECT e.employee_id, e.salary, j.grade_level
FROM employees e, job_grades j
WHERE e.salary BETWEEN j.lowest_sal AND j.highest_sal;
```

### c. Outer Joins (Using (+) Operator)
Retrieve rows that have no matching rows in another table.

```sql
-- Left Outer Join (departments with or without employees)
SELECT d.department_name, e.last_name
FROM departments d, employees e
WHERE d.department_id = e.department_id(+);

-- Right Outer Join (employees with or without departments)
SELECT d.department_name, e.last_name
FROM departments d, employees e
WHERE d.department_id(+) = e.department_id;
```

### d. Self Joins
Join a table to itself.

```sql
SELECT e.employee_id, e.last_name, m.last_name AS manager
FROM employees e, employees m
WHERE e.manager_id = m.employee_id;
```

## 2. ANSI SQL:1999 and Later Joins (Standard Syntax)


### a. INNER JOIN
Returns rows when there is a match in both tables.

```sql
SELECT e.employee_id, e.last_name, d.department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.department_id;
```

### Additional Notes: NATURAL JOIN and USING Operator

#### NATURAL JOIN
The `NATURAL JOIN` clause automatically joins tables based on all columns with the same name and compatible data types in both tables. It eliminates the need to specify the join condition explicitly.

**Example:**
```sql
SELECT e.employee_id, e.last_name, d.department_name
FROM employees e
NATURAL JOIN departments d;
```
*This will join on the `department_id` column if it exists in both tables.*

**Caution:**
- Use `NATURAL JOIN` only when you are certain about the column names and their meanings in both tables.
- If multiple columns have the same name, all are used in the join condition.

#### USING Operator
The `USING` clause specifies the column(s) to join on, simplifying the join condition when the column name is the same in both tables.

**Example:**
```sql
SELECT e.employee_id, e.last_name, d.department_name
FROM employees e
JOIN departments d USING (department_id);
```
*This is equivalent to joining on `e.department_id = d.department_id`.*

**Key Points:**
- The column(s) listed in `USING` must exist in both tables.
- The result set will show the join column only once.

---

### b. LEFT OUTER JOIN
Returns all rows from the left table, and matched rows from the right table.

```sql
SELECT d.department_name, e.last_name
FROM departments d
LEFT OUTER JOIN employees e ON d.department_id = e.department_id;
```

### c. RIGHT OUTER JOIN
Returns all rows from the right table, and matched rows from the left table.

```sql
SELECT d.department_name, e.last_name
FROM departments d
RIGHT OUTER JOIN employees e ON d.department_id = e.department_id;
```

### d. FULL OUTER JOIN
Returns rows when there is a match in one of the tables.

```sql
SELECT d.department_name, e.last_name
FROM departments d
FULL OUTER JOIN employees e ON d.department_id = e.department_id;
```

### e. CROSS JOIN
Returns the Cartesian product of both tables.

```sql
SELECT e.last_name, d.department_name
FROM employees e
CROSS JOIN departments d;
```

### f. Self Join (ANSI Syntax)
```sql
SELECT e.employee_id, e.last_name, m.last_name AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.employee_id;
```

## Key Points

- Pre-ANSI joins use commas and WHERE clause; ANSI joins use explicit JOIN keywords.
- Outer joins in pre-ANSI use the (+) operator; ANSI uses LEFT/RIGHT/FULL OUTER JOIN.
- ANSI syntax is preferred for readability and maintainability.
- Oracle 23ai supports both syntaxes for backward compatibility.

## Practice Questions

1. Write a query to list all employees and their department names (use both syntaxes).
2. Show all departments, including those without employees.
3. List employees and their managers' names.
4. Display all possible combinations of employees and departments.
5. Find employees who do not belong to any department.

---
Refer to the [Oracle 23ai SQL documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/index.html) for more details and advanced usage.
