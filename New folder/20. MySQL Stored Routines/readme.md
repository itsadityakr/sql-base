# MySQL Stored Routines

## 1. What is a Stored Procedure in MySQL?

A **Stored Procedure** is a set of SQL statements stored in the database and executed as a single unit. It allows for encapsulation and reuse of SQL code.

### Key Features:
- **Encapsulation**: Groups multiple SQL statements.
- **Reusability**: Can be invoked multiple times.
- **Parameters**: Supports `IN`, `OUT`, and `INOUT` parameters.

---

## 2. Dropping an Existing Stored Procedure

To avoid conflicts when creating a stored procedure, drop it if it already exists.

```sql
DROP PROCEDURE IF EXISTS procedure_name;
```

---

## 3. Using DELIMITER

The `DELIMITER` command changes the statement delimiter to handle complex SQL routines containing multiple semicolons.

### Changing the Delimiter

```sql
DELIMITER //
```

### Restoring the Delimiter

```sql
DELIMITER ;
```

---

## 4. Creating a Stored Procedure

### Syntax:

```sql
-- Drop the procedure if it already exists
DROP PROCEDURE IF EXISTS procedure_name;

-- Change the delimiter to avoid conflicts
DELIMITER //

-- Create the stored procedure
CREATE PROCEDURE procedure_name (IN param1 datatype, OUT param2 datatype)
BEGIN
    -- SQL statements
    SELECT COUNT(*) INTO param2 FROM table_name WHERE column_name = param1;
END //

-- Restore the delimiter
DELIMITER ;
```

### Example: Increase Salary

```sql
-- Drop the procedure if it already exists
DROP PROCEDURE IF EXISTS IncreaseSalary;

-- Change the delimiter to avoid conflicts
DELIMITER $$

-- Create the stored procedure
CREATE PROCEDURE IncreaseSalary(IN emp_id INT, IN percent_increase DECIMAL(5,2))
BEGIN
    UPDATE employees
    SET salary = salary + (salary * percent_increase / 100)
    WHERE id = emp_id;
END $$

-- Restore the delimiter
DELIMITER ;
```

### Calling the Stored Procedure

```sql
CALL IncreaseSalary(1, 10);  -- Increase salary of employee with id 1 by 10%
```

---

## 5. Argument Passing in Stored Procedures

Stored procedures can accept different types of parameters:
- **IN**: Input parameters.
- **OUT**: Output parameters.
- **INOUT**: Both input and output parameters.

### Example with Parameter Passing

```sql
-- Drop the procedure if it already exists
DROP PROCEDURE IF EXISTS UpdateEmployeeSalary;

-- Change the delimiter to avoid conflicts
DELIMITER $$

-- Create the stored procedure
CREATE PROCEDURE UpdateEmployeeSalary(IN emp_id INT, INOUT emp_salary DECIMAL(10,2))
BEGIN
    -- Retrieve current salary
    SELECT salary INTO emp_salary FROM employees WHERE id = emp_id;
    
    -- Update the salary
    UPDATE employees SET salary = salary + emp_salary WHERE id = emp_id;
END $$

-- Restore the delimiter
DELIMITER ;
```

### Calling the Procedure with INOUT Parameter

```sql
SET @emp_salary = 1000;
CALL UpdateEmployeeSalary(1, @emp_salary);
SELECT @emp_salary;  -- This will return the updated salary of employee with ID 1
```

---

## 6. Returning Output in Variables from a Stored Procedure

Stored procedures can return values using `OUT` parameters.

### Example: Get Employee Salary

```sql
-- Drop the procedure if it already exists
DROP PROCEDURE IF EXISTS GetEmployeeSalary;

-- Change the delimiter to avoid conflicts
DELIMITER $$

-- Create the stored procedure
CREATE PROCEDURE GetEmployeeSalary(IN emp_id INT, OUT emp_salary DECIMAL(10,2))
BEGIN
    SELECT salary INTO emp_salary FROM employees WHERE id = emp_id;
END $$

-- Restore the delimiter
DELIMITER ;
```

### Calling the Procedure

```sql
CALL GetEmployeeSalary(1, @salary);
SELECT @salary;  -- This will return the salary of employee with ID 1
```

---

## 7. User-Defined Functions (UDFs) in MySQL

**User-Defined Functions (UDFs)** return a single value and can be used in SQL queries like built-in functions.

### Syntax:

```sql
-- Drop the function if it already exists
DROP FUNCTION IF EXISTS function_name;

-- Change the delimiter to avoid conflicts
DELIMITER $$

-- Create the function
CREATE FUNCTION function_name (param1 datatype, param2 datatype)
RETURNS return_datatype
DETERMINISTIC  -- Guarantees that the function returns the same result for the same input
BEGIN
    -- SQL logic
    RETURN result;
END $$

-- Restore the delimiter
DELIMITER ;
```

### Example: Calculate Bonus

```sql
-- Drop the function if it already exists
DROP FUNCTION IF EXISTS CalculateBonus;

-- Change the delimiter to avoid conflicts
DELIMITER $$

-- Create the function
CREATE FUNCTION CalculateBonus(salary DECIMAL(10,2), bonus_rate DECIMAL(5,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN salary * bonus_rate / 100;
END $$

-- Restore the delimiter
DELIMITER ;
```

### Using the Function

```sql
SELECT name, CalculateBonus(salary, 10) AS bonus
FROM employees;
```

**Output:**

| name    | bonus  |
|---------|--------|
| John    | 5000   |
| Alice   | 4500   |
| Bob     | 6000   |

---

## 8. Keywords and Options in Stored Routines

### DETERMINISTIC

Indicates that a function will always produce the same result for the same input parameters.

```sql
CREATE FUNCTION function_name (param1 datatype)
RETURNS return_datatype
DETERMINISTIC
BEGIN
    -- SQL logic
    RETURN result;
END;
```

### NO SQL

Specifies that the function does not contain SQL statements.

```sql
CREATE FUNCTION function_name (param1 datatype)
RETURNS return_datatype
NO SQL
BEGIN
    -- Function logic
END;
```

### READS SQL DATA

Indicates that the function reads data from the database but does not modify it.

```sql
CREATE FUNCTION function_name (param1 datatype)
RETURNS return_datatype
READS SQL DATA
BEGIN
    -- Function logic that reads data
END;
```

### MODIFIES SQL DATA

Indicates that the function modifies database data.

```sql
CREATE FUNCTION function_name (param1 datatype)
RETURNS return_datatype
MODIFIES SQL DATA
BEGIN
    -- Function logic that modifies data
END;
```

### CONTAINS SQL

Specifies that the function contains SQL statements but does not modify data.

```sql
CREATE FUNCTION function_name (param1 datatype)
RETURNS return_datatype
CONTAINS SQL
BEGIN
    -- Function logic
END;
```

### SQL DATA ACCESS Options

- **NO SQL**: The routine does not contain SQL statements.
- **READS SQL DATA**: The routine reads data but does not modify it.
- **MODIFIES SQL DATA**: The routine modifies data.
- **CONTAINS SQL**: The routine contains SQL statements that are not covered by the other categories.

---

## Summary

- **Stored Procedures**: Encapsulate and reuse SQL logic with parameters (`IN`, `OUT`, `INOUT`).
- **DELIMITER**: Change and restore delimiters for defining procedures and functions.
- **User-Defined Functions (UDFs)**: Return a single value and can be used in SQL queries.
- **Keywords**: Understand `DETERMINISTIC`, `NO SQL`, `READS SQL DATA`, and other options to define the behavior of routines.

---

- by Aditya Kumar