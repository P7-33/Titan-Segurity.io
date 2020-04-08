---
title: 'Nim''s author on v1 launch: Personal words about version 1'
date: 2019-09-26T02:17:00+01:00
draft: false
---

Personal words about version 1
==============================

After all these years, we finally did it! The long expected version 1 is here.

When I started Nim's development I had a small simple language in mind that compiles to C; its implementation should not be more than 20,000 lines of code. The core guideline has always been that Nim should be a small language with a macro system, which should be capable of extending Nim with all the features that the small core is missing.

The current compiler plus the parts of the standard library it uses has roughly 140,000 lines of code, runs on a plethora of operating systems and CPU architectures, can also compile Nim code to C++ and JavaScript, and Nim's meta programming capabilities are top of the class. While the language is not nearly as small as I would like it to be, it turned out that meta programming cannot replace all the building blocks that a modern language needs to have.

For example, while Nim manages to implement async via its macro system, the macro system needs to be able to compile code into a state machine. And these state machines need some form of goto and a way to capture their environment. So Nim's core needed to grow so called "closure iterators" to enable this.

Furthermore, we don't really know yet how to leverage a macro system in order to give us extensibility on the type system level, so Nim's core needed generics and constraints for generics.

About the development process
-----------------------------

Having said that, I am pleased with the language's progress, and version 1 means that we now have a different development process: Previously Nim was driven way too much by the "Principle of Least Surprise" where everybody could claim "er, I think this should work..." and the implementation would follow along and grow some special cases. Special cases then might backfire and eventually make the system _harder_ to understand and eventually _create_ new surprises. Starting with version 1 we follow the "spec first" development: First we write an RFC, then we discuss it, then write the spec, then we implement it, then the insights gained from the implementation flow back into the spec.

Yes, I know the spec/manual has some omissions and bugs but it's improving and the new "destructors" language feature was developed with the "spec first" approach and I can tell you that development, even with a flawed spec, works much better and produces a higher quality outcome.

Nim's Future
------------

We want to focus on Nim's tooling, including Nimsuggest (Nim's code completion engine for diverse editors), Nimble (Nim's package manager) and Nimpretty (Nim's source code formatting tool). Personally I regard "incremental recompilation" (IC) the next big milestone for the Nim compiler. IC will further speed up Nim's already fast compile-times and cache the results of macro expansions and other constructs.

About concepts and owned: People told me these two features are essential for shipping with version 1 because they change how Nim code should be written in practice. Actually I disagree, the language works well without concept and the existing concepts are also usable, albeit their syntax and semantics leave a lot to be desired. And it's unclear if we will end up with owned in the language, I also have other ideas how to improve Nim's memory management story.

But this is all a bit besides the point. The point of version 1 was to finally ship what we have, not what we wish we had. The future is bright, version 1 is the beginning. It's like a marriage, it doesn't stop with the wedding.

  
  
from Hacker News https://ift.tt/2m85i1b