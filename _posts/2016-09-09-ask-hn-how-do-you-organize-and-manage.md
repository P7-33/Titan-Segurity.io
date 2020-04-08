---
title: 'Ask HN: How do you organize and manage database migrations?'
date: 2019-10-31T05:22:00+01:00
draft: false
---

[Ask HN: How do you organize and manage database migrations?](https://news.ycombinator.com/item?id=21405501)

2 points by [anonfunction](https://news.ycombinator.com/user?id=anonfunction) [9 minutes ago](https://news.ycombinator.com/item?id=21405501) | [hide](https://news.ycombinator.com/hide?id=21405501&goto=item%3Fid%3D21405501) | [past](https://hn.algolia.com/?query=Ask%20HN%3A%20How%20do%20you%20organize%20and%20manage%20database%20migrations%3F&sort=byDate&dateRange=all&type=story&storyText=false&prefix&page=0) | [web](https://www.google.com/search?q=Ask%20HN%3A%20How%20do%20you%20organize%20and%20manage%20database%20migrations%3F) | [favorite](https://news.ycombinator.com/fave?id=21405501&auth=6475cfa2f14a6b85a07a3c31a605fa6a58612290) | [discuss](https://news.ycombinator.com/item?id=21405501)

When building services that rely on relational databases, in my case postgres, what are some best practices and tools to help manage schema changes?

We've been using migrations and doing it all manually but it's become a bottleneck and a little bit of a nightmare with multiple consumers of the database all needing slight changes.

Another concern is multiple environments, from local development to staging and production. We're using docker-compose for local development which runs the entire "full" schema and then I'm manually applying the migration files to staging and production before we deploy.

I've looked at some projects like flywaydb\[1\] and liquibase\[2\] but both are not completely free and seem proprietary. Does anyone know of another system that could help manage database schema versioning and migrations?

Thanks so much HN, this is something that I have been struggling with.

1: https://flywaydb.org/

2: https://ift.tt/2o6cNlU

  
  

![](https://news.ycombinator.com/s.gif)  

[Guidelines](https://news.ycombinator.com/newsguidelines.html) | [FAQ](https://news.ycombinator.com/newsfaq.html) | [Support](mailto:hn@ycombinator.com) | [API](https://github.com/HackerNews/API) | [Security](https://news.ycombinator.com/security.html) | [Lists](https://news.ycombinator.com/lists) | [Bookmarklet](https://news.ycombinator.com/bookmarklet.html) | [Legal](http://www.ycombinator.com/legal/) | [Apply to YC](http://www.ycombinator.com/apply/) | [Contact](mailto:hn@ycombinator.com)  
  

  
  
from Hacker News https://ift.tt/3321i2T