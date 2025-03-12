![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

# **GROUP BY Clause**

The `GROUP BY` clause is a powerful feature in SQL used to group rows that have the same values in specified columns into summary rows. It is often used with aggregate functions like `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX` to perform calculations on each group of rows. The `GROUP BY` clause is essential for generating reports, summarizing data, and analyzing datasets.

---

## **Purpose of the GROUP BY Clause**
The `GROUP BY` clause:
1. **Groups Rows**: Combines rows with the same values in specified columns into a single row.
2. **Enables Aggregation**: Allows you to perform calculations on each group using aggregate functions.
3. **Summarizes Data**: Provides a way to analyze data at a higher level of granularity.

---

## **Syntax of the GROUP BY Clause**
The basic syntax of the `GROUP BY` clause is:
```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```

### **Key Components**
1. **Columns to Group By**: The columns used to group the rows.
2. **Aggregate Functions**: Functions like `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX` that perform calculations on each group.
3. **Optional HAVING Clause**: Filters groups based on a condition (explained later).

---

## **Using the GROUP BY Clause**

### 1. **Basic Grouping**
The simplest use of the `GROUP BY` clause is to group rows based on a single column.

**Example**:
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```
This retrieves the number of employees in each department.

---

### 2. **Grouping by Multiple Columns**
You can group rows by multiple columns to create more granular groups.

**Example**:
```sql
SELECT department, job_title, COUNT(*) AS employee_count
FROM employees
GROUP BY department, job_title;
```
This retrieves the number of employees in each department and job title combination.

---

### 3. **Using Aggregate Functions**
Aggregate functions are used to perform calculations on each group of rows.

#### a. **COUNT**
Counts the number of rows in each group.

**Example**:
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```

#### b. **SUM**
Calculates the total value of a numeric column for each group.

**Example**:
```sql
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY department;
```

#### c. **AVG**
Calculates the average value of a numeric column for each group.

**Example**:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department;
```

#### d. **MIN and MAX**
Retrieves the minimum and maximum values of a column for each group.

**Example**:
```sql
SELECT department, MIN(salary) AS min_salary, MAX(salary) AS max_salary
FROM employees
GROUP BY department;
```

---

### 4. **Filtering Groups with HAVING**
The `HAVING` clause is used to filter groups based on a condition. It is similar to the `WHERE` clause but operates on groups rather than individual rows.

**Example**:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```
This retrieves departments with an average salary greater than 50,000.

---

## **Key Points About the GROUP BY Clause**

### 1. **Grouping Columns**
- All columns in the `SELECT` clause that are not part of an aggregate function must be included in the `GROUP BY` clause.
- Example:
  ```sql
  SELECT department, job_title, COUNT(*) AS employee_count
  FROM employees
  GROUP BY department, job_title;
  ```

### 2. **Aggregate Functions**
- Aggregate functions perform calculations on each group of rows.
- Common aggregate functions include `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX`.

### 3. **HAVING Clause**
- The `HAVING` clause filters groups after aggregation.
- It is used to apply conditions to aggregated results.

### 4. **Order of Execution**
- The `GROUP BY` clause is executed after the `FROM` and `WHERE` clauses but before the `HAVING` and `ORDER BY` clauses.

---

## **Common Use Cases**

### 1. **Summarizing Data**
Calculate summary statistics for each group.

**Example**:
```sql
SELECT department, COUNT(*) AS employee_count, AVG(salary) AS avg_salary
FROM employees
GROUP BY department;
```

### 2. **Counting Records**
Count the number of records in each group.

**Example**:
```sql
SELECT job_title, COUNT(*) AS employee_count
FROM employees
GROUP BY job_title;
```

### 3. **Filtering Groups**
Use the `HAVING` clause to filter groups based on aggregate results.

**Example**:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

### 4. **Analyzing Data**
Analyze data at a higher level of granularity.

**Example**:
```sql
SELECT YEAR(hire_date) AS hire_year, COUNT(*) AS employee_count
FROM employees
GROUP BY YEAR(hire_date);
```

---

## **Conclusion**
The `GROUP BY` clause is a powerful tool for summarizing and analyzing data in SQL. By grouping rows and applying aggregate functions, you can generate meaningful insights from your data. Always remember to:
- Include all non-aggregated columns in the `GROUP BY` clause.
- Use the `HAVING` clause to filter groups based on aggregate results.
- Combine `GROUP BY` with other clauses like `WHERE`, `ORDER BY`, and `HAVING` for more complex queries.

Mastering the `GROUP BY` clause is essential for data analysis and reporting in SQL.

---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)