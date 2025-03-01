# MySQL Table Constraints and Features

## `NOT NULL`

The `NOT NULL` constraint ensures that a column must have a value; it cannot be `NULL`. This is used to enforce that certain columns always contain data.

### Syntax

```sql
CREATE TABLE table_name (
    column_name datatype NOT NULL,
    ...
);
```

### Example

Create a table with `NOT NULL` constraints:

```sql
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    hire_date DATE
);
```

**Explanation:**

- `first_name`, `last_name`, and `email` are required (`NOT NULL`), meaning they cannot have `NULL` values.

## Setting Default Values

Default values are used when no value is provided for a column during record insertion. This ensures a column has a meaningful value by default.

### Syntax

```sql
CREATE TABLE table_name (
    column_name datatype DEFAULT default_value,
    ...
);
```

### Example

Create a table with a default value for the `status` column:

```sql
CREATE TABLE orders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT NOT NULL,
    order_date DATE NOT NULL,
    status VARCHAR(20) DEFAULT 'Pending'
);
```

**Explanation:**

- `status` will default to `'Pending'` if no value is provided during insertion.

## `PRIMARY KEY`

A `PRIMARY KEY` uniquely identifies each record in a table. It ensures that no two rows have the same value in this column and that the column is not `NULL`.

### Syntax

```sql
CREATE TABLE table_name (
    column_name datatype PRIMARY KEY,
    ...
);
```

### Example

Create a table with a primary key:

```sql
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    hire_date DATE
);
```

**Explanation:**

- `employee_id` is set as the `PRIMARY KEY`, ensuring each employee has a unique identifier.

## `AUTO_INCREMENT`

The `AUTO_INCREMENT` attribute is used with integer columns to automatically generate a unique value for each new row. It is commonly used with primary keys.

### Syntax

```sql
CREATE TABLE table_name (
    column_name INT AUTO_INCREMENT PRIMARY KEY,
    ...
);
```

### Example

Create a table with an `AUTO_INCREMENT` column:

```sql
CREATE TABLE products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(100),
    price DECIMAL(10, 2)
);
```

**Explanation:**

- `product_id` will automatically increment with each new row, providing a unique ID for each product.

## Aliases

Aliases are temporary names for tables or columns used to simplify queries or make them more readable.

### Syntax

```sql
SELECT column_name AS alias_name
FROM table_name AS alias_name;
```

### Example

Using aliases in a query:

```sql
SELECT e.first_name AS fname, e.last_name AS lname
FROM employees AS e;
```

**Explanation:**

- `e` is an alias for the `employees` table.
- `fname` and `lname` are aliases for `first_name` and `last_name` columns, respectively.

### Example with Updated Data

Assuming we have updated the `employees` table with new data:

#### SQL Command

```sql
-- Creating the employees table
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    hire_date DATE DEFAULT CURRENT_DATE
);

-- Inserting initial data
INSERT INTO employees (first_name, last_name, email, hire_date) VALUES
('John', 'Doe', 'john.doe@example.com', '2024-01-15'),
('Jane', 'Smith', 'jane.smith@example.com', '2024-02-20'),
('Emily', 'Johnson', 'emily.johnson@example.com', '2024-03-10');

-- Updating data
UPDATE employees
SET email = 'jane.newemail@example.com', hire_date = '2024-04-01'
WHERE employee_id = 2;

UPDATE employees
SET hire_date = '2024-05-01'
WHERE employee_id = 3;

-- Querying with aliases
SELECT e.first_name AS fname, e.last_name AS lname, e.email AS email, e.hire_date AS date_hired
FROM employees AS e;
```

**Updated Data in `employees` Table:**

| **employee_id** | **first_name** | **last_name** | **email**                  | **hire_date** |
|-----------------|----------------|---------------|----------------------------|--------------|
| 1               | John           | Doe           | john.doe@example.com       | 2024-01-15   |
| 2               | Jane           | Smith         | jane.newemail@example.com  | 2024-04-01   |
| 3               | Emily          | Johnson       | emily.johnson@example.com  | 2024-05-01   |

**Alias Output:**

| **fname** | **lname** | **email**                  | **date_hired** |
|-----------|-----------|----------------------------|----------------|
| John      | Doe       | john.doe@example.com       | 2024-01-15     |
| Jane      | Smith     | jane.newemail@example.com  | 2024-04-01     |
| Emily     | Johnson   | emily.johnson@example.com  | 2024-05-01     |

---

- by Aditya Kumar