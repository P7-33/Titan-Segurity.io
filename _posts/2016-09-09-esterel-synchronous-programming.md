---
title: 'Esterel – Synchronous programming language for complex, reactive systems'
date: 2019-12-28T07:07:00+01:00
draft: false
---

This article is about the programming language. For the mountain range in France, see

[Esterel massif](https://en.wikipedia.org/wiki/Esterel_massif "Esterel massif")

. For the ship, see

[MV Esterel](https://en.wikipedia.org/wiki/MV_Esterel "MV Esterel")

.

**Esterel** is a [synchronous](https://en.wikipedia.org/wiki/Synchronous_programming_language "Synchronous programming language") [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") for the development of complex reactive systems. The [imperative programming](https://en.wikipedia.org/wiki/Imperative_programming "Imperative programming") style of **Esterel** allows the simple expression of [parallelism](https://en.wikipedia.org/wiki/Parallel_computing "Parallel computing") and [preemption](https://en.wikipedia.org/wiki/Preemption_(computing) "Preemption (computing)"). As a consequence, it is well suited for control-dominated model designs.

The development of the language started in the early 1980s, and was mainly carried out by a team of [Ecole des Mines de Paris](https://en.wikipedia.org/wiki/Ecole_des_Mines_de_Paris "Ecole des Mines de Paris") and [INRIA](https://en.wikipedia.org/wiki/INRIA "INRIA") led by [Gérard Berry](https://en.wikipedia.org/wiki/G%C3%A9rard_Berry "Gérard Berry") in France. Current compilers take Esterel programs and generate [C code](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") or hardware (RTL) implementations ([VHDL](https://en.wikipedia.org/wiki/VHDL "VHDL") or [Verilog](https://en.wikipedia.org/wiki/Verilog "Verilog")).

The language is still under development, with several compilers out. The commercial version of **Esterel** is the development environment [Esterel Studio](https://en.wikipedia.org/w/index.php?title=Esterel_Studio&action=edit&redlink=1 "Esterel Studio (page does not exist)"). The company that commercialize it ([Synfora](https://web.archive.org/web/20100615104531/http://www.synfora.com/products/esterelStudio.html)) initiated a normalization process with the [IEEE](https://en.wikipedia.org/wiki/IEEE "IEEE") in April 2007 however the working group (P1778) dissolved March 2011. The [Esterel v7 Reference Manual Version v7 30 – initial IEEE standardization proposal](https://web.archive.org/web/20051230055419/http://www.esterel-technologies.com/files/Esterel-Language-v7-Ref-Man.pdf) is publicly available.

The Multiform Notion of Time
----------------------------

The notion of time used in Esterel differs from that of non-synchronous languages in the following way: The notion of physical time is replaced with the notion of order. Only the simultaneity and precedence of events are considered. This means that the physical time does not play any special role. This is called multiform notion of time. An Esterel program describes a totally ordered sequence of logical instants. At each instant, an arbitrary number of events occur (including 0). Event occurrences that happen at the same logical instant are considered simultaneous. Other events are ordered as their instances of occurrences. There are two types of statements: Those that take zero time (execute and terminate in the same instant) and those that delay for a prescribed number of cycles.

Signals
-------

Signals are the only means of communication. There are valued and non-valued signals. They are further categorized as being input, output, or local signals. A signal has the property of being either present or absent in an instant. Valued signals also contain a value. Signals are broadcast across the program, and that means any process can read or write a signal. The value of a valued signal can be determined in any instant, even if the signal is absent. The default status of a signal is absent. Signals remain absent until they are explicitly set to present using the emit statement. Communication is instantaneous, that means that a signal emitted in a cycle is visible immediately. Note that one can communicate back and forth in the same cycle.

### Signal Coherence rules

*   Each signal is only present or absent in a cycle, never both.
*   All writers run before any readers do.

Thus

```
present A else emit A end 
```

is an [erroneous program](https://en.wikipedia.org/wiki/Erroneous_program "Erroneous program"): the writer "emit A" must run before the reader "present A", but the semantics of the language requires the "present A" to be performed first, resulting in a conflict in the program's semantics.\[_[clarification needed](https://en.wikipedia.org/wiki/Wikipedia:Please_clarify "Wikipedia:Please clarify")_\]

The language constructs
-----------------------

### Primitive Esterel statements

Pure Esterel has eleven primitive statements.[\[1\]](https://en.wikipedia.org/wiki/Esterel#cite_note-1)

`nothing`

Terminates immediately with no other effect.

`pause`

Blocks control flow in the current cycle for resumption in the next cycle.

_p_ `;` _q_

Runs _p_ until it terminates and then, in the same reaction, start _q_.

_p_ `||` _q_

Runs _p_ and _q_ in parallel

`loop` _p_ `end`

Restart the body _p_ as soon as it terminates. Every path through the loop body must contain at least one `pause` statement to avoid unbounded looping within a single reaction.

`signal` _S_ `in` _p_ `end`

Declares a local signal.

`emit` _S_

Make signal _S_ present in the current instant. A signal is absent unless it is emitted.

`present` _S_ `then` _p_ `else` _q_ `end`

If signal _S_ is present in the current instant, immediately run _p_, otherwise run _q_.

`suspend` _p_ `when` _S_

Suspends the execution of the body in instants where _S_ is present.

`trap` _T_ `in` _p_ `end`

Declare a labeled escape block.

`exit` _T_

Jump to the end of the innermost _T_\-labeled escape block.

### Derived Esterel statements

Esterel has several derived constructions:[\[2\]](https://en.wikipedia.org/wiki/Esterel#cite_note-2)[\[3\]](https://en.wikipedia.org/wiki/Esterel#cite_note-3)

Derived statement

Expansion

`halt`

`loop pause end`

`sustain` _s_

`loop emit` _s_`; pause end`

`present` _s_ `then` _p_ `end`

`present` _s_ `then` _p_ `else nothing` `end`

`await` _s_

`trap T in loop pause; present` _s_ `then exit T end end loop end`

`await immediate` _s_

`trap T in loop present` _s_ `then exit T end; pause end loop end`

`suspend` _p_ `when immediate` _s_

`suspend present` _s_ `then pause end;` _p_ `when` _s_

`abort` _p_ `when (immediate)` _s_

`trap T in suspend` _p_ `when (immediate)` _s_`; exit T || await (immediate)` _s_`; exit T; end`

`weak abort` _p_ `when (immediate)` _s_

`trap T in` _p_`; exit T || await (immediate)` _s_`; exit T; end`

`loop` _p_ each _s_

`loop abort` _p_ `; halt when` _s_ `end loop`

`every (immediate)` _s_ `do` _p_ `end every`

`await (immediate)` _s_`; loop` _p_ `each` _s_

### Other Esterel statements

The full Esterel language also has statements for declaring and instantiating modules, for variables, for calling external procedures, and for valued signals.

### Example (ABRO)

The following program emits the output O as soon as both inputs A and B have been received. Reset the behaviour whenever the input R is received.

```
module ABRO: input A, B, R; output O; loop \[ await A || await B \]; emit O each R end module 
```

Advantages of Esterel
---------------------

*   Model of time gives programmer precise control
*   Concurrency convenient for specifying control systems
*   Completely deterministic
*   Finite-state language
    *   Execution time predictable
    *   Much easier to verify formally
*   Can be implemented in hardware as well as in software

Disadvantages of Esterel
------------------------

*   Finite-state nature of the language limits flexibility (but expressivity is sufficient for the chosen application field)
*   Semantic challenges
    *   Avoiding causality violations is often difficult
    *   Difficult to compile in the general case, but simple correctness criteria exist

See also
--------

References
----------

External links
--------------

<img src="https://en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type=1x1" alt="" title="" />

  
  
from Hacker News https://ift.tt/2rWDmyW