---
title: 'Tracking PG&E outages by scraping to a Git repo'
date: 2019-10-14T02:39:00+01:00
draft: false
---

Tracking PG&E outages by scraping to a git repo
-----------------------------------------------

PG&E have [cut off power](https://twitter.com/bedwardstiek/status/1182047040932470784) to several million people in northern California, supposedly as a precaution against wildfires.

As it happens, I’ve been scraping and recording PG&E’s outage data every 10 minutes for the past 4+ months. This data got really interesting over the past two days!

The original data lives in [a GitHub repo](https://github.com/simonw/pge-outages) (more importantly in [the commit history](https://github.com/simonw/pge-outages/commits/master) of that repo).

Reading JSON in a Git repo isn’t particularly productive, so this afternoon I figured out how to transform that data into a SQLite database and publish it with [Datasette](https://github.com/simonw/datasette).

The result is [pge-outages.simonwillison.net](https://pge-outages.simonwillison.net/)

### The data model: outages and snapshots

The three key tables to understand are `outages`, `snapshots` and `outage_snapshots`.

PG&E assign an outage ID to every outage—where an outage is usually something that affects a few dozen customers. I store these in the [outages table](https://pge-outages.simonwillison.net/pge-outages/outages?_sort_desc=outageStartTime).

Every 10 minutes I grab a snapshot of their full JSON file, which reports every single outage that is currently ongoing. I store a record of when I grabbed that snapshot in the [snapshots table](https://pge-outages.simonwillison.net/pge-outages/snapshots?_sort_desc=id).

The most interesting table is `outage_snapshots`. Every time I see an outage in the JSON feed, I record a new copy of its data as an `outage_snapshot` row. This allows me to reconstruct the full history of any outage, in 10 minute increments.

Here are [all of the outages](https://pge-outages.simonwillison.net/pge-outages/outage_snapshots?snapshot=1269) that were represented in [snapshot 1269](https://pge-outages.simonwillison.net/pge-outages/snapshots/1269)—captured at 4:10pm Pacific Time today.

I can run `select sum(estCustAffected) from outage_snapshots where snapshot = 1269` ([try it here](https://pge-outages.simonwillison.net/pge-outages?sql=select+sum%28estCustAffected%29+from+outage_snapshots+where+snapshot+%3D+%3Aid&id=1269)) to count up the total PG&E estimate of the number of affected customers—it’s 545,706!

I’ve installed [datasette-vega](https://github.com/simonw/datasette-vega) which means I can render graphs. Here’s my first attempt at a graph showing [the number of estimated customers affected over time](https://pge-outages.simonwillison.net/pge-outages?sql=select+snapshots.id%2C+title+as+snapshotTime%2C+hash%2C+sum%28outage_snapshots.estCustAffected%29+as+totalEstCustAffected%0D%0Afrom+snapshots+join+outage_snapshots+on+snapshots.id+%3D+outage_snapshots.snapshot%0D%0Agroup+by+snapshots.id+order+by+snapshots.id+desc+limit+150#g.mark=line&g.x_column=snapshotTime&g.x_type=ordinal&g.y_column=totalEstCustAffected&g.y_type=quantitative).

[![](https://static.simonwillison.net/static/2019/pge-outages-graph.png)](https://static.simonwillison.net/static/2019/pge-outages-graph.png)

(I don’t know why there’s a dip towards the end of the graph).

I also defined [a SQL view](https://pge-outages.simonwillison.net/pge-outages/most_recent_snapshot) which shows all of the outages from the most recently captured snapshot (usually within the past 10 minutes if the PG&E website hasn’t gone down) and renders them using [datasette-cluster-map](https://github.com/simonw/datasette-cluster-map).

[![](https://static.simonwillison.net/static/2019/pge-map.jpg)](https://static.simonwillison.net/static/2019/pge-map.jpg)

### Things to be aware of

There are a huge amount of unanswered questions about this data. I’ve just been looking at PG&E’s JSON and making guesses about what things like `estCustAffected` means. Without official documentation we can only guess as to how accurate this data is, or how it should be interpreted.

Some things to question:

*   What’s the quality of this data? Does it reflect accurately on what’s actually going on out there?
*   What’s the exact meaning of the different columns—`estCustAffected`, `currentEtor`, `autoEtor`, `hazardFlag` etc?
*   Various columns (`lastUpdateTime`, `currentEtor`, `autoEtor`) appear to be integer [unix timestamps](https://en.wikipedia.org/wiki/Unix_time). What timezone were they recorded in? Do they include DST etc?

### How it works

I originally wrote the scraper [back in October 2017](https://simonwillison.net/2017/Oct/10/fires-in-the-north-bay/) during the North Bay fires, and moved it to run on Circle CI based on my work building [a commit history of San Francisco’s trees](https://simonwillison.net/2019/Mar/13/tree-history/).

It’s pretty simple: every 10 minutes [a Circle CI job](https://circleci.com/gh/simonw/disaster-scrapers) runs which scrapes [the JSON feed](https://apim.pge.com/cocoutage/outages/getOutagesRegions?regionType=city&expand=true) that powers the PG&E website’s [outage map](https://www.pge.com/myhome/outages/outage/index.shtml).

The JSON is then committed to my [pge-outages GitHub repository](https://github.com/simonw/pge-outages), over-writing the existing [pge-outages.json file](https://github.com/simonw/pge-outages/blob/master/pge-outages.json). There’s some code that attempts to generate a human-readable commit message, but the historic data itself is saved in the commit history of that single file.

### Building the Datasette

The hardest part of this project was figuring out how to turn a GitHub commit history of changes to a JSON file into a SQLite database for use with Datasette.

After a bunch of prototyping in a Jupyter notebook, I ended up with the schema described above.

The code that generates the database can be found in [build\_database.py](https://github.com/simonw/pge-outages/blob/master/build_database.py). I used [GitPython](https://gitpython.readthedocs.io/en/stable/) to read data from the git repository and my [sqlite-utils library](https://sqlite-utils.readthedocs.io/en/stable/python-api.html) to create and update the database.

### Deployment

Since this is a large database that changes every ten minutes, I couldn’t use the usual [datasette publish](https://datasette.readthedocs.io/en/stable/publish.html) trick of packaging it up and re-deploying it to a serverless host (Cloud Run or Heroku or Zeit Now) every time it updates.

Instead, I’m running it on a VPS instance. I ended up trying out Digital Ocean for this, after [an enjoyable Twitter conversation](https://twitter.com/simonw/status/1182077259839991808) about good options for stateful (as opposed to stateless) hosting.

### Next steps

I’m putting this out there and sharing it with the California News Nerd community in the hope that people can find interesting stories in there and help firm up my methodology—or take what I’ve done and spin up much more interesting forks of it.

If you build something interesting with this please let me know, via email (swillison is my Gmail) or [on Twitter](https://twitter.com/simonw).

  
  
from Hacker News https://ift.tt/2IGuUL4