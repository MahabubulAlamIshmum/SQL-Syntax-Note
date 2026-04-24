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

```sql
INSERT INTO Students (FirstName, LastName)
VALUES ('John', 'Doe');
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
WHERE StudentID = 011;
```

### DELETE

```sql
DELETE FROM table_name
WHERE condition;
```

*Example:*

```sql
DELETE FROM Students
WHERE StudentID = 011;
```

---
