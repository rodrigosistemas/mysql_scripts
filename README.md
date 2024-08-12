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

## Modify Database Attributes

- **Add a column:**

    ```sql
    ALTER TABLE <table_name> ADD column_name VARCHAR(30);
    ```

- **Drop a column:**

    ```sql
    ALTER TABLE <table_name> DROP COLUMN column_name;
    ```

### ORDER BY

- **Sort results by a column in ascending order:**

    ```sql
    SELECT * FROM <table_name> ORDER BY <column>;
    ```

- **Sort results by a column in descending order:**

    ```sql
    SELECT * FROM <table_name> ORDER BY <column> DESC;
    ```

### COUNT and GROUP BY

- **COUNT function:** Aggregates the number of times a record appears.

    ```sql
    SELECT COUNT(id), <column> FROM <table_name>
    GROUP BY <column> ORDER BY COUNT(id);
    ```

### JOIN

The `JOIN` clause allows combining two or more tables based on a common column they share.

### DISTINCT

- **Select distinct records, ignoring duplicates:**

    ```sql
    SELECT DISTINCT <column> FROM <table_name>;
    ```

### BETWEEN AND

- **Select records where a column's value is within a specific range:**

    ```sql
    SELECT * FROM <table_name> WHERE <column> BETWEEN value1 AND value2;
    ```

### LIKE

- **Use wildcards to match patterns within a column's data:**

    ```sql
    SELECT * FROM <table_name> WHERE <column> LIKE '%word%';
    ```

- **LIKE with two columns using CONCAT:**

    ```sql
    SELECT * FROM <table_name>
    WHERE CONCAT(first_name, ' ', last_name) LIKE '%John Doe%';
    ```

## Error Handling Scripts

These scripts help manage specific error cases in MySQL, such as resetting table indices and handling foreign key constraints.

### Resetting Table Indexes in MySQL

If you need to reset the auto-increment value of a table's primary key column, follow these steps:

1. **Delete all existing records from the table:**
   
   ```sql
   DELETE FROM table_name;

2. **Reset the auto-increment value to 1 for the primary key column (e.g., `id_usuario`):**

   ```sql
   ALTER TABLE table_name AUTO_INCREMENT = 1;
   ```

### Dropping a Foreign Key Constraint

If you need to remove a foreign key constraint from a table, use the following command:

```sql
ALTER TABLE table_name DROP FOREIGN KEY table_name_ibfk_1;
```

Make sure to replace `table_name` with the actual name of your table, and `table_name_ibfk_1` with the specific name of the foreign key constraint you want to remove.
