---
title: 'More on Postgres Performance'
date: 2019-10-10T03:08:00+01:00
draft: false
---

If you missed my previous post on [Understanding Postgres Performance](http://www.craigkerstiens.com/2012/10/01/understanding-postgres-performance/) its a great starting point. On this particular post I’m going to dig in to some real life examples of optimizing queries and indexes.

### It all starts with stats

I wrote about some of the [great new features in Postgres 9.2](https://postgres.heroku.com/blog/past/2012/12/6/postgres_92_now_available/) in the recent announcement on support of Postgres 9.2 on [Heroku](https://www.heroku.com). One of those awesome features, is [pg\_stat\_statements](http://www.postgresql.org/docs/9.2/static/pgstatstatements.html). Its not commonly known how much information Postgres keeps about your database (beyond the data of course), but in reality it keeps a great deal. Ranging from basic stuff like table size to cardinality of joins to distribution of indexes, and with pg\_stat\_statments it keeps a normalized record of when queries are run.

First you’ll want to turn on pg\_stat\_statments:

```
CREATE extension pg_stat_statements; 
```

What this means it would record both:

```
SELECT id FROM users WHERE email LIKE 'craig@heroku.com'; 
```

and

```
SELECT id FROM users WHERE email LIKE 'craig.kerstiens@gmail.com'; 
```

To a normalized form which looks like this:

```
SELECT id FROM users WHERE email LIKE ?; 
```

### Understanding them from afar

While Postgres collects a great deal of this information dissecting it to something useful is sometimes more mystery than it should be. This simple query will show a few very key pieces of information that allow you to begin optimizing:

```
SELECT (total_time / 1000 / 60) as total_minutes, (total_time/calls) as average_time, query FROM pg_stat_statements ORDER BY 1 DESC LIMIT 100; 
```

The above query shows three key things:

1.  The total time a query has occupied against your system in minutes
2.  The average time it takes to run in milliseconds
3.  The query itself

Giving an output something like:

```
 total_time | avg_time | query ------------------+------------------+------------------------------------------------------------ 295.761165833319 | 10.1374053278061 | SELECT id FROM users WHERE email LIKE ? 219.138564283326 | 80.24530822355305 | SELECT * FROM address WHERE user_id = ? AND current = True (2 rows) 
```

### What to optimize

A general rule of thumb is that most of your very common queries that return 1 or a small set of records should return in ~ 1 ms. In some cases there may be queries that regularly run in 4-5 ms, but in most cases ~ 1 ms or less is an ideal.

To pick where to begin I usually attempt to strike some balance between total time and long average time. In this case I’d start with the second probably, as on the first one I could likely shave an order of magnitude off, on the second I’m hopeful to shave two order of magnitudes off thus reducing the time spent on that query from a cumulative 220 minutes down to 2 minutes.

### Optimizing

From here you probably want to first example my other detail on understanding the explain plan. I want to highlight some of this with a more specific case based on the second query above. The above second query on an example data set does contain an index on user\_id and yet there’s still high query times. To start to get an idea of why I would run:

```
EXPLAIN ANALYZE SELECT * FROM address WHERE user_id = 245 AND current = True 
```

This would yield results:

```
 QUERY PLAN -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- Aggregate (cost=4690.88..4690.88 rows=1 width=0) (actual time=519.288..519.289 rows=1 loops=1) -> Nested Loop (cost=0.00..4690.66 rows=433 width=0) (actual time=15.302..519.076 rows=213 loops=1) -> Index Scan using idx_address_userid on address (cost=0.00..232.52 rows=23 width=4) (actual time=10.143..62.822 rows=1 loops=8) Index Cond: (user_id = 245) Filter: current Rows Removed by Filter: 14 Total runtime: 219.428 ms (1 rows) 
```

Hopefully not being too overwhelmed by this due to having read the other detail on [query plans](http://www.craigkerstiens.com/2012/10/01/understanding-postgres-performance/) we can see that it is using an index as expected. The difference is its having to fetch 15 different rows from the index then discard the bulk of them. The number of rows discarded is showcased by the line:

```
Rows Removed by Filter: 14 
```

_This is just one more of the many improvements in Postgres 9.2 alongside pg\_stat\_statements._

To further optimize this we would great a conditional OR composite index. A conditional would be where only current = true, where as the composite would index both values. A conditional is commonly more valuable when you have a smaller set of what the values may be, meanwhile the composite is when you have a high variability of values. Creating the conditional index:

```
CREATE INDEX CONCURRENTLY idx_address_userid_current ON address(user_id) WHERE current = True; 
```

We can then see the query plan is now even further improved as we’d hope:

```
EXPLAIN ANALYZE SELECT * FROM address WHERE user_id = 245 AND current = True QUERY PLAN -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- Aggregate (cost=4690.88..4690.88 rows=1 width=0) (actual time=519.288..519.289 rows=1 loops=1) -> Index Scan using idx_address_userid_current on address (cost=0.00..232.52 rows=23 width=4) (actual time=10.143..62.822 rows=1 loops=8) Index Cond: ((user_id = 245) AND (current = True)) Total runtime: .728 ms (1 rows) 
```

_If you’re looking for a deeper resource on Postgres I recommend the book [The Art of PostgreSQL](https://theartofpostgresql.com/?affiliate=cek). It is by a personal friend that has aimed to create the definitive guide to Postgres, from a developer perspective. If you use code CRAIG15 you’ll receive 15% off as well._

  
  
from Hacker News https://ift.tt/VMiZdN