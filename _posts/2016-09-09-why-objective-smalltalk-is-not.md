---
title: 'Why Objective-Smalltalk Is (Not) a Smalltalk (2019)'
date: 2020-02-02T11:13:00+01:00
draft: false
---

One of the main goals of

[Objective-Smalltalk](http://objective.st)

is to make it possible to express programs in mixtures of diverse architectural styles, and variations of those styles, naturally and comprehensibly. That needs a mechanism that abstracts from any specific style, while at the same time accommodating all, or at least a wide variety of styles.

I don't know how to do that.

Yet.

### A Smalltalk

Since I don't know how to do that yet, I can't build what I need, and since I can't build what I need I can't experiment with it and learn how to do what I need to do.

Instead of waiting for divine inspiration, designing something from thin air (that will _obviously_ be _perfect_) or just throwing my hands up in despair, I need to pick some starting point from which I can start iterating. In terms of styles, there are a few to choose from, for example _call-return_, _pipes-and-filters_ and _REST_. Call-return seems like an obvious choice, because it is something that is familiar, has widespread support and is very capable of implementing other styles.

Objective-C would have been a pleasant choice: I am very familiar with it and it is very suitable for building architectural and language adapters. This suitability is not an accident either, connectivity was the primary design goal, and the designers succeeded admirably given the constraints.

However, Objective-C also has significant drawbacks as a starting point: having already merged two languages, Smalltalk and C, it is rather large and unwieldy, with weird overlaps and other oddities. Being a superset of C, it also pretty much demands being compiled, whereas I want at least the option of interpretation.

WebScript would be an alternative, but it is not just dead, but also proprietary. It also very closely mimics the somewhat baroque Objective-C syntax, but without the actual reasons for those syntactic compromises or the benefits that this sacrifice brings in Objective-C.

These and most other existing language choices would mean _extending_ an existing language, grammar and implementation, meaning that the architectural features of the language would be almost certainly be 2nd class citizens, being tacked on wherever they can fit. That's not a good starting point (see: Objective-C).

So it really had to be a brand new language, one whose syntax and semantics would be under full control, and a syntactic starting point for the procedural part of that language. For this, I don't know of a better choice than the Smalltalk (keyword) message syntax. The syntax itself is _tiny_, with almost no reserved words or special characters reserved by the language, and almost all "language" features implemented as objects and messages without special syntax.

Having the procedural base as trivial as possible to implement is important, because I don't want to spend too much effort on it. I have (much) bigger fish to fry. Smalltalk also integrates well conceptually and syntactically with Cocoa and Objective-C, my preferred environment, a point not lost on the plethora of Smalltalk-based scripting languages available for Cocoa and GNUstep. And having a rich environment to integrate with is important for a language intended to connect existing pieces, which is what an architectural language does, or should do.

### Not a Smalltalk

So given all the arguments for Smalltalk, surely Objective-Smalltalk is based on one of the existing Smalltalks, such as

[Squeak](https://squeak.org)

, enjoying the great development environment, malleable infrastructure etc.

Not so fast.

Although Smalltalk fits very well conceptually and syntactically, it doesn't fit at all well _technically_. It generally runs in its own world, the _image_, requires a complex and sophisticated VM, with all the integration headaches that entails (FFI, JNI, etc.), and comes with and requires a GC. Integrating multiple tracing GCs is essentially an unsolved problem, so that's a bit of a downer for a language that wants to be able to glue existing pieces together.

The philosophy of current Smalltalks is the exact opposite: it wants to be the entire world. This is understandable: when Smalltalk was created there simply wasn't a "rest of the world" to talk to, and there certainly wasn't room for it on the same machine, an Alto with 128-512KB of RAM and a 2.5MB removable hard disk.

![](https://upload.wikimedia.org/wikipedia/commons/5/5e/Xerox_Alto_mit_Rechner.JPG)

A current Smalltalk has a lot of code, and communities that think it's just the greatest thing on earth, so resistance to change is significant and _reasonable_, both to smaller changes, because they just aren't worth it in that context, and to larger changes because they make things just too different. However, I want to make both large and small changes and not be hobbled by linguistic backwards compatibility.

> \[..\] when ST hit the larger world, it was pretty much taken as "something just to be learned", as though it were Pascal or Algol. Smalltalk-80 never really was mutated into the next better versions of OOP. Given the current low state of programming in general, I think this is a real mistake.

Alan Kay: [prototypes vs classes was: Re: Sun's HotSpot](http://lists.squeakfoundation.org/pipermail/squeak-dev/1998-October/017019.html)

So Objective-Smalltalk takes cues from Smalltalk where this is helpful, but it is not really a new version of Smalltalk. It's not a "[better old thing](http://worrydream.com/EarlyHistoryOfSmalltalk/)" (>45 years), but a (probably worse) "new thing", and for that reason it has to strike out on its own.

  
  
from Hacker News https://ift.tt/2RQL2id