# The Ultimate MySQL Bootcamp

A Udemy course by Colt Steele

##### `Originally Started: 04/27/2023`

## Section 1: Introduction & 5 Minutes of SQL

##### `Originally Started & Completed: 04/27/2023`

This section consist of a few very short videos with trivial, introductory information. It may be worth noting, however, that the course has been updated with MySQL version 8.x in mind.

## Section 2: Getting Started & Installation

##### `Originally Started & Completed: 04/27/2023`

### Section Introduction

In this section we will learn what a database is, as well as SQL vs. MySQL. We will also install MySQL and some GUIs to go along with it.

### What Is A Database?

We begin our MySQL journey with two introductory questions:

1. What is a database?
2. Why do they matter?

**What is a database?**

1. A collection of data
2. A method for accessing and manipulating that data

A database is a structured set of computerized data with an accessible interface.

**Database Vs. Database Management System**

A database is the actual collection of data. Think of it like a gigantic text file in our computer. To actually interface with our database, we make use of Database Management Systems (DBMS). We are going to be giving commands to a Database Management System (MySQL), which then gives commands to the actual data (database) itself.

Often times the two terms get interchanged, mistakenly. MySQL, PostgresSQL, etc are Database Management Systems, not databases. But we may hear sentences like "MySQL is one of the most commonly-used databases."

### SQL Vs. MySQL

What is the difference between SQL and MySQL?

**SQL**

SQL stands for **Structured Query Language**. SQL is the language we use to "talk" to our databases. We give it commands with intent such as:

- "Find All Users"
- "Add a new user with username 'JumboJim'
- "Find all users who are 18 years old"
- "Delete all users"

In code, we are providing commands such as:

```sql
SELECT * FROM Users WHERE age >= 18;
```

**MySQL**

MySQL is a language that works with relational databases.

Working with MySQL is primarily writing SQL. SQL is essentially a standard that database management systems such as MySQL, PostgresSQL, etc. adhere to.

There are slight differences in syntax between SQL and MySQL, but they are minor and infrequent.

1. Once you learn SQL, it's pretty easy to switch to another DBMS that uses SQL
2. What makes databases (DBMS) unique are the features they offer, not the language (SQL) itself.

### Installation - Start Here

Shortly, we will install SQL and a tool called MySQL Workbench. While the tools may be different, the end result of the SQL we run are the same. Behind the scenes, both clients are talking to the same database server, just through different interfaces.

### Installation - Windows

Download the latest MySQL installer from the official website.

After quite a few pages of set-up, we can find the tool we need by searching 'MySQL Command Line Client' in the Windows search box. We can now run MySQL commands in a command line interface!

If we prefer, we can run MySQL Workbench for a more visual approach at working with MySQL.

## Section 3: Creating Databases & Tables

##### `Originally Started & Completed: 04/27/2023`

### Section Introduction

In this section we will really get going with commands that let us use, create and delete databases, as well as create and delete tables inside of those databases.

### Showing Databases

- Can have a bunch of databases within a SQL database server
  - Nothing to do with one another

To show the databases in our database server, we can run:

```sql
SHOW DATABASES;
```

### Creating Databases

To create a new database in our database server, we can run:

```sql
CREATE DATABASE <name>;
```

Examples:

```sql
CREATE DATABASE pet_shop;
```

### Dropping and Using Databases

To delete ("drop") a database from our database server, we can run:

```sql
DROP DATABASE <name>;
```

To begin using a database from our database server, we can run:

```sql
USE <database name>;
```

This will tell MySQL where we are -- what database we want to be interacting with. Note that simply creating a database will not automatically begin using that database.

To see which database we are currently working with, we can run:

```sql
SELECT database();
```

### Introducing Tables

Tables are the true heart of SQL. A database is just a bunch of tables (in a relational database, at least). Tables hold the data. Describe format and shape of our data. A collection of related data held in a structured format within a database.

For example, a Cats table:

| Name   | Breed         | Age |
| ------ | ------------- | --- |
| Blue   | Scottish Fold | 1   |
| Rocket | Persian       | 3   |
| Monty  | Tabby         | 10  |
| Sam    | Munchkin      | 5   |

**Terminology**

- **"Columns":** The headers of the table
- **"Rows":** The actual entries / data in the table

Databases are typically made up of lots of tables.

### Data Types: The Basics

MySQL has _a lot_ of different data types. We assign a type to columns in our tables. This provides consistency with our data and uniformity with what operations are valid on each column. MySQL will enforce these types. Some examples of possible data types are:

