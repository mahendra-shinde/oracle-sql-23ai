# Regular Expression Support in Oracle SQL (23ai)

Oracle SQL provides robust support for regular expressions, enabling advanced string matching, searching, and manipulation directly within SQL statements. Version 23ai continues to enhance these capabilities, making pattern-based data processing more powerful and efficient.

## Key Regular Expression Functions

Oracle SQL offers several built-in functions for working with regular expressions:

| Function                | Description                                                      |
|-------------------------|------------------------------------------------------------------|
| `REGEXP_LIKE`           | Returns TRUE if the string matches the regular expression pattern |
| `REGEXP_INSTR`          | Returns the position of a regex match in a string                |
| `REGEXP_SUBSTR`         | Returns the substring matching a regex pattern                    |
| `REGEXP_REPLACE`        | Replaces substrings matching a regex pattern                      |
| `REGEXP_COUNT`          | Returns the number of times a pattern occurs in a string         |

### 1. REGEXP_LIKE
```sql
SELECT * FROM employees WHERE REGEXP_LIKE(email, '^[A-Za-z0-9._%+-]+@oracle.com$');
```
*Finds employees with emails ending in @oracle.com.*

### 2. REGEXP_INSTR
```sql
SELECT REGEXP_INSTR('abc123def', '\d+') AS position FROM dual;
```
*Returns the position of the first digit sequence.*

### 3. REGEXP_SUBSTR
```sql
SELECT REGEXP_SUBSTR('Order #12345 shipped', '\d+') AS order_num FROM dual;
```
*Extracts the first number from the string.*

### 4. REGEXP_REPLACE
```sql
SELECT REGEXP_REPLACE('Phone: (123) 456-7890', '\D', '') AS digits FROM dual;
```
*Removes all non-digit characters.*

### 5. REGEXP_COUNT
```sql
SELECT REGEXP_COUNT('a1b2c3', '\d') AS digit_count FROM dual;
```
*Counts the number of digits in the string.*

## Regular Expression Syntax

- **Anchors:** `^` (start), `$` (end)
- **Character Classes:** `[A-Za-z]`, `\d`, `\w`, `\s`
- **Quantifiers:** `*`, `+`, `?`, `{n,m}`
- **Groups:** `( ... )`
- **Alternation:** `|`

## New Features in Oracle SQL 23ai

- **Improved Unicode Support:** Enhanced handling of Unicode characters in regex patterns.
- **Performance Enhancements:** Faster regex evaluation for large datasets.
- **Additional Pattern Options:** New flags for case-insensitive and multi-line matching.

## Practical Examples

**Validate Indian Mobile Numbers:**
```sql
SELECT phone FROM customers WHERE REGEXP_LIKE(phone, '^[6-9]\d{9}$');
```

**Extract Domain from Email:**
```sql
SELECT REGEXP_SUBSTR(email, '@(.+)$', 1, 1, NULL, 1) AS domain FROM users;
```

**Replace Multiple Spaces with Single Space:**
```sql
SELECT REGEXP_REPLACE('Oracle    SQL   23ai', ' +', ' ') AS cleaned FROM dual;
```

## References

- [Oracle 23ai SQL Language Reference: Regular Expressions](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/regular-expressions.html)

