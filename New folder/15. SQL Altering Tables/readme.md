# SQL: Altering Tables

In this guide, we will cover how to make changes to an existing table using the `ALTER TABLE` statement. Topics include:
- Adding or removing columns
- Renaming columns
- Renaming a table
- Modifying column properties (changing datatype, default values, setting `NOT NULL`)
- Adding or dropping constraints
- Checking existing constraints

### Random Table: `Employee`

We will use the following `Employee` table for all examples:

| EmployeeID | Name     | Department | Salary | MobileNumber |
|------------|----------|------------|--------|--------------|
| 1          | John     | IT         | 60000  | 9876543210   |
| 2          | Sarah    | HR         | 55000  | 9123456789   |
| 3          | Mike     | IT         | 70000  | 9876543211   |

---

## 1. Adding or Removing a Column

### Basic Syntax: Adding a Column
```sql
ALTER TABLE table_name
ADD column_name datatype;
```

### Example: Adding an `Email` Column
We want to add an `Email` column to the `Employee` table.

#### Query:
```sql
ALTER TABLE Employee
ADD Email VARCHAR(100);
```

#### Output: Updated Table

| EmployeeID | Name     | Department | Salary | MobileNumber | Email      |
|------------|----------|------------|--------|--------------|------------|
| 1          | John     | IT         | 60000  | 9876543210   | NULL       |
| 2          | Sarah    | HR         | 55000  | 9123456789   | NULL       |
| 3          | Mike     | IT         | 70000  | 9876543211   | NULL       |

### Basic Syntax: Removing a Column
```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

### Example: Removing the `MobileNumber` Column
We want to remove the `MobileNumber` column from the `Employee` table.

#### Query:
```sql
ALTER TABLE Employee
DROP COLUMN MobileNumber;
```

#### Output: Updated Table

| EmployeeID | Name     | Department | Salary | Email      |
|------------|----------|------------|--------|------------|
| 1          | John     | IT         | 60000  | NULL       |
| 2          | Sarah    | HR         | 55000  | NULL       |
| 3          | Mike     | IT         | 70000  | NULL       |

---

## 2. Renaming a Column

### Basic Syntax:
```sql
ALTER TABLE table_name
RENAME COLUMN old_column_name TO new_column_name;
```

### Example: Renaming `Name` to `FullName`
We want to rename the `Name` column to `FullName`.

#### Query:
```sql
ALTER TABLE Employee
RENAME COLUMN Name TO FullName;
```

#### Output: Updated Table

| EmployeeID | FullName | Department | Salary | Email      |
|------------|----------|------------|--------|------------|
| 1          | John     | IT         | 60000  | NULL       |
| 2          | Sarah    | HR         | 55000  | NULL       |
| 3          | Mike     | IT         | 70000  | NULL       |

---

## 3. Renaming a Table

### Basic Syntax:
```sql
ALTER TABLE old_table_name
RENAME TO new_table_name;
```

### Example: Renaming `Employee` Table to `Staff`
We want to rename the `Employee` table to `Staff`.

#### Query:
```sql
ALTER TABLE Employee
RENAME TO Staff;
```

#### Output: Updated Table Name
The table is now called `Staff`, and the structure remains the same.

| EmployeeID | FullName | Department | Salary | Email      |
|------------|----------|------------|--------|------------|
| 1          | John     | IT         | 60000  | NULL       |
| 2          | Sarah    | HR         | 55000  | NULL       |
| 3          | Mike     | IT         | 70000  | NULL       |

---

## 4. Modifying Column Properties

### 4.1 Changing Data Type

### Basic Syntax:
```sql
ALTER TABLE table_name
MODIFY column_name new_datatype;
```

### Example: Changing `Salary` Data Type from `INT` to `DECIMAL`
We want to change the `Salary` column from `INT` to `DECIMAL` to allow for more precise values.

#### Query:
```sql
ALTER TABLE Staff
MODIFY Salary DECIMAL(10, 2);
```

#### Explanation:
- `DECIMAL(10, 2)` allows the `Salary` to have up to 10 digits, with 2 decimal places for cents.

---

### 4.2 Changing Default Values

### Basic Syntax:
```sql
ALTER TABLE table_name
ALTER COLUMN column_name SET DEFAULT default_value;
```

### Example: Setting Default Value for `Salary`
We want to set the default value of `Salary` to 50000.

#### Query:
```sql
ALTER TABLE Staff
ALTER COLUMN Salary SET DEFAULT 50000;
```

#### Explanation:
Now, if we add a new employee without specifying a `Salary`, the value will default to 50,000.

---

### 4.3 Changing a Column to `NOT NULL`

### Basic Syntax:
```sql
ALTER TABLE table_name
MODIFY column_name datatype NOT NULL;
```

### Example: Setting `Email` as `NOT NULL`
We want to make sure that every employee has an `Email`, so we set the `Email` column as `NOT NULL`.

#### Query:
```sql
ALTER TABLE Staff
MODIFY Email VARCHAR(100) NOT NULL;
```

#### Explanation:
- The column now requires an email for every entry. If we try to insert a row without an email, it will raise an error.

---

## 5. Adding or Dropping Constraints

### 5.1 Adding a `UNIQUE` Constraint

### Basic Syntax:
```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name UNIQUE (column_name);
```

### Example: Ensure `Email` Is Unique
We want to make sure that each employee has a unique email address.

#### Query:
```sql
ALTER TABLE Staff
ADD CONSTRAINT unique_email UNIQUE (Email);
```

#### Explanation:
This ensures no two employees can have the same email address. If we try to add an employee with a duplicate email, an error will occur.

---

### 5.2 Dropping a Constraint

### Basic Syntax:
```sql
ALTER TABLE table_name
DROP CONSTRAINT constraint_name;
```

### Example: Dropping the `UNIQUE` Constraint on `Email`
If we want to remove the `UNIQUE` constraint from the `Email` column:

#### Query:
```sql
ALTER TABLE Staff
DROP CONSTRAINT unique_email;
```

#### Explanation:
- The `UNIQUE` constraint on `Email` is removed, so duplicate email addresses are now allowed.

---

## 6. Checking Existing Constraints

### Basic Syntax:
To check the existing constraints on a table, you can query the database's system views. The query will vary depending on the RDBMS (e.g., MySQL, PostgreSQL, SQL Server, etc.).

### Example for MySQL:
```sql
SELECT CONSTRAINT_NAME, CONSTRAINT_TYPE
FROM information_schema.TABLE_CONSTRAINTS
WHERE TABLE_NAME = 'Staff';
```

#### Output Example:
| CONSTRAINT_NAME | CONSTRAINT_TYPE |
|-----------------|-----------------|
| PRIMARY         | PRIMARY KEY      |
| unique_email    | UNIQUE           |

#### Explanation:
- This query lists all constraints on the `Staff` table, including the primary key and any unique or foreign key constraints.

---

## Conclusion

This guide covered the following `ALTER TABLE` operations:
- **Add or Remove Columns**: Use `ADD` or `DROP` to modify the structure of your table.
- **Rename Columns or Tables**: Use `RENAME COLUMN` and `RENAME TO` to change the names of columns and tables.
- **Modify Column Properties**: Change data types, set default values, or enforce `NOT NULL` constraints.
- **Add or Drop Constraints**: Enforce or remove uniqueness or other constraints on specific columns.
- **Check Existing Constraints**: Use system queries to view all the constraints applied to your table.

These commands are essential for maintaining and evolving the structure of your database tables while ensuring data integrity.

---

- by Aditya Kumar