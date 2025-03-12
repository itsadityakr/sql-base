![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

# Data Manipulation Language (DML)

**Data Manipulation Language (DML)** is a subset of SQL used to manage and manipulate data within database objects. DML commands allow users to retrieve, insert, update, and delete data in tables. These commands are essential for day-to-day database operations, data analysis, and maintaining the accuracy and relevance of the data within a database system.

---

## Key DML Commands
The primary DML commands are:
1. **SELECT**: Retrieves data from one or more tables.
2. **INSERT**: Adds new rows to a table.
3. **UPDATE**: Modifies existing rows in a table.
4. **DELETE**: Removes rows from a table.

---

## 1. SELECT Statement
The `SELECT` statement is used to retrieve data from one or more tables. It is the most commonly used DML command.

### Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY column ASC|DESC
GROUP BY column
HAVING condition
LIMIT number;
```

### Key Clauses
- **`SELECT`**: Specifies the columns to retrieve.
- **`FROM`**: Specifies the table(s) to query.
- **`WHERE`**: Filters rows based on a condition.
- **`ORDER BY`**: Sorts the result set.
- **`GROUP BY`**: Groups rows with the same values.
- **`HAVING`**: Filters groups based on a condition.
- **`LIMIT`**: Limits the number of rows returned.

### Examples

#### 1. Basic Query
```sql
SELECT first_name, last_name
FROM employees;
```
Retrieves the `first_name` and `last_name` columns from the `employees` table.

#### 2. Filtering with `WHERE`
```sql
SELECT * FROM employees
WHERE department = 'Sales';
```
Retrieves all employees in the Sales department.

#### 3. Sorting with `ORDER BY`
```sql
SELECT * FROM employees
ORDER BY salary DESC;
```
Retrieves all employees sorted by salary in descending order.

#### 4. Grouping with `GROUP BY`
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```
Retrieves the number of employees in each department.

#### 5. Filtering Groups with `HAVING`
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```
Retrieves departments with an average salary greater than 50,000.

#### 6. Limiting Results with `LIMIT`
```sql
SELECT * FROM employees
LIMIT 10;
```
Retrieves the first 10 rows from the `employees` table.

---

## 2. INSERT Statement
The `INSERT` statement is used to add new rows to a table.

### Basic Syntax
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### Examples

#### 1. Inserting a Single Row
```sql
INSERT INTO employees (first_name, last_name, department, salary)
VALUES ('John', 'Doe', 'Sales', 50000);
```
Adds a new employee to the `employees` table.

#### 2. Inserting Multiple Rows
```sql
INSERT INTO employees (first_name, last_name, department, salary)
VALUES ('Jane', 'Smith', 'HR', 60000),
       ('Alice', 'Johnson', 'IT', 70000);
```
Adds two new employees to the `employees` table.

---

## 3. UPDATE Statement
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
Updates the salary of the employee with `employee_id = 101`.

#### 2. Updating Multiple Rows
```sql
UPDATE employees
SET salary = salary * 1.1
WHERE department = 'Sales';
```
Gives a 10% salary raise to all employees in the Sales department.

---

## 4. DELETE Statement
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
Deletes the employee with `employee_id = 101`.

#### 2. Deleting Multiple Rows
```sql
DELETE FROM employees
WHERE department = 'IT';
```
Deletes all employees in the IT department.

---

## Joins in SQL
Joins are used to combine rows from two or more tables based on a related column.

### Types of Joins
1. **INNER JOIN**: Returns rows with matching values in both tables.
2. **LEFT JOIN**: Returns all rows from the left table and matching rows from the right table.
3. **RIGHT JOIN**: Returns all rows from the right table and matching rows from the left table.
4. **FULL JOIN**: Returns all rows when there is a match in either table.

### Example: INNER JOIN
```sql
SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```
Retrieves employee names and their department names by joining the `employees` and `departments` tables.

---

## Conclusion
DML commands (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) are essential for managing and manipulating data in a database. Key points to remember:
- Use `SELECT` to retrieve data.
- Use `INSERT` to add new rows.
- Use `UPDATE` to modify existing rows.
- Use `DELETE` to remove rows.


---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)