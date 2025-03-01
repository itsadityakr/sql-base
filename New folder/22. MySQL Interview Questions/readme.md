# MySQL Interview Questions

**Last Updated: 22 Jul 2024**

MySQL is a free, open-source Relational Database Management System (RDBMS) that stores data in a structured tabular format using rows and columns. It uses Structured Query Language (SQL) for accessing, managing, and manipulating databases. Originally developed by MySQL AB, a Swedish company, it is now owned by Oracle Corporation. Known for its high performance, reliability, and ease of use, MySQL is one of the most popular databases worldwide.

In this guide, we cover 50+ MySQL interview questions with answers, typically asked in interviews for Data Analyst/SQL Developer roles at MAANG and other high-paying companies. Whether you're a fresher or an experienced professional, this guide will help you prepare for your next interview.

## Table of Contents

- [MySQL Interview Questions and Answers for Freshers](#mysql-interview-questions-and-answers-for-freshers)
- [Intermediate MySQL Interview Questions and Answers](#intermediate-mysql-interview-questions-and-answers)
- [Advanced MySQL Interview Questions for Experienced](#advanced-mysql-interview-questions-for-experienced)

---

## MySQL Interview Questions and Answers for Freshers

1. **What is MySQL and How does it differ from other relational databases?**
   MySQL is an open-source RDBMS used for managing structured data with SQL. It is known for its reliability, scalability, and performance.

2. **How to create a database in MySQL?**
   ```sql
   CREATE DATABASE mydatabase;
   ```

3. **Difference between CHAR and VARCHAR data types.**
   - **CHAR:** Fixed-length; padded with spaces.
   - **VARCHAR:** Variable-length; no padding.

4. **Explain the differences between SQL and MySQL?**
   - **SQL:** Language for managing RDBMS.
   - **MySQL:** RDBMS that uses SQL.

5. **What is the MySQL server’s default port?**
   The default port is **3306**.

6. **How can we learn batch mode in MySQL?**
   ```bash
   mysql <batch-file>;
   ```

7. **How many different tables are present in MySQL?**
   There are five types:
   - Heap
   - Merge
   - MyISAM
   - InnoDB
   - ISAM

8. **What are the differences between CHAR and VARCHAR data types in MySQL?**
   - **CHAR:** Fixed length, faster, max 255 characters.
   - **VARCHAR:** Variable length, max 4000 characters.

9. **What is the Difference between CHAR_LENGTH and LENGTH?**
   - **CHAR_LENGTH:** Counts characters.
   - **LENGTH:** Counts bytes.

10. **What do you understand by % and _ in the LIKE statement?**
    - **'%':** Matches zero or more characters.
    - **'_':** Matches exactly one character.

11. **How many index columns can be created in a table?**
    Up to **16** indexed columns.

12. **What are string types available for columns?**
    - SET
    - BLOB
    - TEXT
    - ENUM
    - CHAR
    - VARCHAR

13. **Explain the main difference between FLOAT and DOUBLE.**
    - **FLOAT:** 4 bytes, 8 digits of precision.
    - **DOUBLE:** 8 bytes, 18 digits of precision.

14. **Explain the differences between BLOB and TEXT.**
    - **BLOB:** Binary large object, case-sensitive sorting.
    - **TEXT:** Case-insensitive sorting.

15. **Explain the difference between HAVING and WHERE clause in MySQL.**
    - **WHERE:** Filters rows before grouping.
    - **HAVING:** Filters groups after grouping.

16. **Explain REGEXP?**
    REGEXP is used for pattern matching within a string.

17. **How can we add a column in MySQL?**
    ```sql
    ALTER TABLE tab_name ADD COLUMN col_name col_definition [FIRST|AFTER exist_col];
    ```

18. **How to delete columns in MySQL?**
    ```sql
    ALTER TABLE table_name DROP COLUMN column1, column2…;
    ```

19. **How to delete a table in MySQL?**
    ```sql
    DROP TABLE table-name;
    ```

20. **How are `mysql_fetch_array()` and `mysql_fetch_object()` different from each another?**
    - **mysql_fetch_array():** Fetches a row as an array.
    - **mysql_fetch_object():** Fetches a row as an object.

21. **How to get the top 10 rows?**
    ```sql
    SELECT * FROM table_name LIMIT 0,10;
    ```

22. **How does NOW() differ from CURRENT_DATE()?**
    - **NOW():** Returns date and time.
    - **CURRENT_DATE():** Returns date only.

23. **What is the use of the ‘DISTINCT’ keyword in MySQL?**
    It removes duplicate records from the result set.

24. **Which storage engines are used in MySQL?**
    - MyISAM
    - InnoDB
    - MEMORY
    - CSV
    - ARCHIVE

25. **How to create a table in MySQL?**
    ```sql
    CREATE TABLE Employee (
        Employee_Name VARCHAR(128),
        Employee_ID VARCHAR(128),
        Employee_Salary VARCHAR(16),
        Designation CHAR(4)
    );
    ```

26. **How to insert data in MySQL table?**
    ```sql
    INSERT INTO table_name (field1, field2, field3) VALUES (value1, value2, value3);
    ```

---

## Intermediate MySQL Interview Questions and Answers

27. **Write a statement to find duplicate rows in a MySQL table.**
    ```sql
    SELECT Table_Name, Category
    FROM Product
    GROUP BY Name, Category
    HAVING COUNT(id) > 1;
    ```

28. **What types of relationships are used in MySQL?**
    - One-to-one
    - One-to-many
    - Many-to-many

29. **How to insert Date in MySQL?**
    ```sql
    INSERT INTO table_name (column_name, column_date) VALUES ('DATE: Manual Date', '2023-05-20');
    ```

30. **What is a join? Tell different join types in MySQL.**
    Joins connect two or more tables:
    - **INNER JOIN**
    - **LEFT JOIN**
    - **RIGHT JOIN**
    - **FULL JOIN**

31. **What is a primary key? How to drop the primary key in MySQL?**
    - **Primary Key:** Uniquely identifies each record.
    - **Drop Primary Key:**
      ```sql
      ALTER TABLE table_name DROP PRIMARY KEY;
      ```

32. **What is a heap table in MySQL?**
    - Used for fast, temporary storage.
    - No BLOB or TEXT fields.

33. **What is the main difference between the primary key and the candidate key?**
    - **Primary Key:** Unique identifier, only one per table.
    - **Candidate Key:** Can be used for foreign key references.

34. **What is the difference between DELETE and TRUNCATE commands in MySQL?**
    - **DELETE:** Removes rows based on condition.
    - **TRUNCATE:** Removes all rows, faster and can't be rolled back.

35. **What is InnoDB?**
    - A storage engine providing ACID transactions, row-level locking, and foreign key support.

36. **What is the difference between UNION and UNION ALL in MySQL?**
    - **UNION:** Removes duplicate rows.
    - **UNION ALL:** Includes duplicates.

37. **What is a ‘timestamp’ in MySQL?**
    - Records the time a row is added or updated.

38. **What is the use of ENUMs in MySQL?**
    - Specifies a set of predefined values.

39. **How can you control the max size of a heap in MySQL?**
    ```sql
    SET max_heap_table_size = M;
    ```

40. **What is a view? How to create a view?**
    - **View:** A virtual table created by combining tables.
    - **Create View:**
      ```sql
      CREATE VIEW view_name AS
      SELECT columns
      FROM tables
      [WHERE conditions];
      ```

41. **Where is the MyISAM table stored and what are its storage formats?**
    - Stored on disk:
      - **.frm:** Table definition
      - **.MYD:** Data
      - **.MYI:** Indexes

42. **How can we save images in MySQL?**
    - Store images as BLOBs.

43. **What are triggers and how many triggers are available in MySQL?**
    - **Triggers:** Procedural code executed in response to events.
    - **Types:** 
      - BEFORE INSERT
      - AFTER INSERT
      - BEFORE UPDATE
      - AFTER UPDATE
      - BEFORE DELETE
      - AFTER DELETE

44. **What are the different characteristics of MySQL MyISAM Static and MyISAM Dynamic?**
    - **Static:** Fixed field width, easier to store.
    - **Dynamic:** Variable field width, more flexible.

---

## Advanced MySQL Interview Questions for Experienced

45. **What are Access Control Lists (ACLs)?**
    - Lists of permissions for objects, cached in memory.

46. **What is Normalization and list the different types of

 normalization?**
    - **Normalization:** Organizing data to avoid redundancy.
    - **Types:**
      - First Normal Form (1NF)
      - Second Normal Form (2NF)
      - Third Normal Form (3NF)

47. **What are various ways to create an index?**
    - Using T-SQL statements
    - SQL Server Management Studio
    - Primary Key and UNIQUE constraints

48. **What are clustered index and non-clustered index?**
    - **Clustered Index:** Orders data based on index.
    - **Non-Clustered Index:** Data is not ordered by index.

49. **How to validate emails using a single query?**
    ```sql
    SELECT Email
    FROM Vehicle
    WHERE NOT REGEXP_LIKE(Email, '[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}', 'i');
    ```

50. **How can you handle the `--secure-file-priv` option in MySQL?**
    - Either move your file to the directory specified by `secure_file_priv` or disable `secure_file_priv`.

---

**Credits:** This guide is inspired by GeeksforGeeks. For more details, visit [GeeksforGeeks - MySQL Interview Questions](https://www.geeksforgeeks.org/mysql-interview-questions/).

---

- by Aditya Kumar