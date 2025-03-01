# Data Types in SQL

Understanding data types in SQL is crucial for efficient data storage and retrieval. Here's a breakdown of commonly used SQL data types along with their syntax, examples, and differences.

### Table of Contents
- [1. Decimal](#1-decimal)
- [2. Float](#2-float)
- [3. Double](#3-double)
- [4. Char](#4-char)
- [5. Varchar](#5-varchar)
- [6. Difference Between Char and Varchar](#6-difference-between-char-and-varchar)
- [7. Integer (int)](#7-integer-int)

---

## 1. Decimal
- **Type**: Fixed precision and scale numbers.
- **Syntax**: `DECIMAL(p, s)`
    - `p`: Precision (total number of digits)
    - `s`: Scale (number of digits to the right of the decimal point)

### Example:

```sql
CREATE TABLE Products (
    ProductID INT,
    Price DECIMAL(10, 2)
);

INSERT INTO Products (ProductID, Price)
VALUES (1, 123.45), (2, 98765.43);
```

| ProductID | Price   |
|-----------|---------|
| 1         | 123.45  |
| 2         | 98765.43|

---

## 2. Float
- **Type**: Approximate numerical data type used for floating-point numbers.
- **Syntax**: `FLOAT(n)`
    - `n`: Number of bits used to store the mantissa (precision).
  
### Example:

```sql
CREATE TABLE Measurements (
    MeasurementID INT,
    Temperature FLOAT(7)
);

INSERT INTO Measurements (MeasurementID, Temperature)
VALUES (1, 36.6), (2, 98.6);
```

| MeasurementID | Temperature |
|---------------|-------------|
| 1             | 36.6        |
| 2             | 98.6        |

---

## 3. Double
- **Type**: Similar to `FLOAT`, but with double precision (larger range and more accuracy).
- **Syntax**: `DOUBLE`
  
### Example:

```sql
CREATE TABLE Astronomy (
    PlanetID INT,
    DistanceFromSun DOUBLE
);

INSERT INTO Astronomy (PlanetID, DistanceFromSun)
VALUES (1, 149597870.7), (2, 778547200.4);
```

| PlanetID | DistanceFromSun  |
|----------|------------------|
| 1        | 149597870.7      |
| 2        | 778547200.4      |

---

## 4. Char
- **Type**: Fixed-length character string.
- **Syntax**: `CHAR(n)`
    - `n`: Specifies the length of the string (max 255).
  
### Example:

```sql
CREATE TABLE Employees (
    EmployeeID INT,
    Gender CHAR(1)
);

INSERT INTO Employees (EmployeeID, Gender)
VALUES (1, 'M'), (2, 'F');
```

| EmployeeID | Gender |
|------------|--------|
| 1          | M      |
| 2          | F      |

---

## 5. Varchar
- **Type**: Variable-length character string.
- **Syntax**: `VARCHAR(n)`
    - `n`: Maximum length of the string (up to 65535 characters).
  
### Example:

```sql
CREATE TABLE Customers (
    CustomerID INT,
    CustomerName VARCHAR(50)
);

INSERT INTO Customers (CustomerID, CustomerName)
VALUES (1, 'John Doe'), (2, 'Jane Smith');
```

| CustomerID | CustomerName  |
|------------|---------------|
| 1          | John Doe      |
| 2          | Jane Smith    |

---

## 6. Difference Between Char and Varchar

- `CHAR`: Fixed length.
  - If the defined length is 10, but the input is only 4 characters, it will pad the remaining characters with spaces.
- `VARCHAR`: Variable length.
  - Only uses as much storage as the actual length of the input string.

### Comparison Table:

| Data Type | Storage         | Example Input | Stored As            |
|-----------|-----------------|---------------|----------------------|
| `CHAR(10)`| Fixed, 10 bytes | 'Hello'       | 'Hello     ' (padded)|
| `VARCHAR(10)`| Dynamic, 5 bytes | 'Hello'  | 'Hello' (no padding) |

---

## 7. Integer (int)
- **Type**: Whole number.
- **Syntax**: `INT`
  
### Example:

```sql
CREATE TABLE Orders (
    OrderID INT,
    Quantity INT
);

INSERT INTO Orders (OrderID, Quantity)
VALUES (1, 100), (2, 50);
```

| OrderID | Quantity |
|---------|----------|
| 1       | 100      |
| 2       | 50       |

---

## Summary Table of Data Types

| Data Type | Description                         | Syntax                | Example       |
|-----------|-------------------------------------|-----------------------|---------------|
| Decimal   | Fixed precision numbers             | `DECIMAL(p, s)`       | 123.45        |
| Float     | Approximate numbers (floating point)| `FLOAT(n)`            | 36.6          |
| Double    | Double precision floating point     | `DOUBLE`              | 149597870.7   |
| Char      | Fixed-length character string       | `CHAR(n)`             | 'M'           |
| Varchar   | Variable-length character string    | `VARCHAR(n)`          | 'John Doe'    |
| Int       | Whole numbers                      | `INT`                 | 100           |

--- 

- by Aditya Kumar