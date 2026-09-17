# SQL-Syntax-Note

## Topics

1. [Data Definition Language (DDL)](#1-data-definition-language-ddl)
   * [CREATE](#create)
   * [ALTER](#alter)
   * [DROP](#drop)
2. [Data Manipulation Language (DML)](#2-data-manipulation-language-dml)
   * [SELECT](#select)
   * [INSERT](#insert)
   * [UPDATE](#update)
   * [DELETE](#delete)
3. [Transaction Control Language (TCL)](#3-transaction-control-language-tcl)
   - [BEGIN](#begin)
   - [COMMIT](#commit)
   - [ROLLBACK](#rollback)
   - [SAVEPOINT](#savepoint)
4. [Functions](#4-functions)
   - [Aggregate Functions](#aggregate-functions)
   - [String Functions](#string-functions)
   - [Date and Time Functions](#date-and-time-functions)
5. [Joins](#5-joins)
   - [INNER JOIN](#inner-join)
   - [LEFT JOIN](#left-join)
   - [RIGHT JOIN](#right-join)
   - [FULL OUTER JOIN](#full-outer-join)
   - [CROSS JOIN](#cross-join)
6. [Common Clauses](#6-common-clauses)
    - [WHERE](#where)
    - [GROUP BY](#group-by)
    - [HAVING](#having)
    - [ORDER BY](#order-by)
    - [LIMIT / TOP / FETCH](#limit--top--fetch)
7. [Isnull](#7-isnull)
8. [Distinct](#8-distinct)
9. [Views](#9-views)
10. [Stored Procedures and Functions](#10-stored-procedures-and-functions)
11. [Indexes](#11-indexes)
12. [Subqueries](#12-subqueries) 
---

## 1. Data Definition Language (DDL)

### CREATE

**Create a Database**

```sql
CREATE DATABASE database_name;
```

*Example:*

```sql
CREATE DATABASE University;
```

**Create a Table**

```sql
CREATE TABLE table_name (
    column1 datatype [constraints],
    column2 datatype [constraints],
    .
    .
);
```

*Example:*

```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    FirstName VARCHAR(10) NOT NULL,
    LastName VARCHAR(10) NOT NULL,
    Email VARCHAR(50) UNIQUE,
);
```
NOTE :[ SELECT name FROM sys.tables; ] It is used to show all Table of Database.

---

### ALTER

**Add a Column**

```sql
ALTER TABLE table_name
ADD column_name datatype [constraints];
```

*Example:*

```sql
ALTER TABLE students
ADD department VARCHAR(100);
```

**Modify a Column**

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name new_datatype;
```

*Example:*

```sql
ALTER TABLE students
MODIFY ID VARCHAR(100);
```

**Change a Column**

```sql
ALTER TABLE table_name
CHANGE old_name new_name datatype;
```

*Example:*

```sql
ALTER TABLE Students
CHANGE department course VARCHAR(10);
```

**Drop a Column**

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

*Example:*

```sql
ALTER TABLE students
DROP COLUMN email;
```

---

### DROP

**Drop a Table**

```sql
DROP TABLE table_name;
```

*Example:*

```sql
DROP TABLE Students;
```

**Drop a Database**

```sql
DROP DATABASE database_name;
```

*Example:*

```sql
DROP DATABASE University;
```

---

## 2. Data Manipulation Language (DML)

### SELECT

**Select All (*) Columns form Table**

```sql
SELECT * FROM Students;
```

**Select Specific Columns Form Table**

```sql
SELECT coloum_name,coloum_name FROM Students;
```

---

### INSERT

**Insert Into All Columns**

```sql
INSERT INTO table_name
VALUES (value1, value2, ...);
```

*Example:*

```sql
INSERT INTO Students
VALUES (0112331113, 'Mahabubul','Alam', 'malam2331113@cse.uiu.ac.bd');
```

**Insert Into Specific Columns**

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

*Example:*

```sql
INSERT INTO students (id, name, age, marks)
VALUES (0112331113, 'Mahabubul', 23, 90);
```

### UPDATE

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

*Example:*

```sql
UPDATE Students
SET Email = 'newemail@example.com'
WHERE StudentID = 011......;
```

### DELETE

```sql
DELETE FROM table_name
WHERE condition;
```

*Example:*

```sql
DELETE FROM Students
WHERE StudentID = 011......;
```

---

## 3. Transaction Control Language (TCL)

### BEGIN
```sql
BEGIN;
```

### COMMIT

```sql
COMMIT;
```

### ROLLBACK

```sql
ROLLBACK;
```

### SAVEPOINT

```sql
SAVEPOINT savepoint_name;
```

**Rollback to Savepoint**

```sql
ROLLBACK TO SAVEPOINT savepoint_name;
```

---

## 4. Functions

### Aggregate Functions

- **COUNT()**: Counts the number of rows.
- **SUM()**: Calculates the sum of a numeric column.
- **AVG()**: Calculates the average value.
- **MIN()**: Finds the minimum value.
- **MAX()**: Finds the maximum value.

*Example:*

```sql
SELECT COUNT(*) FROM Orders;

SELECT CustomerID, SUM(TotalAmount) as TotalSpent
FROM Orders
GROUP BY CustomerID;
```

### String Functions

- **UPPER(string)**: Converts to uppercase.
- **LOWER(string)**: Converts to lowercase.
- **SUBSTRING(string, start, length)**: Extracts a substring.
- **TRIM(string)**: Removes whitespace.
- **CONCAT(string1, string2, ...)**: Concatenates strings.

*Example:*

```sql
SELECT UPPER(FirstName), LOWER(LastName)
FROM Customers;
```

### Date and Time Functions

- **NOW()**: Returns current date and time.
- **CURDATE()**: Returns current date.
- **DATE_ADD(date, INTERVAL value unit)**: Adds a time interval to a date.
- **DATEDIFF(date1, date2)**: Returns the difference between two dates.

*Example:*

```sql
SELECT NOW();

SELECT DATE_ADD(CURDATE(), INTERVAL 7 DAY);
```

---

## 5. Joins

### INNER JOIN

Returns records with matching values in both tables.

```sql
SELECT columns
FROM table1
INNER JOIN table2 ON table1.column = table2.column;
```

*Example:*

```sql
SELECT Orders.OrderID, Customers.FirstName, Customers.LastName
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

### LEFT JOIN

Returns all records from the left table, and matched records from the right table.

```sql
SELECT columns
FROM table1
LEFT JOIN table2 ON table1.column = table2.column;
```

### RIGHT JOIN

Returns all records from the right table, and matched records from the left table.

```sql
SELECT columns
FROM table1
RIGHT JOIN table2 ON table1.column = table2.column;
```

### FULL OUTER JOIN

Returns all records when there is a match in either left or right table.

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2 ON table1.column = table2.column;
```

### CROSS JOIN

Returns all possible combinations between rows of two tables.

```sql
SELECT column_list
FROM table1
CROSS JOIN table2;
```

*Example:*

```sql
SELECT color, size
FROM Colors
CROSS JOIN Sizes;
```

---

## 6. Common Clauses

### WHERE

Filters records that meet specific conditions.

```sql
SELECT * FROM table_name
WHERE condition;
```

### GROUP BY

Groups rows that have the same values in specified columns.

```sql
SELECT column1, AGG_FUNC(column2)
FROM table_name
GROUP BY column1;
```

### HAVING

Filters groups according to specified conditions.

```sql
SELECT column1, AGG_FUNC(column2)
FROM table_name
GROUP BY column1
HAVING condition;
```

### ORDER BY

Sorts the result set.

```sql
SELECT column_name
FROM table_name
ORDER BY column_name ASC|DESC;
```

*Example:*

```sql
SELECT Name, Age
FROM Students
ORDER BY Age ASC;
```

### LIMIT / TOP / FETCH

Limits the number of records returned.

- **MySQL, PostgreSQL, SQLite**

  ```sql
  SELECT * FROM table_name
  LIMIT number OFFSET offset;
  ```

- **SQL Server**

  ```sql
  SELECT TOP number * FROM table_name;
  ```

- **Oracle**

  ```sql
  SELECT * FROM table_name
  FETCH FIRST number ROWS ONLY;
  ```

---

## 7. Isnull

It is used to replace data of null values.

**Use Isnull**

```sql
ISNULL(expression, replacement_value)
```

*Example:*

```sql
SELECT Name, ISNULL(Age, 0) AS Age
FROM Students;
```

---

## 8. Distinct

It is used to remove duplicate data and display unique values.

**Use Distinct**

```sql
SELECT DISTINCT column_name
FROM table_name;
```

*Example:*

```sql
select distinct DeptName
from Department;
```

---

## 9. Views

A virtual table based on the result set of an SQL statement.

**Create a View**

```sql
CREATE VIEW view_name AS
SELECT columns
FROM table
WHERE condition;
```

*Example:*

```sql
CREATE VIEW HighValueOrders AS
SELECT OrderID, CustomerID, TotalAmount
FROM Orders
WHERE TotalAmount > 1000;
```

---

## 11. Indexes

Used to speed up the retrieval of data.

**Create an Index**

```sql
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```

**Create a Unique Index**

```sql
CREATE UNIQUE INDEX index_name
ON table_name (column);
```

## 12. Subqueries

A query nested inside another query.

```sql
SELECT column1_name
FROM table1_name
WHERE column2_name = (SELECT column_name FROM table2_name WHERE condition);
```

*Example:*

```sql
SELECT FirstName(Mahabubul), LastName(Alam)
FROM Students
WHERE StudentID IN (SELECT StudentID FROM Course WHERE CG > 3.50);
```

---
