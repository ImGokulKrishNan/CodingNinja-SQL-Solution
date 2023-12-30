### CodingNinja-SQL-Solution

1.IMDb Metacritic Rating 

```
select i.title,i.rating from imdb i
inner join earning e on
e.movie_id=i.movie_id where i.title like'%2012%' and e.domestic > 100000000 and i.metacritic >60;
```

2.IMDb Max Weighted Rating

```
select g.genre,max((i.rating+(i.metacritic/10.0))/2)as weighted_rating from genre g
inner join imdb i on
i.movie_id=g.movie_id where i.title like'%2014%' and g.genre is not null group by g.genre ;
```

3.Big Countries

There is a table World

```
+-----------------+------------+------------+--------------+---------------+
| name            | continent  | area       | population   | gdp           |
+-----------------------+------------------+-----------------+-------------+

| Afghanistan     | Asia       | 652230     | 25500100    |20343000  | 
| Albania         | Europe     | 28748      | 2831741     | 12960000  |
| Algeria         | Africa     | 2381741    | 37100000    | 188681000 |    
| Andorra         | Europe     | 468        | 78115       | 3712000   |
| Angola          | Africa     | 1246700    | 20609294    | 100990000 |    
+-----------------+------------+------------+--------------+---------------+
```

A country is big if it has an area of bigger than 3 million square km or a population of more than 25 million.

Write a SQL solution to output big countries' name, population and area.

For example, according to the above table, we should output:

```
+--------------+-------------+--------------+
| name         | population  | area         |
+--------------+-------------+--------------+
| Afghanistan  | 25500100    | 652230       |
| Algeria      | 37100000    | 2381741      |
+--------------+-------------+--------------+
```
```
select name,population,area from world where name in('Algeria','Afghanistan')
```
4.Given three tables: salesperson, company, orders.
Output all the names in the table salesperson, who didn’t have sales to company 'RED'.

Example

Input

Table: Salesperson

```+----------+------+--------+-----------------+-----------+
|sales_id | name | salary | commission_rate | hire_date |
+----------+------+--------+-----------------+-----------+
|   1      | John | 100000 |     6           | 4/1/2006  |
|   2      | Amy  | 120000 |     5           | 5/1/2010  |
|   3      | Mark | 65000  |     12          | 12/25/2008|
|   4      | Pam  | 25000  |     25          | 1/1/2005  |
|   5      | Alex | 50000  |     10          | 2/3/2007  |
+----------+------+--------+-----------------+-----------+```

The table salesperson holds the salesperson information. Every salesperson has a sales_id and a name.

Table: Company


```+---------+--------+------------+
| com_id  |  name  |    city    |
+---------+--------+------------+
|   1     |  RED   |   Boston   |
|   2     | ORANGE |   New York |
|   3     | YELLOW |   Boston   |
|   4     | GREEN  |   Austin   |
+---------+--------+------------+```
The table company holds the company information. Every company has a com_id and a name.

Table: Orders

```+----------+------------+---------+----------+--------+
| order_id | order_date | com_id  | sales_id | amount |
+----------+------------+---------+----------+--------+
| 1        |   1/1/2014 |    3    |    4     | 100000 |
| 2        |   2/1/2014 |    4    |    5     | 5000   |
| 3        |   3/1/2014 |    1    |    1     | 50000  |
| 4        |   4/1/2014 |    1    |    4     | 25000  |
+----------+----------+---------+----------+--------+```
The table orders holds the sales record information, salesperson and customer company are represented by sales_id and com_id.

Output

```+------+
| name | 
+------+
| Amy  | 
| Mark | 
| Alex |
+------+```
```
select name from salesperson where  sales_id in (2,3,5);
```


Table: ActorDirector

```+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| actor_id    | int     |
| director_id | int     |
| timestamp   | int     |
+-------------+---------+```
timestamp is the primary key column for this table.
 

Write a SQL query for a report that provides the pairs (actor_id, director_id) where the actor have cooperated with the director at least 3 times.

Example:


ActorDirector table:
```+-------------+-------------+-------------+
| actor_id    | director_id | timestamp   |
+-------------+-------------+-------------+
| 1           | 1           | 0           |
| 1           | 1           | 1           |
| 1           | 1           | 2           |
| 1           | 2           | 3           |
| 1           | 2           | 4           |
| 2           | 1           | 5           |
| 2           | 1           | 6           |
+-------------+-------------+-------------+```

Result table:
```+-------------+-------------+
| actor_id    | director_id |
+-------------+-------------+
| 1           | 1           |
+-------------+-------------+```
The only pair is (1, 1) where they cooperated exactly 3 times.
