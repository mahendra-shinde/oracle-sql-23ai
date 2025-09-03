# Steps to Install Sample HR Schema

## Prerequisites

- Oracle Database is installed and running.
- You have access to SQL*Plus or Oracle SQL Developer.
- You have DBA privileges or access to a user who can create other users.

## Installation Steps

1. **Start PowerShell and create a folder for the HR schema files:**

    ```powershell
    cd \
    New-Item -ItemType Directory -Path .\hr-schema
    Set-Location .\hr-schema
    ```

2. **Download the SQL files for the HR Schema from GitHub:**

    ```powershell
    Invoke-WebRequest -Uri "https://raw.githubusercontent.com/oracle-samples/db-sample-schemas/refs/heads/main/human_resources/hr_code.sql" -OutFile "hr_code.sql"
    Invoke-WebRequest -Uri "https://raw.githubusercontent.com/oracle-samples/db-sample-schemas/refs/heads/main/human_resources/hr_create.sql" -OutFile "hr_create.sql"
    Invoke-WebRequest -Uri "https://raw.githubusercontent.com/oracle-samples/db-sample-schemas/refs/heads/main/human_resources/hr_install.sql" -OutFile "hr_install.sql"
    Invoke-WebRequest -Uri "https://raw.githubusercontent.com/oracle-samples/db-sample-schemas/refs/heads/main/human_resources/hr_populate.sql" -OutFile "hr_populate.sql"
    ```

3. **Connect to your database using SQL*Plus and run the installation script:**

    ```powershell
    sqlplus sys/oracle@localhost:1521/freepdb1 as sysdba
    ```

    > If above command fails to connect to database, try following command instead:

    `sqlplus sys/oracle as sydba`

    At the SQL*Plus prompt, run:

    ```sql
    ALTER SESSION SET CONTAINER=FREEPDB1;
    @hr_install.sql
    ```

    > **Note:** Ensure all the SQL files are downloaded inside the `C:\hr-schema` folder before running the installation

4. **When prompted for Password, enter 'hr'**

5. **For Rest of the prompts, just press ENTER each time**

6.  **To Verify if Oracle Transaction Listner is working, try below command in command prompt:**
    `lsnrctl status`


6.  **After Installation is Over, connect using SQL Developer**

	```ini
	Connection-Name= db1
	Hostname= localhost
	Service-Name= freepdb1
	Port= 1521
	Username= hr
	Password= hr
	```

---

## Troubleshooting Common Connectivity Issues

If you encounter issues connecting to the Oracle database, try the following steps:

1. **Check if the Oracle Listener is running:**
    ```powershell
    lsnrctl status
    ```
    If the listener is not running, start it with:
    ```powershell
    lsnrctl start
    ```

2. **Verify the database service is registered with the listener:**
    - In the output of `lsnrctl status`, ensure your service (e.g., `freepdb1`) is listed under "Services Summary".

3. **Test connectivity using tnsping:**
    ```powershell
    tnsping freepdb1
    ```
    If this fails, check your network configuration and firewall settings.

4. **Check your TNS configuration:**
    - Ensure that `tnsnames.ora` (usually in `ORACLE_HOME\network\admin`) contains the correct service name and connection details.

5. **Check for port conflicts or firewall issues:**
    - Make sure port `1521` is open and not blocked by Windows Firewall or other security software.

6. **Review Oracle service status:**
    - Open Services (`services.msc`) and ensure all Oracle services are running.

7. **Check for typos in connection details:**
    - Double-check hostname, service name, port, username, and password.

If problems persist, consult the Oracle alert logs and listener logs for more detailed error messages.