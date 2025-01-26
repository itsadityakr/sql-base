# MySQL Window Functions

## Introduction

**Window Functions** were introduced in MySQL 8.0 and provide advanced capabilities for querying data. They allow you to perform calculations across a set of table rows related to the current row without collapsing the result set. Window functions operate over a specified range of rows defined by the `OVER()` clause.

### Key Window Functions:
- **SUM()**: Calculates the sum of values.
- **ROW_NUMBER()**: Assigns a unique sequential integer to rows within a partition.
- **RANK()**: Assigns a rank to rows within a partition, with gaps in ranking for ties.
- **DENSE_RANK()**: Similar to `RANK()`, but without gaps in ranking.
- **LAG()**: Provides access to a row at a specified physical offset from the current row.
- **LEAD()**: Provides access to a row at a specified physical offset from the current row, but in the future.

---

## 1. Creating a Table

Let's create a sample table named `employees` for demonstration.

```sql
CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    salary DECIMAL(10, 2),
    dept VARCHAR(50)
);

-- Insert sample data
INSERT INTO employees (name, salary, dept) VALUES
('John', 7000, 'HR'),
('Alice', 8500, 'Finance'),
('Bob', 6000, 'HR'),
('Eve', 7500, 'Finance'),
('Charlie', 9000, 'IT'),
('David', 6500, 'IT');
```

---

## 2. Using Window Functions

### 2.1. SUM() Over()

**Purpose:** Calculate the sum of salaries over a specified order.

#### Syntax:

```sql
SELECT 
    name,
    salary,
    SUM(salary) OVER (ORDER BY salary) AS sum_salary
FROM employees;
```

#### Example Code:

```sql
SELECT 
    name,
    salary,
    SUM(salary) OVER (ORDER BY salary) AS sum_salary
FROM employees;
```

#### Visualization:

| name    | salary | sum_salary |
|---------|--------|------------|
| Bob     | 6000   | 6000       |
| David   | 6500   | 12500      |
| John    | 7000   | 19500      |
| Eve     | 7500   | 27000      |
| Alice   | 8500   | 35500      |
| Charlie | 9000   | 44500      |

---

### 2.2. PARTITION BY

**Purpose:** Calculate the sum of salaries within each department.

#### Syntax:

```sql
SELECT 
    name,
    salary,
    dept,
    SUM(salary) OVER (PARTITION BY dept ORDER BY salary) AS dept_sum_salary
FROM employees;
```

#### Example Code:

```sql
SELECT 
    name,
    salary,
    dept,
    SUM(salary) OVER (PARTITION BY dept ORDER BY salary) AS dept_sum_salary
FROM employees;
```

#### Visualization:

| name    | salary | dept    | dept_sum_salary |
|---------|--------|---------|-----------------|
| Bob     | 6000   | HR      | 6000            |
| John    | 7000   | HR      | 13000           |
| Alice   | 8500   | Finance | 8500            |
| Eve     | 7500   | Finance | 16000           |
| Charlie | 9000   | IT      | 9000            |
| David   | 6500   | IT      | 15500           |

---

### 2.3. ROW_NUMBER()

**Purpose:** Assign a unique sequential integer to rows within a partition.

#### Syntax:

```sql
SELECT 
    name,
    salary,
    dept,
    ROW_NUMBER() OVER (PARTITION BY dept ORDER BY salary DESC) AS row_num
FROM employees;
```

#### Example Code:

```sql
SELECT 
    name,
    salary,
    dept,
    ROW_NUMBER() OVER (PARTITION BY dept ORDER BY salary DESC) AS row_num
FROM employees;
```

#### Visualization:

| name    | salary | dept    | row_num |
|---------|--------|---------|---------|
| John    | 7000   | HR      | 1       |
| Bob     | 6000   | HR      | 2       |
| Alice   | 8500   | Finance | 1       |
| Eve     | 7500   | Finance | 2       |
| Charlie | 9000   | IT      | 1       |
| David   | 6500   | IT      | 2       |

---

### 2.4. RANK()

**Purpose:** Assign a rank to each row within a partition, with gaps for ties.

#### Syntax:

```sql
SELECT 
    name,
    salary,
    dept,
    RANK() OVER (PARTITION BY dept ORDER BY salary DESC) AS rank
FROM employees;
```

#### Example Code:

```sql
SELECT 
    name,
    salary,
    dept,
    RANK() OVER (PARTITION BY dept ORDER BY salary DESC) AS rank
FROM employees;
```

#### Visualization:

| name    | salary | dept    | rank |
|---------|--------|---------|------|
| John    | 7000   | HR      | 1    |
| Bob     | 6000   | HR      | 2    |
| Alice   | 8500   | Finance | 1    |
| Eve     | 7500   | Finance | 2    |
| Charlie | 9000   | IT      | 1    |
| David   | 6500   | IT      | 2    |

---

### 2.5. DENSE_RANK()

**Purpose:** Assign a rank to each row within a partition, without gaps for ties.

#### Syntax:

```sql
SELECT 
    name,
    salary,
    dept,
    DENSE_RANK() OVER (PARTITION BY dept ORDER BY salary DESC) AS dense_rank
FROM employees;
```

#### Example Code:

```sql
SELECT 
    name,
    salary,
    dept,
    DENSE_RANK() OVER (PARTITION BY dept ORDER BY salary DESC) AS dense_rank
FROM employees;
```

#### Visualization:

| name    | salary | dept    | dense_rank |
|---------|--------|---------|------------|
| John    | 7000   | HR      | 1          |
| Bob     | 6000   | HR      | 2          |
| Alice   | 8500   | Finance | 1          |
| Eve     | 7500   | Finance | 2          |
| Charlie | 9000   | IT      | 1          |
| David   | 6500   | IT      | 2          |

---

### 2.6. LAG()

**Purpose:** Access data from a previous row in the result set.

#### Syntax:

```sql
SELECT 
    name,
    salary,
    LAG(salary, 1) OVER (ORDER BY salary) AS prev_salary
FROM employees;
```

#### Example Code:

```sql
SELECT 
    name,
    salary,
    LAG(salary, 1) OVER (ORDER BY salary) AS prev_salary
FROM employees;
```

#### Visualization:

| name    | salary | prev_salary |
|---------|--------|-------------|
| Bob     | 6000   | NULL        |
| David   | 6500   | 6000        |
| John    | 7000   | 6500        |
| Eve     | 7500   | 7000        |
| Alice   | 8500   | 7500        |
| Charlie | 9000   | 8500        |

---

### 2.7. LEAD()

**Purpose:** Access data from a subsequent row in the result set.

#### Syntax:

```sql
SELECT 
    name,
    salary,
    LEAD(salary, 1) OVER (ORDER BY salary) AS next_salary
FROM employees;
```

#### Example Code:

```sql
SELECT 
    name,
    salary,
    LEAD(salary, 1) OVER (ORDER BY salary) AS next_salary
FROM employees;
```

#### Visualization:

| name    | salary | next_salary |
|---------|--------|-------------|
| Bob     | 6000   | 6500        |
| David   | 6500   | 7000        |
| John    | 7000   | 7500        |
| Eve     | 7500   | 8500        |
| Alice   | 8500   | 9000        |
| Charlie | 9000   | NULL        |

---

## Summary

- **Window Functions**: Enhance query capabilities by operating on a defined set of rows related to the current row.
- **Functions**: `SUM()`, `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `LAG()`, and `LEAD()` each provide different insights into data.

This guide should help you understand and utilize window functions effectively in MySQL 8.0. Feel free to incorporate this into your GitHub repository for comprehensive database management!

---

- by Aditya Kumar