**Numeric Types**

- INT
- SMALLINT
- TINYINT
- MEDIUMINT
- BIGINT
- DECIMAL
- NUMERIC
- FLOAT
- DOUBLE
- BIT

**String Types**

- CHAR
- VARCHAR
- BINARY
- VARBINARY
- BLOG
- TINYBLOB
- MEDIUMBLOB
- LONGBLOB
- TINYTEXT
- MEDIUMTEXT
- LONGTEXT
- ENUM

**Date Types**

- DATE
- DATETIME
- TIMESTAMP
- TIME
- YEAR

To begin with, we will focus on INT and VARCHAR.

**INT**

- A whole number
- Maxed _signed_ value of 2,147,483,647
  - This means we can have a positive or negative value of this amount
- Can also be written as INTEGER

**VARCHAR**

- A variable-length string
- We can specify the maximum amount of characters: `VARCHAR(100)`
- Examples: 'Coffee!', '-999', 'This is a sentence'

### Basic Data Types Challenge

**Challenge**

Draw a Tweets Table! At a minimum the columns must include:

- A username (max 15 characters)
- The tweet content (max 140 characters)
- Number of favorites

Make sure to specify correct MySQL data types!

**Solution**

Username would be a VARCHAR(15)
Content would be a VARCHAR(140)
Favorites would be an INT

| Username       | Content                | Favorites |
| -------------- | ---------------------- | --------- |
| 'Epitome87'    | 'This is a tweet!'     | 4         |
| 'Coolguy'      | 'My first tweet!'      | 3         |
| 'guitar_queen' | 'I love music!'        | 10        |
| 'lonely_heart' | 'Still looking 4 love' | 0         |

### Creating Tables

We can create a new table similar to how we create a new database:

```sql
CREATE TABLE <name>
(
    <column_name> <data_type>,
    <column_name> <data_type>
);
```

Example:

```sql
CREATE table cats
(
    name VARCHAR(50),
    age INT
);
```

The name of the table is commonly pluralized.

### How Do We Know It Worked?

We can see if our table creation worked by showing the tables in the current database:

```sql
SHOW TABLES;
```

If we want to know more about the tables beside just their name, such as their column names, we can run:

```sql
SHOW COLUMNS FROM <tablename>;
```

Now we can see the field, type, and other information about each column.

We can also run the shorter version of the command:

```sql
DESC <tablename>;
```

Here, DESC is short for "describe". So we are running the command to _describe_ the table.

### Dropping Tables

We can delete ("drop") a table similar to how we delete a database:

```sql
DROP TABLE <tablename>;
```

### Tables Basics Activity

**Challenge**

Create a Pastries table

- It should include 2 columns: name and quantity. Name is 50 characters max.
- Inspect your table/columns in the CLI
- Delete your table!

**Solution**

1. After connecting to the database server, ensure we are in the database we want the table to be created in. We can view our current database with `SELECT database();`. If we are not in the right one, we can navigate to the correct database with `USE <database_name>;`.
2. Create the table with the following SQL:

   ```sql
   CREATE TABLE pastries (
    name VARCHAR(50),
    quantity INT
   );
   ```

3. To view our table for successful creation, we can run:

   ```sql
    SHOW tables;
   ```

4. To see if we set up the shape of our pastries table correctly, we can run:

   ```sql
    DESC pastries;
   ```

5. To delete the pastries table, we can run:
   ```sql
   DROP TABLE pastries;
   ```

### MySQL Comments

We can create comments in our SQL code, just like any other programming language. This is achieved with `--`. This allows us to write notes and document the code.

For example:

```sql
-- This is a comment!
SHOW TABLES;
```

We can quickly ignore SQL code by putting the comment syntax before the SQL code, separated by at least one space:

```sql
-- The below SQL code is commented out, and will not be executed:
-- SHOW TABLES;
```

## Section 4: Inserting Data

##### `Originally Started & Completed: 04/28/2023`

### Section Introduction

Last section we saw how to make databases and how to create tables. But these tables were empty; they had no data! In this section we will explore tools to insert data into these tables.

We will also explore retrieving the data we insert.

### INSERT: The Basics

How do we insert data into these empty tables we created? We use an **INSERT** statement:

```sql
INSERT INTO <tablename> (<column1_name>, <column2_name>)
VALUES (<value1>, <value2>)
```

**Example**:

```sql
INSERT INTO cats(name, age)
VALUES ('Jetson', 7);
```

