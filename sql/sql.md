# Introduction to SQL

SQL stands for Standard Query Language which is used to store, manipulate and retrieve data in database.

## What Can SQL do?

- SQL can execute queries against a database
- SQL can retrieve data from a database
- SQL can insert records in a database
- SQL can update records in a database
- SQL can delete records from a database
- SQL can create new databases
- SQL can create new tables in a database
- SQL can create stored procedures in a database
- SQL can create views in a database
- SQL can set permissions on tables, procedures, and views

**RDBMS**

RDBMS stands for Relational Database Management System. RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access. The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.

Every table is broken up into smaller entities called fields. A field is a column in a table that is designed to maintain specific information about every record in the table.

A record, also called a row, is each individual entry that exists in a table. A record is a horizontal entity in a table.

A column is a vertical entity in a table that contains all information associated with a specific field in a table.

**NOTE**: SQL keywords are not case-sensitive. select is the same as SELECT

**Some of The Most Important SQL Commands**

- **SELECT** - extracts data from a database
- **UPDATE** - updates data in a database
- **DELETE** - deletes data from a database
- **INSERT INTO** - inserts new data into a database
- **CREATE DATABASE** - creates a new database
- **ALTER DATABASE** - modifies a database
- **CREATE TABLE** - creates a new table
- **ALTER TABLE** - modifies a table
- **DROP TABLE** - deletes a table
- **CREATE INDEX** - creates an index (search key)
DROP INDEX - deletes an index

## SELECT DICTINCT

The **SELECT DISTINCT** statement is used to return only distinct (different) values.
```
SELECT DISTINCT column1, column2, ... FROM table_name;
```
## SQL WHERE Clause

The **WHERE** clause is used to filter records.

```
SELECT column1, column2, ... FROM table_name WHERE condition;
```
Operators in The WHERE Clause:

| Operator | Description |
| -------- | ----------- |
| = | Equal |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal |
| <= | Less than or equal |
| <> | Not equal. Note: In some versions of SQL this operator may be written as != |
| BETWEEN | Between a certain range |
| LIKE | Search for a pattern |
| IN | To specify multiple possible values for a column |


## SQL AND, OR and NOT Operators

The **WHERE** clause can be combined with **AND**, **OR**, and **NOT** operators.

The **AND** and **OR** operators are used to filter records based on more than one condition:

- The **AND** operator displays a record if all the conditions separated by AND are TRUE.

```
SELECT column1, column2, ... FROM table_name WHERE condition1 AND condition2 AND condition3 ...;
```

- The **OR** operator displays a record if any of the conditions separated by OR is TRUE.

```
SELECT column1, column2, ... FROM table_name WHERE condition1 OR condition2 OR condition3 ...;
```

- The **NOT** operator displays a record if the condition(s) is NOT TRUE.

```
SELECT column1, column2, ... FROM table_name WHERE NOT condition;
```


## SQL ORDER BY Keyword

The **ORDER BY** keyword is used to sort the result-set in ascending or descending order.

The **ORDER BY** keyword sorts the records in ascending order by default. To sort the records in descending order, use the **DESC** keyword.

```
SELECT column1, column2, ... FROM table_name ORDER BY column1, column2, ... ASC|DESC;
```

## SQL INSERT INTO

The **INSERT INTO** statement is used to insert new records in a table.

It is possible to write the INSERT INTO statement in two ways:

1. Specify both the column names and the values to be inserted:

```
INSERT INTO table_name (column1, column2, column3, ...) VALUES (value1, value2, value3, ...);
```

2. If you are adding values for all the columns of the table, you do not need to specify the column names in the SQL query. However, make sure the order of the values is in the same order as the columns in the table. Here, the INSERT INTO syntax would be as follows:

```
INSERT INTO table_name VALUES (value1, value2, value3, ...);
```


## SQL NULL Values

A field with a NULL value is a field with no value.

If a field in a table is optional, it is possible to insert a new record or update a record without adding a value to this field. Then, the field will be saved with a NULL value.

How to Test for NULL Values?

**IS NULL** Syntax

```
SELECT column_names FROM table_name WHERE column_name IS NULL;
```

**IS NOT NULL** Syntax

```
SELECT column_names FROM table_name WHERE column_name IS NOT NULL;
```


## SQL UPDATE

The **UPDATE** statement is used to modify the existing records in a table.

```
UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition;
```

**NOTE**: Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement. The WHERE clause specifies which record(s) that should be updated. If you omit the WHERE clause, all records in the table will be updated!


## SQL DELETE

The **DELETE** statement is used to delete existing records in a table.

```
DELETE FROM table_name WHERE condition;
```

**NOTE**: Be careful when deleting records in a table! Notice the WHERE clause in the DELETE statement. The WHERE clause specifies which record(s) should be deleted. If you omit the WHERE clause, all records in the table will be deleted!

**Delete All Records**

```
DELETE FROM table_name;
```

## SQL TOP, LIMIT, FETCH FIRST or ROWNUM Clause

