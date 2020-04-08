---
title: 'Think You Know cURL? Care to Prove It?'
date: 2019-12-27T10:51:00+01:00
draft: false
---

Do you happen to remember a browser-based game “You Can’t JavaScript Under Pressure”? It presented coding tasks of ever-increasing difficulty and challenged the player to complete them as quickly as possible. Inspired by that game, \[Ben Cox\] re-implemented it as [You Can’t cURL Under Pressure!](https://blog.benjojo.co.uk/post/you-cant-curl-under-pressure)

In it, the user is challenged in their knowledge of how to use the ubiquitous `curl` in a variety of different ways. Perhaps this doesn’t sound terribly daunting, especially if your knowledge of curl is limited to knowing it is a command-line tool to fetch something from a web server. But curl has a _staggering_ number of features. The man page is _over 4500 lines in length_. [The software’s main site offers a (free) 250+ page guide on how to use curl and libcurl](https://curl.haxx.se/book.html). Reflecting on this is exactly what led \[Ben\] to create his challenge.

[![](https://hackaday.com/wp-content/uploads/2019/12/You-cant-cURL-under-pressure-screenshot.png?w=400)](https://hackaday.com/wp-content/uploads/2019/12/You-cant-cURL-under-pressure-screenshot.png)It’s a wonderful piece of work, but things get **really** interesting once \[Ben\] starts talking about the infrastructure behind it all. At its core the game works by giving the user a problem and a virtual machine, and catching outgoing HTTP calls to see whether they look correct. If the outgoing HTTP call is the right solution for the problem, terminate the current VM and start up the next one with the next problem. He’s put a lot of work into getting suitable VMs up and running quickly, securely, and properly isolated. The code can be found on [the project’s GitHub repository](https://github.com/benjojo/you-cant-curl-under-pressure) for those who want a closer look.

But that’s not all. \[Ben\] says that in the past he’s had a bad habit of presenting interactive features in his blog posts that can’t keep up with sudden demand. So to address that, the system auto-scales as needed with a small Linux cluster; small brick-sized PCs are started and shut down automatically to meet demand. Hey, the only thing cooler than a functioning cluster is a cluster doing an actual job, [like this one that detects NSFW images](https://hackaday.com/2018/07/06/solar-pi-cluster-scours-internet-for-nudes/).

  
  
from Hackaday https://ift.tt/2t7uGYe  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)