
![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

# SQL

This guide provides a **deep dive into the `SELECT` statement**, including code examples and s. For other essential SQL commands (`FROM`, `WHERE`, `JOINS`, `GROUP BY`, `ORDER BY`, `HAVING`, `INSERT`, `UPDATE`, and `DELETE`), only s are provided without code examples.

---

## 1. **SELECT:**
The `SELECT` statement is the most important SQL command for retrieving data from a database. It allows you to specify the columns you want to retrieve, filter rows, sort results, and perform calculations.

### Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name;
```

### Key Features of `SELECT`

#### 1. **Retrieving Specific Columns**
You can specify the columns you want to retrieve.

**Example**:
```sql
SELECT first_name, last_name
FROM employees;
```
This retrieves only the `first_name` and `last_name` columns from the `employees` table.

#### 2. **Retrieving All Columns**
Use `*` to retrieve all columns from a table.

**Example**:
```sql
SELECT * FROM employees;
```
This retrieves all columns from the `employees` table.

#### 3. **Using Aliases**
You can rename columns in the result set using aliases.

**Example**:
```sql
SELECT first_name AS "First Name", last_name AS "Last Name"
FROM employees;
```
This retrieves `first_name` and `last_name` with custom column names.

#### 4. **Using Expressions**
You can perform calculations or concatenations in the `SELECT` clause.

**Example**:
```sql
SELECT first_name || ' ' || last_name AS full_name
FROM employees;
```
This concatenates `first_name` and `last_name` into a single column.

#### 5. **DISTINCT**
Use `DISTINCT` to retrieve unique values.

**Example**:
```sql
SELECT DISTINCT department
FROM employees;
```
This retrieves unique department names from the `employees` table.

#### 6. **LIMIT**
Use `LIMIT` to restrict the number of rows returned.

**Example**:
```sql
SELECT * FROM employees
LIMIT 10;
```
This retrieves the first 10 rows from the `employees` table.

#### 7. **Aggregate Functions**
You can use aggregate functions like `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX` to perform calculations on data.

**Example**:
```sql
SELECT AVG(salary) AS avg_salary
FROM employees;
```
This calculates the average salary of all employees.

---

## 2. **FROM: **
The `FROM` clause specifies the table(s) from which to retrieve data. It is always used with the `SELECT` statement. The `FROM` clause can include one or more tables, and it can also include joins to combine data from multiple tables.

---

## 3. **WHERE: **
The `WHERE` clause filters rows based on a specified condition. It is used to retrieve only the rows that meet the condition. The condition can include comparisons, logical operators, and functions. For example, you can filter rows where a column value equals a specific value, is greater than a value, or matches a pattern.

---

## 4. **JOINS: **
Joins are used to combine rows from two or more tables based on a related column. The most common types of joins are:
- **INNER JOIN**: Returns rows with matching values in both tables.
- **LEFT JOIN**: Returns all rows from the left table and matching rows from the right table.
- **RIGHT JOIN**: Returns all rows from the right table and matching rows from the left table.
- **FULL JOIN**: Returns all rows when there is a match in either table.

Joins are essential for querying data from multiple tables in a relational database.

---

## 5. **GROUP BY: **
The `GROUP BY` clause groups rows with the same values into summary rows. It is often used with aggregate functions like `COUNT`, `SUM`, `AVG`, etc. The `GROUP BY` clause allows you to perform calculations on groups of rows rather than individual rows. For example, you can calculate the total sales for each department or the average salary for each job title.

---

## 6. **ORDER BY: **
The `ORDER BY` clause sorts the result set in ascending or descending order. You can sort by one or more columns, and you can specify the sort order for each column. The `ORDER BY` clause is useful for organizing query results in a meaningful way, such as sorting employees by salary or products by price.

---

## 7. **HAVING: **
The `HAVING` clause filters groups based on a condition. It is used with `GROUP BY` to filter aggregated results. Unlike the `WHERE` clause, which filters rows before grouping, the `HAVING` clause filters groups after grouping. For example, you can use `HAVING` to retrieve only departments with an average salary greater than a specific value.

---

## 8. **INSERT: **
The `INSERT` statement adds new rows to a table. You can insert a single row or multiple rows at once. The `INSERT` statement specifies the table and the values to insert into each column. You can also insert data from another table using a `SELECT` statement.

---

## 9. **UPDATE: **
The `UPDATE` statement modifies existing rows in a table. You can update one or more columns in one or more rows. The `UPDATE` statement specifies the table, the columns to update, and the new values. You can also use a `WHERE` clause to update only specific rows that meet a condition.

---

## 10. **DELETE: **
The `DELETE` statement removes rows from a table. You can delete one or more rows based on a condition specified in the `WHERE` clause. If no condition is specified, all rows in the table are deleted. The `DELETE` statement is irreversible, so use it with caution.

---

## Conclusion
The `SELECT` statement is the cornerstone of SQL and is used to retrieve data from a database. Other commands like `FROM`, `WHERE`, `JOINS`, `GROUP BY`, `ORDER BY`, `HAVING`, `INSERT`, `UPDATE`, and `DELETE` enhance its functionality.


---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)