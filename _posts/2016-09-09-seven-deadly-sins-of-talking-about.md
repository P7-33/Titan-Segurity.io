---
title: 'Seven deadly sins of talking about “types” (2014)'
date: 2019-12-14T07:03:00+01:00
draft: false
---

Rambles around computer science
===============================

Diverting trains of thought, wasting precious time

Tue, 07 Oct 2014
----------------

### Seven deadly sins of talking about “types”

\[Update: this article has been [translated into Japanese](http://postd.cc/7-deadly-sins-of-talking-about-types/)!\]

My essay [“In Search of Types”](https://www.cs.kent.ac.uk/people/staff/srk21/#onward14) attempts to be a dispassionate review of some of the different concepts, purposes and attitudes surrounding the word “type” in programming. I imagine that my passions are still rather thinly veiled in places. But in this post I'm going to come out with a more unabashedly ranty take. Certain statements and attitudes really get up my nose. I was recently exposed to a few of these at Strange Loop (a great conference, I should add). So I've written down a list of “deadly sins” committed by many people (mis-)speaking about “types”

I should add that the theme here is rhetoric. What gets up my nose is when people don't make honest, transparent arguments. Their conclusions needn't be wrong. I program in OCaml a reasonable amount, and it's plain that I get a lot of value from the type checker. But advocates of type systems often try to sell them as a miracle cure, without acknowledging their limitations and undesirable side effects. Can we please move the debate past propaganda and blanket statements?

A contributing factor is that we often struggle to disentangle the many distinct concepts that lurk under the word “type”. My essay tackles this entanglement more directly, although hopefully the following rants will make some useful distinctions.

#### Not distinguishing abstraction from checking

This is my number-one beef. Almost all languages offer data abstraction. Some languages proceed to build a static checking system on top of this. But please, please, don't confuse the two.

We see this equivocation used time and time again to make an entirely specious justification of one language or other. We see it used to talk up the benefits of type systems by hijacking the benefits of data abstraction, as if they were the same thing.

The discussion of “stringly-typed programming” (_sic_) at Strange Loop, both in the [Snively/Laucher](http://www.youtube.com/watch?v=SWTWkYbcWU0) talk and in Chris Morgan's [Rust-flavoured](http://www.youtube.com/watch?v=jVoFws7rp88) talk, was doing exactly this. Yes, it's true that HTTP headers (to borrow Morgan's example) can and should (usually) be abstracted beyond plain strings. But failing to do so is not an omission of compile-time type checking. It's an omission of data abstraction. Time and time again, we see people advancing the bogus argument that if you make the latter omission, you must have made the former. This is simply wrong. Type checkers are one way to gain assurance about software in advance of running it. Wonderful as they can be, they're not the only one. Please don't confuse the means with the ends.

#### Pretending that syntactic overhead is the issue

The Sniveley/Laucher talk included a comment that people like dynamic languages because their syntax is terse. This might be true. But it made me uncomfortable, because it seems to be insinuating a different statement: that people dislike type systems only because of the syntactic overhead of annotations. This is false! Type systems don't just make you write annotations; they force you to structure your code around type-checkability. This is inevitable, since type checking is _by definition_ a specific kind of _syntactic_ reasoning.

To suggest that any distaste for types comes from annotation overhead is a way of dismissing it as a superficial issue. But it's not superficial. It's about the deep consequences type checking has on how code must be structured. It's also (perhaps ironically) about _polymorphism_. In a typed language, only polymorphism which can be proved correct is admissible. In an untyped language, arbitrarily complex polymorphism is expressible. Rich Hickey's [transducers talk](http://www.youtube.com/watch?v=6mTbuzafcII) gave a nice example of how patterns of polymorphism which humans find comprehensible can easily become extremely hard to capture precisely in a logic. Usually they are captured only overapproximately, which, in turn, yields an inexpressive proof system. The end result is that some manifestly correct code does not type-check.

#### Patronising those outside the faith

If somebody stays away from typed languages, it doesn't mean they're stupid, or lack education, or are afraid of maths. There are entirely valid practical reasons for staying away. Please drop the condescending tone.

#### Presenting type-level programming as a good thing

No sane person can argue that we _want_ to bifurcate a programming language into distinct base-level and type-level fragments. Gilad Bracha [calls](http://gbracha.blogspot.co.uk/2014/09/a-domain-of-shadows.html) this the “shadow worlds” problem: to abstract over constructs at level 0, we need a whole new set of level-1 constructs, and so on. This is an antipattern. It's a failure of compositionality. That doesn't mean it can't be justified for pragmatic reasons. ML's module system is the way it is because nobody has figured out the maths to do it any better under the various design constraints of the system (which of course include a proof of soundness). But please, stop pretending that type-level programming is a desirable thing. It's a kludge, and hopefully a temporary one. Personally, I want to write all my specifications in more-or-less the same language I use to write ordinary code. It's the tool's job to prove correctness or, if it must, tell me that it failed. (It should also do so using a straightforward explanation, ideally featuring a counterexample or stripped-down unprovable proposition. I don't know any type checker that does this, currently.)

#### Fetishising Curry-Howard

Curry-Howard is an interesting mathematical equivalence, but it does not advance any argument about how to write software effectively.

#### Equivocating around “type-safety”

Here is a phrase which is used to mean many different things. Old-fashioned “type safety” is what I call “Saraswat-style”, after the famous [“Java is not type-safe”](http://www.cis.upenn.edu/~bcpierce/courses/629/papers/Saraswat-javabug.html) memo. (Of course, it wasn't invented by Saraswat—it was the “standard” meaning of the phrase at the time.) It's a valuable property. But it's actually about memory, not data types: it's definable in terms of a language featuring only a “word” data type (using only minor tweaks of wording from Saraswat's). It's also nothing to do with static checking—“type safety” holds in all “dynamically typed” languages. The reason it's such a useful property is that it can be implemented without sacrificing a lot, unless you want to program close to the machine. Although many implementations happen to use syntactic compile-time reasoning, a.k.a. type checking, to lessen the run-time checking overheads, this is an implementation detail.

Saraswat-style type safety is usually a very good thing. But it's a far cry from proving near-arbitrary correctness properties of code. It's popular to confuse the issue, by saying that if you don't use type systems you don't have “type safety”. This wilful mixing of separate ideas is cashing in on the relatively uncontroversial good value of Saraswat-style safety, and using it to paint “type systems” as a similar no-brainer. Proof has a cost, and the appropriate expenditure depends on the task. It's far from a no-brainer.

#### Omitting the inconvenient truths

If everyone would just use a modern language with a fancy type system, all our correctness problems would be over, right? If you believe this, you've drunk far too much Kool-Aid. Yet, apparently our profession is full of willing cult members. Let me say it simply. Type systems _cannot_ be a one-stop solution for specification and verification. They are limited by definition. They reason only syntactically, and they specify only at the granularity of expressions. They're still useful, but let's be realistic.

Try checking realistic reachability or liveness properties with a type checker, and you will not succeed. In a formal sense, this can be done, and [has been](http://dl.acm.org/citation.cfm?id=1387678), but the resulting system has little in common with type checking as practitioners would recognise it. The authors note that the ostensibly type-style specifications it yields are “bulky” and often “not suitable for human reasoning”. This is hardly surprising, since they are working against the grain of the program's existing syntactic decomposition. To specify and check liveness or reachability, we need to represent programs as some kind of flow graph, where flows are very likely to span multiple functions and multiple modules. It's not an expressionwise view of code, and it's also not the syntax in which most people want to code.

We need to grow up and accept this. Once we've accepted it, what do we do differently? We need a model that lets us assimilate gradual improvements in automatic reasoning, like better SMT solvers, without requiring us to re-type (pun intentional) our code. We need to be able to step up the strength of our specifications without switching language all the time. We need to integrate typed and untyped code, and between distinct languages too.

These ideas are slowly gaining some traction, such as in gradual typing, but have a long way to go. In particular, accommodating multiple languages has some far-reaching consequences for our infrastructure. So far, we implement languages in a particular way: relying on a single in-compiler type checker to establish whole-program invariants. If we embrace multiple languages, we can't build things this way any more. Instead, it's necessary to tackle invariant enforcement not within a per-language compile-time service but within a more generic composition-time service. (Hint: it's called a linker. In short, the linker-like service must do a mix of proof and instrumentation, in a language-neutral way, guided by descriptive information output by the compiler. If you've seen me talk recently, this will probably sound familiar. Ask me for more!)

Coding without proving everything we'd like to prove is an activity which will continue. Meanwhile, late binding, and hence limited applicability of truly ahead-of-time reasoning, is often a requirement, not an implementation decision. Eliminating these can bring benefits, but also can eliminate value. Weighing up costs and benefits, in a way that optimises overall value for a given product, is the right way to think about all these issues. It's a long way from the dogma, rhetoric and blind faith that currently dominate our discourse.

#### Coda

Now that I've ranted my heart out, here's a coda that attempts to be constructive. As I mentioned, part of the problem is that we equivocate when talking about “types”. Instead of saying “type” or “type system”, I encourage anyone to check whether anything from the following alternative vocabulary will communicate the intended meaning. Deciding which term is appropriate is a good mental exercise for figuring out what meaning is actually intended.

*   data abstraction
*   data type
*   predicate, proposition
*   proof, proof system
*   interface specification \[language\]
*   \[compile-time\] checker
*   specification, verification
*   invariant (the thing that “types” are usually specifying!)

If you can think of others, do let me know!

_\[[/research](https://www.cs.kent.ac.uk/people/staff/srk21/blog/research)\] [permanent link](https://www.cs.kent.ac.uk/people/staff/srk21/blog/2014/10/07#seven-type-sins) [contact](https://www.cs.kent.ac.uk/people/staff/srk21/#contact)_

* * *

[![Powered by blosxom](http://blosxom.sourceforge.net/images/pb_blosxom.gif)](http://blosxom.sourceforge.net/)

[validate this page](http://validator.w3.org/check?uri=referer)

  
  
from Hacker News https://ift.tt/1pMjJNY