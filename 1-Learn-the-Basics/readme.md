### **Introduction**  
Databases are essential for storing, managing, and retrieving structured data efficiently. One of the most popular types of databases is the **Relational Database Management System (RDBMS)**, which organizes data into tables with predefined relationships.  

---

### **What are Relational Databases?**  
A **Relational Database (RDB)** is a type of database that stores data in structured tables with rows and columns. Each table has a unique primary key, and relationships are established using foreign keys. This ensures **data integrity, normalization, and efficient querying** using SQL.  

#### **Content:**  
- Data is stored in tabular format.  
- Relationships are established through primary and foreign keys.  
- SQL is used to manipulate and retrieve data.  
- Ensures **ACID (Atomicity, Consistency, Isolation, Durability)** compliance.  

#### **Syntax:**  
Creating a relational database table in MySQL:  
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    age INT NOT NULL,
    designation VARCHAR(50) NOT NULL,
    salary DECIMAL(10,2) NOT NULL
);
```

#### **Statement related to the `employees` table:**  
To display all employees:  
```sql
SELECT * FROM employees;
```

---

### **RDBMS Benefits and Limitations**  

#### **Benefits:**  
- **Structured & Organized Data:** Data is stored in rows and columns.  
- **Data Integrity & Consistency:** Uses primary and foreign keys.  
- **Scalability & Security:** Supports large datasets with user access controls.  
- **ACID Compliance:** Ensures reliability in transactions.  

#### **Limitations:**  
- **Complexity:** Requires a well-defined schema.  
- **Scalability Challenges:** Vertical scaling can be expensive.  
- **Performance Issues:** Complex joins can slow down queries on large datasets.  

#### **Syntax:**  
To enforce data integrity using constraints:  
```sql
ALTER TABLE employees ADD CONSTRAINT chk_age CHECK (age > 18);
```

#### **Statement related to the `employees` table:**  
To retrieve employees earning more than 60,000:  
```sql
SELECT * FROM employees WHERE salary > 60000;
```

---

### **SQL vs NoSQL Databases**  

#### **SQL (Structured Query Language) Databases:**  
- Uses structured tables with rows and columns.  
- Supports **ACID transactions** for data consistency.  
- Uses **SQL queries** for data manipulation.  
- Example: **MySQL, PostgreSQL, SQL Server.**  

#### **NoSQL (Not Only SQL) Databases:**  
- Uses flexible schema (key-value, document, column-based, graph databases).  
- Designed for **horizontal scalability.**  
- Supports high-speed data retrieval for large, unstructured data.  
- Example: **MongoDB, Cassandra, Redis.**  

#### **Syntax:**  
SQL query to fetch employee details:  
```sql
SELECT name, age, designation FROM employees WHERE age > 30;
```

#### **Statement related to the `employees` table:**  
NoSQL equivalent in MongoDB:  
```json
db.employees.find({ "age": { "$gt": 30 } }, { "name": 1, "age": 1, "designation": 1 });
```

---
