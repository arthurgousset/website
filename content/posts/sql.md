---
title: "🤷‍♂️ SQL (noob notes)"
date: 2021-12-20T12:00:00+01:00
draft: false
tags: ["sql", "noob notes"]
showtoc: true
---

## Context

These are noob notes for writing SQL queries (mostly notes-to-self). I use [SQL Tutorial](https://www.sqltutorial.org/sql-cheat-sheet/) and [W3School](https://www.w3schools.com/sql/) to look up syntax questions and other details. To practice concepts I use "easy" [HackerRank SQL questions](https://www.hackerrank.com/domains/sql).

## Querying data from a table


Query data in columns `c1`, `c2` from a table

```sql
SELECT c1, c2 FROM t;
```

Query **all** rows and columns from a table

```sql
SELECT * FROM t;
```

Query data and filter rows with a **condition**

```sql
SELECT c1, c2 FROM t WHERE condition;
```

Query **distinct** rows from a table.

```sql
SELECT DISTINCT c1 FROM t WHERE condition;
```

- Return only distinct (different) values. 
- Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.

*Source: [W3School](https://www.w3schools.com/sql/sqldistinct.asp)*

**Sort** the result set in ascending or descending order

```sql
SELECT c1, c2 FROM t ORDER BY c1 ASC [DESC];
```

**Aliases** for columns

- The `AS` command is used to rename a column or table with an alias.
- An alias only exists for the duration of the query.

```sql
SELECT CustomerID AS ID, CustomerName AS Customer FROM Customers;
```

*Source: [W3School](https://www.w3schools.com/sql/sqlrefas.asp)*

**Aliases** for tables

We use aliases to make the SQL shorter

```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName="Around the Horn" AND c.CustomerID=o.CustomerID;
```

*Source: [W3School](https://www.w3schools.com/sql/sqlrefas.asp)*

## Using SQL Operators

### Arithmetic Operators

Add

```sql
SELECT 30 + 20;
```

Subtract

```sql
SELECT 30 - 20;
```

Multiply

```sql
SELECT 30 * 20;
```

Divide

```sql
SELECT 30 / 10;
```

Modulo

```sql
SELECT 17 % 5;
>>> 2
```

*Source: [W3School](https://www.w3schools.com/sql/sql_operators.asp)*


### Comparison Operators

* `=`	Equal to	
* `>`	Greater than	
* `<`	Less than	
* `>=`	Greater than or equal to	
* `<=`	Less than or equal to	
* `<>`	Not equal to

*Source: [W3School](https://www.w3schools.com/sql/sql_operators.asp)*


### Logical operators

`ALL`	TRUE if all of the **subquery** values meet the condition	

```sql
SELECT ProductName 
FROM Products
WHERE ProductID = ALL (
  SELECT ProductID 
  FROM OrderDetails 
  WHERE Quantity = 10
);
```

`AND`	TRUE if all the conditions separated by AND is TRUE	

```sql
SELECT * FROM Customers
WHERE City = "London" AND Country = "UK";

```

`ANY`	(or `SOME`) TRUE if any of the **subquery** values meet the condition.

`ANY` and `SOME` perform the same and function and probably exist because SQL was standardised late (*Source: [Stack Overflow - Why are they same with different names?](https://stackoverflow.com/questions/1383988/tsql-some-any-why-are-they-same-with-different-names/38778809)*)

```sql
SELECT * FROM Products
WHERE Price > ANY (
  SELECT Price 
  FROM Products 
  WHERE Price > 50
);
```

```sql
SELECT * FROM Products
WHERE Price > SOME (
  SELECT 
  Price 
  FROM Products 
  WHERE Price > 20
);
```




`BETWEEN`	TRUE if the operand is **within the range** of comparisons

```sql
SELECT * FROM Products
WHERE Price BETWEEN 50 AND 60;
```

`EXISTS`	TRUE if the subquery returns one or more records

```sql
SELECT SupplierName
FROM Suppliers
WHERE EXISTS (
  SELECT ProductName 
  FROM Products 
  WHERE Products.SupplierID = Suppliers.supplierID
  AND Price < 20
);
```

`IN`	TRUE if the operand is equal to one of a **list** of expressions	

```sql
SELECT * FROM Customers
WHERE City IN ('Paris','London');
```

`LIKE`	TRUE if the operand **matches a pattern**

```sql
SELECT * FROM Customers
WHERE City LIKE 's%';
```

`NOT`	Displays a record if the condition(s) is NOT TRUE

```sql
SELECT * FROM Customers
WHERE City NOT LIKE 's%';
```

`OR`	TRUE if any of the conditions separated by OR is `TRUE`

```sql
SELECT * FROM Customers
WHERE City = "London" OR Country = "UK";
```


*Source: [W3School](https://www.w3schools.com/sql/sql_operators.asp)*


## Using `COUNT()`, `AVG()` and `SUM()`

- The `COUNT()` function returns the number of rows that matches a specified criterion.
- The `AVG()` function returns the average value of a numeric column.
- The `SUM()` function returns the total sum of a numeric column. 

Example:

```sql
SELECT COUNT(column_name) - COUNT(DISTINCT column_name)
FROM table_name
WHERE condition;
>>> 13
```

*Source: [W3School](https://www.w3schools.com/sql/sql_count_avg_sum.asp)*