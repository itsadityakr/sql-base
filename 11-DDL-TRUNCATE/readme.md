![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)


# DDL `TRUNCATE` Command

The `TRUNCATE` command is a **Data Definition Language (DDL)** statement used to remove all rows from a table while keeping the table structure intact. It is a fast and efficient way to delete all data from a table without dropping and recreating it. Unlike the `DELETE` command, `TRUNCATE` does not log individual row deletions, making it ideal for clearing large tables.

---

## Syntax of `TRUNCATE`
The basic syntax for the `TRUNCATE` command is as follows:

```sql
TRUNCATE TABLE table_name;
```

---

## Key Features of `TRUNCATE`

### 1. **Removes All Rows**
The `TRUNCATE` command deletes all rows from a table, but the table structure (columns, constraints, indexes, etc.) remains unchanged.

### 2. **Faster Than `DELETE`**
`TRUNCATE` is faster than `DELETE` because it does not log individual row deletions. It deallocates the data pages used by the table, making it more efficient for large tables.

### 3. **Cannot Be Rolled Back**
In most database systems, `TRUNCATE` is a DDL command and cannot be rolled back using a transaction. Once executed, the data is permanently deleted.

### 4. **Resets Identity Columns**
If the table has an identity column (e.g., an auto-incrementing primary key), `TRUNCATE` resets the counter to its initial value.

### 5. **Requires Privileges**
Only users with sufficient privileges (e.g., table owner or database administrator) can execute the `TRUNCATE` command.

---

## Common Use Cases of `TRUNCATE`

### 1. **Clearing a Table**
The primary use of `TRUNCATE` is to remove all rows from a table while preserving its structure.

#### Example
```sql
TRUNCATE TABLE employees;
```
This removes all rows from the `employees` table but keeps the table structure intact.

---

### 2. **Resetting Identity Columns**
If a table has an identity column, `TRUNCATE` resets the counter to its initial value.

#### Example
```sql
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);

INSERT INTO employees (first_name, last_name) VALUES ('John', 'Doe');
INSERT INTO employees (first_name, last_name) VALUES ('Jane', 'Smith');

TRUNCATE TABLE employees;
```
After truncating the table, the `employee_id` counter will reset to 1.

---

### 3. **Improving Performance**
For large tables, `TRUNCATE` is more efficient than `DELETE` because it does not log individual row deletions.

#### Example
```sql
TRUNCATE TABLE large_table;
```
This clears the `large_table` quickly and efficiently.

---

## Advanced Usage of `TRUNCATE`

### 1. **Using `TRUNCATE` with Foreign Keys**
If a table is referenced by foreign keys in other tables, `TRUNCATE` may fail unless the foreign key constraints are disabled or the referenced tables are also truncated.

#### Example
```sql
-- Disable foreign key checks (MySQL)
SET FOREIGN_KEY_CHECKS = 0;

TRUNCATE TABLE departments;

-- Re-enable foreign key checks
SET FOREIGN_KEY_CHECKS = 1;
```
This truncates the `departments` table even if it is referenced by foreign keys.

---

### 2. **Truncating Multiple Tables**
Some database systems (e.g., PostgreSQL) allow truncating multiple tables in a single command.

#### Example (PostgreSQL)
```sql
TRUNCATE TABLE employees, departments, projects;
```
This truncates the `employees`, `departments`, and `projects` tables.

---

## Comparison: `TRUNCATE` vs `DELETE`

| Feature                | `TRUNCATE`                          | `DELETE`                          |
|------------------------|-------------------------------------|-----------------------------------|
| **Operation Type**     | DDL (Data Definition Language)      | DML (Data Manipulation Language)  |
| **Speed**              | Faster (deallocates data pages)     | Slower (logs individual rows)     |
| **Rollback**           | Cannot be rolled back               | Can be rolled back                |
| **Identity Columns**   | Resets the counter                  | Does not reset the counter        |
| **Where Clause**       | Not supported                       | Supported                         |
| **Triggers**           | Does not fire triggers              | Fires triggers                    |

---

## Example: Full `TRUNCATE` Workflow

### Step 1: Create a Table
```sql
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);
```

### Step 2: Insert Data
```sql
INSERT INTO employees (first_name, last_name) VALUES ('John', 'Doe');
INSERT INTO employees (first_name, last_name) VALUES ('Jane', 'Smith');
```

### Step 3: Truncate the Table
```sql
TRUNCATE TABLE employees;
```
This removes all rows from the `employees` table and resets the `employee_id` counter.

---

## Conclusion
The `TRUNCATE` command is a powerful and efficient way to remove all rows from a table while keeping its structure intact. Key points to remember:
- It is faster than `DELETE` because it does not log individual row deletions.
- It cannot be rolled back in most database systems.
- It resets identity columns to their initial values.

Use `TRUNCATE` with caution, especially in production environments, as it permanently deletes all data from the table. Always ensure you have a backup before executing `TRUNCATE` commands.

---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)