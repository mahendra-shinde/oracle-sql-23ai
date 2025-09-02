# Steps to Install Oracle Database 23ai Free on Windows

Follow these steps to install Oracle Database 23ai Free on your Windows machine:

## 1. Download Oracle Database 23ai Free

- Go to the official Oracle download page or use the direct link below:
	[Download Oracle Database 23ai Free for Windows (ZIP)](https://download.oracle.com/otn-pub/otn_software/db-express/WINDOWS.X64_239000_free.zip?AuthParam=1756818864_2896b155f334c7ded3f820014d78fdc9)

## 2. Extract the ZIP File

- Right-click the downloaded `WINDOWS.X64_239000_free.zip` file and select **Extract All...**
- Choose a destination folder (e.g., `C:\Oracle23aiFree`).

## 3. Run the Installer

- Open the extracted folder.
- Right-click `setup.exe` and select **Run as administrator**.

## 4. Follow the Installation Wizard

- Accept the license agreement and follow the prompts.
- Choose the installation location and set the Oracle Home user password as required.

> Use Oracle Home directory to `c:\app\oracle` and password as `oracle`

- Wait for the installation to complete.

## 5. Verify the Installation

- After installation, open **Command Prompt** 
- Connect using the default credentials or the ones you set during installation.

    ```
    sqlplus sys/oracle as sysdba
    ```

    > `sys` is default username and `oracle` is password set at installation time.

For more details, refer to the [official Oracle documentation](https://docs.oracle.com/en/database/oracle/oracle-database/23/index.html).
