
# Using Single-Row Functions to Customize Output

Single-row functions in Oracle 23ai operate on single rows and return one result per row. They are essential for data transformation, formatting, and manipulation in SQL queries. These functions do not affect the number of rows returned by a query.

## Types of Single-Row Functions

1. **Character Functions**
	- Manipulate character data (strings).
	- Examples: `UPPER`, `LOWER`, `INITCAP`, `CONCAT`, `SUBSTR`, `LENGTH`, `TRIM`, `REPLACE`.

2. **Number Functions**
	- Perform operations on numeric data.
	- Examples: `ROUND`, `TRUNC`, `MOD`, `FLOOR`, `CEIL`, `ABS`, `POWER`.

3. **Date Functions**
	- Manipulate date and time values.
	- Examples: `SYSDATE`, `CURRENT_DATE`, `ADD_MONTHS`, `MONTHS_BETWEEN`, `NEXT_DAY`, `LAST_DAY`, `EXTRACT`.

4. **Conversion Functions**
	- Convert data from one type to another.
	- Examples: `TO_CHAR`, `TO_DATE`, `TO_NUMBER`, `CAST`.

5. **General Functions**
	- Miscellaneous functions for various tasks.
	- Examples: `NVL`, `NVL2`, `NULLIF`, `COALESCE`, `DECODE`, `CASE`.

## Character Functions Examples

```sql
SELECT UPPER('oracle 23ai') AS upper_case FROM dual; -- Output: ORACLE 23AI
SELECT SUBSTR('Database', 1, 4) AS sub_str FROM dual; -- Output: Data
SELECT LENGTH('Hello') AS length FROM dual; -- Output: 5
```

## Number Functions Examples

```sql
SELECT ROUND(123.456, 2) AS rounded FROM dual; -- Output: 123.46
SELECT MOD(10, 3) AS modulus FROM dual; -- Output: 1
```

## Date Functions Examples

```sql
SELECT SYSDATE AS today FROM dual;
SELECT ADD_MONTHS(SYSDATE, 6) AS future_date FROM dual;
SELECT EXTRACT(YEAR FROM SYSDATE) AS year FROM dual;
```

## Conversion Functions Examples

```sql
SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD') AS today_str FROM dual;
SELECT TO_DATE('2025-09-02', 'YYYY-MM-DD') AS date_val FROM dual;
SELECT TO_NUMBER('12345') AS num_val FROM dual;
```

## General Functions Examples

```sql
SELECT NVL(NULL, 'Default') AS nvl_example FROM dual; -- Output: Default
SELECT DECODE(1, 1, 'One', 'Other') AS decode_example FROM dual; -- Output: One
SELECT CASE WHEN 1=1 THEN 'Yes' ELSE 'No' END AS case_example FROM dual; -- Output: Yes
```

## Key Points

- Single-row functions return one result per row.
- Can be nested and combined in SQL statements.
- Useful for data formatting, cleaning, and transformation.
- Oracle 23ai introduces enhancements, but core single-row functions remain consistent with previous versions.

## Practice Questions

1. Write a query to display the employee names in uppercase from the `EMPLOYEES` table.
2. Show the current date in `YYYY-MM-DD` format.
3. Find the length of each department name in the `DEPARTMENTS` table.
4. Replace all occurrences of 'A' with 'X' in the string 'DATABASE'.
5. Use `NVL` to display 'N/A' if a manager ID is null in the `EMPLOYEES` table.

---
Refer to the [Oracle 23ai SQL documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/index.html) for more details and advanced usage.
