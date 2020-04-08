---
title: 'Find stuff in org-mode anywhere (2017)'
date: 2019-11-30T02:09:00+01:00
draft: false
---

I used [emacsql](https://github.com/skeeto/emacsql) to create and interact with a sqlite3 database. It is a lispy way to generate SQL queries. I will not talk about the code much here, you can see this version [org-db.el](https://kitchingroup.cheme.cmu.edu/media/org-db.el) . The database design consists of several tables that contain the filenames, headlines, tags, properties, (optionally) headline-content, headline-tags, headline-properties, and links. The lisp code is a work in progress, and not something I use on a daily basis yet. This post is a proof of concept to see how well this approach works.

I use hooks to update the database when an org-file is opened (only if it is different than what is in the database based on an md5 hash) and when it is saved. Basically, these functions delete the current entries in the database for a file, then use regular expressions to go to each headline or link in the file, and add data back to the database. I found this to be faster than parsing the org-file with org-element especially for large files. Since this is all done by a hook, anytime I open an org-file anywhere it gets added/updated to the database. The performance of this is ok. This approach will not guarantee the database is 100% accurate all the time (e.g. if something modifies the file outside of emacs, like a git pull), but it doesn't need to be. Most of the files do not change often, the database gets updated each time you open a file, and you can always reindex the database from files it knows about. Time will tell how often that seems necessary.

emacsql lets you use lisp code to generate SQL that is sent to the database. Here is an example:

```
(emacsql-flatten-sql \[:select \[name\] :from main:sqlite\_master :where (= type table)\]) 
```

```
 SELECT name FROM main.sqlite\_master WHERE type = "table"; 
```

There are some nuances, for example, main:sqlite\_master gets converted to main.sqlite\_master. You use vectors, keywords, and sexps to setup the command. emacsql will turn a name like filename-id into filename\_id. It was not too difficulty to figure out, and the author of emacsql was really helpful on a few points. I will be referring to this post in the future to remember some of these nuances!

Here is a list of tables in the database. There are a few primary tables, and then some that store tags, properties, and keywords on the headlines. This is typical of emacsql code; it is a lisp expression that generates SQL. In this next expression org-db is a variable that stores the database connection created in org-db.el.

```
(emacsql org-db \[:select \[name\] :from main:sqlite\_master :where (= type table)\]) 
```

files

tags

properties

keywords

headlines

headline\_content

headline\_content\_content

headline\_content\_segments

headline\_content\_segdir

headline\_content\_docsize

headline\_content\_stat

headline\_tags

headline\_properties

file\_keywords

links

Here is a description of the columns in the files table:

```
(emacsql org-db \[:pragma (funcall table\_info files)\]) 
```

0

rowid

INTEGER

0

nil

1

1

filename

0

nil

0

 

2

md5

0

nil

0

 

and the headlines table.

```
(emacsql org-db \[:pragma (funcall table\_info headlines)\]) 
```

0

rowid

INTEGER

0

nil

1

1

filename\_id

0

nil

0

 

2

title

0

nil

0

 

3

level

0

nil

0

 

4

todo\_keyword

0

nil

0

 

5

todo\_type

0

nil

0

 

6

archivedp

0

nil

0

 

7

commentedp

0

nil

0

 

8

footnote\_section\_p

0

nil

0

 

9

begin

0

nil

0

 

Tags and properties on a headline are stored in headline-tags and headline-properties.

The database is not large if all it has is headlines and links (no content). It got up to half a GB with content, and seemed a little slow, so for this post I leave the content out.

```
du -hs ~/org-db/org-db.sqlite 
```

56M

/Users/jkitchin/org-db/org-db.sqlite

Here we count how many files are in the database. These are just the org-files in my Dropbox folder. There are a lot of them! If I include all the org-files from my research and teaching projects this number grows to about 10,000! You do not want to run org-map-entries on that. Note this also includes all of the org\_archive files.

```
(emacsql org-db \[:select (funcall count) :from files\]) 
```

Here is the headlines count. You can see there is no chance of remembering where these are because there are so many!

```
(emacsql org-db \[:select (funcall count) :from headlines\]) 
```

And the links. So many links!

```
(emacsql org-db \[:select (funcall count) :from links\]) 
```

That is a surprising number of links.

  
  
from Hacker News https://ift.tt/35NFvwY