We specify the columns we want to insert, and in what order the data is to be expected. We then provide the values to those columns, following the same order we provided.

### Code Challenge

Re-create the cats table:

```sql
CREATE TABLE cats (
   name VARCHAR(50),
   age INT
);
```

Insert a cat:

```sql
INSERT INTO cats (name, age)
VALUES ('Blue Steele', 5);
```

And another:

```sql
INSERT INTO cats (name, age)
VALUES ('Jenkins', 7);
```

We could have also added multiple cats at the same time:

```sql
INSERT INTO cats (name, age)
VALUES ('Tonks', 11), ('Wedge', 10);
```

### A Quick Preview of SELECT

So, we have allegedly inserted data into our cats table. But how do we know it worked as we intended?

```sql
SELECT * FROM <table>
```

This retrieves _all_ data we have from a table.

### Code Challenge

To view all rows in our cats table:

```sql
SELECT * FROM cats;
```

### Multi-Inserts

The order we insert our column/value pairs matters! If we tell SQL our name column comes first, we must provide the name first in the values list. However, _between INSERT_ commands we _can_ mix the order up:

```sql
-- Let's put name in before age:
INSERT INTO cats (name, age)
VALUES ('Patrick', 4);

-- Now let's add another cat, its age before name:
INSERT INTO cats (age, name)
VALUES (5, 'Spongebob');
```

Therefore, we do not need to know or memorize a particular order of columns in our table, as the ordering _between_ separate inserts does not matter.

If we mismatch column/value pairs, we will be greeted with an error if the data types conflict!

We can also do **multiple inserts**:

```sql
INSERT INTO cats (name, age)
VALUES ('Meatball', 5), ('Turkey', 1), ('Potato Face', 15);
```

### Code Challenge

-- Single insert (switching order of name and age):

```sql
INSERT INTO cats (age, name)
VALUES (2, 'Beth');
```

-- Multiple Insert:

```sql
INSERT INTO cats (name, age)
VALUES
   ('Meatball', 5),
   ('Turkey', 1),
   ('Potato Face', 15);
```

### INSERT: Exercise

**Exercise**

Create a _people_ table:

- first_name - 20 char limit
- last_name - 20 char limit
- age - int

Insert your first person:

| first_name | last_name | age |
| ---------- | --------- | --- |
| 'Tina'     | 'Belcher' | 13  |

Insert your second person:

| first_name | last_name | age |
| ---------- | --------- | --- |
| 'Bob'      | 'Belcher' | 42  |

Then insert multiple:

| first_name | last_name    | age |
| ---------- | ------------ | --- |
| 'Linda'    | 'Belcher'    | 45  |
| 'Philip'   | 'Frond'      | 38  |
| 'Calvin'   | 'Fischoeder' | 70  |

**Solution**

1.  ```sql
    CREATE TABLE people (
      first_name VARCHAR(20),
      last_name VARCHAR(20),
      age INT
    );
    ```

2.  ```sql
    INSERT INTO people (first_name, last_name, age)
    VALUES ('Tina', 'Belcher', 13);
    ```

3.  ```sql
    INSERT INTO people (age, last_name, first_name)
    VALUES (42, 'Belcher', 'Bob');
    ```

4.  ```sql
    INSERT INTO people (first_name, last_name, age)
    VALUES
      ('Linda', 'Belcher', 45),
      ('Philip', 'Frond', 38),
      ('Calvin', 'Fischoeder', 70);
    ```

Remember, after we create the table we can check it with:

```sql
DESC people;
```

And we can see if our data was correctly inserted with:

```sql
SELECT * FROM people;
```

Finally, since we do not want this table to persist, we can delete it:

```sql
DROP TABLE people;
```

And verify it was deleted:

```sql
SHOW TABLES;
```

### Working With NOT NULL

Remember when we ran `DESC <table>` and saw a column _NULL_ with a Yes or No value? Here is what the output may look like:

| Field | Type        | Null | Key | Default | Extra |
| ----- | ----------- | ---- | --- | ------- | ----- |
| name  | varchar(20) | YES  |     | NULL    |       |
| age   | int         | YES  |     | NULL    |       |

NULL is a value in SQL that means _no value_ -- it means lack of a value. The value is unknown! The 'Yes' and 'No' values we saw tell us whether we are allowed to have a NULL value in that column.

Sometimes we may want intentionally empty (NULL) columns. Sometimes we don't. In the cases where we do not, we set up this constraint when creating our table:

