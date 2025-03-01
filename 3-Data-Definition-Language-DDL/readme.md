# **Data Definition Language (DDL)**  

## **Introduction**  
Data Definition Language (**DDL**) is a subset of SQL that deals with **creating, altering, and deleting** database structures such as tables, schemas, and indexes. Unlike Data Manipulation Language (**DML**), DDL **does not** modify existing data but defines how data is stored.  

---

## **What is DDL?**  
DDL commands **define and modify** the structure of a database. These commands automatically **commit changes** and cannot be rolled back.  

### **Content:**  
Common DDL commands:  
- `CREATE` – Creates database objects such as tables, views, and indexes.  
- `ALTER` – Modifies existing database objects.  
- `DROP` – Deletes database objects permanently.  
- `TRUNCATE` – Removes all records from a table while keeping its structure.  

### **Syntax:**  
Example of a DDL statement:  
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    age INT NOT NULL,
    designation VARCHAR(50) NOT NULL,
    salary DECIMAL(10,2) NOT NULL
);
```

### **Statement related to the `employees` table:**  
To display all table names in the database:  
```sql
SHOW TABLES;
```

---

# **Truncate Table**  

## **What is TRUNCATE?**  
The `TRUNCATE` command removes **all records** from a table without deleting the table structure. It is faster than `DELETE` because it **does not** generate individual delete statements.  

### **Content:**  
- `TRUNCATE` resets **auto-increment** values.  
- Unlike `DELETE`, it **cannot** have a `WHERE` clause.  
- It is a **DDL command** and automatically commits changes.  

### **Syntax:**  
Truncating a table:  
```sql
TRUNCATE TABLE employees;
```

### **Statement related to the `employees` table:**  
To remove all employees while keeping the table:  
```sql
TRUNCATE TABLE employees;
```

---

# **Alter Table**  

## **What is ALTER TABLE?**  
The `ALTER TABLE` command is used to **modify** an existing table’s structure, such as adding, deleting, or modifying columns.  

### **Content:**  
The `ALTER TABLE` command allows:  
1. **Adding a column:** `ADD COLUMN`  
2. **Modifying a column:** `MODIFY COLUMN`  
3. **Deleting a column:** `DROP COLUMN`  
4. **Renaming a column/table:** `RENAME COLUMN/TABLE`  

### **Syntax:**  
Adding a column:  
```sql
ALTER TABLE employees ADD COLUMN department VARCHAR(50);
```
Modifying a column:  
```sql
ALTER TABLE employees MODIFY COLUMN age SMALLINT;
```
Dropping a column:  
```sql
ALTER TABLE employees DROP COLUMN department;
```

### **Statement related to the `employees` table:**  
To add a new column for joining date:  
```sql
ALTER TABLE employees ADD COLUMN joining_date DATE;
```

---

# **Create Table**  

## **What is CREATE TABLE?**  
The `CREATE TABLE` statement is used to **define a new table** in a database. It specifies the table name, column names, and data types.  

### **Content:**  
- A table must have at least one **column** and a **primary key**.  
- Constraints such as `NOT NULL`, `UNIQUE`, and `FOREIGN KEY` can be applied.  
- Data types must be chosen carefully for efficiency.  

### **Syntax:**  
Creating a table:  
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    age INT NOT NULL,
    designation VARCHAR(50) NOT NULL,
    salary DECIMAL(10,2) NOT NULL
);
```

### **Statement related to the `employees` table:**  
To create a new table for department details:  
```sql
CREATE TABLE departments (
    department_id INT PRIMARY KEY AUTO_INCREMENT,
    department_name VARCHAR(50) NOT NULL
);
```

---
