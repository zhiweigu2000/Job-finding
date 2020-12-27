# SQL for Data Science 

From Coursera by UC Davis

SQL: read, write, update data

Relational model: allow easy querying, intuitive

Transactional model: operational

ER model: show relationships, links

Primary keys: a columen whose values unique indentify each row in a table

Foreign keys: one or more columns that could be used to identify a single row in a table


## Select

#### SELECT [column] FROM [table] LIMIT [number of rows]

*: every column


## Create

#### CREATE TABLE [table name]

#### ([column]);

Primary keys must have a value

#### INSERT INTO [table name]

#### ([column])

#### VALUES

#### ([values]);


## Create temporary table

#### CREATE TEMPORARY TABLE [table name] AS

#### (SELECT);


## Comment

Single line: - -

Section: /* ... */


## Where

#### SELECT [column] FROM [table] WHERE [column operator value]

<>: not equal

BETWEEN a AND b: range a to b, inclusive

IS NULL: rows with no value

IN (condition1, condition2, ...): similar to or, with long list of options, order does not matter, can use another SELECT

OR: not evaluate second condition if first condition is met

AND: meet both conditions

Order of evaluation: AND before OR, use ()

NOT: exclude options

LIKE: wildcards

Wildcards: special character used to match parts of a value, for text, not for numemrical data

%A: anything ends with A

A%: anything starts with A

%A%: anything that includes A

A%B: anything starts with A and ends with B

_A: match a single character


## Order

#### ORDER BY [characteristic] [ASC/DESC]

Always be last clause in SELECT statement

Sort by column positions or column names

DESC: descending order, only for column it directly precedes

ASC: ascending order, only for column it directly precedes


## Math calculation

#### SELECT [calculation] AS [column name]

Addition, subtraction, multiplication, division


## Aggregate functions

#### SELECT [function ([column])] AS [column name]

AVG(), COUNT(), MIN(), MAX(), SUM()

COUNT(*): include null values

COUNT([column]): ignore null values

COUNT(DISTINCT [column]): distinct values not assumed

MAX, MIN, SUM, AVG: ignore null values


## Group by

#### GROUP BY [column] HAVING [condition] 

NULL will be grouped together

WHERE does not apply for groups, use HAVING for groups


## Subquery

#### WHERE [column] IN 

####     (SELECT [column] FROM [table] where [condition])

Always perform innermost SELECT first


## Join

Cartesian join: cross join

#### SELECT [column] FROM [table1] CROSS JOIN [table2]

Inner join: select matching values

#### SELECT [column] FROM [table1] INNER JOIN [table2] ON [table1.column] = [table2.column]

#### SELECT [column] FROM [table] AS [aliase]

Self join: treat one table as two

#### SELECT [column] FROM [table] AS [aliase1], [table] AS [aliase2]

Left join: all from table 1, match from table 2

#### SELECT [column] FROM [table1] LEFT JOIN [table2] ON [table1.column] = [table2.column]

Right join: all from table 2, match from table 1

#### SELECT [column] FROM [table1] RIGHT JOIN [table2] ON [table1.column] = [table2.column]

Left join could be turn into right join by changing order of tables

Full outer join: match in either table 1 or table 2

#### SELECT [column] FROM [table1] FULL OUTER JOIN [table2] ON [table1.column] = [table2.column]

If not matched, return NULL


## Union

Combine results from two SELECT statement with same number of columns, same data type, same order

#### SELECT [column] FROM [table1] 

#### UNION

#### SELECT [column] FROM [table2] 


## Text strings

Concatenate: join two strings

#### SELECT [string1] || [string2]

Substring

#### SELECT SUBSTR ([string], [starting position], [length of string])

Trim

#### SELECT TRIM ([string])

Upper/lower

#### SELECT UPPER/LOWER ([column name]) FROM [table]



