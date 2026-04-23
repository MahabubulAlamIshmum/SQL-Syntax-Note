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

**Create a Table**

```sql
CREATE TABLE table_name (
    column1 datatype [constraints],
    column2 datatype [constraints],
    ...
);
```

*Example:*

```sql
CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
);
```

---

### ALTER

```sql
ALTER TABLE Customers
ADD Age INT;
```

---

### DROP

```sql
DROP TABLE Customers;
```

---

## 2. Data Manipulation Language (DML)

### SELECT

```sql
SELECT * FROM Customers;
```

---

### INSERT

```sql
INSERT INTO Customers (FirstName, LastName)
VALUES ('John', 'Doe');
```
