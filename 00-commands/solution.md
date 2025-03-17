### **`DATABASE` Commands**  

---

1. **Difference between a database and a table in MySQL**  
   - A **database** is a collection of tables, views, and other database objects that store structured data.  
   - A **table** is a structured set of rows and columns that store data within a database.

2. **Why use `USE database_name;` before executing queries?**  
   - It sets the default database for subsequent queries, ensuring that all operations (e.g., `SELECT`, `INSERT`, etc.) are executed on the specified database without needing to specify the database name in each query.

3. **What happens if you `USE` a non-existent database?**  
   - MySQL returns an error:  
     ```
     ERROR 1049 (42000): Unknown database 'database_name'
     ```

4. **Can two databases have the same name in MySQL? Why or why not?**  
   - No, each database name must be unique within a MySQL server instance.  
   - MySQL stores databases as directories in the file system, and duplicate directory names are not allowed.

5. **Default storage engine in MySQL & its effect**  
   - The default storage engine is **InnoDB**.  
   - It supports transactions, foreign keys, row-level locking, and ACID compliance.

6. **Effect of executing `DROP DATABASE` without selecting a database**  
   - `DROP DATABASE` is not dependent on the currently selected database.  
   - It deletes the specified database along with all its tables, views, and objects.

7. **Check if a database exists before creating or deleting it**  
   - Use:  
     ```sql
     SHOW DATABASES LIKE 'database_name';
     ```
   - Or query `INFORMATION_SCHEMA.SCHEMATA`:  
     ```sql
     SELECT SCHEMA_NAME FROM INFORMATION_SCHEMA.SCHEMATA WHERE SCHEMA_NAME = 'database_name';
     ```

8. **What happens if you attempt to create an existing database?**  
   - MySQL returns an error:  
     ```
     ERROR 1007 (HY000): Can't create database; database exists
     ```
   - Prevent this with:  
     ```sql
     CREATE DATABASE IF NOT EXISTS database_name;
     ```

9. **Effect of `DROP DATABASE` on active connections**  
   - Existing connections are terminated.  
   - Running transactions are rolled back.

10. **Can you rename a database in MySQL? Workaround?**  
    - No, MySQL does not support `RENAME DATABASE`.  
    - Workaround:  
      1. Create a new database.  
      2. Copy tables (`CREATE TABLE new_db.table AS SELECT * FROM old_db.table`).  
      3. Drop the old database.

11. **Can a user with limited privileges execute `SHOW DATABASES;`?**  
    - No, unless they have the `SHOW DATABASES` privilege.  
    - Restrict access by ensuring users only have `SHOW DATABASES` privilege for their databases.

12. **Difference between `SHOW DATABASES` and querying `INFORMATION_SCHEMA`**  
    - `SHOW DATABASES;` lists all databases the user has access to.  
    - `INFORMATION_SCHEMA.SCHEMATA` provides metadata and additional details about databases.

13. **Backup a database before dropping it**  
    - Use `mysqldump`:  
      ```bash
      mysqldump -u root -p database_name > backup.sql
      ```

14. **Can a database be restored after being dropped?**  
    - No, unless a backup exists.  
    - If backed up, restore using:  
      ```bash
      mysql -u root -p database_name < backup.sql
      ```

15. **List databases created by a specific user**  
    - Query `INFORMATION_SCHEMA.SCHEMATA`:  
      ```sql
      SELECT SCHEMA_NAME FROM INFORMATION_SCHEMA.SCHEMATA WHERE SCHEMA_OWNER = 'user_name';
      ```

---

### **DataTypes**  

---

1. **Difference between `CHAR` and `VARCHAR`**  
   - `CHAR(n)`: Fixed-length, always stores `n` characters (padded with spaces if shorter).  
   - `VARCHAR(n)`: Variable-length, stores only the needed space.  
   - Use `CHAR` for fixed-size values (e.g., country codes).  
   - Use `VARCHAR` for varying-length text (e.g., names, emails).

2. **Why is `DECIMAL` preferred over `FLOAT` or `DOUBLE` for financial calculations?**  
   - `DECIMAL` provides exact precision, whereas `FLOAT` and `DOUBLE` can have rounding errors due to binary floating-point representation.

3. **What happens when inserting a string longer than `VARCHAR(n)`?**  
   - MySQL either truncates the string (if `STRICT_TRANS_TABLES` is disabled) or throws an error (if enabled).

4. **Limitations of `TEXT` and `BLOB` compared to `VARCHAR`**  
   - Cannot have a default value.  
   - Limited indexing (only first few characters are indexed).  
   - Uses separate storage, leading to performance overhead.

5. **Difference between `DATETIME` and `TIMESTAMP`**  
   - `DATETIME`: Stores date and time without considering time zones.  
   - `TIMESTAMP`: Stores date and time in UTC and converts it to the session’s time zone.

6. **Effect of inserting `123.456` into `DECIMAL(5,2)`**  
   - MySQL rounds it to `123.46`, since only two decimal places are allowed.

7. **Storing Unicode characters in `CHAR`/`VARCHAR` without `utf8mb4`**  
   - Unicode characters may not be stored correctly or may be replaced by `?`.

8. **Can `TEXT` or `BLOB` columns be indexed?**  
   - Yes, but with limitations:  
     - Only a prefix of the column (e.g., first 255 characters) can be indexed.

9. **What happens if you insert `NULL` into a `NOT NULL` column?**  
   - MySQL throws an error unless a default value is defined.

10. **Difference between `BIGINT` and `UUID` for unique identifiers**  
    - `BIGINT`: Integer-based, faster indexing, uses less storage.  
    - `UUID`: 128-bit, globally unique, harder to index efficiently.  
    - Choose `BIGINT` for performance, `UUID` for distributed systems.

11. **Storing JSON data in MySQL**  
    - Use `JSON` data type:  
      ```sql
      CREATE TABLE example (data JSON);
      ```
    - **Advantages**: Flexible schema, built-in functions.  
    - **Disadvantages**: Higher storage cost, limited indexing.

12. **Why is `TIMESTAMP` more efficient than `DATETIME`?**  
    - `TIMESTAMP` requires 4 bytes, while `DATETIME` requires 8 bytes.  
    - Prefer `DATETIME` if you need values beyond `2038` or don’t want time zone conversions.

---



---

