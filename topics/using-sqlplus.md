## Using Oracle SQL*Plus

Oracle SQL*Plus is the default command-line interface for interacting with Oracle databases. It is widely used by database administrators, developers, and support engineers for running SQL and PL/SQL commands, managing database objects, and automating tasks.

### Key Features
- **Command-Line Interface**: Lightweight and fast for direct database access.
- **Script Execution**: Run SQL and PL/SQL scripts for automation and batch processing.
- **Formatting Tools**: Customize output for reports using formatting commands.
- **Spooling**: Save query results to files for later use or reporting.
- **Environment Variables**: Set variables to control session behavior and output.

### Getting Started
1. **Launch SQL*Plus**: Open a terminal or command prompt and type `sqlplus`.
2. **Connect to Database**: Use the command:
	```sh
	sqlplus username/password@hostname:port/service_name
	```
	or for local connections:
	```sh
	sqlplus username/password
	```
3. **Run SQL Commands**: Enter SQL or PL/SQL statements at the prompt and end with a semicolon (`;`).
4. **Execute Scripts**: Use `@scriptname.sql` to run a script file.

### Example: Basic SQL*Plus Session
```sh
sqlplus hr/welcome@localhost:1521/orclpdb1
SQL> SELECT * FROM employees;
SQL> @myscript.sql
SQL> SPOOL output.txt
SQL> EXIT
```

### Useful SQL*Plus Commands
- `SHOW USER` — Displays the current user.
- `DESCRIBE table_name` — Shows table structure.
- `SET PAGESIZE 50` — Sets the number of rows per page.
- `SET LINESIZE 100` — Sets the width of output lines.
- `SPOOL filename` — Writes output to a file.
- `COLUMN col_name FORMAT A20` — Formats column output.

### Tips
- Use SQL*Plus for scripting, automation, and quick database tasks.
- Learn formatting commands for professional report output.
- Use `HELP` command for built-in documentation.

### Resources
- [Oracle SQL*Plus User's Guide and Reference](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqpug/index.html)
