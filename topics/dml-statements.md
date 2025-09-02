# Managing Tables Using DML Statements in Oracle

Data Manipulation Language (DML) statements are used to manage data within schema objects in Oracle 23ai. The main DML statements are `INSERT`, `UPDATE`, `DELETE`, and `MERGE`.

## 1. INSERT Statement
Adds new rows to a table.

```sql
-- Insert a single row
INSERT INTO employees (employee_id, last_name, salary)
VALUES (1001, 'Smith', 5000);

-- Insert multiple rows (Oracle 23ai feature)
INSERT ALL
	INTO employees (employee_id, last_name, salary) VALUES (1002, 'Jones', 6000)
	INTO employees (employee_id, last_name, salary) VALUES (1003, 'Brown', 5500)
SELECT * FROM dual;
```

## 2. UPDATE Statement
Modifies existing rows in a table.

```sql
UPDATE employees
SET salary = salary * 1.1
WHERE department_id = 10;
```

## 3. DELETE Statement
Removes rows from a table.

```sql
DELETE FROM employees
WHERE department_id = 20;
```

## 4. MERGE Statement
Inserts or updates rows in a table based on a condition (also known as UPSERT).

```sql
MERGE INTO employees e
USING new_employees n
ON (e.employee_id = n.employee_id)
WHEN MATCHED THEN
	UPDATE SET e.salary = n.salary
WHEN NOT MATCHED THEN
	INSERT (employee_id, last_name, salary)
	VALUES (n.employee_id, n.last_name, n.salary);
```

## Transaction Control

- `COMMIT`: Saves changes to the database.
- `ROLLBACK`: Undoes changes since the last commit.
- `SAVEPOINT`: Sets a point to which you can roll back.

```sql
INSERT INTO employees (employee_id, last_name) VALUES (1004, 'Taylor');
SAVEPOINT before_raise;
UPDATE employees SET salary = 7000 WHERE employee_id = 1004;
ROLLBACK TO before_raise;
COMMIT;
```

## Key Points

- DML statements affect data, not table structure.
- Changes are not permanent until committed.
- Use `WHERE` clause to avoid unintentional updates or deletes.
- `MERGE` is useful for data warehousing and ETL operations.

## Practice Questions

1. Add a new employee to the `EMPLOYEES` table.
2. Increase the salary of all employees in department 30 by 5%.
3. Remove all employees who have not received a commission.
4. Use `MERGE` to synchronize data between two employee tables.
5. Demonstrate the use of `SAVEPOINT` and `ROLLBACK` in a transaction.

---
Refer to the [Oracle 23ai SQL documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/index.html) for more details and advanced usage.
