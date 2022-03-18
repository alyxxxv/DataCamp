# Introduction to SQL

**Onboarding | Query Result**

Notice the query result tab in the bottom right corner of your screen. This is where the results of your SQL queries will be displayed.
Run this query in the editor and check out the resulting table in the query result tab!

``` sql
SELECT name FROM people;
```
**Beginning your SQL journey**

Now that you're familiar with the interface, let's get straight into it.
SQL, which stands for Structured Query Language, is a language for interacting with data stored in something called a relational database.
You can think of a relational database as a collection of tables. A table is just a set of rows and columns, like a spreadsheet, which represents exactly one type of entity. For example, a table might represent employees in a company or purchases made, but not both.
Each row, or record, of a table contains information about a single entity. For example, in a table representing employees, each row represents a single person. Each column, or field, of a table contains a single attribute for all rows in the table. For example, in a table representing employees, we might have a column containing first and last names for all employees.

# **Selecting Multiple Column**

``` sql
SELECT name, birthdate
FROM people;
```
Sometimes, you may want to select all columns from a table. Typing out every column name would be a pain, so there's a handy shortcut:
``` sql
SELECT *
FROM people;
```
If you only want to return a certain number of results, you can use the **LIMIT**  keyword to limit the number of rows returned:
``` sql
SELECT *
FROM people
LIMIT 10;
```
# **SELECT DISTINCT**

Often your results will include many duplicate values. If you want to select all the unique values from a column, you can use the DISTINCT keyword.
``` sql 
--Digunakan biar tidak ada data yang double(duplikat)
SELECT DISTINCT language
FROM films;
```

# **COUNT**

The COUNT() function lets you do this by returning the number of rows in one or more columns.
``` sql 
--memberikan informasi mengenai jumlah baris pada tabel
SELECT COUNT(*)
FROM people;
```
**Practice with COUNT**

bisa memberikan informasi mengenai jumlah pada data kolom di suatu tabel. 
``` sql 
--For example, to count the number of birth dates present in the people table:
SELECT COUNT(birthdate)
FROM people;
```
It's also common to combine COUNT() with DISTINCT to count the number of distinct values in a column.

``` sql 
--For example, this query counts the number of distinct birth dates contained in the people table:
SELECT COUNT(DISTINCT birthdate)
FROM people;
```
# **Filtering**

 In SQL, the WHERE keyword allows you to filter based on both text and numeric values in a table. There are a few different comparison operators you can use:
 
1. = equal

2. <> not equal

3. < less than

4. '>' greater than

5. <= less than or equal to

6. '>=' greater than or equal to

For example, you can filter text records such as title. The following code returns all films with the title 'Metropolis':
``` sql 
SELECT title
FROM films
WHERE title = 'Metropolis';
```
contoh lain
``` sql 
SELECT *
FROM films
WHERE budget > 10000;
``` 

**Simple filtering of text**
``` sql 
--For example, this query gets the titles of all films which were filmed in China:
SELECT title
FROM films
WHERE country = 'China';
``` 

**WHERE AND**
``` sql 
--give title of films on (1994< release_year<2000)
SELECT title
FROM films
WHERE release_year > 1994
AND release_year < 2000;
``` 
or 
``` sql 
SELECT title
FROM films
WHERE release_year > 1994 AND < 2000;
``` 
**OR**
What if you want to select rows based on multiple conditions where some but not all of the conditions need to be met? For this, SQL has the OR operator.
``` sql 
--For example, the following returns all films released in either 1994 or 2000:
SELECT title
FROM films
WHERE release_year = 1994
OR release_year = 2000;
```
**WHERE AND OR**
```sql
--For example, the following returns all films released in either 1994 or 2000:
SELECT title
FROM films
WHERE release_year = 1994
OR release_year = 2000;
```
```sql
--When combining AND and OR, be sure to enclose the individual clauses in parentheses, like so:
SELECT title
FROM films
WHERE (release_year = 1994 OR release_year = 1995)
AND (certification = 'PG' OR certification = 'R');
```
**BETWEEN**
```SQL 
--Checking for ranges like this is very common, so in SQL the BETWEEN keyword provides a useful shorthand for filtering values within a specified range. This query is equivalent to the one above:
SELECT title
FROM films
WHERE release_year
BETWEEN 1994 AND 2000;
```
example again
```sql
SELECT name
FROM kids
WHERE age BETWEEN 2 AND 12
AND nationality = 'USA';
```
example again
```sql 
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 AND 2000
AND budget > 100000000
AND (language = 'Spanish' OR language = 'French')
```
**WHERE IN**

 The IN operator allows you to specify multiple values in a WHERE clause, making it easier and quicker to specify multiple OR conditions!
 ```sql
 SELECT name
FROM kids
WHERE age IN (2, 4, 6, 8, 10);
```

