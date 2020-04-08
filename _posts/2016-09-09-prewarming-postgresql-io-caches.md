---
title: 'Prewarming PostgreSQL I/O caches'
date: 2019-10-19T06:47:00+01:00
draft: false
---

PostgreSQL uses shared\_buffers to cache blocks in memory. The idea is to reduce  
disk I/O and to speed up the database in the most efficient way  
possible. During normal operations your database cache will be pretty useful and  
ensure good response times. However, what happens if your database instance is  
restarted – for whatever reason? Your PostgreSQL database performance will suffer  
until your I/O caches have filled up again. This takes some time and it can  
be pretty damaging to your query response times.

pg\_prewarm: Filling up your database cache
-------------------------------------------

Fortunately, there are ways in PostgreSQL to fix the problem. pg\_prewarm is a  
module which allows you to automatically prewarm your caches after a database  
failure or a simple restart. The [pg\_prewarm](https://www.postgresql.org/docs/current/pgprewarm.html) module is part of the PostgreSQL  
contrib package and is usually available on your server by default.  
There is no need to install additional third party software. PostgreSQL has all  
you need by default.

<img src="https://www.cybertec-postgresql.com/wp-content/uploads/2019/09/hans-prewarming\_Zeichenfl%C3%A4che-1.png" alt="pg\_prewarm" />

![pg_prewarm](https://www.cybertec-postgresql.com/en/prewarming-postgresql-i-o-caches/)

Warming caches manually or automatically.
-----------------------------------------

Basically, pg\_prewarm can be used in two ways:

*   Manual caching
*   Automatic caching on startup

Let us take a look at both options and see how the module works in detail. In general automatic pre-warming is, in my judgement, the better way to preload caches – but in some cases, it can also make sense to just warm caches manually (usually for testing purposes).

pg\_prewarm: Putting data into shared\_buffers manually
-------------------------------------------------------

Prewarming the cache manually is pretty simple. The following section explains how the process works in general.

The first thing to do is to enable the pg\_prewarm extension in your database:

```
test=# CREATE EXTENSION pg\_prewarm; CREATE EXTENSION
```

To show how a table can be preloaded, I will first create a table and put it into  
the cache:

```
test=# CREATE TABLE t\_test AS SELECT \* FROM generate\_series(1, 1000000) AS id; SELECT 1000000 test=# SELECT \* FROM pg\_prewarm('public.t\_test'); pg\_prewarm ------------ 4425 (1 row) 
```

All you have to do is to call the [pg\_prewarm](https://www.postgresql.org/docs/current/pgprewarm.html) function and pass the name of the  
desired table to the function. In my example, 4425 pages have been read and put  
into the cache.  
4425 blocks translates to roughly 35 MB:

```
test=# SELECT pg\_size\_pretty(pg\_relation\_size('t\_test')); pg\_size\_pretty ---------------- 35 MB (1 row) 
```

Calling pg\_prewarm with one parameter is the easiest way to get started.  
However, the module can do a lot more, as shown in the next listing:

```
test=# \\x Expanded display is on. test=# \\df \*pg\_prewarm\* List of functions -\[ RECORD 1 \] ---------------------+--------------------------------------------- Schema | public Name | pg\_prewarm Result data type | bigint Argument data types | regclass, mode text DEFAULT 'buffer'::text, fork text DEFAULT 'main'::text, first\_block bigint DEFAULT NULL::bigint, last\_block bigint DEFAULT NULL::bigint Type | func 
```

In addition to passing the name of the object you want to cache to the function,  
you can also tell PostgreSQL which part of the table you want to cache. The  
“relation fork” defines whether you want the real data file, the VM (Visibility  
Map) or the FSM (Free Space Map). Usually, caching the main table is just fine.  
You can also tell PostgreSQL to cache individual blocks. While this is flexible,  
it is usually not what you want to do manually.

Automatically populate your PostgreSQL I/O cache
------------------------------------------------

In most cases, people might want pg\_prewarm to take care of caching automatically  
on startup. The way to achieve this is to add pg\_prewarm to  
shared\_preload\_libraries and to restart the database server. The following  
example shows how to configure shared\_preload\_libraries in postgresql.conf:  
shared\_preload\_libraries = ‘pg\_stat\_statements, pg\_prewarm’  
After the server has restarted you should be able to see the “autoprewarm  
master” process which is in charge of starting up things for you.

```
80259 ? Ss 0:00 /usr/pgsql-11/bin/postmaster -D /var/lib/pgsql/11/data/ 80260 ? Ss 0:00 \\\_ postgres: logger 80262 ? Ss 0:00 \\\_ postgres: checkpointer 80263 ? Ss 0:00 \\\_ postgres: background writer 80264 ? Ss 0:00 \\\_ postgres: walwriter 80265 ? Ss 0:00 \\\_ postgres: autovacuum launcher 80266 ? Ss 0:00 \\\_ postgres: stats collector 80267 ? Ss 0:00 \\\_ postgres: autoprewarm master 80268 ? Ss 0:00 \\\_ postgres: logical replication launcher 
```

By default, pg\_prewarm will store a list of blocks which are currently in memory  
on disk. After a crash or a restart, pg\_prewarm will automatically restore the  
cache as it was when the file was last exported.

When to use pg\_prewarm
-----------------------

In general, pg\_prewarm makes most sense if your database and your RAM are really  
really large (XXX GB or more). In such cases, the difference between cached  
and uncached data will be greatest and users will suffer the most if  
performance is bad.

Finally …
---------

If you want to learn more about performance and database tuning in general,  
consider checking out my post about how to track down [slow or time consuming](https://www.cybertec-postgresql.com/en/3-ways-to-detect-slow-queries-in-postgresql/)  
queries. You might also be interested in taking a look at  
[http://pgconfigurator.cybertec.at](http://pgconfigurator.cybertec.at), which is a free website to help you with  
database configuration.

  
  
from Hacker News https://ift.tt/2qj7vsN