# SQL Constraints

In this guide, we will cover SQL constraints, including:
- What a constraint is
- `UNIQUE` constraint
- `CHECK` constraint with `UNIQUE` check
- Custom validation for mobile numbers using `CHECK`

### Random Table: `Employee`

| EmployeeID | Name     | Department | Salary | YearsOfExperience | MobileNumber  |
|------------|----------|------------|--------|-------------------|---------------|
| 1          | John     | IT         | 60000  | 5                 | 9876543210    |
| 2          | Sarah    | HR         | 55000  | 8                 | 9123456789    |
| 3          | Mike     | IT         | 70000  | 10                | 9876543210    |
| 4          | Lucy     | Finance    | 50000  | 3                 | 987654321     |
| 5          | James    | Marketing  | 60000  | 5                 | 9876543211    |

This table will be used for examples of different constraints.

---

## 1. What is a Constraint?

### Definition:
A **constraint** in SQL is a rule that restricts the type of data that can be stored in a table. Constraints help maintain data integrity and ensure that the data meets certain conditions.

### Types of Constraints:
- **NOT NULL**: Ensures a column cannot have `NULL` values.
- **UNIQUE**: Ensures all values in a column are distinct.
- **PRIMARY KEY**: Uniquely identifies each row in a table.
- **FOREIGN KEY**: Ensures referential integrity between two tables.
- **CHECK**: Ensures that a condition is met before data is entered into a table.

---

## 2. UNIQUE Constraint

### Basic Syntax:
```sql
CREATE TABLE table_name (
    column_name datatype UNIQUE
);
```

### Explanation:
The `UNIQUE` constraint ensures that all values in a column are distinct—no duplicates are allowed.

### Example: Ensure Unique Mobile Numbers
We want to make sure that each employee has a unique mobile number.

#### Query:
```sql
CREATE TABLE Employee (
    EmployeeID INT,
    Name VARCHAR(100),
    MobileNumber VARCHAR(15) UNIQUE
);
```

#### Explanation:
- The `MobileNumber` column is restricted by the `UNIQUE` constraint, which ensures no two employees can have the same mobile number.

### Violation Example:
If we tried to insert a new employee with the same mobile number as an existing employee, we would get an error.

#### Violation Example Query:
```sql
INSERT INTO Employee (EmployeeID, Name, MobileNumber)
VALUES (6, 'Alice', '9876543210');
```

#### Output:

```
Error: Duplicate entry '9876543210' for key 'MobileNumber'
```

### Additional Note:
- A table can have multiple `UNIQUE` constraints on different columns, but only one `PRIMARY KEY`.

---

## 3. CHECK Constraint

### Basic Syntax:
```sql
CREATE TABLE table_name (
    column_name datatype CHECK (condition)
);
```

### Explanation:
The `CHECK` constraint allows you to define custom rules for data validation. The data must meet the condition specified in the `CHECK` constraint before it can be inserted or updated in the table.

---

## 4. CHECK with UNIQUE: Validating Length

### Example: Ensure Mobile Number Length is At Least 10 Digits
We will combine `CHECK` with `UNIQUE` to ensure that mobile numbers are unique and that they have at least 10 digits.

#### Query:
```sql
CREATE TABLE Employee (
    EmployeeID INT,
    Name VARCHAR(100),
    MobileNumber VARCHAR(15) UNIQUE CHECK (LENGTH(MobileNumber) >= 10)
);
```

#### Explanation:
- **UNIQUE**: Ensures that no two employees can have the same mobile number.
- **CHECK (LENGTH(MobileNumber) >= 10)**: Ensures that the mobile number has at least 10 digits.

### Example Output:

| EmployeeID | Name  | MobileNumber |
|------------|-------|--------------|
| 1          | John  | 9876543210   |
| 2          | Sarah | 9123456789   |
| 3          | Mike  | 9876543210   |
| 4          | Lucy  | 987654321    |

- Lucy's mobile number violates the `CHECK` constraint because it has fewer than 10 digits.
- Mike's entry also violates the `UNIQUE` constraint because he shares the same number as John.

#### Violation Example:
If an employee tries to register with a number less than 10 digits:

```sql
INSERT INTO Employee (EmployeeID, Name, MobileNumber)
VALUES (7, 'Bob', '12345');
```

#### Output:

```
Error: Check constraint 'MobileNumber_length_check' failed.
```

---

## 5. Custom Constraint: Mobile Number Validation (10 Digits)

### Basic Syntax:
To ensure mobile numbers are at least 10 digits long, we use the `CHECK` constraint with a length condition.

```sql
CREATE TABLE Employee (
    EmployeeID INT,
    Name VARCHAR(100),
    MobileNumber VARCHAR(15) CHECK (LENGTH(MobileNumber) >= 10)
);
```

### Example Explanation:
We will ensure that mobile numbers are always at least 10 digits long. The table will prevent any insert or update if the length condition is not met.

#### Query:
```sql
INSERT INTO Employee (EmployeeID, Name, MobileNumber)
VALUES (6, 'Alice', '123456789'); -- Violates length constraint
```

#### Output:

```
Error: Check constraint 'MobileNumber_length_check' failed.
```

#### Explanation:
- **CHECK (LENGTH(MobileNumber) >= 10)**: This ensures that any mobile number inserted into the `Employee` table must be at least 10 digits long. If an attempt is made to insert a number shorter than 10 digits, the insert fails.

---

## Conclusion

- **UNIQUE** ensures no duplicate values exist in a column.
- **CHECK** allows you to enforce specific rules on data, such as the length of a string or numeric range.
- Combining **UNIQUE** and **CHECK** constraints can ensure both uniqueness and data integrity, such as enforcing a rule that mobile numbers are unique and at least 10 digits long.

---

- by Aditya Kumar