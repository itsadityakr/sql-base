![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

# Introduction to SQL

---

SQL (Structured Query Language) is a programming language used to interact with databases. It is a standard language for managing and manipulating data in relational database management systems (RDBMS). SQL was first developed by IBM in the 1970s.

## Why Use SQL?
- Retrieve and filter data from databases
- Insert, update, and delete records
- Create and modify database structures
- Control user access and permissions

## Components of SQL

SQL consists of several key components that help in database communication:

### 1. Queries
Queries allow you to retrieve data from a database. The `SELECT` statement is the most commonly used SQL command for fetching data.

#### Example:
```sql
SELECT * FROM employees;
```

<img src="../assets/table (1).png" alt="table">


This retrieves all records from the `employees` table.

### 2. Data Definition Language (DDL)
DDL is used to define and modify the structure of a database. It includes commands such as:
- `CREATE` - To create databases, tables, views, etc.
- `ALTER` - To modify an existing database structure
- `DROP` - To delete databases or tables
- `TRUNCATE` - To remove all records from a table

#### Example:
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    department VARCHAR(50),
    salary DECIMAL(10, 2),
    hire_date DATE,
    manager_id INT,
    department_id INT
);
```
This creates a table named `employees` with eight columns.

### 3. Data Manipulation Language (DML)
DML is used to manage data stored in a database. It includes:
- `SELECT` - To retrieve data
- `INSERT` - To add new records
- `UPDATE` - To modify existing records
- `DELETE` - To remove records

#### Example:
```sql
INSERT INTO employees (first_name, last_name, department, salary, hire_date, manager_id, department_id)
VALUES ('John', 'Doe', 'Sales', 50000, '2022-01-15', NULL, 1),
       ('Jane', 'Smith', 'HR', 60000, '2021-05-20', NULL, 2),
       ('Alice', 'Johnson', 'IT', 70000, '2023-03-10', NULL, 3),
       ('Bob', 'Brown', 'Sales', 55000, '2022-11-01', 1, 1),
       ('Charlie', 'Davis', 'Marketing', 65000, '2023-07-22', NULL, 4);
```
This inserts a new employee record.

### 4. Data Control Language (DCL)
DCL is used for managing access permissions in a database. It includes:
- `GRANT` - To give privileges
- `REVOKE` - To remove privileges

#### Example:
```sql
GRANT SELECT ON employees TO user1;
```
This allows `user1` to read data from the `employees` table.

## Popular SQL Databases
SQL is used in many database management systems, such as:
- **MySQL** - Open-source and widely used
- **PostgreSQL** - Advanced features and reliability
- **Microsoft SQL Server** - Used in enterprise applications
- **Oracle Database** - Powerful and used in large systems

## Summary
SQL is an essential tool for database management. It helps users store, retrieve, and manipulate data efficiently. Understanding SQL commands and their uses can make working with databases easier and more effective.

---

# Relational Databases and RDBMS

## What is a Relational Database?
A **relational database** is a type of database that organizes data into structured tables consisting of rows and columns. Each table represents an entity (such as customers, employees, or products), and relationships between tables are defined using keys (primary keys and foreign keys). 

### Example of a Table (Employees):
<img src="../assets/table (1).png" alt="table">

Each row represents a record, and each column represents an attribute of that record.

## What is an RDBMS?
A **Relational Database Management System (RDBMS)** is software used to manage relational databases. It provides functionalities like:
- Data storage and retrieval
- Data security and access control
- Query execution using SQL (Structured Query Language)
- Transaction management (ACID properties)

### Examples of RDBMS:
- MySQL
- PostgreSQL
- Microsoft SQL Server
- Oracle Database
- SQLite

## Benefits of Relational Databases
### 1. **Data Integrity**
   - Ensures accuracy and consistency through constraints (Primary Key, Foreign Key, Unique, etc.).
### 2. **Scalability**
   - Suitable for small to enterprise-level applications.
### 3. **Security**
   - Provides role-based access control (RBAC) to restrict unauthorized access.
### 4. **ACID Compliance**
   - Ensures Atomicity, Consistency, Isolation, and Durability for reliable transactions.
### 5. **Structured Data Storage**
   - Data is well-organized in tables, making it easier to retrieve and analyze.

## Limitations of Relational Databases
### 1. **Complex Queries Can Be Slow**
   - Joins across multiple tables can lead to performance issues in large datasets.
### 2. **Rigid Schema**
   - Requires predefined schemas, making it harder to adapt to frequent changes in data structure.
### 3. **Scalability Challenges**
   - Horizontal scaling (distributing data across multiple servers) is difficult compared to NoSQL databases.
### 4. **Storage Overhead**
   - Indexing, constraints, and relationships can consume more storage compared to simpler data storage solutions.

## SQL vs NoSQL
| Feature          | SQL (Relational Database) | NoSQL (Non-Relational Database) |
|-----------------|-------------------------|--------------------------------|
| **Structure**   | Table-based (rows & columns) | Document, Key-Value, Graph, Column-family |
| **Schema**      | Fixed schema (predefined) | Flexible schema (dynamic) |
| **Scalability** | Vertical Scaling (limited horizontal scaling) | Horizontal Scaling (better for big data) |
| **Transactions** | ACID-compliant | Eventual consistency (some support ACID) |
| **Examples**    | MySQL, PostgreSQL, SQL Server, Oracle | MongoDB, Cassandra, Redis, DynamoDB |
| **Use Case**    | Banking, ERP, e-commerce, structured data applications | Real-time analytics, social networks, IoT, unstructured data |

## Summary
Relational databases (RDBMS) are powerful for structured data management, ensuring integrity and security. However, for applications requiring high flexibility and scalability, NoSQL databases may be a better choice. Understanding the differences helps in selecting the right database for a given use case.

---

# SQL vs NoSQL

### Example of a Table (Employees) in SQL:
| ID  | Name   | Age | Department |
|-----|--------|-----|------------|
| 1   | Alice  | 30  | HR         |
| 2   | Bob    | 25  | IT         |
| 3   | Charlie| 35  | Sales      |

Each row represents a record, and each column represents an attribute of that record.

### Example of NoSQL Document (MongoDB):
```json
{
  "employees": [
    { "id": 1, "name": "Alice", "age": 30, "department": "HR" },
    { "id": 2, "name": "Bob", "age": 25, "department": "IT" },
    { "id": 3, "name": "Charlie", "age": 35, "department": "Sales" }
  ]
}
```
In NoSQL, data is stored in JSON-like documents instead of rows and columns.


## SQL vs NoSQL
| Feature          | SQL (Relational Database) | NoSQL (Non-Relational Database) |
|-----------------|-------------------------|--------------------------------|
| **Structure**   | Table-based (rows & columns) | Document, Key-Value, Graph, Column-family |
| **Schema**      | Fixed schema (predefined) | Flexible schema (dynamic) |
| **Scalability** | Vertical Scaling (limited horizontal scaling) | Horizontal Scaling (better for big data) |
| **Transactions** | ACID-compliant | Eventual consistency (some support ACID) |
| **Examples**    | MySQL, PostgreSQL, SQL Server, Oracle | MongoDB, Cassandra, Redis, DynamoDB |
| **Use Case**    | Banking, ERP, e-commerce, structured data applications | Real-time analytics, social networks, IoT, unstructured data |

---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)