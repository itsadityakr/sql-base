## ```DATABASE``` Commands

---


1. What is the difference between a database and a table in MySQL?  
2. Why do we need to use the `USE database_name;` command before executing queries?  
3. What happens if you try to `USE` a database that does not exist?  
4. Can you create two databases with the same name in MySQL? Why or why not?  
5. What is the default storage engine for MySQL databases? How does it affect database operations?  
6. What will happen if you execute `DROP DATABASE` without selecting a database first?  
7. How can you check if a database exists before creating or deleting it? (Hint: Use `SHOW DATABASES` or `INFORMATION_SCHEMA`)  
8. What will happen if you attempt to create a database that already exists? How can you prevent this? (Hint: `CREATE DATABASE IF NOT EXISTS`)  
9. What is the effect of using `DROP DATABASE` on active connections to that database?  
10. Can you rename a database in MySQL? If not, what is the workaround?  
11. If a user has limited privileges, can they execute `SHOW DATABASES;`? How can you restrict access to viewing all databases?  
12. What are the differences between `SHOW DATABASES` and querying the `INFORMATION_SCHEMA`?  
13. How would you backup a database before dropping it? (Hint: `mysqldump` command)  
14. Can a database be restored after being dropped? If yes, how? If no, why?  
15. How can you list only the databases created by a specific user? (Hint: Check `INFORMATION_SCHEMA.SCHEMATA`)  

---

## DataTypes

  
1. What is the difference between `CHAR` and `VARCHAR`? When would you use one over the other?  
2. Why is `DECIMAL` preferred over `FLOAT` or `DOUBLE` for financial calculations?  
3. What happens when you insert a string longer than the defined `VARCHAR(n)` size?  
4. What are the limitations of `TEXT` and `BLOB` data types compared to `VARCHAR`?  
5. How does `DATETIME` differ from `TIMESTAMP` in MySQL?   
6. If you define a column as `DECIMAL(5,2)`, what will happen if you insert `123.456`?  
7. What happens if you try to store Unicode characters in a `CHAR` or `VARCHAR` column without specifying `utf8mb4` encoding?  
8. Can a `TEXT` or `BLOB` column be indexed? What are the limitations?  
9. What will happen if you try to store a `NULL` value in a `NOT NULL` column? How can you prevent this?  
10. What is the difference between `BIGINT` and `UUID` for storing unique identifiers? Which one would you choose and why?  
11. How can you store JSON data in MySQL, and what are the advantages and disadvantages of using the `JSON` data type?  
12. Why is `TIMESTAMP` generally more efficient than `DATETIME`? In what cases would you still prefer `DATETIME`?  

---

## Operators  

1. How does `DIV` differ from `/` in MySQL, and when should you use one over the other?  
2. What is the difference between `!=`, `<>`, and `<=>` in MySQL? In what scenario is `<=>` particularly useful?  
3. How does operator precedence impact the evaluation of the following query?  
   ```sql
   SELECT 10 + 5  2 > 20 OR 15 / 3 = 5 AND NOT (8 MOD 3 = 2);
   ```  
4. Why is using `IS NULL` preferred over `= NULL` when checking for NULL values?  
5. What is the key difference between `AND`, `OR`, and `XOR` operators in MySQL? Provide an example where `XOR` is necessary.  
6. What will be the result of the following bitwise operation in MySQL, and why?  
   ```sql
   SELECT 10 | 5, 10 & 5, 10 ^ 5;
   ```  
7. How does MySQL handle division by zero when using `/`, `DIV`, and `%`?  
8. If a column contains `NULL` values, how does `BETWEEN` behave when filtering records?  
9. Explain how the `LIKE` operator behaves with wildcard characters `_` and `%`. What happens if an escape character is used incorrectly?  
10. Given the following query, will the result be different in MySQL 5.7 and MySQL 8.0? Why?  
   ```sql
   SELECT  FROM employees WHERE first_name LIKE 'A%' AND salary > 50000 ORDER BY salary DESC;
   ```
11. What is the performance impact of using `IN` vs. `EXISTS`? In what cases is `EXISTS` preferred?  
12. Can you create an index on a column used in bitwise operations? How does indexing affect the performance of bitwise filters?  
13. How does MySQL internally process a query that combines arithmetic, logical, and bitwise operators?  
14. In what scenarios can operator misuse lead to full table scans, and how can you optimize such queries?  
15. If an `UPDATE` statement contains multiple assignment operations using `=`, does MySQL execute them sequentially or simultaneously? Provide an example.  

---

## Statements

1. What is the primary purpose of the `SELECT` statement, and how does it differ from `INSERT`?  
2. How does `ORDER BY` work when sorting a column with `NULL` values?  
3. What is the difference between `DELETE` and `TRUNCATE` in SQL?  
4. Why should you always use a `WHERE` clause with `UPDATE` and `DELETE` statements?  
5. Explain the difference between `HAVING` and `WHERE` in SQL queries.  
6. What happens if you try to insert a row into a table with an `AUTO_INCREMENT` primary key and provide a value manually?  
7. What will be the output of the following query if the `employees` table is empty?  
   ```sql
   SELECT  FROM employees WHERE department = 'IT';
   ```  
