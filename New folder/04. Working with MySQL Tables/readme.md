# Working with MySQL Tables

## Creating a Table

To create a table in MySQL, use the `CREATE TABLE` command. Below is an example of creating a table named `employees` with columns for ID, first name, last name, email, and hire date. The table is populated with 10 entries.

### SQL Command

```sql
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100),
    hire_date DATE
);
```

### Example Data Insertions

```sql
INSERT INTO employees (first_name, last_name, email, hire_date) VALUES
('John', 'Doe', 'john.doe@example.com', '2024-01-15'),
('Jane', 'Smith', 'jane.smith@example.com', '2024-02-20'),
('Emily', 'Johnson', 'emily.johnson@example.com', '2024-03-10'),
('Michael', 'Williams', 'michael.williams@example.com', '2024-04-25'),
('Sarah', 'Brown', 'sarah.brown@example.com', '2024-05-05'),
('David', 'Jones', 'david.jones@example.com', '2024-06-18'),
('Laura', 'Garcia', 'laura.garcia@example.com', '2024-07-30'),
('James', 'Martinez', 'james.martinez@example.com', '2024-08-22'),
('Linda', 'Hernandez', 'linda.hernandez@example.com', '2024-09-10'),
('Robert', 'Moore', 'robert.moore@example.com', '2024-10-01');
```

**Explanation:**

- `CREATE TABLE employees (...);` defines a new table called `employees` with columns for employee ID, first name, last name, email, and hire date.
- `employee_id` is set as an `INT` type with `AUTO_INCREMENT` to automatically generate unique IDs.
- `VARCHAR` types are used for text fields with varying lengths.
- `DATE` type is used for the `hire_date` field.

## Inserting Data into the Table

To insert data into the `employees` table, use the `INSERT INTO` command.

### SQL Command

```sql
INSERT INTO employees (first_name, last_name, email, hire_date) VALUES
('John', 'Doe', 'john.doe@example.com', '2024-01-15'),
('Jane', 'Smith', 'jane.smith@example.com', '2024-02-20'),
('Emily', 'Johnson', 'emily.johnson@example.com', '2024-03-10'),
('Michael', 'Williams', 'michael.williams@example.com', '2024-04-25'),
('Sarah', 'Brown', 'sarah.brown@example.com', '2024-05-05'),
('David', 'Jones', 'david.jones@example.com', '2024-06-18'),
('Laura', 'Garcia', 'laura.garcia@example.com', '2024-07-30'),
('James', 'Martinez', 'james.martinez@example.com', '2024-08-22'),
('Linda', 'Hernandez', 'linda.hernandez@example.com', '2024-09-10'),
('Robert', 'Moore', 'robert.moore@example.com', '2024-10-01');
```

**Explanation:**

- `INSERT INTO employees (column_names) VALUES (value1, value2, ...);` adds new rows to the table.
- Each set of values corresponds to a row in the table.

## Reading Data from the Table

To retrieve data from the `employees` table, use the `SELECT` command.

### SQL Command

```sql
SELECT * FROM employees;
```

**Example Output:**

| **employee_id** | **first_name** | **last_name** | **email**                  | **hire_date** |
|-----------------|----------------|---------------|----------------------------|--------------|
| 1               | John           | Doe           | john.doe@example.com       | 2024-01-15   |
| 2               | Jane           | Smith         | jane.smith@example.com     | 2024-02-20   |
| 3               | Emily          | Johnson       | emily.johnson@example.com  | 2024-03-10   |
| 4               | Michael        | Williams      | michael.williams@example.com | 2024-04-25   |
| 5               | Sarah          | Brown         | sarah.brown@example.com    | 2024-05-05   |
| 6               | David          | Jones         | david.jones@example.com    | 2024-06-18   |
| 7               | Laura          | Garcia        | laura.garcia@example.com   | 2024-07-30   |
| 8               | James          | Martinez      | james.martinez@example.com | 2024-08-22   |
| 9               | Linda          | Hernandez     | linda.hernandez@example.com | 2024-09-10   |
| 10              | Robert         | Moore         | robert.moore@example.com   | 2024-10-01   |

**Explanation:**

- `SELECT * FROM employees;` retrieves all columns and rows from the `employees` table.
- `*` denotes that all columns should be included in the result set.

---

- by Aditya Kumar