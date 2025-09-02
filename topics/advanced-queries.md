# Manipulating Data Using Advanced Queries

Advanced SQL queries allow you to perform complex data manipulation tasks that go beyond basic SELECT, INSERT, UPDATE, and DELETE statements. Below are some advanced techniques and examples for manipulating data in Oracle SQL:

## 1. MERGE Statement (Upsert)
The `MERGE` statement allows you to insert, update, or delete rows in a target table based on matching conditions from a source table or subquery.

```sql
MERGE INTO target_table t
USING source_table s
ON (t.id = s.id)
WHEN MATCHED THEN
	UPDATE SET t.value = s.value
WHEN NOT MATCHED THEN
	INSERT (id, value) VALUES (s.id, s.value);
```

## 2. Multi-Table INSERT
Insert data into multiple tables using a single statement.

```sql
INSERT ALL
	INTO employees_archive VALUES (employee_id, first_name, last_name)
	INTO employees_audit VALUES (employee_id, SYSDATE, 'ARCHIVED')
SELECT employee_id, first_name, last_name FROM employees WHERE status = 'INACTIVE';
```

## 3. Inline Views and Subquery Factoring (WITH Clause)
Use subqueries in the FROM clause or factor them out for reuse and clarity.

```sql
WITH high_earners AS (
	SELECT employee_id, salary FROM employees WHERE salary > 10000
)
SELECT * FROM high_earners WHERE ROWNUM <= 5;
```

## 4. Correlated Subqueries for Updates
Update a table using values from another table, correlated by a key.

```sql
UPDATE employees e
SET salary = (
	SELECT AVG(salary)
	FROM employees
	WHERE department_id = e.department_id
)
WHERE EXISTS (
	SELECT 1 FROM departments d WHERE d.department_id = e.department_id
);
```

## 5. Using RETURNING INTO for DML
Capture values from inserted, updated, or deleted rows directly into variables.

```sql
DECLARE
	v_id employees.employee_id%TYPE;
BEGIN
	INSERT INTO employees (first_name, last_name) VALUES ('John', 'Doe')
	RETURNING employee_id INTO v_id;
END;
```

## 6. Advanced DELETE with Subquery
Delete rows based on complex conditions using subqueries.

```sql
DELETE FROM employees
WHERE department_id IN (
	SELECT department_id FROM departments WHERE location_id = 1700
);
```

## 7. Pivoting and Unpivoting Data
Transform rows to columns and vice versa for reporting.

```sql
-- Pivot example
SELECT * FROM (
	SELECT department_id, job_id, salary FROM employees
)
PIVOT (
	SUM(salary) FOR job_id IN ('IT_PROG', 'SA_REP', 'HR_REP')
);

-- Unpivot example
SELECT * FROM (
	SELECT department_id, it_prog, sa_rep, hr_rep FROM department_salaries
)
UNPIVOT (
	salary FOR job IN (it_prog AS 'IT_PROG', sa_rep AS 'SA_REP', hr_rep AS 'HR_REP')
);
```

---

These advanced techniques help you efficiently manipulate and transform data in Oracle databases, supporting complex business requirements and reporting needs.

