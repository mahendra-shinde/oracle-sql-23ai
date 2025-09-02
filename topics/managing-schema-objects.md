
# Managing Schema Objects in Oracle Databases

Schema objects are logical structures that directly refer to the data in a database. Managing these objects is a core part of database administration and development in Oracle.

---

## What are Schema Objects?

Schema objects are database objects that belong to a specific user (schema) and include tables, views, sequences, synonyms, indexes, clusters, procedures, functions, packages, and triggers.

---

## Common Schema Objects

- **Tables:** Store data in rows and columns.
- **Views:** Virtual tables based on SQL queries.
- **Sequences:** Generate unique numeric values.
- **Synonyms:** Aliases for database objects.
- **Indexes:** Improve query performance.
- **Clusters:** Store related tables together for performance.
- **Procedures/Functions:** Stored PL/SQL code for business logic.
- **Packages:** Groups of related procedures/functions.
- **Triggers:** Code that runs automatically in response to events.

---

## Creating Schema Objects

### Create Table
```sql
CREATE TABLE employees (
	id NUMBER PRIMARY KEY,
	name VARCHAR2(100),
	hire_date DATE
);
```

### Create View
```sql
CREATE VIEW emp_names AS SELECT id, name FROM employees;
```

### Create Sequence
```sql
CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1;
```

### Create Index
```sql
CREATE INDEX emp_name_idx ON employees (name);
```

---

## Modifying Schema Objects

### Alter Table (Add Column)
```sql
ALTER TABLE employees ADD (email VARCHAR2(100));
```

### Alter Table (Modify Column)
```sql
ALTER TABLE employees MODIFY (name VARCHAR2(200));
```

### Alter Table (Drop Column)
```sql
ALTER TABLE employees DROP COLUMN hire_date;
```

---

## Dropping Schema Objects

### Drop Table
```sql
DROP TABLE employees;
```

### Drop View
```sql
DROP VIEW emp_names;
```

### Drop Sequence
```sql
DROP SEQUENCE emp_seq;
```

### Drop Index
```sql
DROP INDEX emp_name_idx;
```

---

## Best Practices
- Use meaningful names for schema objects.
- Regularly review and clean up unused objects.
- Use constraints and indexes to enforce data integrity and improve performance.
- Document schema changes for team collaboration.

---

## References
- [Oracle 23ai SQL Language Reference: Schema Objects](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/Schema-Objects.html)
