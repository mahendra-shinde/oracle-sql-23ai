
# Introduction to Data Definition Language in Oracle

Data Definition Language (DDL) statements are used to define, modify, and remove schema objects such as tables, views, indexes, and more in Oracle 23ai. DDL statements automatically commit any transaction in progress.

## Common DDL Statements

1. **CREATE**: Creates new database objects (tables, views, indexes, etc.).
2. **ALTER**: Modifies the structure of existing objects.
3. **DROP**: Removes objects from the database.
4. **TRUNCATE**: Removes all rows from a table, but keeps its structure.
5. **RENAME**: Changes the name of a database object.
6. **COMMENT**: Adds comments to the data dictionary for documentation.

## Examples

### 1. CREATE TABLE
```sql
CREATE TABLE employees (
	employee_id NUMBER PRIMARY KEY,
	last_name VARCHAR2(50),
	salary NUMBER(8,2),
	hire_date DATE
);
```

### 2. ALTER TABLE
```sql
ALTER TABLE employees ADD (email VARCHAR2(100));
ALTER TABLE employees MODIFY (salary NUMBER(10,2));
ALTER TABLE employees DROP COLUMN email;
```

### 3. DROP TABLE
```sql
DROP TABLE employees;
```

### 4. TRUNCATE TABLE
```sql
TRUNCATE TABLE employees;
```

### 5. RENAME
```sql
RENAME employees TO staff;
```

### 6. COMMENT
```sql
COMMENT ON TABLE employees IS 'Stores employee details';
COMMENT ON COLUMN employees.salary IS 'Monthly salary of employee';
```

## Key Points

- DDL statements auto-commit; changes cannot be rolled back.
- Use DDL to manage schema, not data.
- TRUNCATE is faster than DELETE but cannot be rolled back.
- Always check dependencies before dropping or altering objects.

## Practice Questions

1. Create a table for departments with columns for ID and name.
2. Add a column for manager ID to the employees table.
3. Remove the salary column from the employees table.
4. Rename the departments table to depts.
5. Add a comment to the employees table describing its purpose.

---
Refer to the [Oracle 23ai SQL documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/index.html) for more details and advanced usage.
