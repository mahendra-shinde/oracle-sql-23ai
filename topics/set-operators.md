
# Using Set Operators

Set operators in SQL are used to combine the results of two or more SELECT statements into a single result set. Oracle 23ai supports several set operators, each with specific rules and use cases.

## Types of Set Operators

1. **UNION**
	- Combines the results of two queries and removes duplicate rows.
2. **UNION ALL**
	- Combines the results of two queries and includes all duplicates.
3. **INTERSECT**
	- Returns only the rows that are common to both queries.
4. **MINUS**
	- Returns rows from the first query that are not present in the second query.

## Syntax

```sql
SELECT column_list FROM table1
<set_operator>
SELECT column_list FROM table2;
```

**Note:**
- The number and data types of columns in all SELECT statements must be the same.
- The column names in the final result set are taken from the first SELECT statement.

## Examples

### 1. UNION
```sql
SELECT department_id FROM employees
UNION
SELECT department_id FROM departments;
```

### 2. UNION ALL
```sql
SELECT department_id FROM employees
UNION ALL
SELECT department_id FROM departments;
```

### 3. INTERSECT
```sql
SELECT department_id FROM employees
INTERSECT
SELECT department_id FROM departments;
```

### 4. MINUS
```sql
SELECT department_id FROM departments
MINUS
SELECT department_id FROM employees;
```

## Key Points

- `UNION` removes duplicates; `UNION ALL` does not.
- `INTERSECT` and `MINUS` are unique to Oracle and some other databases.
- ORDER BY can only be used at the end of the last SELECT statement.
- All SELECT statements must have the same number of columns and compatible data types.

## Practice Questions

1. List all unique job IDs from both `EMPLOYEES` and `JOB_HISTORY` tables.
2. Find department IDs that exist in `DEPARTMENTS` but not in `EMPLOYEES`.
3. Show department IDs that are present in both `EMPLOYEES` and `DEPARTMENTS`.
4. Display all department IDs from both tables, including duplicates.
5. Combine the first and last names of employees and job history records into a single list.

---
Refer to the [Oracle 23ai SQL documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/index.html) for more details and advanced usage.
