# SQL Joins

Joins are used in SQL to combine rows from two or more tables based on a related column between them. They allow you to retrieve and manipulate data across multiple tables in a database. In this guide, we'll cover:

- Cross Joins
- Inner Joins
- Left Joins
- Right Joins
- On Delete Cascade

---

## 1. Random Table Visualization

To illustrate different types of joins, let’s create and use the following sample tables:

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
| 3            | Marketing      |

---

## 2. Cross Join

### Definition
A **Cross Join** (Cartesian Join) returns the Cartesian product of two tables. This means it combines each row from the first table with each row from the second table.

### SQL Syntax
```sql
SELECT *
FROM Employee
CROSS JOIN Department;
```

### Explanation
- **CROSS JOIN**: Combines every row from `Employee` with every row from `Department`.

### Output
| EmployeeID | Name | DepartmentID | DepartmentID | DepartmentName |
|------------|------|--------------|--------------|----------------|
| 1          | John | 1            | 1            | IT             |
| 1          | John | 1            | 2            | HR             |
| 1          | John | 1            | 3            | Marketing      |
| 2          | Sarah| 2            | 1            | IT             |
| 2          | Sarah| 2            | 2            | HR             |
| 2          | Sarah| 2            | 3            | Marketing      |
| 3          | Mike | 1            | 1            | IT             |
| 3          | Mike | 1            | 2            | HR             |
| 3          | Mike | 1            | 3            | Marketing      |

### Key Points
- **Cartesian Product**: Results in a large number of rows, which can be inefficient with large tables.

---

## 3. Inner Join

### Definition
An **Inner Join** returns rows when there is a match between the columns in both tables. If there is no match, the row is excluded.

### SQL Syntax
```sql
SELECT e.EmployeeID, e.Name, d.DepartmentName
FROM Employee e
INNER JOIN Department d ON e.DepartmentID = d.DepartmentID;
```

### Explanation
- **INNER JOIN**: Combines rows from `Employee` and `Department` where `DepartmentID` matches in both tables.

### Output
| EmployeeID | Name | DepartmentName |
|------------|------|----------------|
| 1          | John | IT             |
| 2          | Sarah| HR             |
| 3          | Mike | IT             |

### Key Points
- **Matching Rows**: Only rows with matching `DepartmentID` in both tables are included.

---

## 4. Left Join

### Definition
A **Left Join** (or Left Outer Join) returns all rows from the left table and the matched rows from the right table. If there is no match, NULL values are returned for columns from the right table.

### SQL Syntax
```sql
SELECT e.EmployeeID, e.Name, d.DepartmentName
FROM Employee e
LEFT JOIN Department d ON e.DepartmentID = d.DepartmentID;
```

### Explanation
- **LEFT JOIN**: Returns all rows from `Employee` and the matching rows from `Department`. If no match is found, `DepartmentName` will be NULL.

### Output
| EmployeeID | Name | DepartmentName |
|------------|------|----------------|
| 1          | John | IT             |
| 2          | Sarah| HR             |
| 3          | Mike | IT             |

### Key Points
- **All Rows from Left Table**: Ensures all rows from `Employee` are included, even if there’s no matching department.

---

## 5. Right Join

### Definition
A **Right Join** (or Right Outer Join) returns all rows from the right table and the matched rows from the left table. If there is no match, NULL values are returned for columns from the left table.

### SQL Syntax
```sql
SELECT e.EmployeeID, e.Name, d.DepartmentName
FROM Employee e
RIGHT JOIN Department d ON e.DepartmentID = d.DepartmentID;
```

### Explanation
- **RIGHT JOIN**: Returns all rows from `Department` and the matching rows from `Employee`. If no match is found, `EmployeeID` and `Name` will be NULL.

### Output
| EmployeeID | Name | DepartmentName |
|------------|------|----------------|
| 1          | John | IT             |
| 3          | Mike | IT             |
| 2          | Sarah| HR             |
| NULL       | NULL | Marketing      |

### Key Points
- **All Rows from Right Table**: Ensures all rows from `Department` are included, even if there’s no matching employee.

---

## 6. On Delete Cascade

### Definition
**On Delete Cascade** is a referential action that automatically deletes rows in a child table when the corresponding rows in the parent table are deleted. This maintains data integrity by removing dependent data.

### SQL Syntax
```sql
CREATE TABLE Department (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
);

CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID) ON DELETE CASCADE
);
```

### Explanation
- **ON DELETE CASCADE**: If a row in the `Department` table is deleted, all corresponding rows in the `Employee` table are automatically deleted.

### Example:
1. **Insert Data**:
    ```sql
    INSERT INTO Department (DepartmentID, DepartmentName) VALUES (1, 'IT'), (2, 'HR');
    INSERT INTO Employee (EmployeeID, Name, DepartmentID) VALUES (1, 'John', 1), (2, 'Sarah', 2);
    ```

2. **Delete Department**:
    ```sql
    DELETE FROM Department WHERE DepartmentID = 1;
    ```

3. **Verify Employee Table**:
    ```sql
    SELECT * FROM Employee;
    ```

### Output
| EmployeeID | Name  | DepartmentID |
|------------|-------|--------------|
| 2          | Sarah | 2            |

- **John** is deleted from the `Employee` table because his `DepartmentID` (1) was deleted from the `Department` table.

### Key Points
- **Automatic Deletion**: Ensures that dependent data in child tables is removed when the parent data is deleted.

---

## Summary

- **Cross Join**: Produces a Cartesian product of two tables.
- **Inner Join**: Returns rows with matching values in both tables.
- **Left Join**: Returns all rows from the left table and matched rows from the right table.
- **Right Join**: Returns all rows from the right table and matched rows from the left table.
- **On Delete Cascade**: Automatically deletes related rows in child tables when a row in the parent table is deleted.

Understanding these types of joins and referential actions will help you effectively manage and query relational databases. If you have further questions or need more examples, feel free to ask!

---

- by Aditya Kumar