```markdown
# SQL Commands - MySQL

## MySQL Installation

To install MySQL on your system, run the following commands:

```bash
sudo apt install mysql-server
sudo apt install mysql-client
mysql --version
```

## MySQL Manual

To access the MySQL manual, use the following command:

```bash
man mysql
```

## Local Access

To access MySQL locally, use the following command:

```bash
mysql -u root -p
```

## Secure MySQL Installation

The secure installation of MySQL (`mysql-secure-installation`) allows you to:

- Restrict access only from `localhost` for the `root` user.
- Remove anonymous access.
- Remove the `test` database.
- Change the default password.

To run the secure installation, use:

```bash
sudo mysql_secure_installation
```

First, change the password for the `root` user.

### Modify User Password

To change the password for the `root` user and ensure it can only be accessed from `localhost`, execute:

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
```

> **Note:** Be sure to replace `123456` with a secure password.

## MySQL Configuration

To start configuring MySQL, run:

```bash
sudo mysql_secure_installation
```

## Show MySQL Users

To list users in MySQL, you can use the following commands:

```sql
SELECT USER FROM mysql.user;
SELECT USER, HOST FROM mysql.user;
```

```markdown
# Start and Stop MySQL Server

## Linux - Start and Stop the Server

To start, stop, or restart the MySQL server on Linux, you can use the following commands:

```bash
/etc/init.d/mysql start
/etc/init.d/mysql stop
/etc/init.d/mysql restart
```

## Linux - Service Commands

Depending on your Linux distribution, you might need to use service commands. These commands might vary, commonly using `mysqld` or `mysql`:

```bash
service mysql start
service mysql stop
service mysql restart
service mysql status
```

```markdown
# MySQL Commands - Database and Table Operations

## Checking All Ports (Linux)

To review all ports in Linux, use the following command:

```bash
cat /etc/services
```

- **Default MySQL port:** `3306`

## Primary and Foreign Keys

- **Primary Keys:** Identify a table.
- **Foreign Keys:** Create relationships between tables and help prevent duplicate entries.

## MySQL Commands

### Connecting to MySQL as the Root User

To connect to MySQL using the root user, run the following command:

```bash
sudo mysql -u root -p
```

> You will be prompted for the password if there is a password configuration.

### Creating Databases and Tables

1. **Show all databases:**

    ```sql
    SHOW DATABASES;
    ```

2. **Create a new database:**

    ```sql
    CREATE DATABASE <database_name>;
    ```

3. **Use a specific database:**

    ```sql
    USE <database_name>;
    ```

4. **Show all tables in the database:**

    ```sql
    SHOW TABLES;
    ```

5. **Create a new table:**

    ```sql
    CREATE TABLE <table_name> (
        id INT(10) NOT NULL AUTO_INCREMENT,
        name VARCHAR(60) NOT NULL,
        surname VARCHAR(60) NOT NULL,
        address VARCHAR(60),
        PRIMARY KEY (id)
    );
    ```

6. **Describe table structure:**

    ```sql
    DESCRIBE <table_name>;
    ```

### CRUD Operations

#### CREATE

7. **Insert data into a table:**

    ```sql
    INSERT INTO <table_name> (name, surname, address)
    VALUES ('Juan', 'De la Torre', 'Avenida SQL 123');
    ```

#### READ

8. **Select data from a table:**

    - Select all records:

        ```sql
        SELECT * FROM <table_name>;
        ```

    - Select specific columns:

        ```sql
        SELECT column1, column2 FROM <table_name>;
        ```

    - Select specific records with conditions:

        ```sql
        SELECT * FROM <table_name> WHERE id = 1;
        ```

    - Select the first few records (LIMIT):

        ```sql
        SELECT * FROM <table_name> LIMIT X;
        ```

#### UPDATE

9. **Update existing records in a table:**

    ```sql
    UPDATE <table_name> SET name = 'Juan Pablo', address = 'Av. SQL 78901' WHERE id = 1;
    ```

    > Only the specified fields will be updated.

#### DELETE

10. **Delete records from a table:**

    ```sql
    DELETE FROM <table_name> WHERE id = 1;
    ```

    > This will delete the records where the condition is met, leaving empty spaces.

### Additional Commands

- **Drop a database:**

    ```sql
    DROP DATABASE <database_name>;
    ```

- **Drop a table:**

    ```sql
    DROP TABLE <table_name>;
    ```