```sql
CREATE TABLE cats (
  name VARCHAR(20) NOT NULL,
  age INT NOT NULL
)
```

Now we are not allowed to insert a cat that does not have a name or age specified.

### Sidenote: Quotes in MySQL

When we are working with text in MySQL, we provide those values in quotes. While MySQL allow both single and double quotes for strings, other flavors of SQL do not. For this reason, we conventionally prefer the use of single quotes.

But what if we have a literal quote / apostrophe within our string? How would we work with that? We need to **escape** that apostrophe with a `\`:

```sql
INSERT INTO shops (name)
VALUES ('Mario\'s Pizza');
```

### Adding DEFAULT Values

Going back to the output of our `DESC <table>` command, there was a `Default` column. This describes the default value of a column. By default there is no default! But we can change this:

```sql
CREATE table cats (
  name VARCHAR(50) DEFAULT 'Kitty Cat',
  age INT DEFAULT 99
);
```

Isn't setting `NOT NULL` _and_ `DEFAULT` redundant? After all, if we will be given a default value even when providing none, nothing will ever be `NULL`, right?

Nope! We can still manually set things to `NULL` if we do not specify `NOT NULL`:

```sql
INSERT INTO cats (name, age)
VALUES (NULL, 3)
```

### Code Challenge

Define a table with a DEFAULT name specified:

```sql
CREATE TABLE cats  (
    name VARCHAR(20) DEFAULT 'no name provided',
    age INT DEFAULT 99
);
```

Notice the change when you describe the table:

```sql
DESC cats;
```

Insert a cat without a name:

```sql
INSERT INTO cats (age) VALUES(13);
```

Or a nameless, ageless cat:

```sql
INSERT INTO cats () VALUES();
```

Combine NOT NULL and DEFAULT:

```sql
CREATE TABLE cats4  (
    name VARCHAR(20) NOT NULL DEFAULT 'unnamed',
    age INT NOT NULL DEFAULT 99
);
```

### Introducing Primary Keys

Once again, revisiting our output when we run `DESC <table>`, we saw a `Key` column, which were all empty in our case. What's up with that?

We need to be able to distinguish rows easily from one another, especially when they are allowed to store identical data (such as names). We can give unique IDs to each row. We _could_ just add an "id" column into our table, but what would stop us from giving multiple rows the same ID? Then they would not truly be identifiable as unique.

Instead, we make use of a **Primary Key**. A primary key is a _unique identifier_ for each row. We can add on the `PRIMARY KEY` constraint when creating our table:

```sql
CREATE TABLE unique_cats (
  cat_id INT PRIMARY KEY,
  name VARCHAR(100),
  age INT
);
```

Now, when we run `DESC unique_cats`, we get "PRI" under our "Key" column. We _must_ provide an ID for each cat we insert, and each ID _must_ be unique!

However, keeping track of what IDs we have used already, or which to use next, can be rather tedious. We will learn a better way to use the power of primary keys shortly.

Note: Using `NOT NULL` with `PRIMARY KEY` is redundant! By nature, primary keys can never be null.

### Code Challenge

One way of specifying a PRIMARY KEY

```sql
CREATE TABLE unique_cats (
	cat_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL
);
```

Another option:

```sql
CREATE TABLE unique_cats2 (
	cat_id INT,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    PRIMARY KEY (cat_id)
);
```

In the second option, we report the primary key later on -- not directly when the column that serves as the primary key is being defined.

### Working With AUTO_INCREMENT

To avoid the headache of manually assigning unique IDs to our primary key columns, we can make use of **AUTO_INCREMENT**.
Using this keyword will automatically increment (starting at 1, although we can change that default) our IDs.

We will be combining `AUTO_INCREMENT` with `PRIMARY KEY` all the time:

```sql
CREATE TABLE <table> (
  id INTO AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100)
);
```

Now we do not manually have to specify that we will be inserting into the primary key column, nor do we manually provide a value for that column:

```sql
INSERT INTO <table> (name)
VALUES ('Matthew');
```

### Code Challenge

AUTO_INCREMENT:

```sql
CREATE TABLE unique_cats3 (
    cat_id INT AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    PRIMARY KEY (cat_id)
);
```

We could have also written:

```sql
CREATE TABLE unique_cats3 (
  cat_id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  age INT NOT NULL
);
```

### Create Table Insert Exercise

**Exercise**

Define an Employees table, with the following fields:

- id: number (automatically increments) and primary key
- last_name: text, mandatory
- first_name: text, mandatory
- middle_name: text, not mandatory
- age: number, mandatory
- current_status: text, mandatory, defaults to 'employed'

**Solution**

```sql
CREATE TABLE employees (
  id INT PRIMARY KEY AUTO_INCREMENT,
  last_name VARCHAR(100) NOT NULL,
  first_name VARCHAR(100) NOT NULL,
  middle_name VARCHAR(100),
  age INT NOT NULL,
  current_status VARCHAR(100) NOT NULL DEFAULT 'employed'
);
```

## Section 5: CRUD Basics

##### `Originally Started & Completed: 04/29/2023`

### Section Introduction

In this section we will learn how to implement **CRUD** operators with MySQL.

### Introducing CRUD

**CRUD** is an acronym (not specific to SQL):

**C**reate
**R**ead
**U**pdate
**D**elete

These are operators we will often do on rows of data.

We've already seen how to **create** individual rows using `INSERT INTO`. We've also seen that we can insert multiple rows at once.

### Getting Our New Dataset

To make working in this section easier, we will get a new set of data to practice what we learn on. Delete any old cats tables and create a new one:

```sql
CREATE TABLE cats (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(100),
  breed VARCHAR(100),
  age INT
);

