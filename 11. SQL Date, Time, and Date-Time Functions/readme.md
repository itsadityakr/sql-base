# SQL Date, Time, and Date-Time Functions

SQL provides robust support for handling date and time values. This guide covers the various data types for representing dates and times, as well as many powerful functions to manipulate and extract date-time data.

### Table of Contents
- [1. Date Data Types](#1-date-data-types)
  - [DATE](#date)
  - [TIME](#time)
  - [DATETIME](#datetime)
  - [TIMESTAMP](#timestamp)
- [2. Current Date and Time Functions](#2-current-date-and-time-functions)
  - [CURDATE()](#curdate)
  - [CURTIME()](#curtime)
  - [NOW()](#now)
  - [CURRENT_TIMESTAMP()](#current_timestamp)
  - [UTC_TIMESTAMP()](#utc_timestamp)
- [3. Date and Time Extraction Functions](#3-date-and-time-extraction-functions)
  - [DAY()](#day)
  - [MONTH()](#month)
  - [YEAR()](#year)
  - [HOUR()](#hour)
  - [MINUTE()](#minute)
  - [SECOND()](#second)
  - [DAYNAME()](#dayname)
  - [MONTHNAME()](#monthname)
  - [DAYOFWEEK()](#dayofweek)
  - [WEEK()](#week)
  - [QUARTER()](#quarter)
- [4. Date Formatting Functions](#4-date-formatting-functions)
  - [DATE_FORMAT()](#date_format)
  - [TIME_FORMAT()](#time_format)
- [5. Date and Time Math Functions](#5-date-and-time-math-functions)
  - [DATE_ADD()](#date_add)
  - [DATE_SUB()](#date_sub)
  - [DATEDIFF()](#datediff)
  - [TIMEDIFF()](#timediff)
  - [ADDDATE()](#adddate)
  - [SUBDATE()](#subdate)
- [6. More Date and Time Functions](#6-more-date-and-time-functions)
  - [LAST_DAY()](#last_day)
  - [EXTRACT()](#extract)
  - [STR_TO_DATE()](#str_to_date)
  - [FROM_UNIXTIME()](#from_unixtime)
  - [TO_DAYS()](#to_days)
- [7. Using TIMESTAMP with Default and ON UPDATE](#7-using-timestamp-with-default-and-on-update)

---

## 1. Date Data Types

### DATE
- **Type**: Stores only date values in the format `YYYY-MM-DD`.
- **Syntax**: `DATE`
  
#### Example:

```sql
CREATE TABLE Birthdays (
    PersonID INT,
    BirthDate DATE
);

INSERT INTO Birthdays (PersonID, BirthDate)
VALUES (1, '1990-01-01'), (2, '1985-05-15');
```

| PersonID | BirthDate   |
|----------|-------------|
| 1        | 1990-01-01  |
| 2        | 1985-05-15  |

---

### TIME
- **Type**: Stores only time values in the format `HH:MM:SS`.
- **Syntax**: `TIME`
  
#### Example:

```sql
CREATE TABLE OfficeHours (
    EmployeeID INT,
    StartTime TIME,
    EndTime TIME
);

INSERT INTO OfficeHours (EmployeeID, StartTime, EndTime)
VALUES (1, '09:00:00', '17:00:00'), (2, '10:30:00', '18:30:00');
```

| EmployeeID | StartTime | EndTime  |
|------------|-----------|----------|
| 1          | 09:00:00  | 17:00:00 |
| 2          | 10:30:00  | 18:30:00 |

---

### DATETIME
- **Type**: Stores both date and time in `YYYY-MM-DD HH:MM:SS` format.
- **Syntax**: `DATETIME`
  
#### Example:

```sql
CREATE TABLE Meetings (
    MeetingID INT,
    MeetingTime DATETIME
);

INSERT INTO Meetings (MeetingID, MeetingTime)
VALUES (1, '2024-09-17 10:30:00'), (2, '2024-12-01 14:00:00');
```

| MeetingID | MeetingTime        |
|-----------|--------------------|
| 1         | 2024-09-17 10:30:00|
| 2         | 2024-12-01 14:00:00|

---

### TIMESTAMP
- **Type**: Similar to `DATETIME`, but also stores timezone information. Typically used to track changes in rows.
- **Syntax**: `TIMESTAMP`

#### Example:

```sql
CREATE TABLE Audits (
    AuditID INT,
    LastModified TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

INSERT INTO Audits (AuditID)
VALUES (1);
```

| AuditID | LastModified        |
|---------|---------------------|
| 1       | 2024-09-17 15:30:00 |

---

## 2. Current Date and Time Functions

### CURDATE()
- **Description**: Returns the current date.
- **Syntax**: `CURDATE()`

#### Example:

```sql
SELECT CURDATE();
```

| CURDATE()  |
|------------|
| 2024-09-17 |

---

### CURTIME()
- **Description**: Returns the current time.
- **Syntax**: `CURTIME()`

#### Example:

```sql
SELECT CURTIME();
```

| CURTIME() |
|-----------|
| 16:30:45  |

---

### NOW()
- **Description**: Returns the current date and time.
- **Syntax**: `NOW()`

#### Example:

```sql
SELECT NOW();
```

| NOW()                |
|----------------------|
| 2024-09-17 16:30:45  |

---

### CURRENT_TIMESTAMP()
- **Description**: Synonym for `NOW()`. Returns the current date and time.
- **Syntax**: `CURRENT_TIMESTAMP()`

---

### UTC_TIMESTAMP()
- **Description**: Returns the current UTC (Coordinated Universal Time) date and time.
- **Syntax**: `UTC_TIMESTAMP()`

#### Example:

```sql
SELECT UTC_TIMESTAMP();
```

| UTC_TIMESTAMP()       |
|-----------------------|
| 2024-09-17 14:30:45   |

---

## 3. Date and Time Extraction Functions

### DAY()
- **Description**: Extracts the day of the month from a date.
- **Syntax**: `DAY(date)`

#### Example:

```sql
SELECT DAY('2024-09-17');
```

| DAY('2024-09-17') |
|-------------------|
| 17                |

---

### MONTH()
- **Description**: Extracts the month from a date.
- **Syntax**: `MONTH(date)`

#### Example:

```sql
SELECT MONTH('2024-09-17');
```

| MONTH('2024-09-17') |
|---------------------|
| 9                   |

---

### YEAR()
- **Description**: Extracts the year from a date.
- **Syntax**: `YEAR(date)`

#### Example:

```sql
SELECT YEAR('2024-09-17');
```

| YEAR('2024-09-17') |
|--------------------|
| 2024               |

---

### HOUR()
- **Description**: Extracts the hour from a time or datetime.
- **Syntax**: `HOUR(time)`

#### Example:

```sql
SELECT HOUR('16:30:45');
```

| HOUR('16:30:45') |
|------------------|
| 16               |

---

### MINUTE()
- **Description**: Extracts the minute from a time or datetime.
- **Syntax**: `MINUTE(time)`

#### Example:

```sql
SELECT MINUTE('16:30:45');
```

| MINUTE('16:30:45') |
|--------------------|
| 30                 |

---

### SECOND()
- **Description**: Extracts the second from a time or datetime.
- **Syntax**: `SECOND(time)`

#### Example:

```sql
SELECT SECOND('16:30:45');
```

| SECOND('16:30:45') |
|--------------------|
| 45                 |

---

### DAYNAME()
- **Description**: Returns the name of the day of the week for a given date.
- **Syntax**: `DAYNAME(date)`

#### Example:

```sql
SELECT DAYNAME('2024-09-17');
```

| DAYNAME('2024-09-17') |
|-----------------------|
| Tuesday               |

---

### MONTHNAME()
- **Description**: Returns the full name of the month for a given date.
- **Syntax**: `MONTHNAME(date)`

#### Example:

```sql
SELECT MONTHNAME('2024-09-17');
```

| MONTHNAME('2024-09-17') |
|-------------------------|
| September               |

---

### DAYOFWEEK()
- **Description**: Returns the index of the day of the week (1 = Sunday, 7 = Saturday).
- **Syntax**: `DAYOFWEEK(date)`

#### Example:

```

sql
SELECT DAYOFWEEK('2024-09-17');
```

| DAYOFWEEK('2024-09-17') |
|-------------------------|
| 3                       |

---

### WEEK()
- **Description**: Returns the week number of the year for a date.
- **Syntax**: `WEEK(date)`

#### Example:

```sql
SELECT WEEK('2024-09-17');
```

| WEEK('2024-09-17') |
|--------------------|
| 38                 |

---

### QUARTER()
- **Description**: Returns the quarter of the year for a date (1 = January-March, 2 = April-June, etc.).
- **Syntax**: `QUARTER(date)`

#### Example:

```sql
SELECT QUARTER('2024-09-17');
```

| QUARTER('2024-09-17') |
|-----------------------|
| 3                     |

---

## 4. Date Formatting Functions

### DATE_FORMAT()
- **Description**: Formats a date according to the given format string.
- **Syntax**: `DATE_FORMAT(date, format)`
  
#### Example:

```sql
SELECT DATE_FORMAT('2024-09-17', '%W, %M %d, %Y');
```

| DATE_FORMAT()             |
|---------------------------|
| Tuesday, September 17, 2024|

### Common Format Codes:
- `%W` - Full weekday name
- `%M` - Full month name
- `%d` - Day of the month (two digits)
- `%Y` - Year (four digits)

---

### TIME_FORMAT()
- **Description**: Formats a time according to the given format string.
- **Syntax**: `TIME_FORMAT(time, format)`

#### Example:

```sql
SELECT TIME_FORMAT('16:30:45', '%h:%i %p');
```

| TIME_FORMAT()   |
|-----------------|
| 04:30 PM        |

---

## 5. Date and Time Math Functions

### DATE_ADD()
- **Description**: Adds a specified time interval to a date.
- **Syntax**: `DATE_ADD(date, INTERVAL expr unit)`
  
#### Example:

```sql
SELECT DATE_ADD('2024-09-17', INTERVAL 7 DAY);
```

| DATE_ADD()        |
|-------------------|
| 2024-09-24        |

---

### DATE_SUB()
- **Description**: Subtracts a specified time interval from a date.
- **Syntax**: `DATE_SUB(date, INTERVAL expr unit)`

#### Example:

```sql
SELECT DATE_SUB('2024-09-17', INTERVAL 1 MONTH);
```

| DATE_SUB()        |
|-------------------|
| 2024-08-17        |

---

### DATEDIFF()
- **Description**: Returns the difference in days between two dates.
- **Syntax**: `DATEDIFF(date1, date2)`

#### Example:

```sql
SELECT DATEDIFF('2024-12-25', '2024-09-17');
```

| DATEDIFF() |
|------------|
| 99         |

---

### TIMEDIFF()
- **Description**: Returns the difference between two time values.
- **Syntax**: `TIMEDIFF(time1, time2)`

#### Example:

```sql
SELECT TIMEDIFF('15:30:00', '14:00:00');
```

| TIMEDIFF() |
|------------|
| 01:30:00   |

---

### ADDDATE()
- **Description**: Adds days to a date.
- **Syntax**: `ADDDATE(date, days)`

#### Example:

```sql
SELECT ADDDATE('2024-09-17', 10);
```

| ADDDATE()       |
|-----------------|
| 2024-09-27      |

---

### SUBDATE()
- **Description**: Subtracts days from a date.
- **Syntax**: `SUBDATE(date, days)`

#### Example:

```sql
SELECT SUBDATE('2024-09-17', 10);
```

| SUBDATE()       |
|-----------------|
| 2024-09-07      |

---

## 6. More Date and Time Functions

### LAST_DAY()
- **Description**: Returns the last day of the month for the given date.
- **Syntax**: `LAST_DAY(date)`

#### Example:

```sql
SELECT LAST_DAY('2024-09-17');
```

| LAST_DAY('2024-09-17') |
|------------------------|
| 2024-09-30             |

---

### EXTRACT()
- **Description**: Extracts a part of a date or time (like year, month, day).
- **Syntax**: `EXTRACT(unit FROM date)`

#### Example:

```sql
SELECT EXTRACT(YEAR FROM '2024-09-17');
```

| EXTRACT(YEAR) |
|---------------|
| 2024          |

---

### STR_TO_DATE()
- **Description**: Converts a string to a date using a specified format.
- **Syntax**: `STR_TO_DATE(str, format)`

#### Example:

```sql
SELECT STR_TO_DATE('17-09-2024', '%d-%m-%Y');
```

| STR_TO_DATE()   |
|-----------------|
| 2024-09-17      |

---

### FROM_UNIXTIME()
- **Description**: Converts a Unix timestamp to a date.
- **Syntax**: `FROM_UNIXTIME(unix_timestamp)`

#### Example:

```sql
SELECT FROM_UNIXTIME(1609459200);
```

| FROM_UNIXTIME() |
|-----------------|
| 2021-01-01      |

---

### TO_DAYS()
- **Description**: Returns the number of days between the given date and the year 0.
- **Syntax**: `TO_DAYS(date)`

#### Example:

```sql
SELECT TO_DAYS('2024-09-17');
```

| TO_DAYS()  |
|------------|
| 738300     |

---

## 7. Using `TIMESTAMP` with Default and `ON UPDATE`

### `TIMESTAMP` with `DEFAULT` and `ON UPDATE`

- **Description**: The `TIMESTAMP` column can automatically store the current timestamp when a record is created (`DEFAULT CURRENT_TIMESTAMP`) and automatically update the timestamp when the record is modified (`ON UPDATE CURRENT_TIMESTAMP`).

#### Example:

```sql
CREATE TABLE Orders (
    OrderID INT,
    OrderDate TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

INSERT INTO Orders (OrderID) VALUES (1);

-- After some updates

UPDATE Orders SET OrderID = 2 WHERE OrderID = 1;
```

| OrderID | OrderDate           |
|---------|---------------------|
| 1       | 2024-09-17 15:30:00 |
| 2       | 2024-09-17 16:00:00 |

---

## Conclusion

This detailed guide covers not only basic date and time functions but also advanced date manipulation, extraction, and formatting functions. Use these powerful SQL functions to manage your date and time data efficiently in any database application.

---
- by Aditya Kumar