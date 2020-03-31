# SQL-Cheat-Sheet

Connect to the Postgres REPL
```````
$ psql
```````

Postgres REPL Commands
```
\q  Quit Database
```
```
\l  List Databases
```
```
\i  import
```

CREATE DATABASE database_name; Create a database

\c database_name Connect to a database

\d Display Relations

\dt List tables in database

CTRL + C Kill the current command

CMD + K Clears the screen

SHOW data_directory; Shows location of database

Create a Table in your schema

CREATE TABLE table_name (
  id BIGSERIAL PRIMARY KEY,
  column_2 INTEGER,
  column_3 VARCHAR(255),
  column_4 BOOLEAN,
  column_5 INTEGER REFERENCES other_table(id)
);
\d table_name View table column info

Find All Columns and Rows in a Table

SELECT * FROM <table name>;

The asterisk or star symbol (*) means all columns.

The semi-colon (;) terminates the statement like a period in sentence or question mark in a question.

Examples:

SELECT * FROM books;
SELECT * FROM products;
SELECT * FROM users;
SELECT * FROM countries;
Finding the Data You Want

SELECT <columns> FROM <table> WHERE <condition>;
Equality Operator

Find all rows that a given value matches a column's value.

SELECT <columns> FROM <table> WHERE <column name> = <value>;
Examples:

SELECT * FROM contacts WHERE first_name = "Andrew";
SELECT first_name, email FROM users WHERE last_name = "Chalkley";
SELECT name AS "Product Name" FROM products WHERE stock_count = 0;
SELECT title "Book Title" FROM books WHERE year_published = 1999;
Adding a Row to a Table

Inserting a single row:

INSERT INTO <table> VALUES (<value 1>, <value 2>, ...);
This will insert values in the order of the columns prescribed in the schema.

Examples:

INSERT INTO users VALUES  (1, "chalkers", "Andrew", "Chalkley");
INSERT INTO users VALUES  (2, "ScRiPtKiDdIe", "Kenneth", "Love");

INSERT INTO movies VALUES (3, "Starman", "Science Fiction", 1984);
INSERT INTO movies VALUES (4, "Moulin Rouge!", "Musical", 2001);
Updating All Rows in a Table

An update statement for all rows:

UPDATE <table> SET <column> = <value>;
The = sign is different from an equality operator from a WHERE condition. It's an assignment operator because you're assigning a new value to something.

Examples:

UPDATE users SET password = "thisisabadidea";
UPDATE products SET price = 2.99;
Updating Specific Rows

An update statement for specific rows:

UPDATE <table> SET <column> = <value> WHERE <condition>;
Examples:

UPDATE users SET password = "thisisabadidea" WHERE id = 3;
UPDATE blog_posts SET view_count = 1923 WHERE title = "SQL is Awesome";
Removing Data from All Rows in a Table

To delete all rows from a table:

DELETE FROM <table>;
Examples:

DELETE FROM logs;
DELETE FROM users;
DELETE FROM products;
Removing Specific Rows

To delete specific rows from a table:

DELETE FROM <table> WHERE <condition>;
Examples:

DELETE FROM users WHERE email = "andrew@teamtreehouse.com";
DELETE FROM movies WHERE genre = "Musical";
DELETE FROM products WHERE stock_count = 0;
Pattern Matching

Placing the percent symbol (%) any where in a string in conjunction with the LIKE keyword will operate as a wildcard. Meaning it can be substituted by any number of characters, including zero!

SELECT <columns> FROM <table> WHERE <column> LIKE <pattern>;
Examples:

SELECT title FROM books WHERE title LIKE "Harry Potter%Fire";
SELECT title FROM movies WHERE title LIKE "Alien%";
SELECT * FROM contacts WHERE first_name LIKE "%drew";
SELECT * FROM books WHERE title LIKE "%Brief History%";
Counting Results

To count rows you can use the COUNT() function.

SELECT COUNT(*) FROM <table>;
To count unique entries use the DISTINCT keyword too:

SELECT COUNT(DISTINCT <column>) FROM <table>;
To count aggregated rows with common values use the GROUP BY keywords:

SELECT COUNT(<column>) FROM <table> GROUP BY <column with common value>;
Calculating Averages

To get the average value of a numeric column use the AVG() function.

SELECT AVG(<numeric column>) FROM <table>;
SELECT AVG(<numeric column>) FROM <table> GROUP BY <other column>;
Ordering Columns

Ordering by a single column criteria:

SELECT * FROM <table name> ORDER BY <column> [ASC|DESC];

ASC is used to order results in ascending order.

DESC is used to order results in descending order.

Examples:

SELECT * FROM books ORDER BY title ASC;
SELECT * FROM products WHERE name = "Sonic T-Shirt" ORDER BY stock_count DESC;
SELECT * FROM users ORDER BY signed_up_on DESC;
SELECT * FROM countries ORDER BY population DESC;
