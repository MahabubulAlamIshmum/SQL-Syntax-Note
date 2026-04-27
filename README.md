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
3. [Functions](#7-functions)
   - [Aggregate Functions](#aggregate-functions)
   - [String Functions](#string-functions)
   - [Date and Time Functions](#date-and-time-functions)
4. [Joins](#8-joins)
   - [INNER JOIN](#inner-join)
   - [LEFT JOIN](#left-join)
   - [RIGHT JOIN](#right-join)
   - [FULL OUTER JOIN](#full-outer-join)

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

```sql
SELECT * FROM Students;
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

## 3. Functions

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

## 4. Joins

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

