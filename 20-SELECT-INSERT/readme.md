![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)


# **INSERT Statement**

The `INSERT` statement is used in SQL to add new rows of data into a table. It is one of the fundamental Data Manipulation Language (DML) commands and is essential for populating and maintaining databases. The `INSERT` statement allows you to specify the table and the values to be inserted into each column.

---

## **Purpose of the INSERT Statement**
The `INSERT` statement:
1. **Adds New Rows**: Inserts one or more rows into a table.
2. **Populates Tables**: Fills tables with data for querying and analysis.
3. **Supports Multiple Formats**: Allows inserting single rows, multiple rows, or data from another table.

---

## **Syntax of the INSERT Statement**
The basic syntax of the `INSERT` statement is:
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### **Key Components**
1. **Table Name**: The name of the table where data will be inserted.
2. **Columns**: The columns in which data will be inserted (optional if inserting values for all columns).
3. **Values**: The values to be inserted into the specified columns.

---

## **Using the INSERT Statement**

### 1. **Inserting a Single Row**
The simplest use of the `INSERT` statement is to add a single row to a table.

**Example**:
```sql
INSERT INTO employees (first_name, last_name, department, salary)
VALUES ('John', 'Doe', 'Sales', 50000);
```
This inserts a new row into the `employees` table with the specified values.

---

### 2. **Inserting Multiple Rows**
You can insert multiple rows in a single `INSERT` statement by specifying multiple sets of values.

**Example**:
```sql
INSERT INTO employees (first_name, last_name, department, salary)
VALUES ('Jane', 'Smith', 'HR', 60000),
       ('Alice', 'Johnson', 'IT', 70000);
```
This inserts two new rows into the `employees` table.

---

### 3. **Inserting Data into All Columns**
If you are inserting values into all columns of a table, you can omit the column names.

**Example**:
```sql
INSERT INTO employees
VALUES (1, 'John', 'Doe', 'Sales', 50000);
```
This inserts a new row into the `employees` table, assuming the table has columns in the order `employee_id`, `first_name`, `last_name`, `department`, and `salary`.

---

### 4. **Inserting Data from Another Table**
You can insert data into a table from another table using a `SELECT` statement.

**Example**:
```sql
INSERT INTO new_employees (first_name, last_name, department)
SELECT first_name, last_name, department
FROM employees
WHERE hire_date > '2023-01-01';
```
This inserts rows into the `new_employees` table from the `employees` table for employees hired after January 1, 2023.

---

### 5. **Inserting Default Values**
If a column has a default value defined, you can use the `DEFAULT` keyword to insert the default value.

**Example**:
```sql
INSERT INTO employees (first_name, last_name, department, salary)
VALUES ('John', 'Doe', 'Sales', DEFAULT);
```
This inserts a new row into the `employees` table, using the default value for the `salary` column.

---

## **Key Points About the INSERT Statement**

### 1. **Column Order**
- If you specify column names, the values must be in the same order as the columns.
- If you omit column names, the values must be in the order of the table's columns.

### 2. **Data Types**
- The values being inserted must match the data types of the corresponding columns.

### 3. **Constraints**
- The `INSERT` statement must comply with any constraints (e.g., `NOT NULL`, `UNIQUE`, `PRIMARY KEY`) defined on the table.

### 4. **Auto-Increment Columns**
- For auto-increment columns (e.g., `employee_id`), you can omit the value, and the database will automatically generate it.

---

## **Common Use Cases**

### 1. **Adding New Records**
Insert new data into a table.

**Example**:
```sql
INSERT INTO customers (customer_name, email, phone)
VALUES ('John Doe', 'john.doe@example.com', '123-456-7890');
```

### 2. **Bulk Insert**
Insert multiple rows at once.

**Example**:
```sql
INSERT INTO products (product_name, price, category)
VALUES ('Laptop', 1000, 'Electronics'),
       ('Smartphone', 500, 'Electronics'),
       ('Tablet', 300, 'Electronics');
```

### 3. **Copying Data**
Insert data from one table into another.

**Example**:
```sql
INSERT INTO archived_orders (order_id, order_date, total_amount)
SELECT order_id, order_date, total_amount
FROM orders
WHERE order_date < '2023-01-01';
```

### 4. **Using Default Values**
Insert rows with default values for certain columns.

**Example**:
```sql
INSERT INTO employees (first_name, last_name, department, salary)
VALUES ('John', 'Doe', 'Sales', DEFAULT);
```

---

## **Conclusion**
The `INSERT` statement is a fundamental SQL command for adding data to a table. By mastering the `INSERT` statement, you can:
- Add single or multiple rows to a table.
- Insert data from another table.
- Use default values and handle auto-increment columns.

Always ensure that the data being inserted complies with the table's structure and constraints. The `INSERT` statement is essential for maintaining and populating databases, making it a critical skill for anyone working with SQL.

---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)