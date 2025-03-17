![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)


# SQL Cheat Sheet: Keywords & Their Usage

---

## SQL Fundamentals
- **Keywords:** SELECT, FROM, WHERE, GROUP BY, ORDER BY, HAVING, JOIN, INSERT, UPDATE, DELETE, CREATE, ALTER, DROP, TRUNCATE, DISTINCT, LIMIT, UNION, UNION ALL
- **Data Types:** INT, VARCHAR, DATE, FLOAT, BOOLEAN, TEXT, BLOB, ENUM, DECIMAL, TIME, TIMESTAMP
- **Operators:** =, <>, >, <, >=, <=, LIKE, IN, BETWEEN, AND, OR, NOT, EXISTS, ANY, ALL

---
## Data Definition Language (DDL)
DDL is used to define and modify database structures.

| Command   | Works With | Purpose |
|-----------|-----------|---------|
| CREATE    | TABLE, DATABASE, INDEX, VIEW | Creates new database objects |
| ALTER     | TABLE, COLUMN, DATABASE | Modifies existing table structure |
| DROP      | TABLE, DATABASE, INDEX, VIEW | Deletes database objects |
| TRUNCATE  | TABLE | Removes all records from a table without logging individual row deletions |

---
## Data Manipulation Language (DML)
DML is used to manage data within database objects.

| Command   | Works With | Purpose |
|-----------|-----------|---------|
| SELECT    | FROM, WHERE, GROUP BY, ORDER BY, HAVING, JOIN, LIMIT, DISTINCT | Retrieves data from tables |
| INSERT    | INTO, VALUES, SELECT | Adds new records to a table |
| UPDATE    | SET, WHERE | Modifies existing records |
| DELETE    | FROM, WHERE | Removes records from a table |

---
## SELECT Query Enhancements

| Keyword       | Works With | Purpose |
|--------------|------------|---------|
| FROM         | TABLE | Specifies the table to retrieve data from |
| WHERE        | SELECT, UPDATE, DELETE | Filters records based on a condition |
| GROUP BY     | SELECT, HAVING | Aggregates records with similar values |
| ORDER BY     | SELECT | Sorts query results |
| HAVING       | GROUP BY | Filters aggregated data |
| JOIN         | SELECT, FROM | Combines rows from multiple tables |
| DISTINCT     | SELECT | Removes duplicate records from results |
| LIMIT        | SELECT | Restricts the number of returned records |
| UNION        | SELECT | Combines the results of two queries and removes duplicates |
| UNION ALL    | SELECT | Combines the results of two queries without removing duplicates |

---
## SQL Joins
Joins combine rows from two or more tables based on a related column.

| Join Type | Works With | Purpose |
|-----------|-----------|---------|
| INNER JOIN | SELECT, FROM | Returns records with matching values in both tables |
| LEFT JOIN  | SELECT, FROM | Returns all records from the left table and matched records from the right |
| RIGHT JOIN | SELECT, FROM | Returns all records from the right table and matched records from the left |
| FULL JOIN  | SELECT, FROM | Returns all records when there is a match in either table |
| CROSS JOIN | SELECT, FROM | Returns the Cartesian product of two tables |
| SELF JOIN  | SELECT, FROM | Joins a table with itself |

---
## SQL Constraints
Constraints ensure data integrity within tables.

| Constraint | Works With | Purpose |
|------------|------------|---------|
| PRIMARY KEY | CREATE, ALTER | Ensures each row has a unique identifier |
| FOREIGN KEY | CREATE, ALTER | Links tables together |
| UNIQUE      | CREATE, ALTER | Ensures all values in a column are unique |
| CHECK       | CREATE, ALTER | Enforces a condition on values in a column |
| DEFAULT     | CREATE, ALTER | Sets a default value for a column |
| NOT NULL    | CREATE, ALTER | Ensures a column cannot have NULL values |
| AUTO_INCREMENT | CREATE, ALTER | Automatically generates a unique number for new rows |

---
## SQL Aggregate Functions
Aggregate functions perform calculations on multiple rows of data.

| Function | Works With | Purpose |
|----------|-----------|---------|
| COUNT()  | SELECT | Returns the number of rows matching criteria |
| SUM()    | SELECT | Adds up all values in a column |
| AVG()    | SELECT | Calculates the average of values in a column |
| MIN()    | SELECT | Returns the smallest value in a column |
| MAX()    | SELECT | Returns the largest value in a column |
| GROUP_CONCAT() | SELECT, GROUP BY | Concatenates values into a single string |

---
## SQL Subqueries & Set Operators

| Feature | Works With | Purpose |
|---------|-----------|---------|
| Subquery | SELECT, INSERT, UPDATE, DELETE | A query within another query |
| EXISTS | WHERE | Checks if a subquery returns any results |
| ANY | WHERE | Compares a value to any in a subquery result set |
| ALL | WHERE | Compares a value to all values in a subquery result set |
| INTERSECT | SELECT | Returns common records between two queries |
| EXCEPT | SELECT | Returns records from the first query that are not in the second |

---
## SQL Transactions & Indexing

| Feature | Works With | Purpose |
|---------|-----------|---------|
| TRANSACTION | BEGIN, COMMIT, ROLLBACK | Groups multiple SQL commands into a single unit |
| COMMIT | TRANSACTION | Saves all changes made in the transaction |
| ROLLBACK | TRANSACTION | Reverts all changes made in the transaction |
| SAVEPOINT | TRANSACTION | Creates a save point within a transaction |
| INDEX | CREATE, DROP | Improves the performance of queries |
| CLUSTERED INDEX | TABLE | Determines the physical order of data in a table |
| NON-CLUSTERED INDEX | TABLE | Creates a logical order of data using pointers |

---

This cheat sheet provides a detailed guide to SQL keywords and their relationships, helping with quick reference and learning!

---
![Static Badge](https://img.shields.io/badge/Aditya%20Kumar-black?style=for-the-badge&logo=atlasos&logoColor=%23ffffff)