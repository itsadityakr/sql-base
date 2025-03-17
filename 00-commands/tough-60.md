## ```DATABASE``` Commands

---

 **1. What is the difference between a database and a table in MySQL?**  
- A **database** is a **collection of tables** that store structured data.  
- A **table** is a structured format **inside a database** that holds rows (records) and columns (fields).  

Example:  
- A **database**: `company_db`  
- A **table inside the database**: `employees`  

---

 **2. Why do we need to use the `USE database_name;` command before executing queries?**  
- MySQL needs to know **which database** you are working with before running queries.  
- If you **don’t specify a database**, MySQL **doesn’t know** where to execute queries.  

Example:  
```sql
USE company_db;
SELECT * FROM employees;
```
- Now, any SQL commands will **apply to `company_db`**.  

---

 **3. What happens if you try to `USE` a database that does not exist?**  
- MySQL will return an **error**:  
  ```
  ERROR 1049 (42000): Unknown database 'database_name'
  ```
- The database must be created **before using it**.  

---

 **4. Can you create two databases with the same name in MySQL? Why or why not?**  
- **No**, you **cannot** create two databases with the same name.  
- MySQL stores databases as directories in the file system, and duplicate names would cause conflicts.  

---

 **5. What is the default storage engine for MySQL databases? How does it affect database operations?**  
- **Default storage engine:** `InnoDB`  
- **InnoDB Features:**  
  - Supports **transactions** (`COMMIT`, `ROLLBACK`).  
  - Uses **row-level locking** for better performance.  
  - Supports **foreign keys** (relationships between tables).  
- Other storage engines: `MyISAM`, `Memory`, `CSV`, etc.  

---

 **6. What will happen if you execute `DROP DATABASE` without selecting a database first?**  
- Nothing bad happens **as long as you specify the database to drop**:
  ```sql
  DROP DATABASE company_db;
  ```
- If you accidentally **drop the wrong database**, the data is **lost permanently** unless you have a backup.  

---

 **7. How can you check if a database exists before creating or deleting it?**  
- Use `SHOW DATABASES`:
  ```sql
  SHOW DATABASES;
  ```
- Use `INFORMATION_SCHEMA`:
  ```sql
  SELECT SCHEMA_NAME FROM INFORMATION_SCHEMA.SCHEMATA WHERE SCHEMA_NAME = 'company_db';
  ```

---

 **8. What will happen if you attempt to create a database that already exists? How can you prevent this?**  
- MySQL will return an **error** if the database already exists.  
- To prevent errors, use:
  ```sql
  CREATE DATABASE IF NOT EXISTS company_db;
  ```
- This **only creates** the database if it does **not already exist**.  

---

 **9. What is the effect of using `DROP DATABASE` on active connections to that database?**  
- **All active connections** are **terminated** immediately.  
- Any running queries on the database **fail**.  
- The database is **removed permanently** along with its tables and data.  

---

 **10. Can you rename a database in MySQL? If not, what is the workaround?**  
- **No**, MySQL **does not support renaming databases**.  
- Workaround:
  1. Create a **new database**:
     ```sql
     CREATE DATABASE new_db;
     ```
  2. Copy tables from the old database:
     ```sql
     INSERT INTO new_db.employees SELECT * FROM old_db.employees;
     ```
  3. Drop the old database:
     ```sql
     DROP DATABASE old_db;
     ```

---

 **11. If a user has limited privileges, can they execute `SHOW DATABASES;`? How can you restrict access to viewing all databases?**  
- **By default**, users **see only the databases they have access to**.  
- **Admin users** see all databases.  
- To restrict access:
  ```sql
  REVOKE SHOW DATABASES ON *.* FROM 'user_name'@'host';
  ```
- This prevents a user from listing **all** databases.  

---

 **12. What are the differences between `SHOW DATABASES` and querying the `INFORMATION_SCHEMA`?**  
| Feature | `SHOW DATABASES` | `INFORMATION_SCHEMA` |
|---------|-----------------|----------------------|
| Purpose | Lists all databases | Provides details of databases, tables, columns |
| Output Format | Simple list | Structured table |
| Filtering | No filtering | Can use `WHERE` conditions |
| Access Control | Shows only allowed databases | Can query specific schemas |