INSERT INTO cats(name, breed, age)
VALUES ('Ringo', 'Tabby', 4),
       ('Cindy', 'Maine Coon', 10),
       ('Dumbledore', 'Maine Coon', 11),
       ('Egg', 'Persian', 4),
       ('Misty', 'Tabby', 13),
       ('George Michael', 'Ragdoll', 9),
       ('Jackson', 'Sphynx', 7);
```

### Officially Introducing SELECT

For the **Read** part of CRUD: How do we retrieve and search data already in a table?

We've already been quickly introduced to the answer: `SELECT`!

So far we have only seen how to select every column for every row from a table with:

```sql
SELECT * FROM <table>;
```

The `*` is what lets SQL know we want every column and every row. But we can refine our reads further. We do so with **SELECT Expressions** (what columns do we want?), which can be more than just `*`:

```sql
SELECT <column_name> from <table>;
```

### The WHERE Clause

`WHERE` allows us to narrow down the rows we are working with.

- Not just limited to being used with `SELECT`

**Example**

```sql
SELECT * FROM cats WHERE age = 4;
SELECT * FROM cats WHERE name = 'Tonks';
```

### Rapid Fire Exercises

1. Select the cat ID for all rows:

```sql
SELECT cat_id FROM cats;
```

2. Select the name and breed for all rows:

```sql
SELECT name, breed FROM cats;
```

3. Select just the Tabby cats:

```sql
SELECT name, age FROM cats WHERE breed = 'Tabby';
```

4. Select the cat ID and ages for cats that have the same ID as their age:

```sql
SELECT cat_id, age FROM cats WHERE cat_id = age;
```

### Aliases

We can rename columns using an _alias_, using the `AS` keyword.

**Example**

```sql
SELECT cat_id AS id FROM cats;
SELECT name as cat_name FROM cats;
```

### Using UPDATE

How do we alter existing data? We make use of the `UPDATE` keyword!

```sql
UPDATE <table>
SET <column> = <new_value>
WHERE <condition>
```

**Example**

```sql
UPDATE cats
SET breed = 'Shorthair'
WHERE breed = 'Tabby';
```

**Note:** We had to specify the `WHERE` in order to be more precise with our update. Otherwise, every row would receive the update!

We can do multiple updates at once. The following will do an update on two columns at once, for every row:

```sql
UPDATE employees
SET current_status = 'Fired', last_name = 'Who Cares?';
```

### A Quick Rule of Thumb

Try SELECTing before you UPDATE! This allows you to see if your target for the updating is what you actually want and expect.

### UPDATE Exercise

**Exercise**

1. Change Jackson's name to 'Jack'
2. Change Ringo's breed to 'British Shorthair'
3. Update both Main Coons' ages to be 12

**Solution**

```sql
UPDATE cats
SET name = 'Jack'
WHERE name = 'Jackson';
```

```sql
UPDATE cats
SET breed = 'British Shorthair'
WHERE name = 'Ringo';
```

```sql
UPDATE cats
SET age = 12
WHERE breed = 'Main Coon';
```

### Introducing DELETE

Time for the D in CRUD: Delete! This will remove the specified row(s) from the table:

```sql
DELETE FROM <table> WHERE <condition>
```

Note we _could_ leave out the `WHERE` from a `DELETE`, but that would delete all rows, leaving us with an empty table!

**Example**

```sql
DELETE FROM cats
WHERE name = 'Egg';
```

### DELETE Exercise

**Exercise**

1. Delete all 4 year old cats
2. Delete cats whose age is the same as their ID
3. Delete all cats 🙀

**Solution**

```sql
DELETE FROM cats
WHERE age = 4;
```

```sql
DELETE FROM cats
WHERE age = cat_id;
```

```sql
DELETE FROM cats;
```

## Section 6: CRUD Challenge

### Section Introduction

This section will be purely exercises to help reinforce SQL CRUD operations.

### Introducing the CRUD Challenge

We are spring cleaning! We have a surplus of shirts that we want to give away, so we want to create a shirt database. Let's do the following:

1. Create a new database called _shirts_db_
2. Create a new table called _shirts_
3. It will have a shirt_id, article, color, size, and last_worn
4. Insert the starting data (in a single line):

   ```
   ('t-shirt', 'white', 'S', 10),
   ('t-shirt', 'green', 'S', 200),
   ('polo shirt', 'black', 'M', 10),
   ('tank top', 'blue', 'S', 50),
   ('t-shirt', 'pink', 'S', 0),
   ('polo shirt', 'red', 'M', 5),
   ('tank top', 'white', 'S', 200),
   ('tank top', 'blue', 'M', 15)
   ```

5. Add a new shirt: Purple polo shirt, size M, last worn 50 days ago
6. Select all shirts, but only print out article and color
7. Select all medium shirts, but print everything but shirt_id
8. Update all polo shirts; change their size to L
9. Update the shirt that was last worn 15 days ago to 0 days ago
10. Update all white shirts; change size to 'XS' and color to 'off white'
11. Delete all old shirts last worn exactly 200 days ago
12. Delete all tank tops; our tastes have changed!
13. Delete all shirts; oh no!
14. Drop the entire shirts table; oh god, no!

**Solution for CREATE Exercises**

Create the database:

```sql
CREATE DATABASE shirts_db;
```

Let's see if it created properly:

```sql
SHOW databases;
```

Good! We see it in the list of databases; now let's interact with it:

```sql
USE shirts_db;
```

Okay, but are we actually interacting with the correct database? Let's see:

```sql
SELECT database();
```

Whew!

Now create the shirts table:

```sql
CREATE TABLE shirts (
  shirt_id INT PRIMARY KEY AUTO_INCREMENT,
  article VARCHAR(50),
  color VARCHAR(50),
  size VARCHAR(5),
  last_worn INT
);
```

But did it actually get created? Let's look:

```sql
SHOW tables;
```

Okay, it exists. But let's see if the table looks how we envisioned:

```sql
DESC shirts;
```

And add some starter data:

```sql
INSERT INTO shirts (article, color, size, last_worn)
VALUES ('t-shirt', 'white', 'S', 10),
   ('t-shirt', 'green', 'S', 200),
   ('polo shirt', 'black', 'M', 10),
   ('tank top', 'blue', 'S', 50),
   ('t-shirt', 'pink', 'S', 0),
   ('polo shirt', 'red', 'M', 5),
   ('tank top', 'white', 'S', 200),
   ('tank top', 'blue', 'M', 15);
