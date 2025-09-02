
# Introduction to Data Dictionary Views

The data dictionary in Oracle 23ai is a set of read-only tables and views that provide information about the database, its structure, users, and objects. Data dictionary views are essential for database administration, development, and troubleshooting.

## Types of Data Dictionary Views

1. **USER_ Views**: Show information about objects owned by the current user.
2. **ALL_ Views**: Show information about objects accessible to the current user.
3. **DBA_ Views**: Show information about all objects in the database (requires DBA privileges).
4. **V$ Views (Dynamic Performance Views)**: Provide real-time performance and status information.

## Commonly Used Data Dictionary Views

| View Name           | Description                                 |
|---------------------|---------------------------------------------|
| USER_TABLES         | Tables owned by the user                    |
| USER_TAB_COLUMNS    | Columns in user's tables                    |
| USER_VIEWS          | Views owned by the user                     |
| USER_CONSTRAINTS    | Constraints on user's tables                |
| USER_INDEXES        | Indexes owned by the user                   |
| ALL_TABLES          | Tables accessible to the user               |
| DBA_TABLES          | All tables in the database                  |
| V$SESSION           | Current database sessions                   |
| V$DATABASE          | Information about the database              |

## Example Queries

### 1. List All Tables Owned by the User
```sql
SELECT table_name FROM USER_TABLES;
```

### 2. List All Columns in a Table
```sql
SELECT column_name, data_type FROM USER_TAB_COLUMNS WHERE table_name = 'EMPLOYEES';
```

### 3. Find All Constraints on a Table
```sql
SELECT constraint_name, constraint_type FROM USER_CONSTRAINTS WHERE table_name = 'EMPLOYEES';
```

### 4. List All Indexes on a Table
```sql
SELECT index_name FROM USER_INDEXES WHERE table_name = 'EMPLOYEES';
```

### 5. View All Views Accessible to the User
```sql
SELECT view_name FROM USER_VIEWS;
```

### 6. Check Current Database Sessions (Requires Privileges)
```sql
SELECT sid, serial#, username, status FROM V$SESSION;
```

## Key Points

- Data dictionary views are read-only.
- Use uppercase for object names in queries (Oracle stores them in uppercase by default).
- DBA_ views require special privileges.
- V$ views provide dynamic, real-time information.

## Practice Exercises

1. List all tables accessible to you in the database.
2. Find all columns and their data types in the DEPARTMENTS table.
3. Show all constraints on the JOBS table.
4. List all indexes on the EMPLOYEES table.
5. Display all views you own.

---
Refer to the [Oracle 23ai SQL documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/index.html) for more details and advanced usage.
