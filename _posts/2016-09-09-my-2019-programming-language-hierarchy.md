---
title: 'My 2019 programming language hierarchy'
date: 2019-11-29T02:09:00+01:00
draft: false
---

Earlier today I was considering which language I should use for an upcoming project and realized that 1) I had a good amount of experiences / context to argue for each side and 2) that I’d had similar internal arguments in the past for many other projects so I thought this might make good content for a post. In this post I’ll try to delineate my current internal hierarchy for languages, why I have them in this order, and any other relevant info that comes to mind. I have a feeling this will be extremely controversial (how do you compare two languages?) but by doing this, I hope to 1) know what I think by getting these thoughts outside of my brain and on DOM, 2) get some feedback on where my thoughts disagree with those of others, and 3) archive this so I can revisit it in future years.

Not every language that exists is listed here cause I don’t actually consider every language known to man to build my projects in. Hopefully that needs no further explanation. Also I’ll probably be wrong about a lot of things I declare in this post, that’s part of the reason (#2) that I’m posting this in the first place.

Onwards.

top languages
=============

These are the languages that I have front of mind to tackle a project with.

python
------

Until recently (really [when I joined Instagram](https://blog.iamhamy.xyz/posts/2019-h1-in-review/) where they use Python a fair amount), I had kind of written Python off as a programming language. Before IG, I had really only used Python in side projects in high school (omg so long ago!) and for academic projects (you know, those half-baked, built-for-a-5-minute-demo code blobs) so I’m assuming that lack of ecosystem exposure is really what stunted this relationship for so long.

Anyway, Python is now my go-to language for pretty much any project where performance is not paramount. It’s simple (almost beautifully simple without sacrificing code ergonomics), #justworks pretty much everywhere, and has a huge, active community of people making it better and creating projects for almost any goal. This means that I can get up-and-running very fast and the internals are so good that I could reasonably create a robust system for almost any scale.

The only downside I’ve seen is really just performance and that only seems to matter when you need to do things extremely fast and / or at really high load (when small performance losses really start to add up). For most of my projects this is a fine trade off.

In fact, the only time I’ve really run into an issue is for complex / media-intensive projects. For instance some of my [#webz](https://labs.iamhamy.xyz/projects/webz/) outputs (example below) take several hours to complete where in a faster language it may be a magnitude smaller (though I’d bet much of that is just due to my own code inefficency, lul).

_A #webz output_

Some things I was pleasantly surprised to find well-supported in the language when I dove back in a few months ago (they may have been there all along and I just didn’t find them /shrug):

*   unit testing
*   mocks
*   async
*   typing

### python pros

*   simple
*   fast enough for almost everything
*   great, huge, and active community
*   a package for almost anything you’re trying to do
*   just works
*   just works everywhere

### python cons

*   not great for super intensive jobs (thinking live video stuff, big / complex image manipulations, etc.)
*   at high scale you may also feel burden of relative slowness (like startup times on lambdas that get hit a ton)

### python conclusion

For almost every project, I first see if Python makes sense. It just works and can get up-and-running super quick. That makes it my top choice.

cSharp
------

Before [my first gig out of college (at APT)](https://www.linkedin.com/in/hamiltongreene/), I had never written a line of C#. My idea of it was that it was a monolithic, legacy language that only old, crufty enterprises used in the same realm as COBOL, Visual Basic, and PHP (lol).

To some extent, I feel like that hunch wasn’t totally off - I don’t see _that_ many startups / people writing their stuff in C#, but that doesn’t mean that they don’t exist (they do). However after really diving in (mostly writing in it for ~2 years), I’ve found it to be a really well designed, fast, and safe language that, again, just works and is getting constant updates from Microsoft (and after open sourcing, I’d assume many others as well). I often announce my like for C# with “C# is basically a better version of Java”. #fightme

On top of C#’s speed and ergonomics (big fan of Linq - it’s functional-ish syntax - as well as its normal syntax), C# has been widely used in the industry for quite some time so, similar to Python, has a devoted community with many packages and docs for much of your needs. Also it’s the primary citizen of Unity which I’ve been eyeing for a while for future, more complex (think 3d!) iterations of audio visualizers, like [moon-eye](https://labs.iamhamy.xyz/projects/moon-eye/):

VIDEO

Some downsides of C# is that I feel like there is some friction in just getting started (there are a good amount of dependencies you need to DL), I’m not 100% confident in the cross-platform experience (though anecdotally I run Linux and C# has worked fine and they’re def working on it), and I feel like the build process and common libs like web frameworks etc. just aren’t as simple to use as Python (though if you compare to many other languages, they’re still far simpler imo).

### c# pros

*   pretty darn fast
*   big community
*   been around for awhile so lots of docs and battle-tested libs
*   works everywhere, mostly
*   a well-designed language

### c# cons

### c# conclusion

If Python just isn’t fast enough, I’ll see if I can use C#. C# doesn’t seem to have quite as many libraries for #everything like Python, but is much faster, works cross-platform for the most part, and feels v nice to write in.

Rust
----

I’ll be honest, I’m more of a Rust fan-boy than an actual Rust developer but it’s still one of the top (3rd) languages I usually think about when considering what language to build a project in. The main reason for not yet taking the plunge is it’s kinda hard.

Don’t get me wrong, I think that it’s an extremely well-designed language and it seems like the internet agrees. But I’ve read [the book](https://doc.rust-lang.org/book/) (great book btw!) and tried a few times to get simple programs working as expected but each time was like “ugh, f this I could’ve written this 5 different ways in Python, stood up a website to interact / show off / ingest it, and written a launch post by now” and then stopped and written it in Python.

I think what gets me is the necessity to think about how your program is handling memory, both from the ownership aspect and size / location aspect. Of course you’ve had to do this in other languages like C and C++ for instance, but that’s one of the reasons both of those are near the bottom of my hierarchy. It’s important because that’s what all these languages are really doing behind the scenes - altering data - but I just don’t think it’s necessary for me to really need to think about this - Python and C# seem to agree.

But I think it’s something that is good to know and that’s one of the reasons why, despite this feature (not a flaw), that Rust is still in my top 3. I just need to find a problem that could benefit from its speed enough to warrant me taking the leap (and / or just take a month and make it happen).

Okay so that was a lot of barf all about why Rust is bad so why’s it good? Well it’s supposed to be super duper fast, it’s a language that is said to be most “correct” in that if you can get it to compile then that thing will likely run 5ever unless there’s like catastrophic interference (though this adds to the learning curve cause you’ve gotta fight the compiler to make it pass), it’s got like every modern feature and is actually pretty ergonomic / pretty to write in minus maybe all the memory Boxing / Unboxing #magic, plus it’s cool and new.

Like I bet if I rewrote [#webz](https://labs.iamhamy.xyz/projects/webz/) in Rust, it would be ~10x faster than the Python implementation (though also think it would take me 10+x longer to write than the Python one).

_A #webz output_

### Rust pros

*   v fast
*   has all ze modern features
*   v type safe / strong emphasis on correctness
*   a pretty language, minus all the memory things
*   extremely active community

### Rust cons

*   memory (Ahhh!)
*   high learning curve due to focus on “correctness”
*   new-ish and community isn’t quite as big as others so less things written / documented

### Rust conclusion

Rust is a language that’s basically on my “wish list”. I’ve never written anything substantial in it but it just seems super cool and if I can ever get over my fear of memory management maybe I’ll be more than a #fanboi. #swoon

middle languages
================

These are languages that I’ll use if it’s really the right tool for the job (like if a framework / lib / assignment / project / domain requirement is that I write in it) but that I don’t default to if I don’t have to.

javascript
----------

Oh Javascript. Honestly Javascript has come a long way since I first started using it (or more accurately, I’ve probably come a long way since misusing it in blobs of nested JQuery callback hell), but it’s not my favorite language. Like if I’m writing a server thing I’m almost definitely gonna choose !Javascript. But if it’s something that I want visitable by a browser then probably Javascript (though [wasm](https://webassembly.org/) may change that (and entice me to use Rust!!1)).

Javascript is cool cause it’s a first-class citizen (really primary) of web and web is accessible like everywhere and thus it’s a great and flexible tool. It’s pretty simple and when you add that to its inherent domain reach, you get a very large and active community of devs creating lots of packages and docs for you to use. Like any large and active community there’s gonna be some good stuff and some maybe-not-so-good stuff (like I always try to prefer [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) over [W3schools](https://www.w3schools.com/jsref/jsref_splice.asp) but if W3schools is the only one that has it then fine) but this is almost totally a plus.

Javascript just isn’t suuupppeeerr fast though browsers have done a great job making optimizations to make it run v fast. It also isn’t that cross-platform. Like I’d say Javascript runs on the web, but wouldn’t really say it runs on Windows, Mac, or Linux though you could certainly get it to.

One thing that Javascript is super good at (partially due to the maturity of the web as a platform, the maturity of this particular usecase, and its near-total-coupling with HTML / CSS (though you could argue some frameworks like React get it away from this)) is UI creation, design, and interaction. So while I might not use Javascript to do my heavy application lifting, I probably would consider it for creating a frontend for that application lifting (even over system-native UI frameworks / libs, mostly due to low cross-platform capability #buildonceruneverywhere).

### javascript pros

*   primary web citizen (for now) so it basically runs everywhere
*   huge, active community so lots of docs and libs
*   simple
*   v easy to get up-and-running (open in browser)
*   really great UI ecosystem

### javascript cons

*   not really cross platform but kinda
*   not suuuppppeeeerr fast

### javascript conclusion

I use Javascript for web things. If it’s not a web thing (like gets hit directly by a browser) or have a UI, then JS probably isn’t involved cause it’s not super fast, isn’t as easy as Python, and not _really_ cross platform.

go
--

Some people love Go. I am not one of those people. But I think I understand why.

Go is pretty fast, like 2⁄3 the speed of C in my mental model. It’s pretty simple with simple syntax and setup. It works everywhere (I think). It has a strong community.

But I think it’s ugly and it feels so simple that it’s almost tedious.

That’s really my only complaint with the language, but that’s enough to get it down to #5.

### go pros

*   fast
*   simple
*   good standard library
*   good community

### go cons

*   I think it’s ugly in that it’s too simple
*   I also don’t like the whole organization structure they force you into, though maybe that’s changed since last I touched it (and I know there are workarounds but I am #lazy)

### go conclusion

I’ll use Go if I’m contributing to a project in Go or someone wants to build in Go or I need to build in Go, but I’m not really ever thrilled to write in Go.

java
----

Java is there. It’s been there. It’ll continue to be there.

It works well, has a huge, mature community, and is continually being updated. But I think C# is a better version of it. So I’ll just use C#.

### java pros

*   fast
*   works everywhere (I think)
*   big, active community

### java cons

*   I think C# is better
*   seems kinda old and outdated, idk

### java conclusion

Java will do what you need it to do but I prefer C#.

bottom languages
================

These are languages that I’m going to go out of my way to avoid.

c / c++
-------

People will probably rage at me for slapping these bad boys together. But those people are likely already raging at me for other things I’ve said so what’s a little more #rage?

These languages are fast and feel like they’ve been around forever. They kinda feel like the ancient ones that are all powerful but have huge downsides. You know like Zeus and all his random courtships that somehow end in tragedy.

Of course some people love them but I think those are the people that are willing to take the time to really get to know them through many hours of tracking down memory leaks. I’m not one of those people (right now) as I’ve spoken to in my section on [Rust](https://labs.iamhamy.xyz/posts/2019-programming-language-hierarchy/#rust). So for the time being, I’m trying to give these languages some space.

Also I wrote a few C++ programs for a graphics class in college and I didn’t really understand the math nor the language so think I may still be scarred from that experience.

### c / c++ pros

*   mature codebase and community, so lots of docs and lots of libs
*   v fast - I’d almost say that they’re the gold standard for performance in the programming industry but I don’t really know anything about that
*   I hear they’re getting more modern! but also that some internal structures are making them hard to modernize but idrk

### c / c++ cons

*   ew, memory
*   They don’t seem very fun
*   Rust is shinier

PHP
---

I’ve only written in PHP once in college and I’ve only dabbled in [Hack](https://hacklang.org/) (Facebook’s PHP fork) at work a bit so I don’t have much real experience to back up these opinions with. Of course, I don’t have a lot of real experience to back up many of the preceding opinions so I’m not going to let that stop me now. Onwards.

The internet doesn’t seem to look fondly on PHP. But also a ton of people use PHP. Mixing that in with my own experiences, I’d say that PHP works. Though it might have some serious downsides. But it’ll probably work for you if you want to use it.

But you don’t just have to work, you also have to be better than Python for me to want to use you all the time. I currently don’t think it’s achieved that thus I mostly won’t use it.

### PHP pros

*   A lot of people use it, so probably lots of docs / libs
*   Can be pretty fast (I think)

### PHP cons

*   not better than Python imo
*   internet seems to have some bad feelings towards it, but I didn’t really do my research so idk

Swift
-----

I don’t really like Apple things. Swift is an Apple thing. But it’s also one of the Apple things I like most, so this whole paragraph is really nil in the grand scheme of judging Swift.

I don’t usually like Apple things cause they often make it very closed-system. My only evidence is that I have a Pixel and I can’t do those funny reactions that iMessage users love so much and everybody complains when I turn a group green. QQ

But all that baggage, again, isn’t really Swift’s fault. Everyone I know that uses Swift for iOS development (and even some server-side!) says they like the language. But it seems (from like 5 mins of reading) that it’s not super easy for Android. Maybe more of Apple’s closed-system things, idk.

Anywho mostly I don’t use Swift cause I’ve never had a good enough reason to try it out. Again, if it’s not better than Python for my use case then probably not gonna use it. I don’t do much mobile dev so that’s probably a big factor in this scenario but there you have it.

I’m skipping pros and cons cause I don’t really know that much about Swift.

### Swift conclusion

I don’t do much mobile dev and I haven’t heard much about Swift being a lot better than Python for non mobile so I haven’t tried it and likely will continue not to.

Assembly
--------

Too low-level. V verbose. Kinda confusing. I choose Python.

fin
===

Thanks for listening to my long-winded programming language rant! That’s all I’ve got for you (for now). If you would like to discuss a point I’ve made in this post / provide feedback / give suggestions / just rage you can [contact me via methods listed in my contact page](https://iamhamy.xyz/connect/) or just comment below. If you want to read more rants from me, consider [subscribing](https://iamhamy.xyz/subscribe/).

Always building / ranting / posting

\-HAMY.OUT

  
  
from Hacker News https://ift.tt/2XUs7Eg