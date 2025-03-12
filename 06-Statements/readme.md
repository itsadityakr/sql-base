![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

# SQL Basics: SELECT, CREATE, INSERT, UPDATE, and DELETE Statements

SQL (Structured Query Language) is the standard language for interacting with relational databases. The core operations in SQL are often referred to as **CRUD** (Create, Read, Update, Delete). This guide provides a detailed explanation of the `SELECT`, `CREATE`, `INSERT`, `UPDATE`, and `DELETE` statements, along with examples.

---

## SELECT Statement
The `SELECT` statement is used to retrieve data from one or more tables. It is the most commonly used SQL statement.

### Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY column ASC|DESC
LIMIT number;
```

### Examples

#### 1. Retrieving All Columns
```sql
SELECT * FROM employees;
```
This query retrieves all columns from the `employees` table.

#### 2. Retrieving Specific Columns
```sql
SELECT first_name, last_name FROM employees;
```
This query retrieves only the `first_name` and `last_name` columns.

#### 3. Filtering Data with `WHERE`
```sql
SELECT * FROM employees WHERE department = 'Sales';
```
This query retrieves all employees in the Sales department.

#### 4. Sorting Data with `ORDER BY`
```sql
SELECT * FROM employees ORDER BY salary DESC;
```
This query retrieves all employees sorted by salary in descending order.

#### 5. Limiting Results with `LIMIT`
```sql
SELECT * FROM employees LIMIT 10;
```
This query retrieves the first 10 rows from the `employees` table.

#### 6. Aggregating Data with `GROUP BY`
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```
This query retrieves the number of employees in each department.

---

## CREATE Statement
The `CREATE` statement is used to create new database objects, such as tables, views, or indexes.

### Basic Syntax for Creating a Table
```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);
```

### Examples

#### 1. Creating a Table
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    hire_date DATE,
    salary DECIMAL(10, 2),
    department VARCHAR(50)
);
```
This query creates a table named `employees` with columns for employee details.

#### 2. Creating a Table with Constraints
```sql
CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(50) UNIQUE,
    manager_id INT,
    FOREIGN KEY (manager_id) REFERENCES employees(employee_id)
);
```
This query creates a `departments` table with a foreign key constraint linking `manager_id` to the `employees` table.

---

## INSERT Statement
The `INSERT` statement is used to add new rows to a table.

### Basic Syntax
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### Examples

#### 1. Inserting a Single Row
```sql
INSERT INTO employees (employee_id, first_name, last_name, hire_date, salary, department)
VALUES (101, 'John', 'Doe', '2023-10-25', 50000, 'Sales');
```
This query adds a new employee to the `employees` table.

#### 2. Inserting Multiple Rows
```sql
INSERT INTO employees (employee_id, first_name, last_name, hire_date, salary, department)
VALUES (102, 'Jane', 'Smith', '2023-09-15', 60000, 'HR'),
       (103, 'Alice', 'Johnson', '2023-08-10', 70000, 'IT');
```
This query adds two new employees to the `employees` table.

#### 3. Inserting Data from Another Table
```sql
INSERT INTO new_employees (first_name, last_name, department)
SELECT first_name, last_name, department
FROM employees
WHERE hire_date > '2023-01-01';
```
This query inserts data into `new_employees` from the `employees` table for employees hired after January 1, 2023.

---

## UPDATE Statement
The `UPDATE` statement is used to modify existing rows in a table.

### Basic Syntax
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### Examples

#### 1. Updating a Single Row
```sql
UPDATE employees
SET salary = 55000
WHERE employee_id = 101;
```
This query updates the salary of the employee with `employee_id = 101`.

#### 2. Updating Multiple Rows
```sql
UPDATE employees
SET salary = salary * 1.1
WHERE department = 'Sales';
```
This query gives a 10% salary raise to all employees in the Sales department.

#### 3. Updating with Subqueries
```sql
UPDATE employees
SET salary = (SELECT AVG(salary) FROM employees)
WHERE department = 'HR';
```
This query sets the salary of all HR employees to the average salary of all employees.

---

## DELETE Statement
The `DELETE` statement is used to remove rows from a table.

### Basic Syntax
```sql
DELETE FROM table_name
WHERE condition;
```

### Examples

#### 1. Deleting a Single Row
```sql
DELETE FROM employees
WHERE employee_id = 101;
```
This query deletes the employee with `employee_id = 101`.

#### 2. Deleting Multiple Rows
```sql
DELETE FROM employees
WHERE department = 'IT';
```
This query deletes all employees in the IT department.

#### 3. Deleting All Rows
```sql
DELETE FROM employees;
```
This query deletes all rows from the `employees` table (use with caution!).

#### 4. Deleting with Subqueries
```sql
DELETE FROM employees
WHERE salary < (SELECT AVG(salary) FROM employees);
```
This query deletes all employees whose salary is below the average salary.

---

## Conclusion
The `SELECT`, `CREATE`, `INSERT`, `UPDATE`, and `DELETE` statements are the core of SQL and are used to perform CRUD operations on databases. Here’s a quick summary:

- **SELECT**: Retrieves data from a table.
- **CREATE**: Creates new database objects like tables.
- **INSERT**: Adds new rows to a table.
- **UPDATE**: Modifies existing rows in a table.
- **DELETE**: Removes rows from a table.

---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)