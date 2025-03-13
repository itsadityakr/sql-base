![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

# Managing Databases in MySQL

In MySQL, databases are containers that hold tables, views, and other database objects. This guide explains how to perform common database operations, such as listing, creating, selecting, and deleting databases.

---

## 1. List All Databases
To view all databases on a MySQL server, use the `SHOW DATABASES` command.

### Syntax
```sql
SHOW DATABASES;
```

![alt text](./assets/image.png)

---

## 2. Create a Database
To create a new database, use the `CREATE DATABASE` command.

### Syntax
```sql
CREATE DATABASE database_name;
```

### Example
```sql
CREATE DATABASE company;
```
![alt text](./assets/image-1.png)

This creates a new database named `company`.

---

## 3. Use or Select a Database
To select a database for use in subsequent queries, use the `USE` command.

### Syntax
```sql
USE database_name;
```

### Example
```sql
USE company;
```
This selects the `company` database. All subsequent queries will operate on this database.

---

## 4. Delete a Database
To delete a database, use the `DROP DATABASE` command. Be cautious, as this operation permanently removes the database and all its contents.

### Syntax
```sql
DROP DATABASE database_name;
```

### Example
```sql
DROP DATABASE company;
```
This deletes the `company` database.

![alt text](./assets/image.png)

---

## 5. See the Selected Database
To check which database is currently selected, use the `SELECT DATABASE()` function.

### Syntax
```sql
SELECT DATABASE();
```

![alt text](./assets/image-2.png)

This shows that `company` is the currently selected database.

---

## Summary of Commands
| Command                  | Description                                      | Example                              |
|--------------------------|--------------------------------------------------|--------------------------------------|
| `SHOW DATABASES;`        | Lists all databases on the server.               | `SHOW DATABASES;`                   |
| `CREATE DATABASE db_name;`| Creates a new database.                         | `CREATE DATABASE company;`  |
| `USE db_name;`           | Selects a database for use.                      | `USE company;`                  |
| `DROP DATABASE db_name;` | Deletes a database and all its contents.         | `DROP DATABASE company;`    |
| `SELECT DATABASE();`     | Shows the currently selected database.           | `SELECT DATABASE();`                |

---

## Conclusion
Managing databases in MySQL is straightforward with the `SHOW DATABASES`, `CREATE DATABASE`, `USE`, `DROP DATABASE`, and `SELECT DATABASE()` commands. These commands allow you to:
- List all databases.
- Create new databases.
- Select a database for use.
- Delete databases.
- Check the currently selected database.

Always exercise caution when using `DROP DATABASE`, as it permanently deletes the database and all its contents.

---

![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)