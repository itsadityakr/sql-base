# Modifying and Deleting Data in MySQL

## Modifying Data in a Table

To modify data in a MySQL table, you use the `UPDATE` command. This command allows you to change existing records based on specific conditions.

### Updating Data

To update data in a table, use the following syntax:

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### Example

Update the email address of an employee with a specific `employee_id`:

```sql
UPDATE employees
SET email = 'john.newemail@example.com'
WHERE employee_id = 1;
```

**Example Output:**

| **employee_id** | **first_name** | **last_name** | **email**                  | **hire_date** |
|-----------------|----------------|---------------|----------------------------|--------------|
| 1               | John           | Doe           | john.newemail@example.com  | 2024-01-15   |

**Explanation:**

- `UPDATE employees SET email = 'john.newemail@example.com' WHERE employee_id = 1;` modifies the `email` of the employee with `employee_id` 1 to `john.newemail@example.com`.

## Deleting Data from a Table

To delete specific rows from a table, use the `DELETE` command.

### Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

### Example

Delete an employee with a specific `employee_id`:

```sql
DELETE FROM employees
WHERE employee_id = 1;
```

**Example Output:**

The employee with `employee_id` 1 is removed from the table.

**Explanation:**

- `DELETE FROM employees WHERE employee_id = 1;` removes the record where `employee_id` is 1.

### Deleting All Data from a Table

To delete all rows from a table but keep the table structure intact, omit the `WHERE` clause:

```sql
DELETE FROM employees;
```

**Explanation:**

- `DELETE FROM employees;` removes all rows from the `employees` table.

## Deleting a Table

To delete an entire table from the database, use the `DROP TABLE` command.

### Syntax

```sql
DROP TABLE table_name;
```

### Example

Drop the `employees` table:

```sql
DROP TABLE employees;
```

**Explanation:**

- `DROP TABLE employees;` removes the entire `employees` table, including all of its data and structure.

---

- by Aditya Kumar