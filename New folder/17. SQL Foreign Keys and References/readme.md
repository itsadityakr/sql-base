# SQL Foreign Keys and References

This guide explains **foreign keys** and **references** in SQL. We will:
- Define foreign keys and references
- Create random tables
- Provide SQL code examples
- Show how to use foreign keys to enforce data integrity

---

## 1. What is a Foreign Key?

A **foreign key** is a column or a set of columns in a table that uniquely identifies a row in another table. It establishes a relationship between two tables, ensuring that the data in one table corresponds to the data in another table.

### Purpose of Foreign Key:
- **Data Integrity**: Ensures that values in one table match values in another, maintaining consistency.
- **Relationships**: Connects related data across tables.

### Visual Example

Consider two tables: `Employee` and `Department`.

### Table 1: `Employee`

| EmployeeID | Name     | DepartmentID |
|------------|----------|--------------|
| 1          | John     | 1            |
| 2          | Sarah    | 2            |
| 3          | Mike     | 1            |

### Table 2: `Department`

| DepartmentID | DepartmentName |
|--------------|----------------|
| 1            | IT             |
| 2            | HR             |

In this example:
- `Employee` has a `DepartmentID` column that references `DepartmentID` in the `Department` table.
- `DepartmentID` in `Employee` is a **foreign key** that establishes a relationship with the `Department` table.

---

## 2. SQL Code to Create Foreign Key and Reference

### Create `Department` Table

```sql
CREATE TABLE Department (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
);
```

- **DepartmentID** is the **primary key** of the `Department` table, uniquely identifying each department.

### Create `Employee` Table with Foreign Key

```sql
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);
```

- **FOREIGN KEY (DepartmentID)**: This establishes `DepartmentID` in the `Employee` table as a foreign key that references `DepartmentID` in the `Department` table.

### Explanation

- **FOREIGN KEY (DepartmentID)**: Ensures that every `DepartmentID` in the `Employee` table must match an existing `DepartmentID` in the `Department` table. This maintains referential integrity.

---

## 3. Inserting Data into Tables

### Insert Data into `Department`

```sql
INSERT INTO Department (DepartmentID, DepartmentName) 
VALUES (1, 'IT'), (2, 'HR');
```

### Insert Data into `Employee`

```sql
INSERT INTO Employee (EmployeeID, Name, DepartmentID) 
VALUES (1, 'John', 1), (2, 'Sarah', 2), (3, 'Mike', 1);
```

- **John** and **Mike** work in the **IT** department (`DepartmentID` 1).
- **Sarah** works in the **HR** department (`DepartmentID` 2).

---

## 4. Retrieving Data with Foreign Key Relationship

### SQL Query to Retrieve Data

```sql
SELECT e.EmployeeID, e.Name, d.DepartmentName
FROM Employee e
JOIN Department d ON e.DepartmentID = d.DepartmentID;
```

### Explanation

- **JOIN**: Combines rows from `Employee` and `Department` tables based on the foreign key relationship.
- **ON e.DepartmentID = d.DepartmentID**: Matches `DepartmentID` in `Employee` with `DepartmentID` in `Department` to pull related data.

### Output

| EmployeeID | Name  | DepartmentName |
|------------|-------|----------------|
| 1          | John  | IT             |
| 2          | Sarah | HR             |
| 3          | Mike  | IT             |

### Key Points

- This query displays each employee along with their department name by leveraging the foreign key relationship.

---

## Summary

- **Foreign Key**: A column in one table that uniquely identifies rows in another table, enforcing referential integrity.
- **Reference**: The foreign key column points to the primary key column in another table, creating a link between the two tables.

By understanding and using foreign keys, you ensure that your database maintains accurate and consistent data across related tables. If you have any more questions or need further examples, feel free to ask!

---

- by Aditya Kumar