# **Introduction to NULL and IS NULL**
In SQL, NULL represents a missing or unknown value. You can check for NULL values using the expression IS NULL. For example, to count the number of missing birth dates in the people table:
```sql
SELECT COUNT(*)
FROM people
WHERE birthdate IS NULL;
```
As you can see, IS NULL is useful when combined with WHERE to figure out what data you're missing.

Sometimes, you'll want to filter out missing values so you only get results which are not **NULL** . To do this, you can use the **IS NOT NULL** operator.

For example, this query gives the names of all people whose birth dates are not missing in the people table.
```sql
SELECT name
FROM people
WHERE birthdate IS NOT NULL;
```

# **LIKE and NOT LIKE**
the WHERE clause can be used to filter text data. However, so far you've only been able to filter by specifying the exact text you're interested in. In the real world, often you'll want to search for a pattern rather than a specific text string.

In SQL, the LIKE operator can be used in a WHERE clause to search for a pattern in a column. To accomplish this, you use something called a wildcard as a placeholder for some other values. There are two wildcards you can use with LIKE:

The % wildcard will match zero, one, or many characters in text. For example, the following query matches companies like 'Data', 'DataC' 'DataCamp', 'DataMind', and so on:

```sql
SELECT name
FROM companies
WHERE name LIKE 'Data%';
```
The _ wildcard will match a single character. For example, the following query matches companies like 'DataCamp', 'DataComp', and so on:
```sql 
SELECT name
FROM companies
WHERE name LIKE 'DataC_mp';
```
You can also use the NOT LIKE operator to find records that don't match the pattern you specify.

# **Aggregate functions**
**Average**
```sql 
SELECT AVG(budget)
FROM films;
```
**MIN and MAX**
```sql 
SELECT MAX(budget)
FROM films;
```
**SUM**
```sql
SELECT SUM(budget)
FROM films;
```

**Combining aggregate functions with WHERE**
```sql
SELECT SUM(budget)
FROM films
WHERE release_year >= 2010;
```
```sql 
SELECT AVG(gross)
FROM films
WHERE title LIKE 'A%';
```
# **Aliasing**
 SQL allows you to do something called aliasing. Aliasing simply means you assign a temporary name to something. To alias, you use the AS keyword, which you've already seen earlier in this course. (Intinya aliasing ini kek mengganti nama kolom sesuai kita biar ga bingung)

For example, in the above example we could use aliases to make the result clearer:
```sql 
SELECT MAX(budget) AS max_budget,
       MAX(duration) AS max_duration
FROM films;
```
# **ORDER BY**
In SQL, the ORDER BY keyword is used to sort results in ascending or descending order according to the values of one or more columns.

By default ORDER BY will sort in ascending order (intinya buat mengurutkan). If you want to sort the results in descending order, you can use the DESC keyword. For example,
```sql 
SELECT title
FROM films
ORDER BY release_year DESC;
```
# **GROUP BY**
ften you'll need to aggregate results. For example, you might want to count the number of male and female employees in your company. Here, what you want is to group all the males together and count them, and group all the females together and count them. In SQL, GROUP BY allows you to group a result by one or more columns, like so:
``` sql
SELECT sex, count(*)
FROM employees
GROUP BY sex;
```
```sql
SELECT sex, count(*)
FROM employees
GROUP BY sex
ORDER BY count DESC;
```
# **HAVING**
```sql
SELECT release_year
FROM films
GROUP BY release_year
HAVING COUNT(title) > 10;
```
**All together now**
```sql
SELECT release_year, AVG(budget) AS avg_budget, AVG(gross) AS avg_gross
FROM films
WHERE release_year > 1990
GROUP BY release_year
HAVING AVG(budget) > 60000000
ORDER BY avg_gross DESC;
```
