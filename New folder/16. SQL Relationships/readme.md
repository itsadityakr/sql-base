# SQL Relationships

In relational databases, tables are connected using relationships, allowing data to be linked in meaningful ways. Here, we'll discuss three common types of relationships:

- **One-to-One (1:1)**
- **One-to-Many (1:Many)**
- **Many-to-Many (Many:Many)**

For each relationship, I’ll explain how it works, write SQL code to create tables, insert data, and retrieve data with simple queries.

---

## 1. One-to-One (1:1) Relationship

### Definition:
In a **One-to-One** relationship, each row in Table A corresponds to only one row in Table B, and vice versa. This is used when a record in one table should have only one matching record in another table.

### Example:
Let’s consider two tables:
- `Employee`: Stores basic employee information.
- `EmployeeDetails`: Stores additional information about the employee, such as address and date of birth. Each employee can have only one set of details.

### SQL Code to Create Tables for One-to-One Relationship:

#### Step 1: Create `Employee` Table
```sql
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100)
);
```
- **Explanation**: `EmployeeID` is the **primary key** (unique identifier) for the `Employee` table, and `Name` stores the employee’s name.

#### Step 2: Create `EmployeeDetails` Table
```sql
CREATE TABLE EmployeeDetails (
    EmployeeID INT PRIMARY KEY,
    Address VARCHAR(255),
    DateOfBirth DATE,
    FOREIGN KEY (EmployeeID) REFERENCES Employee(EmployeeID)
);
```
- **Explanation**:
  - The `EmployeeDetails` table has its own `EmployeeID`, which is also the **primary key**.
  - The **foreign key** `EmployeeID` links this table to the `Employee` table, ensuring that each detail row corresponds to an existing employee.

### Inserting Data into the Tables:
```sql
-- Insert data into Employee table
INSERT INTO Employee (EmployeeID, Name) VALUES (1, 'John'), (2, 'Sarah');

-- Insert data into EmployeeDetails table
INSERT INTO EmployeeDetails (EmployeeID, Address, DateOfBirth) 
VALUES (1, '123 Street', '1990-01-01'), (2, '456 Avenue', '1985-05-15');
```

### Retrieving Data:
```sql
-- Join the two tables to display all information about employees
SELECT e.EmployeeID, e.Name, d.Address, d.DateOfBirth
FROM Employee e
JOIN EmployeeDetails d ON e.EmployeeID = d.EmployeeID;
```

### Output:
| EmployeeID | Name  | Address    | DateOfBirth |
|------------|-------|------------|-------------|
| 1          | John  | 123 Street | 1990-01-01  |
| 2          | Sarah | 456 Avenue | 1985-05-15  |

### Key Points:
- One employee has one set of details.
- This relationship is enforced by the **foreign key** in the `EmployeeDetails` table.

---

## 2. One-to-Many (1:Many) Relationship

### Definition:
In a **One-to-Many** relationship, a row in Table A can be related to many rows in Table B. However, each row in Table B is related to only one row in Table A.

### Example:
Let’s consider two tables:
- `Department`: Stores department information.
- `Employee`: Stores employee information, where each employee belongs to one department, but each department can have many employees.

### SQL Code to Create Tables for One-to-Many Relationship:

#### Step 1: Create `Department` Table
```sql
CREATE TABLE Department (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
);
```

#### Step 2: Modify `Employee` Table to Include `DepartmentID`
```sql
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);
```
- **Explanation**:
  - The `DepartmentID` in the `Employee` table is a **foreign key** that references the `DepartmentID` in the `Department` table.
  - This creates a **One-to-Many** relationship: one department can have many employees, but each employee belongs to only one department.

### Inserting Data into the Tables:
```sql
-- Insert data into Department table
INSERT INTO Department (DepartmentID, DepartmentName) 
VALUES (1, 'IT'), (2, 'HR');

-- Insert data into Employee table
INSERT INTO Employee (EmployeeID, Name, DepartmentID)
VALUES (1, 'John', 1), (2, 'Sarah', 2), (3, 'Mike', 1);
```

### Retrieving Data:
```sql
-- Display all employees and their departments
SELECT e.EmployeeID, e.Name, d.DepartmentName
FROM Employee e
JOIN Department d ON e.DepartmentID = d.DepartmentID;
```

### Output:
| EmployeeID | Name  | DepartmentName |
|------------|-------|----------------|
| 1          | John  | IT             |
| 2          | Sarah | HR             |
| 3          | Mike  | IT             |

### Key Points:
- Each department can have many employees.
- The **foreign key** in the `Employee` table enforces this relationship.

---

## 3. Many-to-Many (Many:Many) Relationship

### Definition:
In a **Many-to-Many** relationship, many rows in Table A can be related to many rows in Table B. To handle this, we create a **junction table** (also called a linking table) to store the relationships.

### Example:
Let’s consider three tables:
- `Employee`: Stores employee information.
- `Project`: Stores project information.
- `EmployeeProject`: Junction table that links employees to projects. One employee can work on multiple projects, and one project can have multiple employees.

### SQL Code to Create Tables for Many-to-Many Relationship:

#### Step 1: Create `Project` Table
```sql
CREATE TABLE Project (
    ProjectID INT PRIMARY KEY,
    ProjectName VARCHAR(100)
);
```

#### Step 2: Create `EmployeeProject` Junction Table
```sql
CREATE TABLE EmployeeProject (
    EmployeeID INT,
    ProjectID INT,
    PRIMARY KEY (EmployeeID, ProjectID),
    FOREIGN KEY (EmployeeID) REFERENCES Employee(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Project(ProjectID)
);
```
- **Explanation**:
  - `EmployeeProject` is a **junction table** that links `Employee` and `Project` using foreign keys.
  - The combination of `EmployeeID` and `ProjectID` serves as a **composite primary key**, ensuring each employee is linked to a project only once.

### Inserting Data into the Tables:
```sql
-- Insert data into Project table
INSERT INTO Project (ProjectID, ProjectName) 
VALUES (1, 'Alpha'), (2, 'Beta');

-- Insert data into EmployeeProject table (linking employees to projects)
INSERT INTO EmployeeProject (EmployeeID, ProjectID) 
VALUES (1, 1), (1, 2), (2, 1), (3, 2);
```

### Retrieving Data:
```sql
-- Display all employees and the projects they are working on
SELECT e.Name, p.ProjectName
FROM Employee e
JOIN EmployeeProject ep ON e.EmployeeID = ep.EmployeeID
JOIN Project p ON ep.ProjectID = p.ProjectID;
```

### Output:
| Name  | ProjectName |
|-------|-------------|
| John  | Alpha       |
| John  | Beta        |
| Sarah | Alpha       |
| Mike  | Beta        |

### Key Points:
- One employee can work on many projects, and one project can have many employees.
- The **junction table** `EmployeeProject` handles this relationship using **foreign keys** that link to both `Employee` and `Project`.

---

## Conclusion

In this guide, we covered the three main types of relationships in SQL databases:

1. **One-to-One (1:1)**: Each row in one table is linked to exactly one row in another table.
2. **One-to-Many (1:Many)**: One row in a table is linked to multiple rows in another table.
3. **Many-to-Many (Many:Many)**: Many rows in one table can be related to many rows in another table, handled through a **junction table**.

### Example Queries:
- We created tables for each relationship, inserted data, and wrote SQL queries to display related data using **JOIN** clauses.
  
---

- by Aditya Kumar