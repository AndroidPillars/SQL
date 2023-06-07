# Topics

| S.No | Content | Status |
| --------	 | ------------ | ------------ |  
| 1 | [Databases](README.md#databases) | :heavy_check_mark: | 
| 2 | [SQL](README.md#sql) | :heavy_check_mark: |  
| 3 | [DBMS](README.md#dbms) | :heavy_check_mark: |  
| 4 | [Comment](README.md#comment) | :heavy_check_mark: |  
| 7 | [Database Queries](README.md#database-queries) | :heavy_check_mark: |  
| 5 | [SELECT](README.md#select) |
| 4 | [DISTINCT](README.md#distinct) |
| 5 | [COUNT](README.md#count) |
| 6 | [WHERE](README.md#where) |
| 7 | [ORDER BY](README.md#order-by) |
| 8 | [LIMIT](README.md#limit) |
| 9 | [BETWEEN](README.md#between) |
| 10 | [IN](README.md#in) |
| 11 | [LIKE and ILIKE](README.md#like-and-ilike) |
| 12 | [Aggregation Function](README.md#aggregation-function) |  
| 13 | [GROUP BY](README.md#group-by) |  
| 14 | [HAVING](README.md#having) |  
| 15 | [AS](README.md#as) |  
| 16 | [JOIN](README.md#join) | 
| 17 | [INNER JOIN](README.md#inner-join) | 


## Databases

- Databases is a collection of data that allows users to Store and Organize data.
- They are useful when dealing with large amount of data.
- It is Mainly used by the Data Scientist, Web and Mobile App Developers.
- Types - Relational (Table Format), Hierarchical, Network, NoSQL etc.

:arrow_up: [__Back to Top__](README.md#topics)  

## SQL

- SQL (Structured Query Language) is the programming Language used to communicate with our Database.
- It will be used to perform CRUD operations on the records stored in the database.

:arrow_up: [__Back to Top__](README.md#topics)  

## DBMS

- DBMS (Database Management System) is a software which is used to manage the database.
- In other words, it is a software interface between database and end user that is responsible for authentication, concurrency, logging, backup, optimization etc.
- Some of the Database Management Softwares used for RDBMS (Relational Database Management System)
    - MySql – OpenSource
    - SQL Server – Microsoft
    - Oracle – IBM
    - PostgreSQL - OpenSource

:arrow_up: [__Back to Top__](README.md#topics)  

## Comment

- A comment is an explanation or description of the source code of the program. 
- Generally Comment makes the program easier to read and understand. 
- These are the statements that are not executed by the compiler or an interpreter.
- Type -> Single Line Comment, Multiple Line Comment.

__Example__

```ruby 
-- Single Line Comment
```  

```ruby  
/*
Multiple 
Line 
Comment
*/
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## Data Types

- Boolean (True or False)
- Character (char - Fixed Length, varchar - Maximum Legth and text)
- Numeric (Integer and Floating point Number)
- Temporal (date, time, timestamp and interval)
- UUID (Universally Unique Identifier) - which is essentially an algorithmically unique code in order to make sure you have an unique identifier for a Particular row.
- Array - Stores an Array of strings, numbers, etc..
- JSON
- Hstore key-value pair
- Special types such as Network Address and Geometric Data.

## Character Data

- CHAR -> For Example: If we set CHAR(5) it stores fixed length string of length 5. (Max 255 bytes)
- VARCHAR -> For Example: If we set VARCHAR(5) it stores variable length string of length 5. (Max 65535 bytes).

```ruby
SHOW CHARACTER SET; -- It shows various character sets that are supported.
```

```ruby
VARCHAR(10) CHARACTER SET utf8; -- Particular column is set to utf8
```

```ruby
CREATE DATABASE TadmurFSM CHARACTER SET UTF8; -- Entire database is set to utf8
```  

## Database Queries

__Examples__

```ruby
CREATE DATABASE DatabaseName; -- To Create a New Database.
```  

```ruby
SHOW DATABASES; (or) SHOW SCHEMAS; -- To show all the Databases.
```

```ruby
DROP DATABASE DatabaseName; (or) DROP SCHEMA DatabaseName; -- To Delete a Database.
```

```ruby
DROP DATABASE IF EXISTS DatabaseName; -- It prevents the error (i.e.) Shows a Warning if DB is not found.
```

```ruby
USE DatabaseName; -- To Select the specific Database.
``` 

:arrow_up: [__Back to Top__](README.md#topics)  

## Table Queries

## CREATE

- To create a Table in SQL we need to use CREATE keyword and column syntax.

__Example (General Syntax)__

```ruby
CREATE TABLE TableName(
column_name_one TYPE column_constraint,
column_name_two TYPE column_constraint
);
```  

```ruby
DESCRIBE TableName; -- It Describes all the columns in the table.
```

```ruby
DROP TABLE TableName; -- To Drop the Table
```

```ruby
ALTER TABLE TableName
ADD column_name DECIMAL(3,2); -- Adds a new column column_name to the TableName table
```  

```ruby
ALTER TABLE TableName
DROP COLUMN column_name; -- the column_name column from TableName table
```  

```ruby
ALTER TABLE TableName
DROP column_name; -- the column_name column from TableName table
```

## Primary Key

- A Primary Key is a column or a group of columns used to identify a row uniquely and non-nullable in a Table.
- Primary Key are also important since they allow us to decide which columns should be used for joining tables together.

```ruby
CREATE TABLE TableName(
id INT PRIMARY KEY,
column_name_one VARCHAR(30),
column_name_two DECIMAL(3,2)
);
```  

## INSERT

- Insert allows us to add Rows in a Table.
- We can also insert values from Another Table.

__NOTE__

- The inserted row values must match up for the table including constraints.
- SERIAL columns do not need to be provided a value (i.e.) since it's a sequence it will automatically update the next available integer for that row.

__Example (General Syntax)__

```ruby
INSERT INTO TableName VALUES (value1, value2,...) -- To Insert a row.
```

```ruby
INSERT INTO TableName VALUES (value1, value2,...), (value1, value2,...); -- To Insert more than one row.
```

```ruby
INSERT INTO TableName(column1, column2,...) VALUES (value1, value2,...) -- To Insert a row.
```

```ruby
INSERT INTO TableName(column1) VALUES (value1) -- To Insert a Specific Column.
```

```ruby
INSERT INTO  TableName(column1, column2,...) 
SELECT column1, column2,...
FROM another_table 
WHERE condition;
```  

## SELECT

- SELECT is the most common statement used to retrieve informations from a Table.
- In General, it is not a good practice to use asterik(*) in SELECT Statement unless we need all Columns (i.e.)
- It will automatically query everything which increases the traffic b/w the Database Server and the Application which can slow down the retrieval of Results.
- The Semicolon is to denote the end of a Query but it is not mandatory.

__Example__

```ruby
SELECT * FROM TableName; -- To displays all rows and columns in the Table
```

```ruby
SELECT column_name FROM TableName; -- To displays specific columns in the Table
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## WHERE

- WHERE Statement allows us to specify conditions on columns for the rows to be returned.  
- The Conditions are used to filter the rows returned from the SELECT Statement.

__Example__

```ruby
SELECT column_name FROM TableName WHERE Conditions; -- General Syntax
```

```ruby
SELECT column_name FROM TableName WHERE Condition1 AND Condition2; -- We can use AND/OR to combine the relational operators.
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## ORDER BY

- ORDER BY is used to sort rows based on a Column value in Ascending or Descending Order.

__Example 1 (Sorting the rows in Ascending Order)__

```ruby
SELECT column_name FROM TableName ORDER BY column_name ASC
```

__Example 2 (Sorting the rows in Descending Order)__

```ruby
SELECT column_name FROM TableName ORDER BY column_name DESC
```

__Example 3 (Sorting the rows in Ascending and Descending Order for multiple Columns)__

```ruby
SELECT column_name FROM TableName ORDER BY column_name1 DESC, column_name2 ASC
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## LIMIT

- The LIMIT command allows us to limit the number of rows returned for a Query.

__Example 1 (General Syntax)__

```ruby
SELECT column_name FROM TableName LIMIT Numbers
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## BETWEEN

- The BETWEEN Operator can be used to match a value against a range of Values (i.e.) Value BETWEEN Low AND High.
- It similar to that of Value >= Low AND Value <= High.
- We can also combine BETWEEN with the NOT Logical Operator (i.e.) Value NOT BETWEEN Low AND High.
- It similar to that of Value < Low AND Value > High.

__Note__

- The BETWEEN Operator can also be used with Dates but we need to format that in YYYY-MM-DD (i.e.) Date BETWEEN 2023-01-01 AND 2023-01-31    

__Example 1 (General Synatx)__

```ruby
SELECT column_name FROM TableName WHERE column_name BETWEEN Value1 AND Value2;
```

__Example 2 (General Synatx using NOT)__

```ruby
SELECT column_name FROM TableName WHERE column_name NOT BETWEEN Value1 AND Value2;
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## IN

- We can use the IN operator to create a conditions that checks to see if a Value is included in a List of Multiple Options.
- For Example, If a user name shows up in a List of known Names (i.e.) Value IN (Option1, Option2,...,Option_n).

__Example 1 (General Synatx)__

```ruby
SELECT column_name FROM TableName WHERE column_name IN (Option1, Option2,..., Option_n);
```

__Example 2 (General Synatx using NOT)__

```ruby
SELECT column_name FROM TableName WHERE column_name NOT IN (Option1, Option2,..., Option_n);
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## LIKE and ILIKE

- The LIKE Operator can used for Pattern Matching with string data.
- For Example, If we want to match against a general pattern in String (i.e.) Mails ending with '@gmail.com' and Names begin with 'A'
- It also allows us to perform pattern matching against String data with the use of Wild Characters (i.e.) 
- Percent(%) which matches any sequence of characters and UnderScore(_) which matches any single Character.   

__Note__

- We can use LIKE for Case-Sensitive and ILIKE for Case-InSensitive    

__Example 1 (Searches for the Ending Character)__

```ruby
SELECT column_name FROM TableName WHERE column_name LIKE 'value%'
```  

__Example 2 (Searches for the Starting Character)__

```ruby
SELECT column_name FROM TableName WHERE column_name LIKE '%value'
```  

__Example 3 (Searches for the Starting and Ending Character)__

```ruby
SELECT column_name FROM TableName WHERE column_name LIKE '%value%'
```  

__Example 4 (Searches for the Missing Character)__

```ruby
SELECT column_name FROM TableName WHERE column_name LIKE 'valu_'
```

:arrow_up: [__Back to Top__](README.md#topics)  

## DISTINCT

- DISTINCT keyword will be used to return only the Distinct values in a Column (i.e.) Used to to avoid duplicate values in a column.
- The DISTINCT of a Column works with or without parenthesis.

__Example__

```ruby
SELECT DISTINCT column_name FROM TableName; -- General Syntax without parenthesis
```

```ruby
SELECT DISTINCT(column_name) FROM TableName; -- General Syntax with parenthesis
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## COUNT

- The COUNT Function returns the number of input rows that matches a specific condition of a Query.
- We can apply COUNT on a specific column (or) just pass COUNT(*) to retrive the returned result.
- The COUNT will works only with the parenthesis (i.e.) it is just a function which acts on something.

__Example 1 (General Syntax)__

```ruby
SELECT COUNT(*) FROM TableName;
```  

__Example 2 (Getting Count of a Specific Column)__

```ruby
SELECT COUNT(column_name) FROM TableName;
```  

__Example 3 (Getting Count of a Specific Column with DISTINCT Keyword)__

```ruby
SELECT COUNT(DISTINCT(column_name)) FROM TableName;
```  

:arrow_up: [__Back to Top__](README.md#topics)  



## Aggregation Function

- SQL provides a variety of Aggregation Function.
- The main idea of aggregate function is to take multiple inputs and return a single output.
- The most common aggregate functions are AVG(), COUNT(), MAX(), MIN() and SUM().
- AVG() -> Returns a Average Value.
- COUNT() -> Returns a number of Values.
- MAX() -> Returns a maximum Value.
- MIN() -> Returns a minimum Value.
- SUM() -> Returns sum of All Values. 

__Note__

- The aggregate function call can happen only in the SELECT Clause or the HAVING Clause.
- Where the AVG() returns the floating value and you can use ROUND() to specify precision after the decimal.
- Where the COUNT() simply returns the number of rows, which means by convention we just use COUNT(*).

__Example 1 (Returns Minimum Value)__

```ruby
SELECT MIN(column_name) FROM TableName
```

__Example 2 (Returns Maximum Value)__

```ruby
SELECT MAX(column_name) FROM TableName
```

__Example 3 (Returns both Minimum and Maximum Value)__

```ruby
SELECT MIN(column_name1), MAX(column_name2) FROM TableName
``` 

__Example 4 (Returns count of the Rows)__

```ruby
SELECT COUNT(*) FROM TableName
```

__Example 5 (Returns the Average Value)__

```ruby
SELECT AVG(CustomerID) FROM TableName
```


__Example 6 (Round Off the Value)__

```ruby
SELECT ROUND(AVG(CustomerID), 2) FROM TableName
```  


__Example 7 (Sum the Values)__

```ruby
SELECT SUM(column_name) FROM TableName
```  

:arrow_up: [__Back to Top__](README.md#topics)  


## GROUP BY

- GROUP BY allows us to aggregate columns per some category.

__NOTE__

- We need to choose categorical column to GROUP BY.
- The categorical Columns are non-continious.
- The GROUP BY clause must appear right after a FROM or WHERE statement.
- In the SELECT statement, columns must have an aggregate function or be in the GROUP By call.
- WHERE statement should not refer to the aggregation result.
- If we want to sort results based on the aggregate function, make sure to reference the entire function (i.e.) for ORDER BY. 

__Example 1 (General Syntax using GROUP BY)__

```ruby
SELECT category_column, AGG(data_column) 
FROM TableName 
GROUP BY category_column;
```  

__Example 2 (GROUP BY with WHERE Condition)__

```ruby
SELECT category_column, AGG(data_column) 
FROM TableName 
WHERE condition
GROUP BY category_column;
```

__Example 3 (GROUP BY with ORDER BY)__

```ruby
SELECT CategoryID, SUM(Price) FROM TableName
GROUP BY CategoryID
ORDER BY SUM(PRICE)
LIMIT Number;
```  

## HAVING

- The Havings clause allows us to filter after an aggregation has already taken place (i.e.) it comes after the GROUP BY call.
- We cannot use WHERE to filter based on aggregate results, because those happened after a WHERE is executed.

__Example 1 (General Syntax)__

```ruby
SELECT category_column_1, category_column_2, AGG(data_column) 
FROM TableName 
GROUP BY category_column_1, category_column_2
HAVING AGG(data_column) > value
ORDER BY category_column_1
```  

:arrow_up: [__Back to Top__](README.md#topics)  

## AS

- As clause allows us to create "alias" for a column or result.
- The AS Operator gets executed at the very end of a Query (i.e.) we cannot use inside the WHERE Operator.

__Example 1 (General Syntax with Column Name)__

```ruby
SELECT column_name as new_name FROM TableName
```

__Example 2 (General Syntax with Aggregation Function)__

```ruby
SELECT AGG(data_column) as new_name FROM TableName
```

:arrow_up: [__Back to Top__](README.md#topics)  

## JOIN

- JOIN allows us to combine informations from multiple Table.
- Different kinds of JOINs -> Inner JOINS, OUTER JOINS, FULL JOINS and UNION.  

:arrow_up: [__Back to Top__](README.md#topics)  

## INNER JOIN

- The Inner Join will result the set of records that matches in both the Tables.

__NOTE__

- Default JOIN will be considered to be INNER JOIN

__Example 1 (General Syntax)__

```ruby
SELECT column_name 
FROM TableNameOne
INNER JOIN TableNameTwo on TableNameOne.column_matches = TableNameTwo.column_matches
```  

:arrow_up: [__Back to Top__](README.md#topics)  


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
- Table Constraints will use the following keywords (i.e.) 
- CHECK (Condition) -  To check a condition when inserting or updating data.
- REFERENCES - To constraint the value stored in the column that must exist in a column in another Table.
- UNIQUE (column_list) - Forces the value stored in the Column listed inside the paranthesis to be unique.
- PRIMARY KEY (column_list) - Allows us to define the primary key that consists of multiple columns.

## Commonly Used Constraints

- The most commonly used constraints are listed below.
- NOT NULL Constraint ensures that a columns cannot have NULL Value.
- UNIQUE Constraint ensures that all values in a column are different.
- PRIMARY KEY uniquely identifies each row/record in a database table.
- FOREIGN KEY Constraints data based on columns in other Table.
- CHECK Constraint ensures that all values in a column satisfy certain conditions.
- Exclusion Constraint ensures that if any two rows are compared on the specified column or expression using the specified operator, not all of these comparsion will return TRUE.  


## SERAIL (Data Type)

- A Sequence is a special kind of database object that generates a sequence of Integers.
- It is often used as a primary key column in a Table.
- If the row is later removed, the column with the SERAIL data type will not adjust (i.e.) 
- For Example In SERAIL data type 1,2,3 if we removed 2 then it will be like 1,3

__Example 1 (General Syntax)__

```ruby
CREATE TABLE TableName(
column_id SERIAL PRIMARY KEY,
column_age SMALLINT NOT NULL,
);
```

__Example 2 (Foreign Key References)__

```ruby
CREATE TABLE TableName(
column_id INTEGER REFERENCES ReferedTableName(column_id),
);
```

## UPDATE

- The UPDATE keyword allows us to change the value of the Columns in a Table.

__Example__

```ruby
UPDATE TableName
SET column1 = value1, column2 = value2,...
WHERE condition;
```

```ruby
UPDATE TableName
SET column1 = value1
WHERE column1 IS NULL;
```

```ruby
UPDATE TableName
SET column1 = column2
```

```ruby
UPDATE TableA
SET column1 = TableB.value1
FROM TableB
WHERE TableA.id = TableB.id;
```  

```ruby
UPDATE TableName
SET column1 = column2
RETURNING table_id, table_name
```  

## DELETE

- We can use the DELETE clause to remove rows from a Table (Refer Example 1).
- We can delte rows based on their presence in other Tables (Refer Example 2).
- We can also all rows from a Table (Refer Example 3).
- Similar to UPDATE command, We can also add in a RETURNING call to return rows that were removed (Refer Example 4).

__Example 1__

```ruby
DELETE FROM TableName 
WHERE condition
```  

__Example 2__

```ruby
DELETE FROM TableNameA
USING TableNameB
WHERE condition TableNameA.id = TableNameA.id
```  

__Example 3__

```ruby
DELETE FROM TableName 
``` 
__Example 4__

```ruby
DELETE TableName
WHERE column_name = "Enter Name or value"
RETURNING column_name1, column_name2
```  

## ALTER

- The ALTER Clause allows for changes to an existing Table Structure Such as
- Adding, Droping or Renaming Columns.
- Changing a Column Data Type.
- Set Default values for a Column.
- Adding CHECK Constraints.
- Rename Table.

__Example 1 (General Syntax)__

```ruby
ALTER TABLE table_name action;
```

__Example 2 (Adding New Column)__

```ruby
ALTER TABLE table_name
ADD COLUMN new_column_name TYPE;
```  

__Example 3 (Removing Column)__

```ruby
ALTER TABLE table_name
DROP COLUMN column_name;
``` 

__Example 4 (Renaming Table Name)__

```ruby
ALTER TABLE table_name
RENAME TO new_table_name;
``` 

__Example 5 (Renaming Column)__

```ruby
ALTER TABLE table_name
RENAME COLUMN column_name TO new_column_name;
``` 

__Example 6 (Alter Constraints)__

```ruby
ALTER TABLE table_name
DROP COLUMN column_name 
SET DEFAULT value || DROP DEFAULT || SET NOT NULL || DROP NOT NULL || ADD CONSTRAINT constraint_name;
```

## DROP

- DROP removes for the complete removal of a column in a Table.
- This will also automatically remove all of it's indexes and constraints involving in the column.

__NOTE__

- However, it will not remove columns used in views, triggers, or stored procedures without the additional CASCADE clause. 

__Example 1 (General Syntax)__

```ruby
ALTER TABLE table_name
DROP COLUMN column_name;
```

__Example 2 (To Remove all Dependencies)__

```ruby
ALTER TABLE table_name
DROP COLUMN column_name CASCADE; 
```


__Example 3 (Check existence to Avoid Error)__

```ruby
ALTER TABLE table_name
DROP COLUMN IF EXISTS column_name; 
```  

__Example 4 (Drop Multiple Columns)__

```ruby
ALTER TABLE table_name
DROP COLUMN column_name_one,
DROP COLUMN column_name_two;
```  

## CHECK Constarint

- The CHECK Constraint allows us to create more customized constraints that adhere to a certain condition.
- Such as making sure all inserted integer values fall below a certain threshold.

__Example__

```ruby
CREATE TABLE TableName(
column_id SERIAL PRIMARY KEY,
column_name_one VARCHAR(50) NOT NULL,
column_name_two VARCHAR(50) NOT NULL,
column_name_three DATE CHECK (column_name_three > condition),
column_name_four DATE CHECK (column_name_four > column_name_three),
column_name_five INTEGER CHECK (column_name_five > 0)
);
```

## Timestamps and Extract

- Functions and Operations related to the specific Data Types (i.e.) TIMEZONE, NOW, TIMEOFDAY, CURRENT_TIME, CURRENT_DATE

__NOTE__

- This will be more useful when creating our own database and tables rather than querying a database.
- Careful considerations should be made when designing a Table for choosing a time data type.
- Depending on the situation we may or may not need the full Level of TIMESTAMPTZ.
- TIME -> Contains only Time.
- DATE -> Contains only Date.
- TIMESTAMP -> Contains Date and Time.
- TIMESTAMPTZ -> Contains Date, Time and Timezone.

__Example 1 (For Getting Current Date)__

```ruby
SELECT CURRENT_DATE
```

__Example 1 (For Getting Current TIME)__

```ruby
SELECT CURRENT_TIME
```

## Need to Know

- SQL supports comparsion Operators (i.e.) =,>,<,>=,<=,<>(or)!=
- It also supports logical Operators (i.e.) AND, OR, NOT
