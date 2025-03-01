# SQL Concepts CASE, IS NULL, NOT LIKE

This guide covers basic SQL topics with examples and outputs:
- CASE Statements
- IS NULL
- NOT LIKE

### Random Table: `Employee`

| EmployeeID | Name     | Department | Salary | YearsOfExperience | Status   |
|------------|----------|------------|--------|-------------------|----------|
| 1          | John     | IT         | 60000  | 5                 | Active   |
| 2          | Sarah    | HR         | 55000  | 8                 | Active   |
| 3          | Mike     | IT         | 70000  | 10                | Active   |
| 4          | Lucy     | Finance    | 50000  | 3                 | Resigned |
| 5          | James    | Marketing  | 60000  | 5                 | Active   |
| 6          | Karen    | Finance    | NULL   | 12                | Retired  |

---

## 1. CASE Statement

### Basic Syntax:
```sql
SELECT column1,
    CASE
        WHEN condition1 THEN result1
        WHEN condition2 THEN result2
        ELSE result3
    END AS new_column_name
FROM table_name;
```

### Explanation:
The `CASE` statement allows you to implement conditional logic in SQL, similar to "if-else" statements in programming languages. You use it to test conditions and return a result based on whether those conditions are true or false.

- **WHEN**: Specifies the condition to be checked.
- **THEN**: Specifies what to return if the condition is true.
- **ELSE**: Specifies what to return if none of the conditions are true (optional).
- **END**: Closes the `CASE` block.

### Example: Salary Categorization
We will categorize employees' salaries as either **Low**, **Medium**, or **High**.

#### Query:
```sql
SELECT Name, Salary,
    CASE
        WHEN Salary < 55000 THEN 'Low'
        WHEN Salary BETWEEN 55000 AND 65000 THEN 'Medium'
        ELSE 'High'
    END AS SalaryCategory
FROM Employee;
```

#### Output:

| Name  | Salary | SalaryCategory |
|-------|--------|----------------|
| John  | 60000  | Medium         |
| Sarah | 55000  | Medium         |
| Mike  | 70000  | High           |
| Lucy  | 50000  | Low            |
| James | 60000  | Medium         |
| Karen | NULL   | High           |

### Explanation:
- **WHEN Salary < 55000 THEN 'Low'**: If the salary is below 55,000, it’s categorized as 'Low'.
- **WHEN Salary BETWEEN 55000 AND 65000 THEN 'Medium'**: Salaries between 55,000 and 65,000 are labeled 'Medium'.
- **ELSE 'High'**: Any salary greater than 65,000 is categorized as 'High'.
- **NULL** values like Karen’s are handled implicitly as they don’t break the `CASE` logic unless explicitly dealt with.

---

## 2. IS NULL

### Basic Syntax:
```sql
SELECT column1, column2
FROM table_name
WHERE column_name IS NULL;
```

### Explanation:
`IS NULL` is used to check whether a value in a column is `NULL` (i.e., missing or undefined). A `NULL` value is different from an empty string or a zero—it represents the absence of any value.

### Example: Find Employees with Undefined Salaries
We want to find all employees whose salaries have not been defined (i.e., they are `NULL`).

#### Query:
```sql
SELECT Name, Salary
FROM Employee
WHERE Salary IS NULL;
```

#### Output:

| Name  | Salary |
|-------|--------|
| Karen | NULL   |

### Explanation:
- **WHERE Salary IS NULL**: This condition checks for rows where the `Salary` field is `NULL`. In this example, Karen is the only employee with no salary information.

---

## 3. NOT LIKE

### Basic Syntax:
```sql
SELECT column1
FROM table_name
WHERE column_name NOT LIKE pattern;
```

### Explanation:
`NOT LIKE` is used to filter out rows where a column does not match a given pattern. The two main wildcard symbols used in pattern matching are:
- **%**: Matches zero or more characters.
- **_**: Matches exactly one character.

### Example: Exclude Names Starting with "J"
We want to find all employees whose names do **not** start with the letter "J".

#### Query:
```sql
SELECT Name
FROM Employee
WHERE Name NOT LIKE 'J%';
```

#### Output:

| Name  |
|-------|
| Sarah |
| Mike  |
| Lucy  |
| Karen |

### Explanation:
- **NOT LIKE 'J%'**: This condition excludes any names starting with the letter "J". The `%` wildcard allows for any number of characters to follow the "J", but we’re excluding these rows. 
- Only employees with names that do not start with "J" are returned: Sarah, Mike, Lucy, and Karen.

---

## Summary of Concepts:

- **CASE**: Allows conditional logic in queries. You can add multiple conditions to return specific results.
- **IS NULL**: Used to check for missing values in a column. 
- **NOT LIKE**: Excludes rows that match a specific pattern, often used for filtering strings.

These concepts are foundational for manipulating and querying data effectively in SQL. Each helps solve different types of problems, from conditional logic to handling missing data and pattern matching.

---

- by Aditya Kumar