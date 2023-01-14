# SQL
Getting started with SQL 

## Databases

- Databases allows users to Store and Organize data.
- They are useful when dealing with large amount of data.
- It is Mainly used by the Data Scientist, Web and Mobile App Developers.

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

## IN

- We can use the IN operator to create a conditions that checks to see if a Value is included in a List of Multiple Options.
- For Example, If a user name shows up in a List of known Names (i.e.) Value IN (Option1, Option2,...,Option_n).

__Example__

```ruby
SELECT column_name FROM TableName WHERE column_name IN (Option1, Option2,..., Option_n);
```

```ruby
SELECT column_name FROM TableName WHERE column_name NOT IN (Option1, Option2,..., Option_n);
```

## LIKE and ILIKE

- The LIKE Operator can used for Pattern Matching with string data.
- For Example, If we want to match against a general pattern in String (i.e.) Mails ending with '@gmail.com' and Names begin with 'A'
- It also allows us to perform pattern matching against String data with the use of Wild Characters (i.e.) 
- Percent(%) which matches any sequence of characters and UnderScore(_) which matches any single Character.   

__Example__

```ruby
SELECT column_name FROM TableName WHERE column_name LIKE 'value%'
```  

```ruby
SELECT column_name FROM TableName WHERE column_name LIKE '%value'
```  

```ruby
SELECT column_name FROM TableName WHERE column_name LIKE '%value%'
```  

```ruby
SELECT column_name FROM TableName WHERE column_name LIKE 'valu_'
```

__Note__

- We can use LIKE for Case-Sensitive and ILIKE for Case-InSensitive  

## Aggregation Function

- SQL provides a variety of Aggregation Function.
- The main idea of aggregate function is to take multiple inputs and return a single o/p.
- The most common aggregate functions are listed below,
- AVG() -> Returns a Average Value.
- COUNT() -> Returns a number of Values.
- MAX() -> Returns a maximum Value.
- MIN() -> Returns a minimum Value.
- SUM() -> Returns sum of All Values. 

__Note__

- The aggregate function call can happen only in the SELECT Clause or the HAVING Clause.
- Where the AVG() returns the floating value and you can use ROUND() to specify precision after the decimal.
- Where the COUNT() simply returns the number of rows, which means by convention we just use COUNT(*).

__Example__

```ruby
SELECT MIN(column_name) FROM TableName
```

```ruby
SELECT MAX(column_name) FROM TableName
```

```ruby
SELECT MAX(column_name) FROM TableName
``` 

```ruby
SELECT MIN(column_name1), MAX(column_name2) FROM TableName
``` 

```ruby
SELECT COUNT(*) FROM TableName
```

```ruby
SELECT AVG(CustomerID) FROM TableName
```

```ruby
SELECT ROUND(AVG(CustomerID), 2) FROM TableName
```  

```ruby
SELECT SUM(column_name) FROM TableName
```  

## GROUP BY

- GROUP BY allows us to aggregate columns per some category.

__NOTE__

- We need to choose categorical column to GROUP BY.
- The categorical Columns are non-continious.
- The GROUP BY clause must appear right after a FROM or WHERE statement.
- In the SELECT statement, columns must have an aggregate function or be in the GROUP By call.
- WHERE statement should not refer to the aggregation result.
- If we want to sort results based on the aggregate function, make sure to reference the entire function (i.e.) for ORDER BY. 

__Example__

```ruby
SELECT category_column, AGG(data_column) FROM TableName GROUP BY category_column
```  

```ruby
SELECT category_column, AGG(data_column) FROM TableName WHERE column_name GROUP BY category_column
```

```ruby
SELECT CategoryID, SUM(Price) FROM TableName
GROUP BY CategoryID
ORDER BY SUM(PRICE)
LIMIT Number
```  

## HAVING

- The Havings clause allows us to filter after an aggregation has already taken place (i.e.) it comes after the GROUP BY call.
- We cannot use WHERE to filter based on aggregate results, because those happened after a WHERE is executed.

__Example__

```ruby
SELECT category_column_1, category_column_2, AGG(data_column) 
FROM TableName 
GROUP BY category_column_1, category_column_2
HAVING AGG(data_column) > value
ORDER BY category_column_1
```  

## AS

- As clause allows us to create "alias" for a column or result.
- The AS Operator gets executed at the very end of a Query (i.e.) we cannot use inside the WHERE Operator.

__Example__

```ruby
SELECT column_name as new_name FROM TableName
```

```ruby
SELECT AGG(data_column) as new_name FROM TableName
```

## JOIN

- JOIN allows us to combine informations from multiple Table.
- Different kinds of JOINs -> Inner JOINS, OUTER JOINS, FULL JOINS and UNION

## INNER JOIN

