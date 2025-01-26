# MySQL Views, HAVING, and ROLLUP

## 1. What is a View in MySQL?

A **View** is a virtual table that displays the results of a SQL query. Views help you simplify complex queries by storing them under a name, allowing for easier reuse.

### Syntax:
```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

### Example:

Given the following `employees` table:

| id  | name    | department | salary |
|-----|---------|------------|--------|
| 1   | John    | IT         | 50000  |
| 2   | Alice   | HR         | 45000  |
| 3   | Bob     | IT         | 60000  |
| 4   | Carol   | HR         | 40000  |
| 5   | Dave    | IT         | 55000  |

We can create a view for IT department employees:

```sql
CREATE VIEW IT_Employees AS
SELECT id, name, salary
FROM employees
WHERE department = 'IT';
```

When querying this view:

```sql
SELECT * FROM IT_Employees;
```

**Result:**

| id  | name  | salary |
|-----|-------|--------|
| 1   | John  | 50000  |
| 3   | Bob   | 60000  |
| 5   | Dave  | 55000  |

---

## 2. The HAVING Clause

The **HAVING** clause filters records after they've been grouped using `GROUP BY`. It's typically used with aggregate functions (`SUM()`, `COUNT()`, etc.).

### Syntax:
```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1
HAVING condition;
```

### Example:

Find the total salary for each department and filter departments where the total salary is greater than 100,000:

```sql
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY department
HAVING total_salary > 100000;
```

**Result:**

| department | total_salary |
|------------|--------------|
| IT         | 165000       |

---

## 3. Using ROLLUP in MySQL

**ROLLUP** is used with `GROUP BY` to add subtotals and a grand total to grouped data. It’s useful for summary reports.

### Syntax:
```sql
SELECT column1, column2, aggregate_function(column3)
FROM table_name
GROUP BY ROLLUP (column1, column2);
```

### Example:

Calculate total salary for each employee and department, with subtotals and grand totals:

```sql
SELECT department, name, SUM(salary) AS total_salary
FROM employees
GROUP BY ROLLUP(department, name);
```

**Result:**

| department | name  | total_salary |
|------------|-------|--------------|
| HR         | Alice | 45000        |
| HR         | Carol | 40000        |
| HR         | NULL  | 85000        |  -- Subtotal for HR
| IT         | John  | 50000        |
| IT         | Bob   | 60000        |
| IT         | Dave  | 55000        |
| IT         | NULL  | 165000       |  -- Subtotal for IT
| NULL       | NULL  | 250000       |  -- Grand Total

---

## 4. Combining View, HAVING, and ROLLUP

### Step 1: Create a View for Employee Salaries by Department
```sql
CREATE VIEW Department_Salaries AS
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY department;
```

### Step 2: Use HAVING to Filter Departments with Salaries Greater Than 100,000
```sql
SELECT department, total_salary
FROM Department_Salaries
HAVING total_salary > 100000;
```

**Result:**

| department | total_salary |
|------------|--------------|
| IT         | 165000       |

### Step 3: Use ROLLUP to Add Subtotals and Grand Total
```sql
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY ROLLUP(department)
HAVING SUM(salary) > 100000 OR department IS NULL;
```

**Result:**

| department | total_salary |
|------------|--------------|
| IT         | 165000       |
| NULL       | 250000       | -- Grand Total

---

## Summary of Key Concepts:

- **Views**: Simplify complex queries by encapsulating them in virtual tables.
- **HAVING**: Filters groups after aggregation (`GROUP BY`).
- **ROLLUP**: Adds subtotals and grand totals for grouped data.

---

- by Aditya Kumar