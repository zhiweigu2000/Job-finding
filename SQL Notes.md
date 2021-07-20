# SQL Notes

From SQL for Data Science on Coursera by UC Davis and other online sources

SQL: read, write, update data

Relational model: tables linked to other tables

Transactional model: operational

ER model: show relationships, links

Primary keys: a column whose values are unique and can be used to identify each row in a table, only one primary key in the table

Foreign keys: one or more columns that could be used to identify a single row in a table

Unique keys: columns that have unique values


## Select

#### SELECT [column] FROM [table] LIMIT [number of rows]

*: every column

#### LIMIT [count] OFFSET [skip]

OFFSET: skip number of rows before return

LIMIT: return number of rows


## Delete

#### DELETE FROM [table] WHERE [condition]


## Update

#### UPDATE [table]

#### SET [column] = [value]

#### WHERE [condition]


## Create

#### CREATE TABLE [table name]

#### ([column]);

Primary keys must have a value

#### INSERT INTO [table name]

#### ([column])

#### VALUES

#### ([values]);


## Comment

Single line: - -

Section: /* ... */


## Where

#### SELECT [column] FROM [table] WHERE [column operator value] 

#### SELECT [column] FROM [table] WHERE [column] in [query] and [column] in [query]

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

WHERE does not apply for groups, WHERE before GROUP BY

HAVING for groups, HAVING after GROUP BY


## Subquery

#### WHERE [column] IN 

####     (SELECT [column] FROM [table] where [condition])

Always perform innermost SELECT first


## Join
![image](https://user-images.githubusercontent.com/76275089/124783488-afe42980-df77-11eb-9e51-b14ae3b289e0.png)

#### SELECT [column] FROM [table1] CROSS JOIN [table2]

Cross join: include all values, match everything in table A to table B
![image](https://user-images.githubusercontent.com/76275089/124779233-30a12680-df74-11eb-8708-2a005a51eda5.png)

#### SELECT [column] FROM [table1] INNER JOIN [table2] ON [table1.column] = [table2.column]

Inner join: select matching values, values that both table 1 and table 2 have
![image](https://user-images.githubusercontent.com/76275089/124779197-2848eb80-df74-11eb-97f8-e7b0bbec65c4.png)

#### SELECT [column] FROM [table1] LEFT JOIN [table2] ON [table1.column] = [table2.column]

Left (outer) join: all from table 1, match ones from table 2
![image](https://user-images.githubusercontent.com/76275089/124779154-20894700-df74-11eb-8d9d-14b582966ce1.png)

#### SELECT [column] FROM [table1] RIGHT JOIN [table2] ON [table1.column] = [table2.column]

Right (outer) join: all from table 2, match ones from table 1
![image](https://user-images.githubusercontent.com/76275089/124779117-17987580-df74-11eb-8e1c-2cc16272a933.png)

#### SELECT [column] FROM [table1] FULL OUTER JOIN [table2] ON [table1.column] = [table2.column]

Full outer join: match in either table 1 or table 2

Outer join: If not matched, return NULL

#### SELECT [column] FROM [table] AS [aliase1], [table] AS [aliase2]

Self join: treat one table as two


## Union
![image](https://user-images.githubusercontent.com/76275089/124783537-bb375500-df77-11eb-97bd-e72c99b63a60.png)

Combine results from two SELECT statement with same number of columns, same data type, same order, up and down

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


## Case

#### SELECT

#### CASE

#### WHEN [C1] THEN [E1]

#### WHEN [C2] THEN [E2]

#### ELSE [E3]

#### END [name]


## Views

#### CREATE VIEW [view_name] AS SELECT [column] FROM [table]

Create a temporary table


## Window function

Rows can maintain their separate identities

#### SELECT [function ([column])] OVER (PARTITION BY [column] ORDER BY [column]) AS [column name]

PARTITION BY: order in groups

Functions: 

SUM()/AVG()/COUNT()

ROW_NUMBER(): return row number

RANK()/DENSE_RANK(): return rank number, rank skips number for identical rows (e.g. 1, 2, 2, 4, 5), dense rank does not (e.g. 1, 2, 2, 3, 4)

NTILE([number]): return percentile number

LAG([column], [number]) / LEAD([column], [number]): lag returns one row later, lead returns one row earlier

#### SELECT [function ([column])] OVER [column] AS [column name] 

#### FROM [table] WHERE [condition]

#### WINDOW [function] AS (PARTITION BY [column] ORDER BY [column]) 



