# Filtering Data with `WHERE` Clause in MySQL

## Using `WHERE` to Filter Data

The `WHERE` clause in SQL is used to filter records based on specified conditions. It allows you to retrieve only those rows that meet the criteria you define.

### Example Scenario

Let's use the `employees` table created earlier. Assume we want to filter employees based on their hire date and last name.

### SQL Commands

#### 1. Filtering by Hire Date

To find all employees hired after a specific date:

```sql
SELECT * FROM employees
WHERE hire_date > '2024-06-01';
```

**Example Output:**

| **employee_id** | **first_name** | **last_name** | **email**                  | **hire_date** |
|-----------------|----------------|---------------|----------------------------|--------------|
| 6               | David          | Jones         | david.jones@example.com    | 2024-06-18   |
| 7               | Laura          | Garcia        | laura.garcia@example.com   | 2024-07-30   |
| 8               | James          | Martinez      | james.martinez@example.com | 2024-08-22   |
| 9               | Linda          | Hernandez     | linda.hernandez@example.com | 2024-09-10   |
| 10              | Robert         | Moore         | robert.moore@example.com   | 2024-10-01   |

**Explanation:**

- `WHERE hire_date > '2024-06-01';` filters employees whose `hire_date` is after June 1, 2024.

#### 2. Filtering by Last Name

To find employees with a specific last name:

```sql
SELECT * FROM employees
WHERE last_name = 'Smith';
```

**Example Output:**

| **employee_id** | **first_name** | **last_name** | **email**                  | **hire_date** |
|-----------------|----------------|---------------|----------------------------|--------------|
| 2               | Jane           | Smith         | jane.smith@example.com     | 2024-02-20   |

**Explanation:**

- `WHERE last_name = 'Smith';` retrieves employees whose last name is `Smith`.

#### 3. Combining Conditions

To filter employees hired after a specific date and with a certain last name:

```sql
SELECT * FROM employees
WHERE hire_date > '2024-01-01' AND last_name = 'Johnson';
```

**Example Output:**

| **employee_id** | **first_name** | **last_name** | **email**                  | **hire_date** |
|-----------------|----------------|---------------|----------------------------|--------------|
| 3               | Emily          | Johnson       | emily.johnson@example.com  | 2024-03-10   |

**Explanation:**

- `WHERE hire_date > '2024-01-01' AND last_name = 'Johnson';` retrieves employees hired after January 1, 2024, and whose last name is `Johnson`.

### Additional Conditions

You can use various operators in the `WHERE` clause to refine your search:

- `=`: Equal to
- `!=` or `<>`: Not equal to
- `<`: Less than
- `>`: Greater than
- `<=`: Less than or equal to
- `>=`: Greater than or equal to
- `BETWEEN ... AND ...`: Within a range
- `LIKE`: Pattern matching (e.g., `LIKE 'John%'`)
- `IN (...)`: Match any value within a list
- `IS NULL`: Check for null values

---

- by Aditya Kumar