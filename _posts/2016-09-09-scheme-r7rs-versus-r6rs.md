---
title: 'Scheme: R7RS versus R6RS'
date: 2020-01-12T01:17:00+01:00
draft: false
---

InPhase asked today on `#scheme` about the R7RS vs R6RS debate. I followed the original debate closely and have experience both using and implementing R6RS. I also recently added R7RS support in [Akku.scm](https://akkuscm.org/) 0.3.0, so I feel like I can weigh in on this. It’s a topic that many feel passionately about, and I’m also firmly on one side of the debate, but I will try to keep my own opinions and hyperbole out of it this time.

The number argument
===================

If you simply asked around, you might get the answer that R6RS is just so much bigger than R5RS/R7RS (and bigger is presumed to be not as good). It looks obvious on the surface, but defenders of R6RS see it is a canard. Here are the numbers, based on the [latest updated documents](https://weinholt.se/scheme/r6rs/).

*   AI Memo № 349: 43 pages.
*   RRS: 35 pages.
*   R2RS: 76 pages.
*   R3RS: 43 pages.
*   R4RS: 55 pages.
*   R5RS: 50 pages.
*   R6RS: 91 + 72 = 163 pages (not counting the non-normative appendices and the rationale, which I think is fair).
*   R7RS: 88 pages (similarly not counting the overview).

By these numbers we see that R6RS is 185% the size of R7RS and 326% the size of R5RS. The argument looks true, at least on the surface. These numbers hide the fact that R6RS contains 15 pages of formal semantics.

Is it fair to count these pages as a point against R6RS? The formal semantics are a good reference for implementers who are unsure about some corner of the language and can be used to validate an implementation’s semantics. Here are the recent numbers again, excluding formal semantics, appendices, bibliographies and indices:

*   R5RS: 40 pages (excluding section 7.2 and forwards).
*   R6RS: 60 + 65 = 125 pages (excluding Appendix A and forwards).
*   R7RS: 65 pages (excluding section 7.2 and forwards).

The 65 pages from the R6RS standard libraries are the only remaining part of the number argument that still holds.

**R7RS side**: The R6RS is too big. **R6RS side**: It’s smaller than it appears.

The condition system
====================

R6RS specifies a condition system with 14 standard condition types for code that raises exceptions. R5RS does not provide any standard way to handle or distinguish exceptions and not even a way to raise exceptions. R7RS borrows `guard`, `raise` and `raise-continuable` from R6RS but does not specify a complete condition system.

Instead of a condition system, R7RS has `error-object-message`, `error-object-irritants`, `error-object?`, `read-error?` and `file-error?`. These are not necessarily meant to work with a new distinct type, but may simply work with e.g. symbols and vectors. This gives the implementer the freedom to reuse whatever condition objects were used before they implemented R7RS support.

The condition system in R6RS comes from the pain of trying to write any kind of error handling at all in R5RS. It was not possible to, let’s say, write portable code that reliably writes to the file system and correctly handles I/O errors. In contrast, if an R6RS program tries to open a file it does not have access to then it will get an exception with an `&i/o-file-protection` condition as well as a few other conditions that together give a complete picture of the condition. In Chez Scheme (which also adds the extra `&format`):

```
(guard (exn ((i/o-file-protection-error? exn) (simple-conditions exn))) (open-file-output-port "/dev/foo")) ;; => (# # ;; # # ;; # #) 
```

User code has the same access to these conditions as the implementer and can be construct, inspect and pretty print them.

However, this means that anyone implementing R6RS should go through all their code and update it to raise the correct conditions.

**R7RS side**: The condition system is too big and burdensome. **R6RS side**: It lets us write portable code that catches exceptions.

Undefined behavior controversy
==============================

This is a big philosophical difference between the reports. I’ll let the documents themselves tell the story.

> As defined by this document, the Scheme programming language is safe in the following sense: The execution of a safe top-level program cannot go so badly wrong as to crash or to continue to execute while behaving in ways that are inconsistent with the semantics described in this document, unless an exception is raised.
> 
> — Revised6 Report on the Algorithmic Language Scheme

That’s for R6RS, although it does later leave room for implementations to add unsafe features. But it’s clear that a program that doesn’t import such extra libraries is safe. It will not have a buffer overflow waiting for an attacker to use it.

> When speaking of an error situation, this report uses the phrase “an error is signaled” to indicate that implementations must detect and report the error. \[…\]
> 
> **If such wording does not appear** in the discussion of an error, then implementations are not required to detect or report the error, though they are encouraged to do so. Such a situation is sometimes, but not always, referred to with the phrase “an error.” In such a situation, an implementation **may or may not signal an error**; \[…\]
> 
> For example, it is an error for a procedure to be passed an argument of a type that the procedure is not explicitly specified to handle, even though such domain errors are seldom mentioned in this report. Implementations may signal an error, extend a procedure’s domain of definition to include such arguments, or **fail catastrophically**.
> 
> — Revised7 Report on the Algorithmic Language Scheme

“Fail catastrophically” is presumably not too far away from the nasal demons of C compilers. The report does not say what will happen if a program does `(string-ref "" -1)` or `(car 0)`.

Implementation restrictions provide even more ways that things can go wrong:

> This report uses the phrase “may report a violation of an implementation restriction” to indicate circumstances under which an implementation is permitted to report that it is unable to continue execution of a correct program because of some restriction imposed by the implementation. Implementation restrictions are discouraged, but **implementations are encouraged to report violations of implementation restrictions**.
> 
> For example, an implementation may report a violation of an implementation restriction if it **does not have enough storage to run a program**, or if **an arithmetic operation would produce an exact number that is too large** for the implementation to represent.
> 
> — Revised7 Report on the Algorithmic Language Scheme

So an implementation is also within its rights to _not_ detect out of memory errors or integer overflow. R6RS does not work that way:

> Implementations must raise an exception when they are unable to continue correct execution of a correct program due to some implementation restriction. For example, an implementation that does not support infinities must raise an exception with condition type `&implementation-restriction` when it evaluates an expression whose result would be an infinity.
> 
> — Revised6 Report on the Algorithmic Language Scheme

**R7RS side**: Safety is not a desirable language feature. **R6RS side**: Safety is an essential language feature.

Optional is better argument
===========================

R7RS requires that implementations support 7-bit ASCII (except for NUL in strings). This is different from R5RS, which is character set agnostic. And it’s different again from R6RS which requires full Unicode support.

Unicode is one of several optional features in R7RS. Appendix B gives a list of feature identifiers that may be missing in any given implementation:

*   `exact-closed` - The algebraic operations `+`, `-`, `*`, and `expt` where the second argument is a non-negative integer produce exact values given exact inputs.
*   `exact-complex` - Exact complex numbers are provided.
*   `ieee-float` - Inexact numbers are IEEE 754 binary floating point values.
*   `full-unicode` - All Unicode characters present in Unicode version 6.0 are supported as Scheme characters.

*   `ratios` - `/` with exact arguments produces an exact result when the divisor is nonzero.

A benefit of these features being optional is that R7RS is easier to implement in certain environments. We can see that R7RS strings can be implemented as C strings, which also do not support NUL characters. An R7RS Scheme targeting ECMAScript can let `(+ 1 1)` evaluate to `2.0` and `(/ 1 2)` to `0.5`. An R7RS targeting an AVR microcontroller can exclude Unicode support. This will lead to more R7RS implementations, which is good.

Now the other side of the argument. Implementations which don’t implement these features will likely list them as restrictions in their documentation. Nothing stops an implementer from similarly claiming compliance with R6RS and listing some restrictions. Some targets will require certain restrictions, such as due to memory limits on microcontrollers. But if these features are taken as optional in the language itself then we can’t write portable code that uses these features. The burden is on the user to provide a full Unicode library if our software requires the use of Unicode.

**R7RS side**: It is too burdensome and/or restrictive to require all these features. **R6RS side**: It is too burdensome and/or difficult to write portable code without these features.

syntax-case
===========

The choice of macro system is a very contended issue. The result of this particular controversy was that R7RS just kept `syntax-rules` from R5RS. In R6RS there is both `syntax-rules` and the more powerful `syntax-case`, in which `syntax-rules` can be written in just a few lines.

I don’t think I can properly make justice to the arguments for and against `syntax-case` in this article. There are other popular macro systems with the same expressiveness, and perhaps the popularity of some of those is the largest reason why R7RS didn’t choose `syntax-case`.

In R5RS and R7RS it is not possible to [write macros that violate syntactic hygiene](http://okmij.org/ftp/Scheme/Dirty-Macros.pdf). The macro system is based on rewriting rules, which happen to easily be Turing complete, but which do not have access to the Scheme language itself. They can therefore also not deconstruct strings or create new identifiers. That’s why `define-record-type` in R7RS (and SRFI 9) requires the user to write out all procedure names for all fields. This is also a simple motivation for wanting a more powerful macro system.

A macro expander like `syntax-rules` is a very tricky piece of code and `syntax-case` is even tricker. Those interested can check out [Oscar Waddell’s PhD thesis](https://web.archive.org/web/20010615153947/https://www.cs.indiana.edu/~owaddell/papers/thesis.ps.gz). Requiring a tricky macro system is obviously a burden for the implementer and perhaps another reason why R7RS did not add `syntax-case`.

From the side of R6RS, adding `syntax-case` made sense. It is a great feature to have as a user of the language. We can run any Scheme code at expansion time and easily write macros that insert new identifiers, even while preserving hygiene.

Bottom line
===========

I’ve not written about all controversies. The record system of R6RS has also received criticism. But I have shown a number of essential differences between R7RS and R6RS. I think that this is a fair summary:

**R6RS is more demanding on implementers but easier on users. Conversely, R7RS is easier on implementers but more demanding on users.**

Finally, a caveat for this whole article is that it applies to R7RS\-small vs R6RS. Much might change with R7RS-large.

  
  
from Hacker News https://ift.tt/2R74Vj9