---
title: 'Google Patches Chrome Zero-Day Vulnerabilities Under Active Attack'
date: 2019-11-02T07:52:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/10/Chrome-shutterstock-website.jpg)

Google has started rolling out a software update that includes security fixes for a couple of critical zero-day vulnerabilities in its Chrome web browser on Windows, Mac and Linux.  The incoming software will roll out _“over the coming days/weeks”_, and will update the stable channel to build 78.0.3904.87. According to an [official blog post](https://chromereleases.googleblog.com/2019/10/stable-channel-update-for-desktop_31.html), the update fully mitigates the two bugs, at least one of which is said to already have an active exploit that criminals are using to hijack computers.  

Technical details are hard to come by at this point in time, and Google says it would like to keep things that way until a majority of users have updated to the fixed version(s). However, the company did reveal that one of the vulnerabilities (**CVE-2019-13720**) is affecting Chrome’s audio component, while the other (**CVE-2019-13721**) is part of the PDFium library.  

While the former was reported by Kaspersky researchers, Anton Ivanov and Alexey Kulaev, last Tuesday, the latter was reported earlier this month by an anonymous user who goes by their online pseudonym, _‘banananapenguin’_. According to Google, it is the former, the one reported by folks at Kaspersky, that is being actively exploited by hackers in the wild.  

According to [The Hacker News](https://thehackernews.com/2019/11/chrome-zero-day-update.html), both **the bugs are use-after-free vulnerabilities**, a type of memory corruption that can enable hackers to potentially modify data in the system memory from a remote location. Thereafter, they can escape sandbox protections to surreptitiously escalate privileges and run arbitrary malicious code on affected systems. Basically, both are critical flaws that could pose severe security threats, which is why Google is advising all users to update to the latest version of Chrome as soon as possible.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/google-patches-chrome-zero-day/)  
\[the\_ad id='1307'\]