```

Finally, let's add that new purple shirt:

```sql
INSERT INTO shirts (article, color, size, last_worn)
VALUES ('polo shirt', 'purple', 'M', 50);
```

**Solution for READ Exercises**

```sql
SELECT article, color
FROM shirts;
```

```sql
SELECT article, color, size, last_worn
FROM shirts
WHERE size = 'M';
```

**Solution for UPDATE Exercises**

```sql
UPDATE shirts
SET size = 'L'
WHERE article = 'polo shirt';
```

```sql
UPDATE shirts
SET last_worn = 0
WHERE last_worn = 15;
```

```sql
UPDATE shirts
SET size = 'XS', color = 'off white'
WHERE color = 'white';
```

**Solution for DELETE Exercises**

```sql
DELETE FROM shirts
WHERE last_worn = 200;
```

```sql
DELETE FROM shirts
WHERE article = 'tank top';
```

```sql
DELETE FROM shirts;
```

```sql
DROP TABLE shirts;
```

## Section 7: String Functions

##### `Originally Started: 05/01/2023, Originally Completed: 5/04/2023`

### Section Introduction

In this section we will explore some of the operations we can perform on string data. We will do so on a books database that we create.

### The World of String Functions

These are built-in operators that we can perform on text columns. There are LOTS!

### Loading Our Books Data

We will load up our books table by running the provided SQL file.

From within the MySQL shell, we can run the following to execute an SQL file:

```
source file_name.sql
```

### CONCAT

Short for concatenate, the `CONCAT` function combines strings together.

While we would typically concatenate data we retrieve from our table, we can also do so on hard-coded pieces of text:

```sql
SELECT CONCAT('H', 'e', 'l', 'l', 'o');
-- Result: Hello
```

A more practical example, using our books table:

```sql
SELECT CONCAT(author_fname, ' ', author_lname)
FROM books;
```

This will produce a column with the title 'CONCAT(author_fname, ' ', author_lname)', which is not very useful. Typically we rename the result of a CONCAT:

```sql
SELECT CONCAT(author_fname, ' ', author_lname) AS author_name
FROM books;
```

We can also use the variant `CONCAT_WS` (concatenation with separator). It is similar to the above concatenate method, but we provide the character we want to use as the separator as the first argument. For example:

```sql
SELECT CONCAT_WS('!', 'Hi', 'Bye', 'LOL');
-- Result: Hi!Bye!lol
```

### SUBSTRING

The `SUBSTRING` (and also `SUBSTR`) methods takes a single larger string and returns a portion of it. There are a few variations on the way we can call it, but the first argument is always the sample string.

In one variant, the next argument is the starting substring index (starting from 1), and the third argument is the desired length. This will return a substring within that index:

```sql
SELECT SUBSTRING('Hello World', 1, 4);
-- Result: Hell
```

We can also provide a single argument after the sample string. This will be the starting index. The resulting substring will be up until the ending of the string:

```sql
SELECT SUBSTRING('Hello World', 7);
-- Result: World
```

We can also use a negative starting index. This will count backward from the end of the string, and then go forward until the end:

```sql
SELECT SUBSTRING('Hello World', -3);
-- Result: Wor
```

In our books table, let's shorten our book titles to only 15 characters:

```sql
SELECT SUBSTRING(title, 1, 15) FROM books;
```

There is also a `SUBSTR()` variation; in case you want to save a few keystrokes!

### Combining String Functions

String functions can be easily combined. For example, if we want to shorten our book titles, and have them end with '...', we can do so with:

```sql
SELECT CONCAT(SUBSTR(title, 1, 10), '...') AS short_title
FROM books;
```

And if we want to write each author's name in a `FirstInitial.LastInitial.` format:

```sql
SELECT CONCAT(SUBSTR(author_fname, 1, 1), '.', SUBSTR(author_lname, 1, 1), '.')) AS author_initials
FROM books;
```

In other words, just like most programming languages, we can pass the result of one function to another.

### Sidenote: SQL Formatting

Although SQL does not care about how we format our code, most editors will have functionality to format pleasantly.

### REPLACE

Replace parts of a string with the `REPLACE` function.

```sql
REPLACE(str, from_str, to_str);
```

**Example:**

```sql
SELECT REPLACE('Hello World', 'Hell', '%$#@');
-- Output: %$#@o World

