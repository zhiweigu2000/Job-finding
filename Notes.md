# SQL for Data Science 

From Coursera by UC Davis

SQL: read, write, update data

Relational model: allow easy querying, intuitive

Transactional model: operational

ER model: show relationships, links

Primary keys: a columen whose values unique indentify each row in a table

Foreign keys: one or more columns that could be used to identify a single row in a table


## Select

#### SELECT [column] FROM [table] LIMIT [number of rows];

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

#### SELECT [column_name] FROM [table_name] WHERE [column name operator value]

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

#### ORDER BY [characteristic] 

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
