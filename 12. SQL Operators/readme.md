# SQL Operators

SQL provides various types of operators to perform operations on data stored in a database. This guide covers the relational, logical, and set operators (`IN`, `NOT IN`, `BETWEEN`) with detailed examples.

### Table of Contents
- [1. Relational Operators](#1-relational-operators)
  - [Equal (`=`)](#equal-)
  - [Not Equal (`<>`, `!=`)](#not-equal-)
  - [Greater Than (`>`, `>=`)](#greater-than-)
  - [Less Than (`<`, `<=`)](#less-than-)
- [2. Logical Operators](#2-logical-operators)
  - [AND](#and)
  - [OR](#or)
  - [NOT](#not)
- [3. Set Operators](#3-set-operators)
  - [IN](#in)
  - [NOT IN](#not-in)
  - [BETWEEN](#between)

---

## 1. Relational Operators

Relational operators compare two values. They are often used in `WHERE` clauses to filter records based on a condition.

### Equal (`=`)
- **Description**: Checks if two values are equal.
- **Syntax**: `column = value`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Salary = 50000;
```

| EmployeeID | Name    | Salary |
|------------|---------|--------|
| 101        | Alice   | 50000  |
| 102        | Bob     | 50000  |

---

### Not Equal (`<>`, `!=`)
- **Description**: Checks if two values are not equal.
- **Syntax**: `column <> value` or `column != value`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Salary <> 50000;
```

| EmployeeID | Name    | Salary |
|------------|---------|--------|
| 103        | Charlie | 45000  |
| 104        | David   | 55000  |

---

### Greater Than (`>`, `>=`)
- **Description**: Checks if one value is greater than another. `>=` also includes equality.
- **Syntax**: `column > value` or `column >= value`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Salary > 50000;
```

| EmployeeID | Name    | Salary |
|------------|---------|--------|
| 104        | David   | 55000  |
| 105        | Eve     | 60000  |

---

### Less Than (`<`, `<=`)
- **Description**: Checks if one value is less than another. `<=` also includes equality.
- **Syntax**: `column < value` or `column <= value`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Salary < 50000;
```

| EmployeeID | Name    | Salary |
|------------|---------|--------|
| 103        | Charlie | 45000  |

---

## 2. Logical Operators

Logical operators allow you to combine multiple conditions in a SQL query.

### AND
- **Description**: Combines two conditions, returning true only if both conditions are true.
- **Syntax**: `condition1 AND condition2`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Salary > 40000 AND Department = 'Sales';
```

| EmployeeID | Name    | Salary | Department |
|------------|---------|--------|------------|
| 101        | Alice   | 50000  | Sales      |
| 102        | Bob     | 50000  | Sales      |
| 104        | David   | 55000  | Sales      |

---

### OR
- **Description**: Combines two conditions, returning true if either condition is true.
- **Syntax**: `condition1 OR condition2`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Salary < 50000 OR Department = 'HR';
```

| EmployeeID | Name    | Salary | Department |
|------------|---------|--------|------------|
| 103        | Charlie | 45000  | IT         |
| 106        | Frank   | 50000  | HR         |

---

### NOT
- **Description**: Reverses the result of a condition. If the condition is true, `NOT` makes it false, and vice versa.
- **Syntax**: `NOT condition`
  
#### Example:

```sql
SELECT * FROM Employees WHERE NOT Department = 'IT';
```

| EmployeeID | Name    | Salary | Department |
|------------|---------|--------|------------|
| 101        | Alice   | 50000  | Sales      |
| 102        | Bob     | 50000  | Sales      |
| 106        | Frank   | 50000  | HR         |

---

## 3. Set Operators

### IN
- **Description**: The `IN` operator allows you to check if a value is within a specified set of values.
- **Syntax**: `column IN (value1, value2, ...)`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Department IN ('Sales', 'HR');
```

| EmployeeID | Name    | Salary | Department |
|------------|---------|--------|------------|
| 101        | Alice   | 50000  | Sales      |
| 102        | Bob     | 50000  | Sales      |
| 106        | Frank   | 50000  | HR         |

#### Example Explanation:
In this query, we are selecting all employees whose department is either 'Sales' or 'HR'.

---

### NOT IN
- **Description**: The `NOT IN` operator checks if a value is *not* within a specified set of values.
- **Syntax**: `column NOT IN (value1, value2, ...)`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Department NOT IN ('Sales', 'HR');
```

| EmployeeID | Name    | Salary | Department |
|------------|---------|--------|------------|
| 103        | Charlie | 45000  | IT         |
| 105        | Eve     | 60000  | IT         |

#### Example Explanation:
This query fetches employees who do not belong to the 'Sales' or 'HR' departments.

---

### BETWEEN
- **Description**: The `BETWEEN` operator is used to filter the result set within a specific range. It includes both the starting and ending values.
- **Syntax**: `column BETWEEN value1 AND value2`
  
#### Example:

```sql
SELECT * FROM Employees WHERE Salary BETWEEN 45000 AND 55000;
```

| EmployeeID | Name    | Salary |
|------------|---------|--------|
| 101        | Alice   | 50000  |
| 102        | Bob     | 50000  |
| 103        | Charlie | 45000  |
| 104        | David   | 55000  |

#### Example Explanation:
This query returns employees with salaries between 45,000 and 55,000 (inclusive).

---

## More Complex Examples Combining Operators

### Example 1: Using Relational, Logical, and `IN`
```sql
SELECT * FROM Employees 
WHERE Salary >= 45000 AND Department IN ('Sales', 'HR');
```

| EmployeeID | Name    | Salary | Department |
|------------|---------|--------|------------|
| 101        | Alice   | 50000  | Sales      |
| 102        | Bob     | 50000  | Sales      |
| 106        | Frank   | 50000  | HR         |

#### Example Explanation:
This query selects employees who have a salary of at least 45,000 and work in either the 'Sales' or 'HR' department.

---

### Example 2: Using `NOT IN` and `OR`
```sql
SELECT * FROM Employees 
WHERE Salary > 50000 OR Department NOT IN ('HR', 'Sales');
```

| EmployeeID | Name    | Salary | Department |
|------------|---------|--------|------------|
| 103        | Charlie | 45000  | IT         |
| 104        | David   | 55000  | Sales      |
| 105        | Eve     | 60000  | IT         |

#### Example Explanation:
This query returns employees with a salary greater than 50,000 or employees who are not in the 'HR' or 'Sales' departments.

---

### Example 3: Using `BETWEEN` with `AND`
```sql
SELECT * FROM Employees 
WHERE Salary BETWEEN 45000 AND 60000 AND Department = 'IT';
```

| EmployeeID | Name    | Salary | Department |
|------------|---------|--------|------------|
| 103        | Charlie | 45000  | IT         |
| 105        | Eve     | 60000  | IT         |

#### Example Explanation:
This query filters employees who work in the 'IT' department and have salaries between 45,000 and 60,000.

---

## Summary of SQL Operators

| **Operator** | **Description**                                | **Example**                                      |
|--------------|------------------------------------------------|--------------------------------------------------|
| `=`          | Equal to                                        | `Salary = 50000`                                 |
| `<>`, `!=`   | Not equal to                                    | `Salary <> 50000`                               
| `>`          | Greater than                                    | `Salary > 50000`                                 |
| `>=`         | Greater than or equal to                        | `Salary >= 50000`                                |
| `<`          | Less than                                       | `Salary < 50000`                                 |
| `<=`         | Less than or equal to                           | `Salary <= 50000`                                |
| `AND`        | Both conditions must be true                    | `Salary > 50000 AND Department = 'Sales'`        |
| `OR`         | At least one condition must be true             | `Salary > 50000 OR Department = 'Sales'`         |
| `NOT`        | Reverse the result of a condition               | `NOT Department = 'IT'`                          |
| `IN`         | Value must match one in a list of values        | `Department IN ('Sales', 'HR')`                  |
| `NOT IN`     | Value must not match any in a list of values    | `Department NOT IN ('IT', 'HR')`                 |
| `BETWEEN`    | Value must be within a specified range          | `Salary BETWEEN 45000 AND 55000`                 |

---

This detailed guide provides explanations and examples of the most commonly used SQL operators. Each operator is explained with practical examples and outputs for a clear understanding of their functionality.

---
- by Aditya Kumar