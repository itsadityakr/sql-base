# **Aggregate Queries in SQL**  

## **Introduction**  
Aggregate queries in SQL **perform calculations** on multiple rows and return a single result. These queries are useful for **summarizing data** such as totals, averages, and counts.  

---

## **What are Aggregate Functions?**  
Aggregate functions **process multiple rows** and return a single value. They are commonly used with the `GROUP BY` clause for **categorizing data**.  

### **Content:**  
Common aggregate functions in SQL:  
- `SUM()` – Calculates the total sum of a numeric column.  
- `COUNT()` – Counts the number of rows.  
- `AVG()` – Computes the average value of a numeric column.  
- `MIN()` – Finds the minimum value in a column.  
- `MAX()` – Finds the maximum value in a column.  

### **Syntax:**  
```sql
SELECT AGGREGATE_FUNCTION(column_name) FROM table_name WHERE condition;
```

### **Statement related to the `employees` table:**  
To get the **total salary of all employees**:  
```sql
SELECT SUM(salary) FROM employees;
```

---

# **SUM() Function**  

## **What is SUM()?**  
The `SUM()` function **adds up all values** in a numeric column.  

### **Content:**  
- Works only with **numeric columns**.  
- Often used with `GROUP BY` to total amounts for specific categories.  

### **Syntax:**  
```sql
SELECT SUM(salary) FROM employees;
```

### **Statement related to the `employees` table:**  
To calculate the **total salary paid to employees**:  
```sql
SELECT SUM(salary) AS total_salary FROM employees;
```

---

# **COUNT() Function**  

## **What is COUNT()?**  
The `COUNT()` function **counts the number of rows** that match a condition.  

### **Content:**  
- `COUNT(*)` counts **all rows**, including NULL values.  
- `COUNT(column_name)` counts **only non-null values**.  

### **Syntax:**  
```sql
SELECT COUNT(*) FROM employees;
```

### **Statement related to the `employees` table:**  
To count the total number of employees:  
```sql
SELECT COUNT(*) AS total_employees FROM employees;
```

To count the number of employees with a salary **above 70,000**:  
```sql
SELECT COUNT(*) FROM employees WHERE salary > 70000;
```

---

# **AVG() Function**  

## **What is AVG()?**  
The `AVG()` function **calculates the average value** of a numeric column.  

### **Content:**  
- Works only with **numeric values**.  
- Can be combined with `ROUND()` to limit decimal places.  

### **Syntax:**  
```sql
SELECT AVG(salary) FROM employees;
```

### **Statement related to the `employees` table:**  
To find the **average salary of all employees**:  
```sql
SELECT AVG(salary) AS average_salary FROM employees;
```

To get the **average salary of managers**:  
```sql
SELECT AVG(salary) FROM employees WHERE designation = 'Manager';
```

---

# **MIN() Function**  

## **What is MIN()?**  
The `MIN()` function **returns the lowest value** in a column.  

### **Content:**  
- Works with **numeric, date, and text values**.  
- Useful for finding **smallest numbers, earliest dates, or first alphabetic values**.  

### **Syntax:**  
```sql
SELECT MIN(salary) FROM employees;
```

### **Statement related to the `employees` table:**  
To find the **lowest salary** among employees:  
```sql
SELECT MIN(salary) AS lowest_salary FROM employees;
```

To get the **youngest employee's age**:  
```sql
SELECT MIN(age) FROM employees;
```

---

# **MAX() Function**  

## **What is MAX()?**  
The `MAX()` function **returns the highest value** in a column.  

### **Content:**  
- Works with **numeric, date, and text values**.  
- Useful for finding **highest salaries, latest dates, or last alphabetic names**.  

### **Syntax:**  
```sql
SELECT MAX(salary) FROM employees;
```

### **Statement related to the `employees` table:**  
To find the **highest salary** among employees:  
```sql
SELECT MAX(salary) AS highest_salary FROM employees;
```

To get the **oldest employee’s age**:  
```sql
SELECT MAX(age) FROM employees;
```

---

# **SELECT with Aggregate Functions**  

## **Using Aggregates in SELECT Statements**  
Aggregates can be used within `SELECT` to retrieve multiple summaries at once.  

### **Content:**  
- Can combine multiple aggregate functions in a **single query**.  
- Commonly used with `GROUP BY` for categorized summaries.  

### **Syntax:**  
```sql
SELECT SUM(salary), AVG(salary), MIN(salary), MAX(salary), COUNT(*) FROM employees;
```

### **Statement related to the `employees` table:**  
To retrieve **various salary statistics** for all employees:  
```sql
SELECT 
    SUM(salary) AS total_salary, 
    AVG(salary) AS average_salary, 
    MIN(salary) AS lowest_salary, 
    MAX(salary) AS highest_salary, 
    COUNT(*) AS total_employees
FROM employees;
```

To get the **average salary per designation**:  
```sql
SELECT designation, AVG(salary) FROM employees GROUP BY designation;
```

---
