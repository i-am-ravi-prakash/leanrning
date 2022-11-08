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

## SELECT DICTINCT Statement

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

