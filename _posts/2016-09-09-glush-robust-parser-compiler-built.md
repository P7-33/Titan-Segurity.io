---
title: 'Glush: A robust parser compiler built using non-deterministic automatons'
date: 2019-12-14T02:33:00+01:00
draft: false
---

![](https://cdn.sanity.io/images/3do82whm/next/18b2c50584718e1356e696ab22a3499e4ba65b55-5760x3840.png?bg=FFF&w=1001&fm=jpg&fit=max&auto=format "Introducing Glush: a robust, human readable, top-down parser compiler")  

It’s been 45 years since Stephen Johnson wrote Yacc (_Yet another_ compiler-compiler), a parser generator that made it possible for anyone to write fast, efficient parsers. Yacc, and its many derivatives, quickly became popular and were included in many Unix distributions. You would imagine that in 45 years we would have further perfected the art of creating parsers and would have standardized on a single tool. A lot of progress has been made, but there are still annoyances and problems affecting every tool out there.

We’re happy to announce that there’s now another tool for all our toolboxes: [Glush](https://github.com/judofyr/glush) is a parser toolkit that lets you create efficient parsers in multiple languages (currently JavaScript, Go, and Ruby) in a declarative and expressive grammar format. Glush focuses on supporting every type of grammar you can throw at it. This means you can write a grammar that’s easy for humans to read and that can function as a readable specification as well. While supporting a wide range of grammar features Glush maintains best-in-class performance.

In this article we will go into the philosophy behind Glush and its reason for existence. We’re going to start by explaining exactly the type of parser we’re interested in creating. We’ll look at the major parser techniques and tools that exist today and discuss how well they fit into our requirements. In the final section we’ll explain the inner workings of the algorithm behind Glush.

This article covers a wide range of fascinating topics and some of the sections below could easily be expanded to full chapters in order to be fully explained, but given time available (ours and yours) we’re leaving it at a few paragraphs of discussion. If you find something interesting we hope that we’ve provided enough references and links for you to learn more about it.

[](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#background-the-making-of-groq-f2d40c0e80e5)Background: The making of GROQ
------------------------------------------------------------------------------------------------------------------------------------------------

Why did we need Glush? Well, we needed it because of GROQ. GROQ (Graph-Relational Object Queries) is a flexible query language designed for working with JSON data. It was created by the team behind [Sanity.io](https://github.com/sanity-io/holm-glush-article/blob/master/%7Bsanity%7D), where it functions as the primary way of querying structured content. We’re pretty proud with how it has turned out, but to be honest designing and implementing a query language is one of the tasks we wish we didn’t have to do. The need for GROQ appeared back in 2016 when we were dreaming about the optimal way to structure content. We had a very clear plan:

*   We want to structure our content as plain old JSON with its flexibility of nested arrays and objects.
*   We want to put that JSON into a database. This database is the single source of truth.
*   We want to be able to write short, efficient queries for extracting, combining and shaping exactly the content we need.

Fast forward to 2019 and it turns out that GROQ has worked out _very_ well for us and our users. Yes, it’s a new query language to learn, but its expressiveness is surprisingly unique. One concern many users have had is that learning and writing GROQ locks them into our platform. At some level this is true since Sanity.io is currently the only service supporting GROQ, but we feel that it’s important to stress that we don’t _want_ GROQ to be a lock-in. We didn’t create GROQ because we wanted a proprietary technology that would lock users into our platform; we created GROQ because we had strong opinions about how a query language should work and we didn’t want to settle for anything less. As such, earlier this year we announced that we’re [open sourcing GROQ](https://www.sanity.io/blog/we-re-open-sourcing-groq-a-query-language-for-json-documents).

As a part of this initiative we want to make everything about GROQ as open as possible. The obvious first part then is the parser. How can we claim that GROQ is open source if we’re sitting on the only parser? I guess we should open source our parser then? Well, there’s a few problems with just open sourcing our parser.

The first problem is that we didn’t actually have a well-defined specification of the syntax. By open sourcing our parser we would essentially create a situation where the de-facto specification of the syntax becomes whatever that parser does. This is especially suboptimal because that parser is 2000 lines of handwritten Go. It’s unfortunate if people need to dig through exactly how it works in order to replicate every little strange behavior they find.

So no, we think that open sourcing our existing parser would be quite a meaningless gesture which doesn’t tackle the real problems towards an open query language.

[](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#what-does-the-optimal-parser-look-like-1aaa054e0a8c)What does the optimal parser look like?
------------------------------------------------------------------------------------------------------------------------------------------------------------------

What would the optimal open source parser for GROQ look like? Let’s dream a bit!

First of all: We want a **declarative grammar file**. What we really want is a human readable specification of the syntax which happens to be executable as well. That makes it important for the grammar language to be flexible: We want to write the grammar in a way which is it clear for the human reading and writing it, even if that comes at the expense of making it harder for the parser.

We want the grammar file to **specify both the lexing and parsing**. Many parser algorithms are based on the concept that you parse in two steps: First a lexer step where you look at the input and produces tokens (e.g. `1 + 1` would be converted into `NUMBER PLUS NUMBER`), and then you have parser step where you look at the tokens and determine the structure. (Yes, it’s a bit confusing that sometimes "parse" means "do the whole job" and other times it only means the step which looks at tokens.) We don’t mind this separation per se, but it’s important for us to be able to specify _all_ the rules in a single file. If the grammar file can only cover the parsing step we need a separate solution for how to write down the lexer rules. A parser which does both steps at the same time is often called a _scannerless parser_.

We want to be able to generate parsers for **multiple programming languages**. Initially we want to generate a JavaScript parser. Later we want to generate a Go parser which can replace our current internal parser. Other than that we just want to make it easy to add support for more programming languages over time.

We **don’t need super fast performance**. The primary function of this parser is to _correctly_ parse GROQ queries in different languages. For most use cases you don’t need super fast performance since the execution time of the query will completely dominate the time spent parsing. For those cases where you really care about the performance of the parser you might not be able to use this parser. That is okay. You can still then use this parser to verify that you’re parsing everything correctly.

Even though we don’t "care" about performance, it must still have **_reliable_** **performance**. We want to be able to run this parser in production, and it’s important that it doesn’t collapse (e.g. suddenly takes exponential time) on pathological cases.

[](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#what-about-the-existing-tools-and-techniques-f94bf5c7040d)What about the existing tools and techniques?
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Parsing is an interesting field in computer science. I recently discussed different approaches to verifying the correctness of parser algorithm with a computer science professor, and his first statement was "Why are you working on a parsing algorithm? That’s a solved problem!" This is true at a certain level as most grammars (for programming and query languages) can be written in LALR(1) which can be efficiently parsed. A parser is also something you write once and then never need to touch again. It might be hard work to write the initial grammar, but it doesn’t matter so much because you only need to do it once.

However, in practice it turns out that LALR(1) isn’t always the answer. For instance, both GCC, Rust and Go have chosen to use handwritten parsers that are not based on a declarative grammar file. I find this disappointing: We have decades of experience with specifying languages in a declarative format, and apparently it’s still easier to manually write parsers. Obviously there’s something lacking with the algorithms we have today.

This is a problem which has irked me for a long time. One of my weaknesses in getting things done is that I often get distracted by wanting to improve _all of the things_. I have this great idea for a web application, but as I start working on it I find that the web framework has some annoying quirks. Then I’ll start playing with ideas for a better web framework, but as I start working on it I find that the programming language has some annoying quirks. Then I’ll start playing with ideas for a better programming language, but as I start working on it I find that the parser toolkits have some annoying quirks. Now I just need to build the best parser toolkit so I can complete the best programming language so I can complete the best web framework, and then I’ll finish the great web application in _no time_.

The result of this endeavour is that I’ve tried _many_ parser toolkits and read up on pretty much all of the algorithms that are out there. I’m constantly on the lookout for an approach that can handle all of the requirements in the previous section. The algorithm behind Glush is, at this moment in time, what I believe is the most promising solution, but I will be very honest and admit that it’s been a long journey and that it might end up being another dead end.

In this section I will summarize the various parser algorithms and tools that I’ve looked at. This will tell you how I have discovered a technique, learnt something from it, and then eventually end up discarding it for some reason. Unsurprisingly, this section will slowly converge towards the machinery behind Glush.

The classical way of creating a parser involves creating a _context-free grammar_, which is a set of recursive rules that describes the language. There are many different types of grammars, but it turns out that _context-free_ grammars has a nice combination of expressiveness and ease of parsing and therefore they have become ubiquitous. Typically you see context-free grammars written in BNF style:

A context-free grammar for basic arithmetic of single-digit numbers.

```
expr ::= expr "+" expr | expr "-" expr | expr "\*" expr | expr "/" expr | number number ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"
```

There are some fundamental facts that you should be aware of when it comes to context-free grammars.

**Context-free grammars can be ambiguous**. The grammar above for basic arithmetic has an ambiguity as there are multiple ways to interpret a string like `2*3+1`. Should we do the multiplication or the addition first? Well, the grammar says nothing about that. For programming and query languages you probably want to have a grammar which is unambiguous, but it turns out that it’s impossible to determine if a grammar is unambiguous or not.

**Many unambiguous context-free languages can be parsed in O(n), linear, time.** Context-free grammars is just a way of specifying a language and not an algorithm per-se, but many subsets of context-free grammars turns out to be possible to parse in linear time. This is good!

Surprisingly, it turns out that **_all_** **context-free languages, even the most ambiguous ones, can be parsed in O(n3), cubic, time**. This isn’t _great_, but it’s _much better_ than exponential time complexity. I’ll talk more about this in the section for [The CYK algorithm](https://github.com/sanity-io/holm-glush-article#the-cyk-algorithm), but for now be aware that a good parser algorithm should be able to parse all context-free grammars in cubic time.

**The number of possible parses can be exponentional.** The ambiguous grammar above has an exponential amount of different ways to be parsed. A parser algorithm which tries to construct all of these different parse tree will obviously _not_ be able to run in cubic time. The solution around this is to construct a _parse forest_, a compact representation where you share as much as possible between the different trees.

In addition to these facts, it’s good to know about the terms "left-recursion" and "right-recursion". Left-recursion is when you have a grammar rule which refers to itself in the leftmost position. As an example we can look at the parent operator in GROQ. In GROQ you can write `^` to refer to the parent scope, `^.^` to refer to the scope above there, and so on. A natural way to define this is with the following grammar:

A grammar for the parent operator in GROQ:

```
parent ::= "^" | parent ".^"
```

At first it might seem a bit strange, but it reads out very well:

*   The first part states that `^` is a parent operator.
*   The second part states that you can add `.^` to a parent operator to find its parent.

Right-recursion is the same concept, but when you have the recursion in the _rightmost_ position.

Left- and right-recursion are important concepts because they’re often difficult for the parser algorithm to handle efficiently. At the same time, left- and right-recursion are very nice ways to express syntax from a human’s perspective. For instance, the following is a grammar for the parent operator which is not left-recursive. Personally I find this far more convoluted and unobvious than the previous one.

A grammar for the parent operator in GROQ that’s not left-recursive:

```
parent ::= "^" parent\_rest parent\_rest ::= ".^" parent\_rest | # nothing
```

### [](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#ll-lr-lalr-parser-generators-03ecbe1f0978)LL/LR/LALR parser generators

The classical parser generators that have been used for programming languages are based around LL and LR grammars. LL and LR grammars are two different subsets of context-free grammars which are unambiguous and can be efficiently parsed. Yacc, [Bison](https://www.gnu.org/software/bison/), [Jison](https://github.com/zaach/jison), [Racc](https://github.com/ruby/racc), [LALRPOP](https://github.com/lalrpop/lalrpop) are all examples of tools which implements these algorithms.

One nice feature of these parser generators is that they generate code, and that means it’s (often) easy to add support for multiple languages.

The biggest annoyance with these tools is that they only support a subset of context-free grammars, and if you don’t write your grammar in the "accepted form" you will get an error ("shift/reduce conflict" or "reduce/reduce conflict") and no parser. To make life even harder, these tools are often very bad at reporting _why_ or _where_ there is a conflict.

```
$ racc calc.racc.y 16 shift/reduce conflicts 
```

A good example of how big of a problem this is in practice can be found in a case study by Malloy et al. [\[3\]](https://github.com/sanity-io/holm-glush-article#csharp-lalr). They describe the development of a C# parser using proper software engineering techniques: having everything stored in version control, writing test cases, and using a parser generator. They started with a grammar from the C# language definition and used Bison as the parser generator. Turns out that the "obvious" straightforward grammar had 40 shift/reduce and 617 reduce/reduce conflicts. In order for Bison to accept it they had to refactor the grammar over **16 major revisions**. Each and one of these revisions turns the grammar one step _away_ from the original specification and turns it into something that is designed to please Bison. This is the quite opposite of the principle that "programs must be written for people to read, and only incidentally for machines to execute".

For our specific use case this is a major blow. One of our goals was to have a grammar which was as close to the specification as possible. Being forced to rewrite a human-understandable grammar into a less clear machine-understandable grammar is simply not acceptable.  

The CYK algorithm (named after Cocke–Younger–Kasami) is in my opinion of great theoretical importance when it comes to parsing context-free grammars. CYK will parse _all_ context-free parsers in O(n3), including the "simple" grammars that LL/LR can parse in linear time. It accomplishes this by converting parsing into a different problem: CYK shows that parsing context-free languages is equivalent to doing a boolean matrix multiplication. Matrix multiplication can be done naively in cubic time, and as such parsing context-free languages can be done in cubic time. It’s a very satisfying theoretical result, and the actual algorithm is small and easy to understand.

To make things even more interesting, Lee [\[2\]](https://github.com/sanity-io/holm-glush-article#lee-mm) showed that the opposite is true as well: You can use a context-free parser to do matrix multiplication! This is especially interesting because it means that any improvements we can find in parsing context-free languages might help us get better matrix multiplication algorithms.

However, given that CYK uses cubic time on even the simplest grammars it’s not a very practical algorithm, and it’s not the answer to our optimal parser.

### [](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#parsing-expression-grammars-d1d108380177)Parsing expression grammars

_Parsing expression grammars_, or PEG, were introduced by Bryan Ford in 2004 [\[1\]](https://github.com/sanity-io/holm-glush-article#peg-ford) and has been a quite popular technique for parsing in modern days. They are relatively easy to implement and understand, and as such there are many different implementations in a wide range of languages. One of my favorite implementation is [Canopy](http://canopy.jcoglan.com/) by James Coglan. It’s structured as a generator which is written in JavaScript and can generate code for both Java, JavaScript, Python and Ruby.

PEGs are similar to LL/LR parsers in the sense that they can’t parse all context-free grammars, but PEGs always have a well-defined behavior when there’s multiple choices and will never give you a conflict. This is very refreshing after spending hours figuring out how to get rid of the "shift/reduce conflicts". However, in my experience, it turns out that PEGs work great for simple grammars, but as the grammar becomes more complicated it’s hard to make it parse the way I want. For instance, PEG does not support left-recursion at all, and I’ve spent so much time refactoring PEGs to avoid left-recursion while still making it parse the right way. It’s tiresome work.

There has been work on adding support for left-recursion and precedence in PEGs (see [\[4\]](https://github.com/sanity-io/holm-glush-article#left-peg)). This is interesting work which I have played with and attempted to implement, but I’m not convinced that it’s the right way forward. The semantics of PEGs are fundamentally a bit tricky to work with and I think our time is better spent working on parsers which are based on full context-free grammars.

In practice it turns out that writing a PEG has the same problem as writing a LL/LR grammar: You always need to shape the grammar to fit the tool. The main difference is that when your grammar is incorrect LL/LR will give you an error at _compile time_, but a PEG will just not parse the input as you expected. There’s also the additional disadvantage that a PEG parser uses excessive memoization in order to have decent performance.

There has been a lot of research in implementing algorithms that can parse _any_ context-free grammars. The first well-known algorithm is the Earley parser [\[14\]](https://github.com/sanity-io/holm-glush-article#earley) which parses deterministic grammars in linear time and ambiguous grammars in cubic time. Later Tomita [\[5\]](https://github.com/sanity-io/holm-glush-article#tomita-glr) published GLR which uses a graph-structured stack in combination with a LR-style parser in order to support all context-free grammars. And in 2010 Scott and Johnstone published GLL that similarly extends an LL-style parser.

All of this sounds great, but the devil is in the details. Earley is known for not having great performance; Tomita showed that GLR was 5x-10x faster. Even so, in many benchmarks GLR ends up being orders of magnitude slower than handwritten parsers (e.g. [\[16\]](https://github.com/sanity-io/holm-glush-article#all)). The original GLR algorithm by Tomita turns out to not correctly handle certain grammars, and there’s been at least two proposals for how to fix it: Farshi’s [\[7\]](https://github.com/sanity-io/holm-glush-article#farshi-glr) solution and RNGLR [\[6\]](https://github.com/sanity-io/holm-glush-article#scott-rnglr). There has also been work on improving the performance of Earley parsers: Leo in 1991 [\[17\]](https://github.com/sanity-io/holm-glush-article#earley-leo) and Aycock and Horspool in 2002 [\[18\]](https://github.com/sanity-io/holm-glush-article#earley-aycook). GLL appears to be a great solution, but I’ve also seen benchmarks where it’s even slower than GLR.

It’s quite frustrating investigating these algorithms because there are so many variants and tweaks, and there’s little work in comparing them exhaustively to each other. For instance, Earley’s original algorithm included an extra look-ahead in the state, but this turned out to have little effect so it’s often dropped in implementations. And yet, those implementation are still called an "Earley parser". You read one paper where a GLR implementation is superfast, and suddenly you find another paper where a GLR parser is 10x slower than all of the others. [Bison has an implementation of GLR](https://www.gnu.org/software/bison/manual/html_node/GLR-Parsers.html), but it turns out that this displays exponential growth in memory requirements [\[19\]](https://github.com/sanity-io/holm-glush-article#johnstone-glr-eval).

One project deserving special mention is [Marpa](https://metacpan.org/pod/Marpa::R2:) by Jeffrey Kegler. Marpa is a parser toolkit for Perl based on Earley parsing and incorporates all of the known improvements. I really wish I was able to use this across different languages and it’s _kinda_ possible because the runtime is written in C. C is easily usable in every environment _except_ for JavaScript on the web. Porting libmarpa to JavaScript doesn’t seem like an easy undertaking either judging from this comment on its webpage:

> Libmarpa is highly mathematical code. Its internals are, frankly, daunting. For me, Marpa has a real beauty, but nobody could claim it achieves that beauty through simplicity. I once had hopes that reading Marpa would be like experiencing the effortless power of a late Picasso. But Angkor Wat and Hieronymous Bosch show that beauty comes in many forms.

I think this quote accurately describes many of the GLL/GLR-based parsers as well. I have multiple half-finished projects where I try to implement these approaches, but somehow I was never able to finish them up in a way I was happy with. Notably I have started both a Rust and a Java version of a GLL-based parser toolkit that’s now collecting dust somewhere on my hard drive. Maybe someone else can make them viable, but I’ve always been looking for something that feels more fundamental and simpler in its core.

Jeffrey Kegler has also compiled a [timeline of parsing](https://jeffreykegler.github.io/personal/timeline_v3) which lists major breakthroughs in the world of parsing. This is a very good resource with a lot of links and references and I would highly recommend it. A reader should however be aware that it is a _very biased_ account of history which concerns itself mostly with the direct influences of Marpa. There’s no mention of GLL, and more strangely there is not even a single word about GLR which was published back in _1984_ and has seen adoption. This means that if you’re reading the timeline naively it seems to start at 4th BCE and linearly progress into Marpa being the solution.

### [](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#mark-johnsons-top-down-parser-1ee337ffa261)Mark Johnson’s top down parser

Mark Johnson deserves a special mention for his paper "Memoization of top down parsing" [\[8\]](https://github.com/sanity-io/holm-glush-article#mark-memo). This paper starts by representing context-free grammars as functions in Scheme, and then introduces techniques such as memoization and continuation-passing style to make it efficient and general.

This was one of the first papers I read which both was able to parse context-free grammars _and_ showed that such grammars don’t necessarily have to be written in BNF form. It’s also a very good example of describing an algorithm in an incremental approach, slowly adding one feature at a time.

Practically it’s not directly usable as it ends up having exponential complexity in the worst-case due to not having a packed parse forest representation.

In 2010 Matt Might and David Darais published a paper called "Yacc is dead" [\[9\]](https://github.com/sanity-io/holm-glush-article#yacc-dead). I have no idea why they decided on such a clickbaity title because the idea itself is more than fascinating enough! The idea presented is about taking the _derivative_ of a context-free grammar, and using this for parsing. This "derivative" we’re talking about here is not the typical derivative from calculus (in the sense that it tells you the rate of change of a function), but it does obey the regular derivative rules (product rule and chain rule). The concept of derivative of a grammar was first proposed by Brzozowski in 1964 [\[10\]](https://github.com/sanity-io/holm-glush-article#deriv-brz) for regular languages, and this paper extends it to the full power of context-free grammars.

The principle behind parsing with derivatives is a bit strange compared to other approaches. In a typical parsing algorithm you have the _grammar_ and the _input_. As you’re parsing the input you maintain some information about what you’ve parsed so far (the _state_). To parse the complete input you gradually work through it and eventually returns the final state. The grammar stays the same, but the state changes.

When you’re parsing with derivatives you don’t have any state at all, but instead you keep changing the _grammar_ at each step. In a sense, the grammar becomes the state. You start with the initial grammar and look at the first character in the input. Then you create a _new grammar_ which will match the same language, _only without the first character_. This new grammar is what we call "the derivate of the grammar with respect to a character". You can proceed with this for each character in the input, and you’ll end up with a final grammar. If the final grammar matches the empty string, you know that it’s a valid match.

This is such a unique approach and initially it looked very interesting, but it’s not completely smooth. First of all, all of the implementations have been in highly expressive, garbage collected languages (Haskell, Scala, Racket). Their technique is based on representing the grammar using recursively defined data types, and uses lazy evaluation in order to handle left-recursion. It’s unclear to me exactly how you would structure the parser in a language such as C or Rust and how its performance would be. In addition, the performance is not guaranteed by the core algorithm, but is handled by a separate _compaction_ step. This makes me weary that there could be an edge case where the compaction isn’t working optimally (or haven’t been implemented correctly) and there’s a pathological case hidden.

There has been some good follow-up work since the initial article was published. Matt Might published a longer blog post where he describes the approach and links to various implementations and critiques: ["Yacc is dead: An update"](http://matt.might.net/articles/parsing-with-derivatives/). There’s also been a few papers [\[12\]](https://github.com/sanity-io/holm-glush-article#pwd-matt) [\[13\]](https://github.com/sanity-io/holm-glush-article#pwd-compl) [\[11\]](https://github.com/sanity-io/holm-glush-article#pwd-sym) which improves and/or discusses the performance. The conclusion I’ve drawn from all of this work is that creating an effective parser with derivatives is not such a simple task as initially claimed. There’s also no obvious way to support multiple programming languages from a single code base.

[ANTLR](https://www.antlr.org/) is one of the most solid parser toolkits out there. It’s written in Java, but can also generate parsers for C#, Python, JavaScript, Go, C++, Swift and PHP. The fourth version of ANTLR also features a brand new algorithm: Adaptive LL(\*) [\[16\]](https://github.com/sanity-io/holm-glush-article#all).

ALL(\*) is a highly performant parser algorithm which supports ambiguity in the grammar by exploring different paths at runtime and eventually committing to one result. In situations where there are multiple valid parses for two alternatives, ALL(\*) will always pick the first one. This is a sensible approach in many situations, but it’s a bit unfortunate when you’re writing a declarative grammar that should also function as a specification. Once again we see that we need to structure our grammar to fit the tool. ALL(\*) also has worst-case _quartic_ performance, O(n4), which is not best-in-class (but at least not exponential).

### [](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#regular-expressions-and-glushkovs-construction-algorithm-61abed0596bc)Regular expressions and Glushkov’s construction algorithm

Most programmers have seen and used regular expressions; sometimes without completely understanding what’s going on. They are powerful beasts allowing you to solve problems in succinct ways. Regular expressions by themselves are not only powerful, but many programming languages also extend their regular expressions with additional features. Formally there’s a very strict definition of what a regular expression is and can do, and for this part we’re going to look at these _proper_ regular expressions.

Parsing with regular expressions is accomplished by converting the expression into an _automaton_ (also called a _state machine_). Typically you start by converting the expression into an NFA (non-deterministic finite automaton) which is then further converted into a DFA (a deterministic variant). Once you have the DFA you can very efficiently parse any input in linear time.

I never looked that deeply into the various ways of parsing with regular expressions because I’ve known that they are not expressive enough to handle context-free grammars. This changed in early 2019 when I discovered the 2010 paper: "A Play on Regular Expressions" by Fischer, Huch, Wilke [\[20\]](https://github.com/sanity-io/holm-glush-article#glushkov-play). This paper explains how you can use something called _Glushkov’s construction algorithm_ to match regular expressions in idiomatic (functional) Haskell, where they also extended it with basic support for context-free grammars. Exciting!

This was especially exciting because this discovery was all due to a [tiny status by someone named Jamey Sharp](https://toot.cat/@jamey/101393064450390819) on Mastodon (the open-source Twitter alternative):

> tfw you mix up Glushkov’s construction with Brzozowski’s derivatives, amirite?  
>   
> no? that’s just me?

What followed was a fruitful discussion about Glushkov’s construction algorithm where we together were trying to figure out its essence. These type of spontaneous discussions are what makes me appreciate the open-source community so much. You know nothing else about them than their public name and their avatar, and all the focus is on sharing knowledge and solving problems.

After this interaction I continued to play with the approach and started restructuring it into a more standard-looking parsing algorithm written for imperative languages. After months of tweaking and experimentation I was finally able to finalize a decent parser algorithm, and the results are looking very promising. It’s naturally top-down and handles unambiguous grammars sensibly, but still maintains worst-case cubic performance for even the worst-looking ambiguous grammar.

In order to honor its origin I decided to call the first implementation for _Glush_.

Now that we’ve told a bit about the history behind Glush, let’s have a look at how it actually looks. To create a GROQ parser we’ve written a declarative grammar file which Glush reads and can generate parsers from:

A subset of the GROQ grammar file:

```
main = \_ EXPR \_ SPACE = | "\\t" | "\\n" | "\\v" | "\\f" | "\\r" | " " | "\\u0085" | "\\u00A0" COMMENT = "//" !"\\n"\* "\\n" \_ = { SPACE | COMMENT } PIPE = "|" STAR = "\*" @next(!"\*") PARENT = | $parent "^" | $dblparent PARENT ".^" EXPR = 11| NUMBER 11| STRING 11| ARRAY 11| OBJECT 11| $star STAR 11| $this "@" 11| PARENT 11| $paren "(" \_ EXPR \_ ")" 11| "$" $param IDENT $param\_end 11| $ident IDENT $ident\_end 11| FUNC\_CALL 1| $pair EXPR^2 \_ "=>" \_ EXPR^2 2| $or EXPR^2 \_ "||" \_ EXPR^3 3| $and EXPR^3 \_ "&&" \_ EXPR^4 4| $comp EXPR^5 \_ $op COMP\_OP $end \_ EXPR^5 4| $asc EXPR^4 \_ "asc" 4| $desc EXPR^4 \_ "desc" 5| $inc\_range EXPR^6 \_ ".." \_ EXPR^6 5| $exc\_range EXPR^6 \_ "..." \_ EXPR^6 6| $add EXPR^6 \_ "+" \_ EXPR^7 6| $sub EXPR^6 \_ "-" \_ EXPR^7 7| $mul EXPR^7 \_ STAR \_ EXPR^8 7| $div EXPR^7 \_ "/" \_ EXPR^8 7| $mod EXPR^7 \_ "%" \_ EXPR^8 9| $pow EXPR^10 \_ "\*\*" \_ EXPR^9 11| $neg "-" \_ EXPR^8 11| $pos "+" \_ EXPR^10 11| $not "!" \_ EXPR^10 11| $deref EXPR^11 "->" \[ \_ $deref\_field IDENT $end \] 11| $attr\_ident EXPR^11 \_ "." $ident IDENT $ident\_end 11| $pipecall EXPR^11 \_ PIPE FUNC\_CALL 11| $project EXPR^11 \_ PIPE? OBJECT 11| $filter EXPR^11 \_ PIPE? "\[" \_ EXPR \_ "\]" 11| $arr\_expr EXPR^11 \_ PIPE? "\[\]"
```

  
Let’s discuss briefly what this grammar file supports:

*   You can use regular expression syntax like `*`, `+`, `()`, but also the more traditional EBNF syntax for specifying repetition (`[ A ]` and `{ A }`).
*   The grammar works directly on the string and as such you need to be very explicit about where you allow whitespace and comments. The grammar becomes a bit verbose, but it will describe the language completely.
*   You can use `@next` in order to match on the next token. This is required in some cases to avoid ambiguities.
*   The output from the parser is a list of _marks_ and you need to place them in the grammar where you need them (e.g. `$mul`).
*   You handle operator precedence with _precedence levels_ (e.g. `EXPR^11`). This might initially look a bit daunting, but it’s a surprisingly simple concept which allows you full control over associativity and precedence.

Currently Glush is implemented in Ruby and is capable of generating JavaScript parsers. The choice of Ruby as implementation language is purely given my comfort with it as I can efficiently try out different approaches. In the future when the code stabilizes I can see it being useful to port it over to Go to make it easier to use for others.

It should also be mentioned that Glush is still a work-in-progress in many ways. The core algorithm has been refined over the last few weeks and the code base is not entirely up-to-date with latest discoveries. Documentation is severely lacking. This is slightly intentional until all of the pieces fall into place. Currently Glush can only generate JavaScript parsers, but I soon plan on expanding it to generate parsers in Go as well.

We’re actively using Glush in our [JavaScript implementation of GROQ](https://github.com/sanity-io/groq-js) and are committed to making it work as smoothly as possible.

Now that we’ve seen how we can _use_ Glush, let’s take a look at how the algorithm actually works. This section will be _very_ technical and is probably only of interest if you want to learn the nitty-gritty details.

The parser algorithm is based on taking regular expressions and extending them with the ability of defining _rules_ which can be recursive (in any way we want):

```
\# Regular expressions: DIGITS = \[1-9\]+ \[0-9\]\* # ... which can be recursive! EXPR = DIGITS | (EXPR '+' DIGITS)
```

The regular expression language has a lot of various syntax (e.g. `[0-9]*`, `"hello world"`), but internally this can be represented by only a few essential expressions:

1.  The _epsilon_ (`eps`) matches nothing.
2.  A _terminal_ (`'a'`) matches a single character.
3.  A _rule call_ (`r!`) matches a rule.
4.  A _sequence_ (`a b`) matches two expressions followed by each other.
5.  An _alternative_ (`a | b`) matches two expressions in parallel.
6.  A _plus_ (`a+`) matches one or more repetitions of an expression.

The first step which Glush does is to normalize the grammar into these essential expressions. For example, the representation of the regular expression `ab*` would become `'a' (eps | 'b'+')`. The next step involves converting these expressions into a _state machine_. Every terminal and rule call becomes a state, and the other expressions are used for building the transitions between the states. This simplifies the runtime of the parser algorithm because we only deal with three different concepts: terminals, rule calls, and the transitions between them.

### [](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#building-the-state-machine-7fc7674fbab3)Building the state machine

Glush uses, and gets its name from, the [Glushkov’s construction algorithm](https://en.wikipedia.org/wiki/Glushkov%27s_construction_algorithm). This is an algorithm for building a state machine for regular expressions. For some reason, this algorithm seems to be less known than [Thompson’s construction](https://en.wikipedia.org/wiki/Thompson%27s_construction), an alternative algorithm for the same purpose. The advantage of Glushkov’s construction algorithm is that it converts the regular expression directly into a state machine _without_ any epsilon-transitions, while with Thompson’s construction you need a separate pass to eliminate those. In addition, it turns out that Glushkov’s construction algorithm can easily be extended to handle our recursive rule calls.

Glushkov’s construction algorithm starts by computing the _nullability_, the _first set_, the _last set_ and the _pair set_ of an expression. We’ll now look at these four computations in order, with our extension of recursive rule calls.

We say that an expression is _nullable_ if it matches the empty language. More concretely it’s defined as:

1.  The _epsilon_ (`eps`) is nullable.
2.  A _terminal_ (`'a'`) is not nullable.
3.  A _rule call_ (`r!`) is nullable if the body of the rule is nullable.
4.  A _sequence_ (`a b`) is nullable if both expressions are nullable.
5.  An _alternative_ (`a | b`) is nullable if one of the expressions are nullable.
6.  A _plus_ (`a+`) is nullable if the expression is nullable.

There is one crucial detail we must take care of here: How should we deal with recursive rule calls? Notice that a rule call is nullable if the body is nullable, but the body might include a rule call to itself and as such we would have an infinite loop. The solution is to only require a _least fixed-point_ interpretation. This means we’ll start by marking all rule calls as being not-nullable (instead of checking the rule’s body), and then compute the nullability of all the rule bodies. Since there’s no recursion happening now this doesn’t cause an infinite loop. If any of the rule bodies turned out to be nullable then we would mark all of its rule calls as nullable instead of not-nullable. We then repeat the same process until we reach the fix-point where all rule calls are marked correctly. This process must eventually complete because once _all_ rules have been marked as nullable there is nothing more to do.

Once we can determine the nullability of an expression we can build the _first set_. The first set of an expression is the set of terminals and rule calls which occur first in an expression:

1.  The _epsilon_ (`eps`) has an empty first set.
2.  A _terminal_ (`'a'`) has a first set consisting of itself.
3.  A _rule call_ (`r!`) has a first set consisting of itself.
4.  A _sequence_ (`a b`), where `a` is nullable, has a first set which is the union of the first set of `a` and `b`.
5.  A _sequence_ (`a b`), where `a` is not nullable, has the same first set as the first set of `a`.
6.  An _alternative_ (`a | b`) has a first set which is the union of the first set of `a` and `b`.
7.  A _plus_ (`a+`) has the same first set as the first set of `a`.

Similarily, the _last set_ of an expression is the set of terminals and rule calls which occur last in an expression:

1.  The _epsilon_ (`eps`) has an empty last set.
2.  A _terminal_ (`'a'`) has a last set consisting of itself.
3.  A _rule call_ (`r!`) has a last set consisting of itself.
4.  A _sequence_ (`a b`), where `b` is nullable, has a last set which is the union of the last set of `a` and `b`.
5.  A _sequence_ (`a b`), where `b` is not nullable, has the same last set as the last set of `b`.
6.  An _alternative_ (`a | b`) has a last set which is the union of the last set of `a` and `b`.
7.  A _plus_ (`a+`) has the same last set as the last set of `a`.

The final piece of the puzzle is the _pair set_. I’m not going to write out the concrete definition here in prose since it’s a bit verbose, but the principle is not complicated. The pair set contains pairs of terminals and rule calls _which are allowed next to each other_. A few examples should hopefully makes this more clear:

*   The regular expression `abc` has the pair set `{('a','b'), ('b','c')}`; `b` can come after `a` and `c` can come after `b`.
*   The regular expression `(ab)+` has the pair set `{('a','b'), ('b','a')}`; `a` can come after `b` when there’s a repetition.
*   The regular expression `ab?c` has the pair set `{('a', 'b'), ('a', 'c'), ('b', 'c')}`; `c` can come after `a` because the `b` is optional.

With these three sets we can build a quite efficient regular expression engine:

*   We maintain a set of _active terminals_.
*   Initially, the active terminals are populated from the first set of the expression.
*   For each character in the string,
*   loop over each active terminal,
*   and if the terminal matches the character,
*   then we’ll use the pair set to find the _next_ active terminals.
*   After processing all characters, the string was matched if one of the last matched terminals is in the last set.

This algorithm is linear in time with respect to the string.

### [](https://www.sanity.io/blog/why-we-wrote-yet-another-parser-compiler#adding-support-for-recursive-rule-calls-4c1526d3f1b7)Adding support for recursive rule calls

The algorithm presented in last section is only capable of parsing regular expressions. Let’s look at how we can extend it to also support recursive rule calls which will unlock the full power of context-free grammars. As an example for this section I’ll use the basic (ambiguous) grammar for addition. The rule calls have been labelled with underscores in order to be able to distinguish between them. This is crucial because every rule call is concidered unique.

```
digits = \[1-9\]+ \[0-9\]\* expr = digits\_0 | (expr\_1 '+' expr\_2) main = expr\_0
```

The overall strategy for parsing hasn’t changed: We start with the first set and we transition until we reach the last set. However, all of this must happen _per rule_. This means that when we try to transition into a rule call, we want to enter it and transition into its first set instead. Similarily, once we reach transition into the last set, we want to return to wherever we came from and continue transitioning there.

In order to be able to keep track of where we came from, we introduce _contexts_. A new context is created for each rule at each position in the string. The context named `(expr, 2)` represents the parsing of the `expr` rule at position 2. During parsing we maintain a set of active states, where each state is the combination of a terminal and a context. Every context stores a set of _origins_, where an origin is a combination of a rule call and a context. The meaning of an origin is to signal that once we’ve successfully completed the rule, we should continue transition away from that rule call with that given (parent) context. In a sense the origin set forms a call stack: The rule call represents where in the grammar we should return to, and the context represents the parent call frame.

After we’ve successfully matched a terminal there can either be a transition to another terminal or to a rule call. Transitioning to another terminal will just push the terminal as a new active state with the current context. Transitioning to a rule call on the other hand will do various things:

*   We find the context for the rule at the current position (or create it if it doesn’t exist).
*   Inside this rule context we insert a new origin consisting of the rule call and the current context.
*   Then we invoke the rule with the new rule context: We look at the first set of the rule body in order to find a set of terminals. All of these terminals are pushed as new active state together with the rule context.

In addition, if the successfully matched terminal is a part of the last set it means that we have completely parsed a rule. Then we need to look inside the origin set and continue transitioning away from the rule calls.

There are a few more details that need to be handled before this algorithm works correctly. It might not be obvious, but the algorithm presented above only works if any rule call is in the middle (e.g. `s = 'a' b 'c'`).

The problem with a rule call in a left position (e.g. `expr_1` in `expr = expr_1 '+' expr_2`) is that once we enter a new rule we only look at _terminals_ in the first set. The `expr` rule in our example has a first set of `{digits_0, expr_1}` (no terminals!) and using the algorithm as-is would then silently stop parsing anything more. To handle this case we introduce the _enter set_ of a rule call. The enter set contains all rule calls, recursively, that’s at beginning of a rule. We can look at the enter set as the set of additional rule calls that needs to be invoked when you invoke a rule call. In our example grammar the enter set of e.g. `expr_0` is `{digits_0, expr_1}`.

*   Once we transition to a rule call, we need to do one additional thing:
*   We find the enter set of the rule call.
*   For each call inside the enter call:
    *   Find the context for that call’s rule at the current position.
    *   Inside that context we insert a new origin consisting of the call and the _same_ context.
    *   Then we invoke the rule with that context.

An interesting thing is happening here: We’re inserting the context into itself. Let’s say we’re at the beginning of the string and are transitioning into the `expr_0` call. The steps above will then create a context for `(expr, 0)` and add an origin which contains `(expr_1, )`. This represents the left-recursiveness of the grammar: After we’ve parsed an `expr` at the beginning, we should continue with whatever comes after `expr_1` (in this case: `'+' expr_2`) and that should be parsed in the same context. If we’re then able to parse a plus-character and another expression, we should then once again continue with `expr_1` with the same context. We’re always in the same context ("an `expr` that’s parsed at position 0") and we’ll continue parsing it left recursive forever.

That fixed one problem, but it turns out there is another problem as well. We don’t properly handle rule calls that’s in the right position either (e.g. `expr_2` in `expr = expr_1 '+' expr_2`). The reason for this is because once a rule has been successfully parsed we transition away from the rule calls in the origin. However, there is nothing for `expr_2` to transtion into. To handle this case we’ll introduce a _tail call_, which is very similar to how a tail call optimization is done in funcitonal languages. The idea is that once we transition into a rule call which is in the right position (i.e. a part of the last set) we will _not_ do the business with pushing an origin and invoking the rule with a new context. Instead we can just invoke the rule with the _current_ context and that will correctly capture where we can return after the rule is complete.

And there we have it: A way to handle recursive rules (both left and right) in a world of regular expressions. There are some more things to take care of (e.g. handling marks), but those parts are not that substantial.

Here at Sanity we’re always striving towards finding the best possible solutions, and we’re not afraid of taking on complicated projects. This doesn’t mean we constantly reinvent the wheel, but every now and then you need to trust your instincts when you have a new brave idea. Of course, good ideas take time and effort to implement and requires quite a lot of patience.

Glush is by no means a finished project and it’s far from as usable as I want it to be. This is going to be an ongoing process, and over time we hope that Glush will help us make GROQ possible to use across many languages and platforms.

We also hope that the thought process behind Glush itself can be of use to a wider audience. This project builds on fascinating ideas from decades of research in the programming and computer science community. We’re extremely grateful for the willingness of people to share their ideas and this article itself is an attempt to take a part in this.

_If you found this article interesting and would like to work with a real-time document store, [do get in touch](mailto:jobs@sanity.io)._

\[1\] Bryan Ford. 2004. Parsing expression grammars: a recognition-based syntactic foundation. SIGPLAN Not. 39, 1 (January 2004), 111-122. DOI: [https://doi.org/10.1145/982962.964011](https://doi.org/10.1145/982962.964011)

\[2\] Lillian Lee. 2002. Fast context-free grammar parsing requires fast boolean matrix multiplication. J. ACM 49, 1 (January 2002), 1-15. DOI: [http://dx.doi.org/10.1145/505241.505242](http://dx.doi.org/10.1145/505241.505242)

\[3\] Brian A. Malloy, James F. Power, and John T. Waldron. 2002. Applying software engineering techniques to parser design: the development of a C# parser. In Proceedings of the 2002 annual research conference of the South African institute of computer scientists and information technologists on Enablement through technology (SAICSIT '02). South African Institute for Computer Scientists and Information Technologists, Republic of South Africa, 75-82.

\[4\] Sérgio Medeiros, Fabio Mascarenhas, and Roberto Ierusalimschy. 2014. Left recursion in Parsing Expression Grammars. Sci. Comput. Program. 96, P2 (December 2014), 177-190. DOI: [http://dx.doi.org/10.1016/j.scico.2014.01.013](http://dx.doi.org/10.1016/j.scico.2014.01.013)

\[5\] Masaru Tomita. 1985. Efficient Parsing for Natural Language: A Fast Algorithm for Practical Systems. Kluwer Academic Publishers, Norwell, MA, USA.

\[6\] Elizabeth Scott and Adrian Johnstone. 2006. Right nulled GLR parsers. ACM Trans. Program. Lang. Syst. 28, 4 (July 2006), 577-618. DOI: [http://dx.doi.org/10.1145/1146809.1146810](http://dx.doi.org/10.1145/1146809.1146810)

\[7\] Rahman Nozohoor-Farshi, GLR parsing for epsilon-grammars, in: Masaru Tomita (Ed.), Generalized LR Parsing, Kluwer Academic Publishers, Netherlands, 1991, pp. 60–75.

\[8\] Mark Johnson. "Memoization of top down parsing." arXiv preprint cmp-lg/9504016 (1995).

\[9\] Matthew Might, and David Darais. "Yacc is dead." arXiv preprint arXiv:1010.5023 (2010).

\[10\] Janusz A. Brzozowski. 1964. Derivatives of Regular Expressions. J. ACM 11, 4 (October 1964), 481-494. DOI: [http://dx.doi.org/10.1145/321239.321249](http://dx.doi.org/10.1145/321239.321249)

\[11\] Ian Henriksen, Gianfranco Bilardi, and Keshav Pingali. 2019. Derivative grammars: a symbolic approach to parsing with derivatives. Proc. ACM Program. Lang. 3, OOPSLA, Article 127 (October 2019), 28 pages. DOI: [https://doi.org/10.1145/3360553](https://doi.org/10.1145/3360553)

\[12\] Matthew Might, David Darais, and Daniel Spiewak. 2011. Parsing with derivatives: a functional pearl. SIGPLAN Not. 46, 9 (September 2011), 189-195. DOI: [https://doi.org/10.1145/2034574.2034801](https://doi.org/10.1145/2034574.2034801)

\[13\] Michael D. Adams, Celeste Hollenbeck, and Matthew Might. 2016. On the complexity and performance of parsing with derivatives. In Proceedings of the 37th ACM SIGPLAN Conference on Programming Language Design and Implementation (PLDI '16). ACM, New York, NY, USA, 224-236. DOI: [https://doi.org/10.1145/2908080.290812](https://doi.org/10.1145/2908080.290812)

\[14\] Jay Earley. 1970. An efficient context-free parsing algorithm. Commun. ACM 13, 2 (February 1970), 94-102. DOI: [http://dx.doi.org/10.1145/362007.362035](http://dx.doi.org/10.1145/362007.362035)

\[15\] Elizabeth Scott and Adrian Johnstone. 2010. GLL Parsing. Electron. Notes Theor. Comput. Sci. 253, 7 (September 2010), 177-189. DOI: [http://dx.doi.org/10.1016/j.entcs.2010.08.041](http://dx.doi.org/10.1016/j.entcs.2010.08.041)

\[16\] Terence Parr, Sam Harwell, and Kathleen Fisher. 2014. Adaptive LL(\*) parsing: the power of dynamic analysis. SIGPLAN Not. 49, 10 (October 2014), 579-598. DOI: [https://doi.org/10.1145/2714064.2660202](https://doi.org/10.1145/2714064.2660202)

\[17\] Joop M. I. M. Leo. 1991. A general context-free parsing algorithm running in linear time on every LR(k) grammar without using lookahead. Theor. Comput. Sci. 82, 1 (May 1991), 165-176. DOI: [http://dx.doi.org/10.1016/0304-3975(91)90180-A](http://dx.doi.org/10.1016/0304-3975(91)90180-A)

\[18\] Aycock, John, and R. Nigel Horspool. "Practical earley parsing." The Computer Journal 45, no. 6 (2002): 620-630.

\[19\] Adrian Johnstone, Elizabeth Scott, and Giorgios Economopoulos. 2006. Evaluating GLR parsing algorithms. Sci. Comput. Program. 61, 3 (August 2006), 228-244. DOI: [http://dx.doi.org/10.1016/j.scico.2006.04.004](http://dx.doi.org/10.1016/j.scico.2006.04.004)

\[20\] Sebastian Fischer, Frank Huch, and Thomas Wilke. 2010. A play on regular expressions: functional pearl. In Proceedings of the 15th ACM SIGPLAN international conference on Functional programming (ICFP '10). ACM, New York, NY, USA, 357-368. DOI: [https://doi.org/10.1145/1863543.1863594](https://doi.org/10.1145/1863543.1863594)  

  
  
from Hacker News https://ift.tt/2P6ErNN