SELECT REPLACE('cheese bread coffee milk', ' ', ' and ');
-- Output: cheese and bread and coffee and milk
```

```sql
SELECT REPLACE(title, ' ', '-')
FROM books;
-- Output: Our book names with hyphens in between each word of the title
```

### REVERSE

To reverse a string, we can use the `REVERSE` function.

```sql
SELECT REVERSE ('Hello World');
-- Output: 'dlroW olleH'
```

### CHAR_LENGTH

To count the characters in a string, we can use the `CHAR_LENGTH` function.

```sql
SELECT CHAR_LENGTH('Hello');
-- Output: 5
```

```sql
SELECT CHAR_LENGTH(title) FROM books;
```

**Note:** Don't confuse this function with `LENGTH(str)`, which measures the length of the string _measured in bytes_. Although sometimes they produce the same results, this is not always the case.

### UPPER & LOWER

To change an entire string's case, we can use `UPPER` and `LOWER`. We can also use their alias forms, `UCASE` and `LCASE`.

```sql
SELECT UPPER('Hello'); -- 'hello'
SELECT UCASE('Hello'); -- 'hello'

SELECT LOWER('Hello'); -- 'HELLO'
SELECT LCASE('Hello'); -- 'HELLO'
```

```sql
SELECT CONCAT('I LOVE ', UPPER(title), ' !!!')
FROM books; -- 'I LOVE <book_name> !!!'
```

### Other String Functions

While there are many string functions in SQL, the following are some of the more useful ones.

`INSERT`:

```sql
INSERT(str, pos, len, newstr)
```

Insert some substring into another string. Returns the string str, with the substring beginning at position pos and len characters long replaced by the string newstr. Returns the original string if pos is not within the length of the string. Replaces the rest of the string from position pos if len is not within the length of the rest of the string. Returns NULL if any argument is NULL.

**Example**

```sql
SELECT INSERT('Hello Bobby', 6, 0, ' There');
-- 'Hello There Bobby'

