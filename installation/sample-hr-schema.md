# Steps to Install Sample HR Schema

Follow these steps to install the HR schema using the provided `hr-schema.sql` file:

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
    sqlplus sys/orcle@localhost:1521/freepdb1 as sysdba
    ```

    At the SQL*Plus prompt, run:

    ```sql
    @hr_install.sql
    ```

    > **Note:** Ensure all the SQL files are downloaded inside the `C:\hr-schema` folder before running the installation

4. **When prompted for Password, enter 'hr'**

5. **For Rest of the prompts, just press ENTER each time**

6.  **After Installation is Over, connect using SQL Developer**

	```ini
	Connection-Name= db1
	Hostname= localhost
	Service-Name= freepdb1
	Port= 1521
	Username= hr
	Password= hr
	```