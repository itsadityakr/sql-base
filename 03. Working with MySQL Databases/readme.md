# Working with MySQL Databases

## Listing All Existing Databases

To list all existing databases in MySQL, you can use the following command in the MySQL command line interface:

```sql
SHOW DATABASES;
```

**Example Output:**

| **Database Name** |
|-------------------|
| information_schema|
| my_database       |
| mysql             |
| performance_schema|
| sys               |

**Explanation:**

- `SHOW DATABASES;` retrieves and displays the names of all databases available on the MySQL server.

## Creating a New Database

To create a new database in MySQL, use the following command:

```sql
CREATE DATABASE my_new_database;
```

**Example Command:**

```sql
CREATE DATABASE sales_db;
```

**Explanation:**

- `CREATE DATABASE database_name;` creates a new database with the name `database_name`.
- Replace `sales_db` with your desired database name.

## Clearing the MySQL Command Line

To clear the MySQL command line interface screen, you can use the following command:

```sql
system clear;
```

**Explanation:**

- `system clear;` runs the `clear` command of your operating system, which clears the terminal screen. Note that this command might vary based on your operating system and MySQL client.

## Working with a Database

To start working with a specific database, you first need to select it. Use the following command:

```sql
USE my_database;
```

**Example Command:**

```sql
USE sales_db;
```

**Explanation:**

- `USE database_name;` selects the database named `database_name` for subsequent operations like creating tables or querying data.
- Replace `sales_db` with the name of the database you wish to use.

## Deleting a Database

To delete an existing database, use the following command:

```sql
DROP DATABASE my_database;
```

**Example Command:**

```sql
DROP DATABASE sales_db;
```

**Explanation:**

- `DROP DATABASE database_name;` deletes the entire database and all of its tables and data.
- **Warning**: This action is irreversible. Make sure you really want to delete the database before executing this command.

---

- by Aditya Kumar