SELECT INSERT('Hello Bobby', 6, 4, ' There');
-- 'Hello Thereby'
```

`LEFT`:

```sql
LEFT(str, len)
```

Returns the leftmost _len_ characters from the string _str_, or _NULL_ if any argument is _NULL_.
**Example**

```sql
SELECT LEFT('foobarbar', 5);
-- 'fooba'
```

`RIGHT`:

```sql
RIGHT(str, len)
```

Returns the rightmost _len_ characters from the string _str_, or _NULL_ if any argument is _NULL_.
**Example**

```sql
SELECT RIGHT('foobarbar', 5);
-- 'arbar'
```

`REPEAT`:

```sql
REPEAT(str, count)
```

Returns a string consisting of string _str_ repeated _count_ times. If _count_ is less than 1, returns an empty string. Returns _NULL_ if _str_ or _count_ is _NULL_.

```sql
SELECT REPEAT('MySQL', 3);
-- 'MySQLMySQLMySQL'
```

`TRIM`:

```sql
TRIM([{BOTH | LEADING | TRAILING} [remstr] FROM] str), TRIM([remstr FROM] str)
```

Returns the string _str_ with all _remstr_ prefixes or suffixes removed. If none of the specifiers BOTH, LEADING, or TRAILING is given, BOTH is assumed. _remstr_ is optional and, if not specified, spaces are removed

```sql
SELECT TRIM('    Hello World  '); -- 'Hello World'
SELECT TRIM(LEADING '.' FROM '...San Antonio..'); -- 'San Antonio..'
SELECT TRIM(TRAILER '.' FROM '...San Antonio..'); -- '...San Antonio'
SELECT TRIM(BOTH '.' FROM '...San Antonio..'); -- 'San Antonio'
```

### String Functions Exercise

**Exercise**

1. Reverse and Uppercase the following sentence: 'Why does my cat look at me with such hatred?'
2. What does this print out: `SELECT REPLACE(CONCAT('I', ' ', 'like', ' ', 'cats'), ' ', '-');`
3. Replace spaces in our book titles with '->', and name the generated column as title.
4. Print the last name of every author in a column called 'forwards', and the reverse of their last name in a column called 'backwards'.
5. Print out the author's full name in all capitals.
6. Print out the following for each book: `<title> was released in <release_year>`.
7. Print book titles and the length of each title. Call the length character_count.
8. Generate the first 10 characters of each book title followed by '...' in a column called short title. Then print out the last name of an author, followed by a comma, followed by their first name in a column called author. Finally, in a column called stock print out the sentence `<stock_quantity> in stock `for each book.

**Solution**

1.

```sql
SELECT REVERSE(UPPER('Why does my cat look at me with such hatred?'));
```

2. The result of the following MySQL code is **'I-like-cats'**.

```sql
SELECT REPLACE(CONCAT('I', ' ', 'like', ' ', 'cats'), ' ', '-');
```

3.

```sql
SELECT REPLACE(title, ' ', '->') AS title
FROM books;
```

4.

```sql
SELECT author_lname AS forwards, REVERSE(author_lname) AS backwards
FROM books;
```

5.

```sql
SELECT UPPER(CONCAT(author_fname, ' ', author_lname)) AS 'full name in caps'
FROM books;
```

6.

```sql
SELECT CONCAT(title, ' was released in ', released_year) AS blurb
FROM books;
```

7.

```sql
SELECT title, CHAR_LENGTH(title) AS character_count
FROM books;
```

8.

```sql
SELECT CONCAT(SUBSTR(title, 1, 10), REPEAT('.', 3)) AS short_title, CONCAT_WS(',', author_lname, author_fname) AS author, CONCAT(stock_quantity, ' in stock') AS quantity
FROM books;
```
