# **Data Manipulation Language (DML)**  

## **Introduction**  
Data Manipulation Language (**DML**) is a subset of SQL that deals with **retrieving, inserting, updating, and deleting** records in a database. Unlike DDL, which defines the structure, DML focuses on modifying and managing the data within tables.  

---

## **What is DML?**  
DML statements allow users to interact with the data in a database. Unlike DDL, **DML commands can be rolled back** if not committed.  

### **Content:**  
Common DML commands include:  
- `SELECT` – Retrieves data.  
- `INSERT` – Adds new records.  
- `UPDATE` – Modifies existing records.  
- `DELETE` – Removes records.  

### **Syntax:**  
General format of DML statements:  
```sql
SELECT column1, column2 FROM table_name WHERE condition;
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
UPDATE table_name SET column1 = value1 WHERE condition;
DELETE FROM table_name WHERE condition;
```

### **Statement related to the `employees` table:**  
To retrieve all employee data:  
```sql
SELECT * FROM employees;
```

---

# **SELECT Statement**  

## **What is SELECT?**  
The `SELECT` statement is used to retrieve **specific data** from a table based on conditions.  

### **Content:**  
- Can fetch **all columns** (`SELECT *`) or **specific columns**.  
- Can use `DISTINCT` to remove duplicate records.  
- Can filter records using `WHERE`.  

### **Syntax:**  
Basic `SELECT` statement:  
```sql
SELECT name, age FROM employees;
```

### **Statement related to the `employees` table:**  
To get the names and designations of all employees:  
```sql
SELECT name, designation FROM employees;
```

---

# **FROM Clause**  

## **What is FROM?**  
The `FROM` clause specifies the **table** from which data is retrieved.  

### **Content:**  
- Used in `SELECT`, `DELETE`, and `UPDATE` queries.  
- Can be combined with **JOINS** to fetch data from multiple tables.  

### **Syntax:**  
```sql
SELECT name FROM employees;
```

### **Statement related to the `employees` table:**  
To select all employees from the **employees** table:  
```sql
SELECT * FROM employees;
```

---

# **WHERE Clause**  

## **What is WHERE?**  
The `WHERE` clause filters **specific rows** based on conditions.  

### **Content:**  
- Used with `SELECT`, `UPDATE`, and `DELETE`.  
- Supports **comparison** (`=, >, <, !=`) and **logical operators** (`AND, OR, NOT`).  

### **Syntax:**  
```sql
SELECT name FROM employees WHERE age > 30;
```

### **Statement related to the `employees` table:**  
To find employees with a salary greater than 70,000:  
```sql
SELECT name, salary FROM employees WHERE salary > 70000;
```

---

# **ORDER BY Clause**  

## **What is ORDER BY?**  
The `ORDER BY` clause sorts the result set in **ascending (ASC) or descending (DESC) order**.  

### **Content:**  
- By default, sorting is **ascending**.  
- Can sort by multiple columns.  

### **Syntax:**  
```sql
SELECT name, salary FROM employees ORDER BY salary DESC;
```

### **Statement related to the `employees` table:**  
To list employees in **descending order of salary**:  
```sql
SELECT name, salary FROM employees ORDER BY salary DESC;
```

---

# **GROUP BY Clause**  

## **What is GROUP BY?**  
The `GROUP BY` clause **groups rows** with the same values in specified columns.  

### **Content:**  
- Used with **aggregate functions** (`SUM, AVG, COUNT, MAX, MIN`).  
- Groups records based on a **common attribute**.  

### **Syntax:**  
```sql
SELECT designation, COUNT(*) FROM employees GROUP BY designation;
```

### **Statement related to the `employees` table:**  
To count employees per designation:  
```sql
SELECT designation, COUNT(*) FROM employees GROUP BY designation;
```

---

# **HAVING Clause**  

## **What is HAVING?**  
The `HAVING` clause filters **grouped records** based on conditions.  

### **Content:**  
- Works with `GROUP BY`.  
- Similar to `WHERE`, but for **aggregate functions**.  

### **Syntax:**  
```sql
SELECT designation, COUNT(*) FROM employees GROUP BY designation HAVING COUNT(*) > 3;
```

### **Statement related to the `employees` table:**  
To display designations with more than **3 employees**:  
```sql
SELECT designation, COUNT(*) FROM employees GROUP BY designation HAVING COUNT(*) > 3;
```

---

# **JOINS in SQL**  

## **What are Joins?**  
Joins combine **data from multiple tables** based on a **common column**.  

### **Content:**  
Types of joins:  
1. **INNER JOIN** – Matches records in both tables.  
2. **LEFT JOIN** – Includes all records from the left table, matching from the right.  
3. **RIGHT JOIN** – Includes all records from the right table, matching from the left.  
4. **FULL JOIN** – Includes all records from both tables.  

### **Syntax:**  
```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```

### **Statement related to the `employees` table:**  
To join `employees` and `departments`:  
```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```

---

# **INSERT Statement**  

## **What is INSERT?**  
The `INSERT` statement **adds new records** to a table.  

### **Content:**  
- Can insert into **specific columns** or **all columns**.  
- Requires values to match **column data types**.  

### **Syntax:**  
```sql
INSERT INTO employees (name, age, designation, salary) VALUES ('John Doe', 28, 'Engineer', 75000.00);
```

### **Statement related to the `employees` table:**  
To insert a new employee:  
```sql
INSERT INTO employees (name, age, designation, salary) VALUES ('Anna Lee', 26, 'Data Scientist', 70000.00);
```

---

# **UPDATE Statement**  

## **What is UPDATE?**  
The `UPDATE` statement **modifies existing records** in a table.  

### **Content:**  
- Uses `WHERE` to specify the record(s) to update.  
- Omitting `WHERE` updates **all records**.  

### **Syntax:**  
```sql
UPDATE employees SET salary = 85000 WHERE name = 'John Doe';
```

### **Statement related to the `employees` table:**  
To increase the salary of a specific employee:  
```sql
UPDATE employees SET salary = 90000 WHERE name = 'Michael Johnson';
```

---

# **DELETE Statement**  

## **What is DELETE?**  
The `DELETE` statement **removes records** from a table.  

### **Content:**  
- `WHERE` is used to delete **specific records**.  
- Omitting `WHERE` deletes **all records** (use `TRUNCATE` instead for efficiency).  

### **Syntax:**  
```sql
DELETE FROM employees WHERE age < 25;
```

### **Statement related to the `employees` table:**  
To remove employees earning **less than 50,000**:  
```sql
DELETE FROM employees WHERE salary < 50000;
```

---
