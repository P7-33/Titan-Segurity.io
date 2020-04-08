---
title: 'Sentient: a high-level, declarative programming language'
date: 2019-10-01T01:38:00+01:00
draft: false
---

Hello,

#### What is Sentient?

#### Recorded media

#### Example programs

#### Getting started

#### Language syntax

#### Standard library

#### Command-line interface

#### JavaScript API

#### Supported Solvers

#### Syntax Highlighters

#### Miscellaneous

Computer, here’s my problem. Go figure.
=======================================

Sentient is a [high-level](https://sentient-lang.org/intro/high-level), [declarative](https://sentient-lang.org/intro/declarative) programming language that lets you describe _what_ your problem is and not _how_ to solve it. Sentient tries to figure that out for itself. It provides a rich toolkit to allow programmers to express their problems in a familiar way.

The following Sentient program solves the [subset sum problem](https://en.wikipedia.org/wiki/Subset_sum_problem). The challenge is to find a subset of numbers that add up to the given sum. This program iterates through an array of ‘numbers’ and adds them to the ‘sum’ if they are a ‘member’ of the subset. We don’t tell Sentient _how_ to solve the subset sum problem, we just describe _what_ it is.

![](https://sentient-lang.org/images/paperclip.png)

```
array20 numbers; array20 members; sum = 0; numbers.each(function^ (number, index) { sum += members[index] ? number : 0; }); expose numbers, members, sum; 
```

The example above is running in **real-time** in your browser. Sentient is written in JavaScript and is extremely portable. You can compile and run programs on a [command-line](https://sentient-lang.org/cli/overview) or [in a browser](https://sentient-lang.org/api/overview). Sentient can integrate with web applications or node modules alike.

Sentient is an [experimental](https://sentient-lang.org/intro/experimental) programming language that was created by [Chris Patuzzo](https://twitter.com/chrispatuzzo) as an exploration of declarative programming. It’s still in development and has a few rough edges. You can listen to the story of its inception on the [Why Are Computers](http://whyarecomputers.com/4) podcast.

Copyright © 2016, [Chris Patuzzo](https://twitter.com/chrispatuzzo), MIT License

  
  
from Hacker News https://ift.tt/2mwTxBZ