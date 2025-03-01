# MySQL String Functions with Examples

## Table Creation and Initial Data

Let's start by creating a table named `employees` and inserting some initial data.

### SQL Syntax

```sql
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    hire_date DATE DEFAULT CURRENT_DATE
);

INSERT INTO employees (first_name, last_name, email, hire_date) VALUES
('John', 'Doe', 'john.doe@example.com', '2024-01-15'),
('Jane', 'Smith', 'jane.smith@example.com', '2024-02-20'),
('Emily', 'Johnson', 'emily.johnson@example.com', '2024-03-10');
```

### Initial Data in `employees` Table

| **employee_id** | **first_name** | **last_name** | **email**                  | **hire_date** |
|-----------------|----------------|---------------|----------------------------|--------------|
| 1               | John           | Doe           | john.doe@example.com       | 2024-01-15   |
| 2               | Jane           | Smith         | jane.smith@example.com     | 2024-02-20   |
| 3               | Emily          | Johnson       | emily.johnson@example.com  | 2024-03-10   |

## Applying String Functions

### 1. `CONCAT`

**Syntax:**

```sql
CONCAT(string1, string2, ...);
```

**Example SQL Command:**

```sql
SELECT CONCAT(first_name, ' ', last_name) AS full_name
FROM employees;
```

**Explanation:**

- `CONCAT` combines `first_name` and `last_name` with a space in between.

**Result:**

| **full_name**        |
|----------------------|
| John Doe             |
| Jane Smith           |
| Emily Johnson        |

### 2. `IFNULL`

**Syntax:**

```sql
IFNULL(expression, alternate_value);
```

**Example SQL Command:**

```sql
SELECT first_name, IFNULL(email, 'No email provided') AS email_status
FROM employees;
```

**Explanation:**

- `IFNULL` checks if `email` is `NULL`; if it is, it returns `'No email provided'`.

**Result:**

| **first_name** | **email_status**         |
|----------------|--------------------------|
| John           | john.doe@example.com     |
| Jane           | jane.smith@example.com   |
| Emily          | emily.johnson@example.com|

### 3. `CONCAT_WS`

**Syntax:**

```sql
CONCAT_WS(separator, string1, string2, ...);
```

**Example SQL Command:**

```sql
SELECT CONCAT_WS('-', first_name, last_name) AS name_with_dash
FROM employees;
```

**Explanation:**

- `CONCAT_WS` concatenates `first_name` and `last_name` with a dash (`-`) separator.

**Result:**

| **name_with_dash** |
|--------------------|
| John-Doe           |
| Jane-Smith         |
| Emily-Johnson      |

### 4. `SUBSTRING`

**Syntax:**

```sql
SUBSTRING(string, start_position, length);
```

**Example SQL Command:**

```sql
SELECT SUBSTRING(email, 1, 5) AS email_prefix
FROM employees;
```

**Explanation:**

- `SUBSTRING` extracts the first 5 characters from the `email` field.

**Result:**

| **email_prefix** |
|------------------|
| john.            |
| jane.            |
| emily.           |

### 5. `REPLACE`

**Syntax:**

```sql
REPLACE(string, old_substring, new_substring);
```

**Example SQL Command:**

```sql
SELECT REPLACE(email, 'example.com', 'mydomain.com') AS new_email
FROM employees;
```

**Explanation:**

- `REPLACE` changes `example.com` to `mydomain.com` in the `email` field.

**Result:**

| **new_email**                |
|------------------------------|
| john.doe@mydomain.com       |
| jane.smith@mydomain.com     |
| emily.johnson@mydomain.com  |

### 6. `REVERSE`

**Syntax:**

```sql
REVERSE(string);
```

**Example SQL Command:**

```sql
SELECT REVERSE(first_name) AS reversed_name
FROM employees;
```

**Explanation:**

- `REVERSE` reverses the characters in the `first_name` field.

**Result:**

| **reversed_name** |
|-------------------|
| nhoJ             |
| enaJ             |
| ylimE            |

### 7. `UPPER`

**Syntax:**

```sql
UPPER(string);
```

**Example SQL Command:**

```sql
SELECT UPPER(first_name) AS upper_name
FROM employees;
```

**Explanation:**

- `UPPER` converts all characters in `first_name` to uppercase.

**Result:**

| **upper_name** |
|----------------|
| JOHN           |
| JANE           |
| EMILY          |

### 8. `LOWER`

**Syntax:**

```sql
LOWER(string);
```

**Example SQL Command:**

```sql
SELECT LOWER(last_name) AS lower_name
FROM employees;
```

**Explanation:**

- `LOWER` converts all characters in `last_name` to lowercase.

**Result:**

| **lower_name** |
|----------------|
| doe            |
| smith          |
| johnson        |

### 9. `CHAR_LENGTH`

**Syntax:**

```sql
CHAR_LENGTH(string);
```

**Example SQL Command:**

```sql
SELECT CHAR_LENGTH(email) AS email_length
FROM employees;
```

**Explanation:**

- `CHAR_LENGTH` returns the number of characters in the `email` field.

**Result:**

| **email_length** |
|------------------|
| 20               |
| 22               |
| 21               |

### 10. `INSERT`

**Syntax:**

```sql
INSERT(string, position, length, substring);
```

**Example SQL Command:**

```sql
SELECT INSERT(email, 10, 0, 'test.') AS updated_email
FROM employees;
```

**Explanation:**

- `INSERT` adds `'test.'` at position 10 in the `email` field.

**Result:**

| **updated_email**                |
|----------------------------------|
| john.doe@test.example.com        |
| jane.smith@test.example.com      |
| emily.johnson@test.example.com   |

### 11. `LEFT`

**Syntax:**

```sql
LEFT(string, number_of_characters);
```

**Example SQL Command:**

```sql
SELECT LEFT(email, 5) AS left_email
FROM employees;
```

**Explanation:**

- `LEFT` extracts the first 5 characters from the `email` field.

**Result:**

| **left_email** |
|----------------|
| john.          |
| jane.          |
| emily.         |

### 12. `RIGHT`

**Syntax:**

```sql
RIGHT(string, number_of_characters);
```

**Example SQL Command:**

```sql
SELECT RIGHT(email, 10) AS right_email
FROM employees;
```

**Explanation:**

- `RIGHT` extracts the last 10 characters from the `email` field.

**Result:**

| **right_email** |
|-----------------|
| example.com     |
| mydomain.com    |
| example.com     |

### 13. `TRIM`

**Syntax:**

```sql
TRIM(string);
```

**Example SQL Command:**

```sql
SELECT TRIM('   ' FROM email) AS trimmed_email
FROM employees;
```

**Explanation:**

- `TRIM` removes leading and trailing spaces from the `email` field. (Note: This function is more relevant if there were leading or trailing spaces.)

**Result:**

| **trimmed_email**       |
|-------------------------|
| john.doe@example.com    |
| jane.smith@example.com  |
| emily.johnson@example.com|

### 14. `REPEAT`

**Syntax:**

```sql
REPEAT(string, number_of_times);
```

**Example SQL Command:**

```sql
SELECT REPEAT(first_name, 2) AS repeated_name
FROM employees;
```

**Explanation:**

- `REPEAT` repeats the `first_name` field twice.

**Result:**

| **repeated_name** |
|-------------------|
| JohnJohn          |
| JaneJane          |
| EmilyEmily        |

---

- by Aditya Kumar