- The Inner Join will result the set of records that matches in both the Tables.

__NOTE__

- Default JOIN will be considered to be INNER JOIN

__Example__

```ruby
SELECT column_name 
FROM TableNameOne
INNER JOIN TableNameTwo on TableNameOne.column_matches = TableNameTwo.column_matches
```  

## FULL OUTER JOIN

- This will allow us to specify how to deal with values present in both the Tables being Joined.

__Example__

```ruby
SELECT column_name 
FROM TableNameOne
FULL OUTER JOIN TableNameTwo 
on TableNameOne.column_matches = TableNameTwo.column_matches
```  

```ruby
SELECT column_name 
FROM TableNameOne
FULL OUTER JOIN TableNameTwo 
on TableNameOne.column_matches = TableNameTwo.column_matches
WHERE TableNameOne.column_matches IS NULL 
OR TableNameTwo.id IS NULL 
```

## LEFT OUTER JOIN (or) LEFT JOIN

- This LEFT JOIN results in the set of records that are in the LEFT Table, if there is no match with the Right Table, then the results are null.

__Example__

```ruby
SELECT column_name 
FROM TableNameOne
LEFT OUTER JOIN TableNameTwo 
on TableNameOne.column_matches = TableNameTwo.column_matches
```

```ruby
SELECT TableNameOne.column_name 
FROM TableNameOne
LEFT OUTER JOIN TableNameTwo 
on TableNameOne.column_matches = TableNameTwo.column_matches
WHERE TableNameTwo.id IS NULL
```  

## RIGHT OUTER JOIN (or) RIGHT JOIN

- This RIGHT JOIN results in the set of records that are in the Right Table, if there is no match with the Left Table, then the results are null.  

__Example__

```ruby
SELECT column_name 
FROM TableNameOne
RIGHT JOIN TableNameTwo 
on TableNameOne.column_matches = TableNameTwo.column_matches
```

```ruby
SELECT TableNameOne.column_name 
FROM TableNameOne
RIGHT JOIN TableNameTwo 
on TableNameOne.column_matches = TableNameTwo.column_matches
WHERE TableNameOne.id IS NULL
```  

## UNION

- The UNION operator is used to combine the results of Two (or) More SELECT Statements.
- It bascially serves to directly concatenate two results together.

__Example__

```ruby
SELECT column_name FROM TableNameOne
UNION
SELECT column_name FROM TableNameTwo
```  

## Data Types

- Boolean (True or False)
- Character (char, varchar and text)
- Numeric (Integer and Floating point Number)
- Temporal (date, time, timestamp and interval)
- UUID (Universally Unique Identifier) - which is essentially an algorithmically unique code in order to make sure you have an unique identifier for a Particular row.
- Array - Stores an Array of strings, numbers, etc..
- JSON
- Hstore key-value pair
- Special types such as Network Address and Geometric Data.

## Primary Key

- A Primary Key is a column or a group of columns used to identify a row uniquely and non-nullable in a Table.
- Primary Key are also important since they allow us to decide which columns should be used for joining tables together.

## Foreign Key

- A Foreign Key is a field or Group of fields in a table that uniquely identifies a row in another table.
- A Foreign Key is defined in a table that references to the Primary key of other table.
- The Table that contains the foreign key is called referencing table or child table.
- The Table to which the foreign key references is called referenced table or Parent table.
- A Table can have multiple foreign keys depending on its relationship with other tables.
- For Example, If we take the Payment Table, each payment row has its unique payment_id(a primary key) and the customer that made the payment through the customer_id(a foreign key since it references the customer table's primary key)

__NOTE__

- When creating Tables and defining columns, we can use constraints to define columns as being a primary key, or attaching a foreign key relationship to another table.

## Constraints

- Constraints are the rules enforced on data columns on Table.
- They are used to prevent invalid data from being entered in to the database.
- This ensures the accuracy and readibility of the data in the database.
- Two Categories -> Column Constraints, Table Constraints
- Column Constraints means contsraint the data in a column to certain conditions.
- Table Constraints applied to the entire table rather than an to an individual column.

## Commonly Used Constraints

- The most commonly used constraints are listed below.
- NOT NULL Constraint ensures that a columns cannot have NULL Value.
- UNIQUE Constraint ensures that all values in a column are different.
- PRIMARY KEY uniquely identifies each row/record in a database table.
- FOREIGN KEY Constraints data based on columns in other Table.
- CHECK Constraint ensures that all values in a column satisfy certain conditions.
- Exclusion Constraint ensures that if any two rows are compared on the specified column or expression using the specified operator, not all of these comparsion will return TRUE.

## Need to Know

- SQL supports comparsion Operators (i.e.) =,>,<,>=,<=,<>(or)!=
- It also supports logical Operators (i.e.) AND, OR, NOT
