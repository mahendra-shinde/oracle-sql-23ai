
# Restricting and Sorting Data

## Introduction
When working with SQL, you often need to filter (restrict) and sort data to get meaningful results. This section covers the use of the `WHERE` clause for filtering and the `ORDER BY` clause for sorting, with practical examples and tips.

---

## Filtering Data with WHERE
The `WHERE` clause is used to restrict the rows returned by a query based on specified conditions.

**Syntax:**
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Examples:**
- Retrieve employees in department 10:
	```sql
	SELECT first_name, last_name FROM employees WHERE department_id = 10;
	```
- Find employees with salary greater than 5000:
	```sql
	SELECT first_name, salary FROM employees WHERE salary > 5000;
	```

### Common Operators in WHERE
- `=` (equal to)
- `!=` or `<>` (not equal to)
- `>` , `<` , `>=` , `<=`
- `BETWEEN ... AND ...`
- `IN (value1, value2, ...)`
- `LIKE` (pattern matching)
- `IS NULL` / `IS NOT NULL`

**Example:**
```sql
SELECT * FROM employees WHERE last_name LIKE 'S%';
```

---

## Combining Conditions with AND, OR, NOT
You can combine multiple conditions using logical operators:

```sql
SELECT * FROM employees
WHERE department_id = 20 AND salary > 4000;
```

```sql
SELECT * FROM employees
WHERE department_id = 30 OR department_id = 40;
```

```sql
SELECT * FROM employees
WHERE NOT (salary < 3000);
```

---

## Sorting Data with ORDER BY
The `ORDER BY` clause sorts the result set by one or more columns.

**Syntax:**
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;
```

**Examples:**
- Sort employees by salary (highest first):
	```sql
	SELECT first_name, salary FROM employees ORDER BY salary DESC;
	```
- Sort by department, then by last name:
	```sql
	SELECT department_id, last_name FROM employees ORDER BY department_id, last_name;
	```

---

## Limiting Rows with FETCH FIRST
To return only a subset of rows, use `FETCH FIRST`:
```sql
SELECT * FROM employees ORDER BY hire_date DESC FETCH FIRST 5 ROWS ONLY;
```

---

## Practice Exercises
1. List all employees in department 50, sorted by salary (highest to lowest).
2. Find employees whose last name starts with 'A' or 'B', sorted alphabetically.
3. Retrieve the top 3 highest paid employees in each department.

---

**Tip:** Filtering and sorting are often combined in real-world queries. Practice using `WHERE` and `ORDER BY` together for more powerful data retrieval!