8. What happens when you try to update a column that doesn’t exist in the table?  
9. How does MySQL handle duplicate rows in an `INSERT` statement when using `INSERT INTO ... VALUES (...)`?  
10. If you execute `DELETE FROM employees;` without a `WHERE` clause, can you recover the data? How?  
11. How does indexing impact the performance of `SELECT`, `UPDATE`, and `DELETE` operations?  
12. What is the impact of using `EXISTS` vs. `IN` when filtering data? Which one is more efficient?  
13. What are the differences between `DELETE`, `TRUNCATE`, and `DROP` in terms of performance and rollback?  
14. How does MySQL optimize queries that use `JOIN` statements along with `WHERE` filters?  
15. How does MySQL internally process an `UPDATE` query when multiple rows are affected?  

---

## Data Definition Language (DDL)  

1. What is the purpose of Data Definition Language (DDL) in SQL?  
2. How does `CREATE TABLE` differ from `CREATE DATABASE` in SQL?  
3. What are the key differences between `DROP`, `TRUNCATE`, and `DELETE`?  
4. Why does `ALTER TABLE` allow modification of table structures but not directly delete data?  
5. What is the significance of constraints like `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, and `CHECK` in DDL?  
6. How does `TRUNCATE` reset an `AUTO_INCREMENT` column, and why is this important?  
7. What is the purpose of `CASCADE` in `DROP TABLE` and `DROP DATABASE` statements?  
8. How does an index improve performance in a database, and when should you create one?  
9. Why should you be cautious when using `DROP DATABASE`?  
10. How does MySQL handle column data type changes using `ALTER TABLE`?  
11. What happens if you execute `DROP TABLE` on a table that does not exist?  
12. Can you undo a `DROP DATABASE` statement? If so, how?  
13. What happens when you `ALTER TABLE` and add a `NOT NULL` constraint to a column that already contains NULL values?  
14. Can a `TRUNCATE` operation be rolled back in MySQL? Why or why not?  
15. What is the effect of renaming a column using `ALTER TABLE` on existing queries and indexes?  
16. What happens when you `DROP INDEX` on a heavily used column?  
17. If you use `ALTER TABLE` to change a column's datatype, what precautions should you take?  
18. How does MySQL handle `DROP DATABASE` when the database contains foreign key constraints?  
19. What is the difference between `TRUNCATE TABLE employees;` and `DELETE FROM employees;` without a `WHERE` clause?  
20. How does MySQL manage memory and storage after executing `DROP TABLE` or `DROP DATABASE`?  
21. How does the `ALTER TABLE` statement affect database performance on large datasets?  
22. What is the role of the `ENGINE` option in `CREATE TABLE`, and how does it impact database performance?  
23. Why is it recommended to use `IF EXISTS` with `DROP TABLE` and `DROP DATABASE`?  
24. How can `PARTITION BY` be used in `CREATE TABLE`, and what are its advantages?  
25. When should you use `RENAME TABLE` instead of `ALTER TABLE ... RENAME COLUMN`?  
26. How does MySQL handle primary key changes using `ALTER TABLE`?  
27. What are the best practices for creating and dropping indexes to optimize query performance?  
28. What are the security risks of granting `DROP` and `ALTER` privileges to a user?  
29. How does `ALTER TABLE` internally process column addition and deletion in InnoDB vs. MyISAM?  
30. What strategies can be used to optimize database performance when altering large tables?  

---

## Data Manipulation Language (DML)  

1. What is the purpose of Data Manipulation Language (DML) in SQL?  
2. How does `SELECT` differ from `INSERT`, `UPDATE`, and `DELETE` in DML?  
3. Why is `WHERE` essential in `UPDATE` and `DELETE` statements? What happens if you omit it?  
4. How does `GROUP BY` work in conjunction with aggregate functions like `COUNT()`, `SUM()`, and `AVG()`?  
5. What is the key difference between `HAVING` and `WHERE` in SQL?  
6. How does `ORDER BY` impact query performance, and what are some optimization techniques?  
7. What are the different types of `JOIN` operations in SQL, and when should each be used?  
8. How does the `LIMIT` clause improve query efficiency when retrieving large datasets?  
9. What is the significance of `AUTO_INCREMENT` when inserting records?  
10. How does `NULL` impact `SELECT`, `INSERT`, `UPDATE`, and `DELETE` operations in SQL?  
11. What happens if you insert a record without specifying values for all columns?  
12. Can you update multiple columns in a single `UPDATE` statement? Provide an example.  
13. What is the difference between `DELETE FROM employees;` and `TRUNCATE TABLE employees;`?  
14. How does `INSERT INTO ... SELECT ...` work, and when is it useful?  
15. What happens if you try to delete a record referenced by a foreign key?  
16. How does MySQL handle duplicate records when using `INSERT INTO`?  
17. How can you retrieve the top 5 highest-paid employees using `ORDER BY` and `LIMIT`?  
18. How does MySQL treat missing values in `GROUP BY` and `HAVING` conditions?  
19. What happens if you attempt to update a primary key value that is referenced in another table?  
20. How can you prevent accidental data loss when executing `DELETE` statements?  
21. How does indexing affect the performance of `SELECT WHERE` queries?  
22. What are the advantages and disadvantages of using `INNER JOIN` vs. `LEFT JOIN`?  
23. How does MySQL handle sorting when using `ORDER BY` on large datasets?  
24. What techniques can be used to optimize `INSERT` performance for bulk data insertion?  
25. How does MySQL optimize queries with multiple `GROUP BY` columns?  
26. What is the impact of `HAVING` on query execution time compared to `WHERE`?  
27. How can you use `EXPLAIN` to analyze and optimize slow `SELECT` queries?  
28. How does `UPDATE` impact transaction logs and rollback operations?  
29. What are the best practices for performing batch updates efficiently in MySQL?  
30. When should you use `DELETE` vs. `ARCHIVE` for data retention strategies?  

---