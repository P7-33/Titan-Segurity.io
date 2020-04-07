---
title: 'Python history, sorta, the ABC Programming Language'
date: 2020-01-19T17:58:00+01:00
draft: false
---

![Adafruit 2019 3368](https://cdn-blog.adafruit.com/uploads/2020/01/adafruit_2019_3368.jpg)

Python history, sorta, the ABC Programming Language … [from Wikipedia](https://en.wikipedia.org/wiki/ABC_(programming_language)):

> [ABC](https://homepages.cwi.nl/~steven/abc/) is an imperative general-purpose programming language and programming environment developed at CWI, Netherlands by Leo Geurts, Lambert Meertens, and Steven Pemberton. It is interactive, structured, high-level, and intended to be used instead of BASIC, Pascal, or AWK. It is not meant to be a systems-programming language but is intended for teaching or prototyping. The language had a major influence on the design of the Python programming language; Guido van Rossum, who developed Python, previously worked for several years on the ABC system in the mid 1980s.

Good interview that is archived too – [The A-Z of Programming Languages](https://web.archive.org/web/20081229095320/http://www.computerworld.com.au/index.php/id%3B66665771).

It’s interesting that ABC was intended for teaching or prototyping, Guido did electronics as a hobby, developed Python later, and CircuitPython is REALLY good for teaching and prototyping. Full circle, [here’s an interview from 2014](https://medium.com/dropbox-makers/guido-van-rossum-on-finding-his-way-e018e8b5f6b1) –

> **You were an electronics hobbyist before becoming a programmer. How did you get started in electronics?**
> 
> Okay, we’re going waaaay back. I don’t know exactly why I got into electronics as a kid. I remember that from the last grade in elementary school and probably through my second year in university, electronics kits and my own designs were one of my big passions. It wasn’t always an easy path. In elementary school, I took one of the first projects I built into class as a show and tell project. There was no one who understood what it was or why it was interesting or cared. It’s a very vague memory. I just know that I took it in, and it fell flat.

* * *

We’ve tried to cover some historic Python, and Python on hardware efforts too, here are those!

[tinypy](https://blog.adafruit.com/2018/12/04/python-on-hardware-history-tinypy/) – 64k tinypy “batteries not (yet) included” was release in 2008 by Phil Hassey. tinypy is a minimalist implementation of python in 64k of code - [tinypy.org](http://www.tinypy.org/) & [GitHub](https://github.com/philhassey/tinypy).

* * *

![18 124Pythonchip](https://cdn-blog.adafruit.com/uploads/2018/12/18_124pythonchip.jpg)  
[PyMite](https://blog.adafruit.com/2018/12/03/python-on-hardware-history-pymite-python/) (2009?) is a flyweight Python interpreter written from scratch to execute on 8-bit and larger microcontrollers with resources as limited as 64 KiB of program memory (flash) and 4 KiB of RAM. PyMite supports a subset of the Python 2.5 syntax and can execute a subset of the Python 2.5 bytecodes. PyMite can also be compiled, tested and executed on a desktop computer - [PyMite wiki](https://wiki.python.org/moin/PyMite), [Google Code Archive](https://code.google.com/archive/p/python-on-a-chip/), and [python-on-a-chip mailing list](https://groups.google.com/forum/#!forum/python-on-a-chip).

* * *

![Adafruit 2018 1243](https://cdn-blog.adafruit.com/uploads/2019/01/adafruit_2018_1243.jpg)  
[Amoeba (operating system) – Wikipedia](https://en.wikipedia.org/wiki/Amoeba_(operating_system)).

> Amoeba is a distributed operating system developed by Andrew S. Tanenbaum and others at the Vrije Universiteit Amsterdam. The aim of the Amoeba project was to build a timesharing system that makes an entire network of computers appear to the user as a single machine. Development at the Vrije Universiteit was stopped: the source code of the latest version (5.3) was last modified on 30 July 1996.
> 
> **The Python programming language was originally developed for this platform.**

[Read more](https://en.wikipedia.org/wiki/Amoeba_(operating_system)). And…

![Adafruit 2018 1244](https://cdn-blog.adafruit.com/uploads/2019/01/adafruit_2018_1244.jpg)

> **[Why was Python created in the first place?](https://docs.python.org/3/faq/general.html#why-was-python-created-in-the-first-place)**  
> Here’s a very brief summary of what started it all, written by Guido van Rossum:
> 
> __“I had extensive experience with implementing an interpreted language in the ABC group at CWI, and from working with this group I had learned a lot about language design. This is the origin of many Python features, including the use of indentation for statement grouping and the inclusion of very-high-level data types (although the details are all different in Python).__
> 
> __I had a number of gripes about the ABC language, but also liked many of its features. It was impossible to extend the ABC language (or its implementation) to remedy my complaints – in fact its lack of extensibility was one of its biggest problems. I had some experience with using Modula-2+ and talked with the designers of Modula-3 and read the Modula-3 report. Modula-3 is the origin of the syntax and semantics used for exceptions, and some other Python features.__
> 
> __I was working in the Amoeba distributed operating system group at CWI. We needed a better way to do system administration than by writing either C programs or Bourne shell scripts, since Amoeba had its own system call interface which wasn’t easily accessible from the Bourne shell. My experience with error handling in Amoeba made me acutely aware of the importance of exceptions as a programming language feature.__
> 
> __It occurred to me that a scripting language with a syntax like ABC but with access to the Amoeba system calls would fill the need. I realized that it would be foolish to write an Amoeba-specific language, so I decided that I needed a language that was generally extensible.__
> 
> __During the 1989 Christmas holidays, I had a lot of time on my hand, so I decided to give it a try. During the next year, while still mostly working on it in my own time, Python was used in the Amoeba project with increasing success, and the feedback from colleagues made me add many early improvements.__
> 
> __In February 1991, after just over a year of development, I decided to post to USENET. The rest is in the Misc/HISTORY file.”__

> [The Amoeba Distributed Operating System](https://www.cs.vu.nl/pub/amoeba/amoeba.html)
> 
> Amoeba is a powerful microkernel-based system that turns a collection of workstations or single-board computers into a transparent distributed system. It has been in use in academia, industry, and government for about 5 years. It runs on the SPARC (Sun4c and Sun4m), the 386/486, 68030, and Sun 3/50 and Sun 3/60.
> 
> At the Vrije Universiteit, Amoeba runs on a collection of 80 single-board SPARC computers connected by an Ethernet, forming a powerful processor pool. This equipment is pictured below. It is used for research in distributed and parallel operating systems, runtime systems, languages, and applications.
> 
> ![Zoo](https://cdn-blog.adafruit.com/uploads/2019/01/zoo.jpg)
> 
> The V8-SPARC processor pool at the VU.

**Related:**

*   [Welcome to the Amoeba WWW Home Page](https://www.cs.vu.nl/pub/amoeba/).
*   [Amoeba – A Distributed Operating System for the 1990s](https://slideplayer.com/slide/8453131/).