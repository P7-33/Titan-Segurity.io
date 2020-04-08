---
title: 'How to write fast code in Ruby on Rails'
date: 2019-10-12T05:03:00+01:00
draft: false
---

![](http://cdn.shopify.com/s/files/1/0779/4361/articles/laptop_on_desk_with_hands_over_shoulder1_1_1024x1024.jpg?v=1570543223 "  How to Write Fast Code in Ruby on Rails        – Shopify Engineering    ")  

At Shopify, we use [Ruby on Rails](https://engineering.shopify.com/search?q=ruby+on+rails "Ruby on Rails on Shopify Engineering") for most of our projects. For both Rails and Ruby, there exists a healthy amount of stigma toward performance. You’ll often find examples of individuals (and [entire](https://developers.soundcloud.com/blog/building-products-at-soundcloud-part-1-dealing-with-the-monolith "Building Products at SoundCloud —Part I: Dealing with the Monolith") [companies](https://blog.twitter.com/engineering/en_us/a/2013/new-tweets-per-second-record-and-how.html "New Tweets per second record, and how!")) drifting away from Rails in favor of something _better_. On the other hand, there are many who have embraced Ruby on Rails and found success, even at our scale, processing millions of requests per minute (RPM).

Part of Shopify’s success with Ruby on Rails is an emphasis on writing fast code. But, how do you _really_ write _fast_ code? Largely, that’s context sensitive to the problem you’re trying to solve. Let’s talk about a few ways to start writing faster code in Active Record, Rails, and Ruby.

Active Record Performance
=========================

[Active Record](https://guides.rubyonrails.org/active_record_basics.html "Active Record Basics") is Rails’ default Object Relational Mapper (ORM). Active Record is used to interact with your database by generating and executing Structured Query Language (SQL). There are many ways to query large volumes of data poorly. Here are some suggestions to help keep your queries fast.

Know When SQL Gets Executed
---------------------------

Active Record evaluates queries lazily. So, to query efficiently, you should know _when_ queries are executed. Finder methods, calculations, and association methods all cause queries to evaluated. Here’s an example:

Here the code is appending a comment to a blog post _and_ automatically saving it to the database. It isn’t immediately obvious that this executes a SQL insert to save the appended blog post. These kinds of gotchas become easier to spot through reading documentation and experience.

Select Less Where Possible
--------------------------

Another way to query efficiently is to select only what you need. By default, Active Record selects all columns in SQL with `SELECT *`. Instead, you can leverage `select` and `pluck` to take control of your select statements:

Here, we’re selecting all IDs in a blog’s table. Notice `select` returns an Active Record Relation object (that you can chain query methods off of) whereas `pluck` returns an array of raw data.

Forget About The Query Cache
----------------------------

Did you know that if you execute the same SQL within the lifetime of a request, Active Record will only query the database once? Query Cache is one of the last lines of defense against redundant SQL execution. This is what it looks like in action:

In the example, subsequent blog `SELECT`s using the same parameters are loaded from cache. While this is helpful, depending on query cache is a bad idea. Query cache is stored in memory, so its persistence is short-lived. The cache can be disabled, so if your code will run both inside and outside of a request, it may not always be efficient.

Avoid Querying Unindexed Columns
--------------------------------

Avoid querying unindexed columns, it often leads to unnecessary [full table scans](https://en.wikipedia.org/wiki/Full_table_scan "Full Table Scan on Wikipedia"). At scale, these queries are likely to timeout and cause problems. This is more of a database best practice that directly affects query efficiency.

The obvious solution to this problem is to index the columns you need to query. What isn’t always obvious, is _how_ to do it. Databases often lock writes to a table when adding an index. This means large tables can be write-blocked for a long time.

At Shopify, we use a tool called [Large Hadron Migrator (LHM)](https://github.com/shopify/lhm "Large Hadron Migrator - Online MySQL schema migrations") to solve these kinds of scaling migration problems for large tables. On later versions of Postgres and MySQL, there is also concurrent indexing support.

Rails Performance
=================

Zooming out from Active Record, Rails has many other moving parts like Active Support, Active Job, Action Pack, etc. Here are some generalized best practices for writing fast code in Ruby on Rails.

Cache All The Things
--------------------

If you can’t make something faster, a good alternative is to cache it. Things like complex view compilation and external API calls benefit greatly from caching. Especially if the resultant data doesn’t change often.

Taking a closer look at the fundamentals of caching, key naming and expiration are critical to building effective caches. For example:

In the first block, we cache all subscription plan names indefinitely (or until the key is evicted by our caching backend). The second block caches the JSON of all posts for a given blog. Notice how cache keys change in the context of a different blog or when a new post is added to a blog. Finally, the last block caches a global comment count for approved comments. The key will automatically be removed by our caching backend every five minutes after initial fetching.

Throttle Bottlenecks
--------------------

But what about operations you can’t cache? Things like delivering an email, sending a webhook, or even logging in can be abused by users of an application. Essentially, any expensive operation that can’t be cached should be throttled.

Rails doesn’t have a throttling mechanism by default. So, gems like `[rack-attack](https://github.com/kickstarter/rack-attack "Rack middleware for blocking & throttling - GitHub")` and `[rack-throttle](https://github.com/dryruby/rack-throttle "Rack middleware for rate-limiting incoming HTTP requests - GitHub")` can help you throttle unwanted requests. Using `rack-attack:`

This snippet limits a given IP’s post requests to `/admin/sign_in` to 10 in 15 minutes. Depending on your application’s needs, you can also build solutions that throttle further up the stack inside your rails app. Rack-based throttling solutions are popular because they allow you to throttle bad requests before they hit your Rails app.

Do It Later (In a Job)
----------------------

A cornerstone of the request-response model we work with as web developers is speed. Keeping things snappy for users is important. So, what if we need to do something complicated and long-running?

Jobs allow us to defer work to another process through queueing systems often backed by Redis. Exporting a dataset, activating a subscription, or processing a payment are all great examples of job-worthy work. Here’s what jobs look like in Rails:

This is a trivial example of how you would write a CSV exporting job. Active Job is Rails’ job definition framework which plugs into specific queueing backends like [Sidekiq](https://github.com/mperham/sidekiq "Simple, efficient background processing for Ruby - GitHub") or [Resque](https://github.com/resque/resque "Resque is a Redis-backed Ruby library for creating background jobs, placing them on multiple queues, and processing them later").

Start Dependency Dieting
------------------------

Ruby’s ecosystem is rich, and there are a lot of great libraries you can use in your project. But how much is too much? As a project grows and matures, dependencies often turn into liabilities.

Every dependency adds more code to your project. This leads to slower boot times and increased memory usage. Being aware of your project’s dependencies and making conscious decisions to minimize them help maintain speed in the long term.

Shopify’s core monolith, for example, has ~500 gem dependencies. This year, we’ve taken steps to evaluate our gem usage and remove unnecessary dependencies where possible. This lead to removing unused gems, addressing tech debt to remove legacy gems, and using a dependency management service (eg. [Dependabot](https://dependabot.com/ "Dependabot - Automated dependency updates")).

Ruby Performance
================

A framework is only as fast as the language it’s written in. Here are some pointers on writing performant Ruby code. This section is inspired by Jeremy Evans’s [closing keynote on performance at RubyKaigi 2019](https://www.youtube.com/watch?v=RuGZCcEL2F8 "Optimization Techniques Used by the Benchmark Winners - Jeremy Evan - RubyKaigi 2019").

Use Metaprogramming Sparingly
-----------------------------

Changing a program’s structure at runtime is a powerful feature. In a highly dynamic language like Ruby, there are significant performance costs associated to metaprogramming. Let’s look at method definition as an example:

These are three common ways of defining a method in Ruby. The first most common method uses `def`. The second uses `define_method` to define a metaprogrammed method. The third uses `class_eval` to evaluate a string at runtime as source code (which defines a method using `def`).

This is output of a benchmark that measures the speed of these three methods using the [`benchmark-ips` gem](https://github.com/evanphx/benchmark-ips "Provides iteration per second benchmarking for Ruby - GitHub"). Let’s focus on the lower half of the benchmark that measures how many times Ruby could run the method in 5 seconds. For the normal `def` method, it was ran 10.9 million times, 7.7 million times for the `define_method` method, and 10.3 million times for the `class_eval` `def` defined method.

While this is a trivial example, we can conclude there are clear performance differences associated with \_how\_ you define a method. Now, let’s look at method invocation

This simply defines `invoke` and [`method_missing`](https://ruby-doc.org/core-2.6.4/BasicObject.html#method-i-method_missing "Private Instance Methods method_missing - Ruby-Doc.org") methods on an object named `obj`. Then, we call the `invoke` method normally, using the metaprogrammed `send` method, and finally via `method_missing`.

Less surprisingly, a method invoked with `send` or `method_missing` is much slower than a regular method invocation. While these differences might seem minuscule, they add up fast in large codebases, or when called many times recursively. As a rule of thumb, use metaprogramming sparingly to prevent unnecessary slowness.

Know the difference between O(n) and O(1)
-----------------------------------------

What `O(n)` and `O(1)` mean is that there are two kinds of operations. `O(n)` is an operation that scales in time with size, and `O(1)` is one that is constant in time regardless of size. Consider this example:

This becomes very apparent when finding a value in an array compared to a hash. With every element you add to an array, there’s more potential data to iterate through whereas hash lookups are always constant regardless of size. The moral of the story here is to think about how your code will scale with more data.

Allocate Less
-------------

Memory management is a complicated subject in most languages, and Ruby is no exception. Essentially, the more objects you allocate, the more memory your program consumes. High-level languages usually implement [Garbage Collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science) "Garbage collection (computer science) - Wikipedia") to automate removal of unused objects making developers’s lives much easier.

Another aspect of memory management is object mutability. For example, if you need to combine two arrays together, do you allocate a new array or mutate an existing one? Which option is more memory efficient?

Generally speaking, less allocations is better. Rubyists often classify these kinds of self-mutating methods as “dangerous”. Dangerous methods in Ruby often (but not always) end with an exclamation mark. Here’s an example:

The code above allocates an array of symbols. The first `uniq` call allocates and returns a new array with all redundant symbols removed. The second `uniq!` call mutates the receiver directly to remove redundant symbols and returns itself.

If used improperly, dangerous methods can lead to unwanted [side effects](https://en.wikipedia.org/wiki/Side_effect_(computer_science) "Side effect (computer science) - Wikipedia") in your code. A best practice to follow is to avoid mutating global state while leveraging mutation on local state.

Minimize Indirection
--------------------

Indirection in code, especially through layered abstractions, can be described as both a blessing and a curse. In terms of performance, it’s almost always a curse

[Merb](https://en.wikipedia.org/wiki/Merb "Merb - Wikipedia"), a web application framework that was merged into Rails has a motto: “No code is faster than no code.” This can be interpreted as “The more layers of complexity you add to something, the slower it will be.’’ While this isn’t necessarily true for performance optimizing code, it’s still a good principle to remember when refactoring.

An example of necessary indirection is Active Resource, an ORM for interacting with web services. Developers don’t use it for better performance, they use it because manually crafting requests and responses is much more difficult (and error prone) by comparison.

Final Thoughts
==============

Software development is full of tradeoffs. As developers, we have enough difficult decisions to make while juggling technical debt, code style, and code correctness. This is why optimizing for speed shouldn’t come first.

At Shopify, we treat speed as a feature. While it lends itself to better user experiences and lower server bills, it shouldn’t take precedence over the happiness of developers working on an application. Remember to keep your code fun while making it fast!

**Additional Reading**

* * *

We’re always looking for awesome people of all backgrounds and experiences to join our team. Visit our [Engineering career page](http://www.shopify.com/careers/specialties/engineering?itcat=EngBlog&itterm=Post "Engineering Careers at Shopify") to find out what we’re working on.

  
  
from Hacker News https://ift.tt/2Osw68x