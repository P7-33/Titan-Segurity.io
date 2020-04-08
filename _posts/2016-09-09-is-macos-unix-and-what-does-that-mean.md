---
title: 'Is macOS UNIX? (and What Does That Mean?)'
date: 2019-10-21T11:47:00+01:00
draft: false
---

![A MacBook Pro with the lid partially open and the screen glowing onto the keyboard.](https://www.howtogeek.com/wp-content/uploads/2019/09/img_5d8a57d6ac1ea.jpg)

[Razvan Franco Nitoi/Shutterstock](https://www.shutterstock.com/image-photo/bucharest-romania-august-19-2018-apple-1362710882)

Is macOS UNIX or just Unix? Or is it Unix-like? We answer the never-ending debate and explain standards like POSIX and the SUS along the way.

macOS: UNIX or Not?
-------------------

This subject raises a bunch of different questions. What is the lineage of macOS? How much of that hereditary material is still present in today’s macOS, and does it matter? Before we can begin to answer whether something is UNIX, Unix, or Unix-like, we need to be comfortable with what those terms mean. Who gets to decide if something is Unix or UNIX, and what criteria do they use?

Let’s start at the beginning.

Unix was created fifty years ago at [Bell Labs](https://en.wikipedia.org/wiki/Bell_Labs), a research and development company owned by AT&T. Fast-forward to 1973 and Version 4 of Unix, which was rewritten in the C programming language. This made the operating system much more portable and easier to transfer to different hardware platforms. That same year, [Ken Thompson](https://en.wikipedia.org/wiki/Ken_Thompson) and [Dennis Ritchie](https://en.wikipedia.org/wiki/Dennis_Ritchie), two of the core Unix architects, presented a paper at a conference about operating systems. Immediately they received requests for copies of the operating system.

Bound by a [consent decree](https://en.wikipedia.org/wiki/Consent_decree) that dated back to 1956, AT&T had to eschew “any business other than the furnishing of common carrier communications services.” Unix didn’t qualify as something AT&T could profit from. So, the company did something remarkable for that time: distributed Unix as source code with a liberal license. Small charges covered the shipping and packaging and a “reasonable royalty.”

A Proliferation of Unixes
-------------------------

Because Unix was provided “as-is,” it came without support. As a result, a Unix community began to coalesce to help members, and patch and extend Unix. So, you could get the source code, modify it, and get support from the community. That’s got a familiar ring to it. Different flavors of Unix began to appear, adapted and tweaked to suit the organization doing the work.

[Bob Fabry](https://en.wikipedia.org/wiki/Bob_Fabry), a computer science professor at UC Berkeley, was on the program committee for the 1973 Symposium on Operating Systems Principles. He listened to a presentation by Thompson and Ritchie, entitled _The UNIX Time-Sharing System_.

Fabry requested a copy of the operating system, and, in 1974, Unix was installed on a [PDP/11](https://en.wikipedia.org/wiki/PDP-11) at the Computer Sciences Research Group (CSRG) at UC Berkeley. Significantly, Ken Thompson spent a year there, working on what quickly became the university’s own flavor of Unix. Copies of the UC Berkeley changes and additions were distributed and became known as the Berkeley Software Distribution (BSD). Eventually, these became distributions of an entire Unix system, still known as BSD. Version numbers, such as 4.2BSD, identified the different releases.

In 1984, AT&T was released from the strictures of the 1956 consent decree and able to market its operating system properly. It included BSD code, such as [TCP/IP](https://en.wikipedia.org/wiki/Internet_protocol_suite), [vi](https://en.wikipedia.org/wiki/Vi), and the C shell, [csh](https://en.wikipedia.org/wiki/C_shell). Even with this cross-pollination and collaboration, there were difficulties with licensing. BSD contained AT&T code, which was not open source, but the BSD elements were.

### [Read the remaining 25 paragraphs](https://www.howtogeek.com/441599/is-macos-unix-and-what-does-that-mean/)