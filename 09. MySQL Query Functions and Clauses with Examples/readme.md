# MySQL Query Functions and Clauses with Examples

## Original Table

**Table: `employees`**

| **employee_id** | **first_name** | **last_name** | **email**                  | **hire_date** |
|-----------------|----------------|---------------|----------------------------|--------------|
| 1               | John           | Doe           | john.doe@example.com       | 2024-01-15   |
| 2               | Jane           | Smith         | jane.smith@example.com     | 2024-02-20   |
| 3               | Emily          | Johnson       | emily.johnson@example.com  | 2024-03-10   |

---

## 1. `DISTINCT`

### SQL Syntax

```sql
SELECT DISTINCT column_name
FROM employees;
```

### Example Command

```sql
SELECT DISTINCT first_name
FROM employees;
```

### Explanation

- `DISTINCT` retrieves unique values from the `first_name` column.

### Result

| **first_name** |
|----------------|
| John           |
| Jane           |
| Emily          |

---

## 2. `ORDER BY` and Subsorting

### SQL Syntax

```sql
SELECT column1, column2
FROM employees
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC];
```

### Example Command

```sql
SELECT first_name, hire_date
FROM employees
ORDER BY hire_date DESC, first_name ASC;
```

### Explanation

- `ORDER BY` sorts the `hire_date` in descending order and `first_name` in ascending order.

### Result

| **first_name** | **hire_date** |
|----------------|--------------|
| Emily          | 2024-03-10   |
| Jane           | 2024-02-20   |
| John           | 2024-01-15   |

---

## 3. `LIKE`

### SQL Syntax

```sql
SELECT column1, column2
FROM employees
WHERE column_name LIKE pattern;
```

### Example Command

```sql
SELECT first_name, email
FROM employees
WHERE email LIKE '%example.com';
```

### Explanation

- `LIKE '%example.com'` finds emails ending with `example.com`.

### Result

| **first_name** | **email**                  |
|----------------|----------------------------|
| John           | john.doe@example.com       |
| Jane           | jane.smith@example.com     |
| Emily          | emily.johnson@example.com  |

---

## 4. `LIMIT`

### SQL Syntax

```sql
SELECT column_name
FROM employees
LIMIT number_of_rows;
```

### Example Command

```sql
SELECT first_name
FROM employees
LIMIT 2;
```

### Explanation

- `LIMIT 2` returns the first 2 rows from the result set.

### Result

| **first_name** |
|----------------|
| John           |
| Jane           |

---

## 5. `COUNT`

### SQL Syntax

```sql
SELECT COUNT(column_name)
FROM employees;
```

### Example Command

```sql
SELECT COUNT(*) AS total_employees
FROM employees;
```

### Explanation

- `COUNT(*)` counts all rows in the `employees` table.

### Result

| **total_employees** |
|---------------------|
| 3                   |

---

## 6. `GROUP BY`

### SQL Syntax

```sql
SELECT column_name(s), aggregate_function(column_name)
FROM employees
GROUP BY column_name(s);
```

### Example Command

```sql
SELECT last_name, COUNT(*) AS num_employees
FROM employees
GROUP BY last_name;
```

### Explanation

- `GROUP BY last_name` groups rows by `last_name`, and `COUNT(*)` counts the number of employees with each last name.

### Result

| **last_name** | **num_employees** |
|---------------|-------------------|
| Doe           | 1                 |
| Smith         | 1                 |
| Johnson       | 1                 |

---

## 7. `MAX`

### SQL Syntax

```sql
SELECT MAX(column_name)
FROM employees;
```

### Example Command

```sql
SELECT MAX(hire_date) AS latest_hire
FROM employees;
```

### Explanation

- `MAX(hire_date)` returns the most recent hire date.

### Result

| **latest_hire** |
|-----------------|
| 2024-03-10      |

---

## 8. `MIN`

### SQL Syntax

```sql
SELECT MIN(column_name)
FROM employees;
```

### Example Command

```sql
SELECT MIN(hire_date) AS earliest_hire
FROM employees;
```

### Explanation

- `MIN(hire_date)` returns the earliest hire date.

### Result

| **earliest_hire** |
|-------------------|
| 2024-01-15        |

---

## 9. `SUM`

### SQL Syntax

```sql
SELECT SUM(column_name)
FROM employees;
```

### Example Command

```sql
SELECT SUM(employee_id) AS total_ids
FROM employees;
```

### Explanation

- `SUM(employee_id)` adds up all `employee_id` values.

### Result

| **total_ids** |
|---------------|
| 6             |

---

## 10. `AVG`

### SQL Syntax

```sql
SELECT AVG(column_name)
FROM employees;
```

### Example Command

```sql
SELECT AVG(employee_id) AS average_id
FROM employees;
```

### Explanation

- `AVG(employee_id)` calculates the average of `employee_id`.

### Result

| **average_id** |
|----------------|
| 2.0            |

---

- by Aditya Kumar