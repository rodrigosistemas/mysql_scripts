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
```