Example of `INFORMATION_SCHEMA`:
```sql
SELECT SCHEMA_NAME FROM INFORMATION_SCHEMA.SCHEMATA;
```

---

 **13. How would you backup a database before dropping it?**  
- Use the `mysqldump` command to create a backup:  
  ```sh
  mysqldump -u root -p company_db > backup.sql
  ```
- This saves all **tables and data** into a file (`backup.sql`).  
- Later, you can **restore** the database using:
  ```sh
  mysql -u root -p company_db < backup.sql
  ```

---

 **14. Can a database be restored after being dropped? If yes, how? If no, why?**  
- **No**, unless you have a **backup**.  
- If no backup exists, all data is **permanently lost**.  
- To restore a database, use:
  ```sh
  mysql -u root -p < backup.sql
  ```

---

 **15. How can you list only the databases created by a specific user?**  
- Use the `INFORMATION_SCHEMA.SCHEMATA` table:
  ```sql
  SELECT SCHEMA_NAME 
  FROM INFORMATION_SCHEMA.SCHEMATA 
  WHERE SCHEMA_NAME NOT IN ('mysql', 'performance_schema', 'information_schema', 'sys');
  ```
- This filters out **system databases**, showing only **user-created databases**.  

---

## DataTypes

---

 **1. What is the difference between `CHAR` and `VARCHAR`? When would you use one over the other?**  
- `CHAR(n)`:  
  - Stores **fixed-length** strings.  
  - Always **allocates** the full `n` characters, even if the string is shorter.  
  - Example: `CHAR(5)` always uses **5 bytes**, even for `"Hi"` (adds spaces).  
  - **Best for:** Short, consistent-length data like **postal codes, country codes**.  

- `VARCHAR(n)`:  
  - Stores **variable-length** strings.  
  - Uses **only the required space** + 1 extra byte (or 2 bytes for long strings).  
  - Example: `VARCHAR(5)` stores `"Hi"` in **2 bytes** instead of 5.  
  - **Best for:** Long, unpredictable text like **names, addresses**.  

---

 **2. Why is `DECIMAL` preferred over `FLOAT` or `DOUBLE` for financial calculations?**  
- `DECIMAL` **stores exact values**, while `FLOAT` and `DOUBLE` may have **rounding errors**.  
- **Example (floating-point issue):**  
  ```sql
  SELECT 0.1 + 0.2;
  ```
  - **Expected:** `0.3`  
  - **Actual (FLOAT/DOUBLE issue):** `0.30000000000000004`  
- This error is bad for **money calculations** (e.g., banking, billing).  
- **Use `DECIMAL(m, d)`** where:  
  - `m = total digits`  
  - `d = digits after decimal`  

---

 **3. What happens when you insert a string longer than the defined `VARCHAR(n)` size?**  
- If the string is **too long**, MySQL **truncates (cuts) it** and may show a warning.  
- Example:  
  ```sql
  CREATE TABLE test (name VARCHAR(5));
  INSERT INTO test VALUES ('HelloWorld');  -- 'Hello' is stored, 'World' is cut
  ```
- If `STRICT` mode is **ON**, MySQL gives an **error** instead of truncating.  

---

 **4. What are the limitations of `TEXT` and `BLOB` data types compared to `VARCHAR`?**  
| Feature | `VARCHAR` | `TEXT` | `BLOB` |
|---------|----------|--------|--------|
| Storage | Stored **inline** with row | Stored **separately** | Stored **separately** |
| Max Size | 65,535 bytes | 4GB (`LONGTEXT`) | 4GB (`LONGBLOB`) |
| Indexing | **Yes** | **Limited** | **Limited** |
| Sorting | **Fast** | **Slow** | **Slow** |
| Use Case | Short text (e.g., names) | Large text (e.g., blogs) | Binary data (e.g., images) |

- **`TEXT` and `BLOB` do not support full indexing**, making queries slower.  

---

 **5. How does `DATETIME` differ from `TIMESTAMP` in MySQL?**  
