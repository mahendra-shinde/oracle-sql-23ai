## Creating Views in Oracle SQL Database 23ai

Views are virtual tables based on SQL queries. They simplify complex queries, enhance security, and provide data abstraction in Oracle SQL Database 23ai.

### Key Concepts
- **View**: A stored query that users can query like a table.
- **Simple View**: Based on a single table, no functions or groups.
- **Complex View**: Based on multiple tables, may include functions and groups.

### Creating a View
```sql
CREATE VIEW high_salary_employees AS
SELECT employee_id, first_name, salary
FROM employees
WHERE salary > 5000;
```

### Using a View
```sql
SELECT * FROM high_salary_employees;
```

### Modifying and Dropping Views
```sql
CREATE OR REPLACE VIEW high_salary_employees AS ...;
DROP VIEW high_salary_employees;
```

### Tips
- Use views to restrict data access.
- Views can simplify reporting and application development.
- Not all views are updatable.
