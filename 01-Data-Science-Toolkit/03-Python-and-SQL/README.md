# Challenge 3 : Python and SQL

We saw in lecture that data could come from various sources - among which csv files, databases, APIs, or even web pages.  
Here, we will focus on databases (the soccer database we saw in lecture) and use Python to interact with it. `Sqlite` is in fact a simple database that relies on a standalone file.

In order to interact with it, we will use a library that comes with Anaconda, called **sqlite3**. Documentation is available [here](https://docs.python.org/2/library/sqlite3.html).

## Raw SQL
Let's use [DBeaver](https://dbeaver.io/), a **universal database client** for developers, SQL programmers, database administrators and analysts.  
The data you need to peform the next steps is available for download [here](https://www.kaggle.com/hugomathien/soccer/).


Open the **SQL Editor** and write your first SQL query.

```sql
SELECT * FROM Country
```

**Execute** the query (Click on ▶️ or use keyboard shortcut `Ctrl` + `Enter`)

For the next sections, we have provided you - for each question - with a hint, and the solution itself.  
Please try not to look at the solution unless you are too stuck - in which case TAs are here, and more than happy to help !

---

### Projection
Choosing which columns the query shall return.  


🤔 Retrieve `id`, `season`, `stage` and `date` of all matches

<details><summary markdown='span'>Hint
</summary>

Once you have downloaded the Sqlite database, have a look the the `Match` table.
</details>

<details><summary markdown='span'>View solution
</summary>

```sql
SELECT id, season, stage, date
FROM "Match"
```

</details>

---

### Selection
Selecting which **rows** the query shall return.  


🤔 Retrieve matches which happened in France  

<details><summary markdown='span'>Hint 1
</summary>

You need to look at the `Match` table for a specific country ...
</details>

<details><summary markdown='span'>Hint 2
</summary>

Maybe you can find France's `id` in the `Country` table and make use of it ?
</details>


<details><summary markdown='span'>View solution
</summary>

```sql
SELECT *
FROM "Match"
WHERE country_id = 4769
```

</details>


🤔 Retrieve players named **John**
<details><summary markdown='span'>Hint
</summary>
	Try to google "LIKE keyword SQL". It might help you!    
</details>


<details><summary markdown='span'>View solution
</summary>

```SQL
SELECT *
FROM "Player"
WHERE UPPER(player_name) LIKE 'JOHN %'
```

</details>

---

### Counting
Counting the number of rows matching the **selection**  


🤔 How many players are taller than 2.00 meters?

<details><summary markdown='span'>Hint
</summary>    
    Have a look at available SQL operators online: it will help you ! The >= operator for example ...
</details>


<details><summary markdown='span'>View solution
</summary>

```SQL
SELECT COUNT(id)
FROM Player
WHERE height >= 200
```

</details>

---

### Sorting

Sorting the rows based on a column (or a group of columns)  


🤔 Who are the 10 heaviest players?

<details><summary markdown='span'>Hint
</summary>
	Have a look at "ORDER BY statement SQL" online.    
</details>


<details><summary markdown='span'>View solution
</summary>

```SQL
SELECT *
FROM Player
ORDER BY weight DESC
LIMIT 10
```

</details>

---

### Grouping

Grouping rows on a given column C (aggregating rows with a **function** where values of C column are the **same**)  


🤔 How many matches were played on a **per-country** basis?

<details><summary markdown='span'>Hint
</summary>
    The GROUP BY statement is what you are looking for !
</details>


<details><summary markdown='span'>View solution
</summary>

```SQL
SELECT COUNT(id) as match_count, country_id
FROM "Match"
GROUP BY country_id
ORDER BY match_count DESC
```

</details>


🤔 How many matches were played on a per-country basis, ignoring countries with less than 3000 matches?
<details><summary markdown='span'>Hint
</summary>
    In SQL, you can use GROUP BY and ORDER BY in the same query...
</details>


<details><summary markdown='span'>View solution
</summary>

```sql
SELECT COUNT(id) as match_count, country_id
FROM "Match"
GROUP BY country_id
HAVING match_count >= 3000
ORDER BY match_count DESC
```

</details>


🤔 How many matches were
1. won by the home team
2. won by the away team
3. finished with a draw


<details><summary markdown='span'>Hint 1
</summary>
    You need only one query ...
</details>
<details><summary markdown='span'>Hint 2
</summary>
    Have a look at SQL CASE statements online.
</details>

<details><summary markdown='span'>View solution
</summary>

```sql
SELECT 
COUNT(id) AS outcome_count,
CASE 
	WHEN home_team_goal > away_team_goal THEN 'home_win'
	WHEN home_team_goal = away_team_goal THEN 'draw'
	ELSE 'away_win'
END AS outcome
FROM "Match"
GROUP BY outcome
ORDER BY outcome_count DESC
```

</details>

---

### Querying multiple tables

It's time to `JOIN` !  


🤔 Retrieve leagues with their respective country.

<details><summary markdown='span'>Hint
</summary>
	Look up "SQL joins" online to understand how it's done !
</details>


<details><summary markdown='span'>View solution
</summary>

```SQL
SELECT l.name, c.name
FROM League l
JOIN Country c ON l.country_id = c.id
```

</details>


🤔 How many matches where played in each league (with their respective country)?
<details><summary markdown='span'>Hint
</summary>
	You need to join 3 tables together for this one !
</details>

<details><summary markdown='span'>View solution
</summary>

```sql
SELECT
	l.id,
	l.name AS league_name,
	COUNT(m.id) AS match_count,
	c.name AS country_name
FROM "Match" m
JOIN League l ON m.league_id = l.id
JOIN Country c ON l.country_id = c.id
GROUP BY l.id
ORDER BY
	match_count DESC,
	country_name ASC
```

</details>

---

## SQL & Python

Now that you have explored your data with DBeaver, and written queries, let's see how to interact with our database using Python, directly in a notebook.


- Open the Anaconda Prompt, and navigate to this exercise folder:
```bash
cd # Gets back to the $HOME directory
cd Documents/GitHub/ml-week-challenges/01-Data-Science-Toolkit/03-Python-and-SQL
```

- Once you are located in the proper folder, run the following command:

```bash
jupyter notebook
```


Open the `03-Python-and-SQL.ipynb` notebook and follow the steps !


👉 **Tips**

SQL queries tend to get pretty long, especially when you start using `WHERE` or `JOIN`. In Python,
you can use the [triple-quote](https://docs.python.org/3.2/tutorial/introduction.html#strings) syntax to write **multi-line** strings:

```python
# Find the first 3 movies with the letter `Z` in their name.
query = '''
  SELECT * FROM movies
  WHERE title LIKE "%Z%"
  ORDER BY title
  LIMIT 3
'''
rows = db.execute(query)
```

---

You're already here ! Congratulations on completing this SQL challenge 👏 

## Pushing your code to GitHub
Don't forget to push your code !

1. Open GitHub Desktop
1. It should automatically detect that the `03-Python-and-SQL.ipynb` file has changed. If not, ask a TA
1. Make sure this file is ticked, and write a _commit message_ in the bottom left form (For instance: `SQL challenges done`)
1. Click on the "Commit to `master`" button at the bottom of the form
1. Click on the "Push `origin`" button at the top of the window