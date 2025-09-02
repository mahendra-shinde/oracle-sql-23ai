
# Sequences, Synonyms, and Indexes in Oracle SQL

Oracle SQL provides powerful database objects to manage data integrity, simplify object referencing, and optimize query performance. This section covers Sequences, Synonyms, and Indexes with syntax and practical examples.

---

## 1. Sequences

A **Sequence** is a database object that generates unique numeric values, often used for primary keys.

### Creating a Sequence
```sql
CREATE SEQUENCE emp_seq
	START WITH 1
	INCREMENT BY 1
	NOCACHE
	NOCYCLE;
```

### Using a Sequence
```sql
INSERT INTO employees (id, name) VALUES (emp_seq.NEXTVAL, 'John Doe');
```

### Viewing Sequence Value
```sql
SELECT emp_seq.CURRVAL FROM dual;
```

---

## 2. Synonyms

A **Synonym** is an alias for a database object (table, view, sequence, etc.), simplifying SQL statements and providing location transparency.

### Creating a Synonym
```sql
CREATE SYNONYM emp FOR hr.employees;
```

### Using a Synonym
```sql
SELECT * FROM emp;
```

### Dropping a Synonym
```sql
DROP SYNONYM emp;
```

---

## 3. Indexes

An **Index** improves the speed of data retrieval operations on a table at the cost of additional storage and maintenance.

### Creating a Simple Index
```sql
CREATE INDEX emp_name_idx ON employees (name);
```

### Creating a Unique Index
```sql
CREATE UNIQUE INDEX emp_email_uk ON employees (email);
```

### Dropping an Index
```sql
DROP INDEX emp_name_idx;
```

### Types of Indexes
- **B-tree Index (default):** Good for most queries.
- **Bitmap Index:** Efficient for columns with low cardinality (few distinct values).
- **Function-based Index:** Indexes based on expressions or functions.

### Example: Function-based Index
```sql
CREATE INDEX emp_upper_name_idx ON employees (UPPER(name));
```

---

## Best Practices
- Use sequences for generating unique keys.
- Use synonyms to simplify access and support application migration.
- Create indexes on columns frequently used in WHERE, JOIN, or ORDER BY clauses.
- Avoid excessive indexing to reduce overhead on DML operations.

---

## References
- [Oracle 23ai SQL Language Reference: Sequences](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/CREATE-SEQUENCE.html)
- [Oracle 23ai SQL Language Reference: Synonyms](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/CREATE-SYNONYM.html)
- [Oracle 23ai SQL Language Reference: Indexes](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/CREATE-INDEX.html)

