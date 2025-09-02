
# Using Data Dictionary Tables in Oracle

The Oracle Data Dictionary is a set of read-only tables and views that provide information about the database, its structure, and its objects. These tables are essential for database administration, development, and troubleshooting.

---

## What are Data Dictionary Tables?

Data dictionary tables store metadata about the database, such as information about tables, columns, users, privileges, indexes, and more. They are automatically maintained by Oracle.

---

## Key Data Dictionary Views

| View Name         | Description                                      |
|-------------------|--------------------------------------------------|
| `USER_TABLES`     | Info about tables owned by the current user      |
| `ALL_TABLES`      | Info about tables accessible to the user         |
| `DBA_TABLES`      | Info about all tables in the database            |
| `USER_OBJECTS`    | Info about all objects owned by the user         |
| `USER_TAB_COLUMNS`| Info about columns in user's tables              |
| `USER_CONSTRAINTS`| Info about constraints on user's tables          |
| `USER_INDEXES`    | Info about indexes on user's tables              |
| `USER_VIEWS`      | Info about views owned by the user               |

---

## Common Usage Examples

### List All Tables Owned by the User
```sql
SELECT table_name FROM USER_TABLES;
```

### Get Column Details for a Table
```sql
SELECT column_name, data_type, nullable
FROM USER_TAB_COLUMNS
WHERE table_name = 'EMPLOYEES';
```

### List All Objects Owned by the User
```sql
SELECT object_name, object_type, status
FROM USER_OBJECTS;
```

### Find Constraints on a Table
```sql
SELECT constraint_name, constraint_type
FROM USER_CONSTRAINTS
WHERE table_name = 'EMPLOYEES';
```

### List Indexes on a Table
```sql
SELECT index_name, uniqueness
FROM USER_INDEXES
WHERE table_name = 'EMPLOYEES';
```

---

## Best Practices
- Use `USER_` views for objects you own, `ALL_` views for objects you can access, and `DBA_` views (requires DBA privileges) for all objects in the database.
- Always use uppercase for object names in queries (Oracle stores them in uppercase by default).
- Use data dictionary views to audit, troubleshoot, and document your database.

---

## References
- [Oracle 23ai SQL Language Reference: Data Dictionary Views](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/Data-Dictionary-Views.html)
