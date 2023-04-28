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

## Section 5: CRUD Basics

## Section 6: CRUD Challenge

## Section 7: String Functions

```

```