| Feature | `DATETIME` | `TIMESTAMP` |
|---------|-----------|-------------|
| Storage | **8 bytes** | **4 bytes** |
| Range | `1000-01-01` to `9999-12-31` | `1970-01-01` to `2038-01-19` |
| Auto-Update | ❌ No | ✅ Yes (if set to `CURRENT_TIMESTAMP`) |
| Timezone | **Not affected** | **Affected by timezone** |

- **Use `TIMESTAMP`** for automatic updates and timezone-aware values.  
- **Use `DATETIME`** when storing historical or future dates beyond 2038.  

---

 **6. If you define a column as `DECIMAL(5,2)`, what will happen if you insert `123.456`?**  
- `DECIMAL(5,2)` means **5 total digits** (`xxx.yy`).  
- `123.456` has **too many decimal places**, so MySQL **rounds** it to `123.46`.  
- If `STRICT` mode is **ON**, MySQL throws an **error** instead.  

---

 **7. What happens if you try to store Unicode characters in a `CHAR` or `VARCHAR` column without specifying `utf8mb4` encoding?**  
- MySQL **may replace characters** or **store them incorrectly**.  
- Example:
  ```sql
  CREATE TABLE test (name VARCHAR(10) CHARACTER SET latin1);
  INSERT INTO test VALUES ('你好');
  ```
  - The `你好` (Chinese) characters might be **corrupted** because `latin1` doesn’t support them.  
- **Solution:** Always use `utf8mb4` for full Unicode support:
  ```sql
  CREATE TABLE test (name VARCHAR(10) CHARACTER SET utf8mb4);
  ```

---

 **8. Can a `TEXT` or `BLOB` column be indexed? What are the limitations?**  
- **Yes, but only partially** (first `n` characters).  
- **Limitations:**  
  - MySQL requires a **prefix length** for indexing (e.g., `INDEX (column(255))`).  
  - Full indexing **is slow** because `TEXT/BLOB` is stored **separately**.  
  - **No default sorting** for `TEXT/BLOB` columns.  

---

 **9. What will happen if you try to store a `NULL` value in a `NOT NULL` column? How can you prevent this?**  
- MySQL **throws an error**:
  ```
  ERROR 1048 (23000): Column 'column_name' cannot be null
  ```
- **Preventing issues:**  
  - Use a **default value**:
    ```sql
    ALTER TABLE employees MODIFY salary INT NOT NULL DEFAULT 0;
    ```
  - Ensure applications **always provide values** when inserting data.  

---

 **10. What is the difference between `BIGINT` and `UUID` for storing unique identifiers? Which one would you choose and why?**  
| Feature | `BIGINT` | `UUID` |
|---------|---------|-------|
| Storage | **8 bytes** | **16 bytes** |
| Readability | ❌ Not human-friendly | ✅ Easier to work with |
| Indexing Speed | ✅ Faster | ❌ Slower |
| Randomness | ❌ Sequential | ✅ Highly random |

- **Use `BIGINT`** if performance and indexing are critical (e.g., IDs).  
- **Use `UUID`** if you need **random, unique, distributed** IDs (e.g., microservices).  

---

 **11. How can you store JSON data in MySQL, and what are the advantages and disadvantages of using the `JSON` data type?**  
 **Storing JSON:**
```sql
CREATE TABLE users (id INT, data JSON);
INSERT INTO users VALUES (1, '{"name": "Alice", "age": 25}');
```

 **Advantages of `JSON`:**
- **Flexible structure** (no fixed schema).  
- **Built-in functions** (`JSON_EXTRACT()`, `JSON_ARRAY()`).  

 **Disadvantages of `JSON`:**
- **Slower than normal columns** (no indexing).  
- **Takes more storage** than relational data.  
- **Harder to query** than structured tables.  

- **Use `JSON`** when data structure is **dynamic**.  
- **Use normal columns** for **fast and structured** queries.  

---

 **12. Why is `TIMESTAMP` generally more efficient than `DATETIME`? In what cases would you still prefer `DATETIME`?**  
- **`TIMESTAMP` is smaller (4 bytes) and auto-updates**, making it **faster**.  
- **Use `DATETIME`** when:  
  - You need dates **beyond 2038**.  
  - You don’t want timezone conversion issues.  

---

