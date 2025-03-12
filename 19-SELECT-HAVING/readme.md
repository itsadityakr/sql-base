![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

# **HAVING Clause**

The `HAVING` clause is used in SQL to filter groups of rows based on a specified condition. It is often used in conjunction with the `GROUP BY` clause to apply conditions to aggregated results. Unlike the `WHERE` clause, which filters rows before grouping, the `HAVING` clause filters groups after aggregation. This makes it an essential tool for working with grouped data and aggregate functions.

---

## **Purpose of the HAVING Clause**
The `HAVING` clause:
1. **Filters Groups**: Applies conditions to groups of rows created by the `GROUP BY` clause.
2. **Works with Aggregate Functions**: Allows filtering based on calculations like `COUNT`, `SUM`, `AVG`, etc.
3. **Enhances Data Analysis**: Provides a way to refine grouped data for more meaningful insights.

---

## **Syntax of the HAVING Clause**
The basic syntax of the `HAVING` clause is:
```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1
HAVING condition;
```

### **Key Components**
1. **Aggregate Function**: Functions like `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX` that perform calculations on each group.
2. **Condition**: A logical expression that evaluates to `TRUE`, `FALSE`, or `UNKNOWN`. Only groups that satisfy the condition are included in the result set.

---

## **Using the HAVING Clause**

### 1. **Basic Filtering**
The most common use of the `HAVING` clause is to filter groups based on an aggregate condition.

**Example**:
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 10;
```
This retrieves departments with more than 10 employees.

---

### 2. **Filtering with Aggregate Functions**
You can use aggregate functions like `SUM`, `AVG`, `MIN`, and `MAX` in the `HAVING` clause.

**Example**:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```
This retrieves departments with an average salary greater than 50,000.

---

### 3. **Combining with WHERE**
The `HAVING` clause can be used alongside the `WHERE` clause to filter rows before grouping and then filter groups after aggregation.

**Example**:
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
WHERE hire_date > '2023-01-01'
GROUP BY department
HAVING COUNT(*) > 5;
```
This retrieves departments with more than 5 employees hired after January 1, 2023.

---

### 4. **Using Logical Operators**
You can combine multiple conditions in the `HAVING` clause using logical operators like `AND`, `OR`, and `NOT`.

**Example**:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000 AND COUNT(*) > 10;
```
This retrieves departments with an average salary greater than 50,000 and more than 10 employees.

---

## **Key Points About the HAVING Clause**

### 1. **Difference Between WHERE and HAVING**
- **WHERE**: Filters rows before grouping.
- **HAVING**: Filters groups after aggregation.

### 2. **Aggregate Functions**
- The `HAVING` clause is used with aggregate functions like `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX`.

### 3. **Grouping Columns**
- All columns in the `SELECT` clause that are not part of an aggregate function must be included in the `GROUP BY` clause.

### 4. **Order of Execution**
- The `HAVING` clause is executed after the `GROUP BY` clause but before the `ORDER BY` clause.

---

## **Common Use Cases**

### 1. **Filtering Groups**
Retrieve groups that meet specific criteria.

**Example**:
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 10;
```

### 2. **Analyzing Aggregated Data**
Perform calculations on grouped data and filter the results.

**Example**:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

### 3. **Combining with WHERE**
Filter rows before grouping and then filter groups after aggregation.

**Example**:
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
WHERE hire_date > '2023-01-01'
GROUP BY department
HAVING COUNT(*) > 5;
```

### 4. **Using Logical Operators**
Combine multiple conditions to refine grouped data.

**Example**:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000 AND COUNT(*) > 10;
```

---

## **Conclusion**
The `HAVING` clause is a powerful tool for filtering grouped data in SQL. By applying conditions to aggregated results, you can refine your query output and gain deeper insights into your data. Key points to remember:
- Use `HAVING` with aggregate functions like `COUNT`, `SUM`, `AVG`, etc.
- Combine `HAVING` with `WHERE` to filter rows before grouping and groups after aggregation.
- Use logical operators to create complex conditions.

Mastering the `HAVING` clause is essential for advanced data analysis and reporting in SQL.

---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)