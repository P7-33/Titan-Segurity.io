---
title: 'Bryan’s Plans for CircuitPython in 2020 #CircuitPython2020 @siddacious'
date: 2020-01-11T02:25:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/adafruit_blinka_2020_blog-1.jpg)

Hi! I’m Bryan, otherwise know as @siddacious on the Adafruit discord and GitHub. I was excited to write this post and share my thoughts on CircuitPython. Writing this and keeping it concise has proven harder than I expected because after nearly a year of working for Adafruit, my brain is overflowing with ideas. It doesn’t help that I tend to be overly verbose and use too many fancy words

So, here are my goals, aspirations, and ideas for CircuitPython in 2020 (which is, officially _the future)_:

**Documentation**

We already have a lot of documentation. There is a lot of good work to be done in organizing it, keeping it up to date and making it easier to find. Things that might help:

*   Cross linking between relevant API documentation and code examples. 
*   Creating tools to make keeping documentation up to date easier. Computers are bad at writing documentation, but they’re good at connecting things and doing the same thing over and over, so making more use of automation and templating could prove useful
*   Search Engine Optimization we could probably do things to make it easier for search engines to find documentation

**Libraries**

The extensive catalog of libraries is a core strength of CircuitPython. Empowering more people to help write and maintain them is all upside. Things that could help here are

*   Better ground up documentation on how to write a driver and how to write it in a “pythonic” way that plays to the strengths of Python
*   Standards or best practices on what is a sufficient level of documentation for new code. Everyone writing new libraries has to balance their time between code features and documenting them; guidance here would help both the author and consumers by making it clear what expectations are.
*   More tooling to make writing drivers easier.  After nearly a year of writing drivers as a large percentage of my job, it’s quite clear that there is a non-trivial amount of doing the same things library to library. Code that can generate the skeleton of a library from a structured representation of the register map of a sensor would take a lot of the repetition out of writing libraries and allow the author to focus on how the library should work, not the low level details like bit manipulation

My canonical example of this type of automation done well is the “How to Write a Blog Engine in 15 minutes with Ruby on Rails” demo from 2005. This demo is arguably responsible in no small part for making Rails as popular as it is today:  
[https://www.youtube.com/watch?v=Gzj723LkRJY  
  
](https://www.youtube.com/watch?v=Gzj723LkRJY)The Register Library is a huge step in the right direction here. Adding SPI support and writing better documentation for it would be excellent, as well as supplementing it with additional tools.

Other Ideas:

*   Supporting people that want to do workshops with documentation, syllabuses, and general help
*   Concurrency is useful and important. It’s time we tackle it with aplomb
*   Thinking about pedagogy and how best to help people learn. Visual examples and well crafted metaphors would help people new to programming
*   Encouraging and supporting mentorship

I could write another 10 posts worth of ideas, but I suppose this is a good start. Good luck to all my fellow learners in 2020.