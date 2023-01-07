# SQL
Getting started with SQL 

## Databases

- Databases are systems that allow users to store and Organize data.
- They are useful when dealing with large amount of data.
- Mainly used by the Data Scientist, Web and Mobile App Developers.

## SQL

- Structured Query Language
- SQL is the programming Language used to communicate with our Database.

## SELECT

- SELECT is the most common statement used to retrieve informations from a Table.
- In General, it is not a good practice to use asterik(*) in SELECT Statement unless we need all Columns (i.e.)
- It will automatically query everything which increases the traffic b/w the Database Server and the Application which can slow down the retrieval of Results.
- The Semicolon is to denote the end of a Query.

__Example__

```ruby
SELECT * FROM TableName;
```

```ruby
SELECT column_name FROM TableName;
```  

## DISTINCT

- The DISTINCT keyword will be used to return only the Distinct values in a Column (i.e.) Used to to avoid duplicate values in a column.
- The DISTINCT of a Column works with or without parenthesis.

__Example__

```ruby
SELECT DISTINCT column_name FROM TableName;
```

```ruby
SELECT DISTINCT(column_name) FROM TableName;
```

## COUNT

- The COUNT Function returns the number of input rows that matches a specific condition of a Query.
- We can apply COUNT on a specific column or just pass COUNT(*) to retrive the returned result.
- The COUNT will works only with the parenthesis (i.e.) it's a function acting on something.

__Example__

```ruby
SELECT COUNT(*) FROM TableName;
```  

```ruby
SELECT COUNT(column_name) FROM TableName;
```  

```ruby
SELECT COUNT(DISTINCT(column_name)) FROM TableName;
```  

## WHERE

- The WHERE Statement allows us to specify conditions on columns for the rows to be returned.  
- The Conditions are used to filter the rows returned from the SELECT Statement.

__Example__

```ruby
SELECT column_name FROM TableName WHERE Conditions;
```

```ruby
SELECT column_name FROM TableName WHERE Condition1 AND Condition2;
```  

## ORDER BY

- ORDER BY is used to sort rows based on a Column value in Ascending or Descending Order.

__Example__

```ruby
SELECT column_name FROM TableName ORDER BY column_name ASC
```

```ruby
SELECT column_name FROM TableName ORDER BY column_name DESC
```

```ruby
SELECT column_name FROM TableName ORDER BY column_name1 DESC, column_name2 ASC
```  

## LIMIT

- The LIMIT command allows us to limit the number of rows returned for a Query.

__Example__

```ruby
SELECT column_name FROM TableName LIMIT Numbers
```

## BETWEEN

- The BETWEEN Operator can be used to match a value against a range of Values (i.e.) Value BETWEEN Low AND High.
- It similar to that of Value >= Low AND Value <= High.
- We can also combine BETWEEN with the NOT Logical Operator (i.e.) Value NOT BETWEEN Low AND High.
- It similar to that of Value < Low AND Value > High.

__Example__

```ruby
SELECT column_name FROM TableName WHERE column_name BETWEEN Value1 AND Value2;
```

```ruby
SELECT column_name FROM TableName WHERE column_name NOT BETWEEN Value1 AND Value2;
```  

__Note__

- The BETWEEN Operator can also be used with Dates but we need to format that in YYYY-MM-DD (i.e.) Date BETWEEN 2023-01-01 AND 2023-01-31

## Need to Know

- SQL supports comparsion Operators (i.e.) =,>,<,>=,<=,<>(or)!=
- It also supports logical Operators (i.e.) AND, OR, NOT
