---
title: 'A tiny Python exception oddity'
date: 2019-12-17T01:41:00+01:00
draft: false
---

![](https://1.bp.blogspot.com/-qnDvCh03Vx8/XfWGx3OO-xI/AAAAAAAAFFQ/l5K_dR0hC9cRQycaYtYO8dmppmwH1jq2ACLcBGAsYHQ/w1200-h630-p-k-no-nu/cpython3.7.png "Only Python: A Tiny Python Exception Oddity")  

Today, while working on Friendly-traceback (

[improved documentation](https://aroberge.github.io/friendly-traceback-docs/docs/html/)

!) as I have been doing a lot recently, I came into an odd SyntaxError case:

*   The inconsistent behaviour is so tiny, that I doubt most people would notice - including myself before working on Friendly-traceback.
*   This is SyntaxError that is **not** picked up by flake8; however, pylint does pick it up.
*   By Python, I mean CPython.  After trying to figure out why this case was different, I downloaded Pypy and saw that Pypy did not show the odd behaviour.
*   To understand the origin of this different behaviour, one needs to look at some obscure inner parts of the CPython interpreter.
*   **This would likely going to be found totally irrelevant by 99.999% of Python programmers.** If you are not the type of person who is annoyed by tiny oddities, you probably do not want to read any further.

You have been warned.

  

Normal behaviour
----------------

  

When Python finds a SyntaxError, it flags its location.  Let's have a look at a simple case, using CPython 3.7.

  

Notice how it indicates where it found the error, as shown by the red arrow: this happened when it reached a token that was inconsistent with the code entered so far. According to my experience until today, this seemed to be always the case.  Note that using CPython 3.6 yields exactly the same behaviour, and unhelpful error message.

  

Before discussing the case with a different behaviour, let's make a detour and look at Pypy's handling of the same case.

  

Same location indicated, but a much more helpful error message, even though this is version 3.6.  This improved error message was discussed in this

[Pypy blog post](https://morepypy.blogspot.com/2018/04/improving-syntaxerror-in-pypy.html)

.  I strongly suspect that this is what lead to this improved error message in CPython 3.8.

  

Same error message as Pypy ... but the exact location of the error, previously indicated by ^, no longer appears - which could be unfortunate when nested parenthesis (including square and curly brackets) are present.

  

What about Friendly-traceback you ask? I thought you never would! ;-)  

  

Well, here's the information when using CPython 3.7.

  

  

The line about not having enough information from Python refers to the unhelpful message ("invalid syntax"). Hopefully you will agree that the information given by Friendly-traceback would be generally more useful, and especially more so for beginners.   

  

But enough about this case. It is time to look at the odd behaviour one.

  

Odd case
--------

  

Consider the following:

  

Having a variable declared both as a global and nonlocal variable is not allowed.  Let see what happens when this is executed by Pypy.

  

  

So, pypy processed the file passed the nonlocal statement and flagged the location where it encountered a statement which was inconsistent with everything that had been read so far: it thus flagged that as the location of the error.

  

Now, what happens with CPython:

  

  

The location flagged is one line earlier. The nonlocal statement is flagged as problematic but, reading the code up to that point, there is no indication that a global statement was encountered before.

  

Note that, changing the order of the two statements does not change the result: pypy shows the beginning of the second statement (line 6) as the problem, whereas CPython always shows the line before.

Why does it matter to me?
-------------------------

If you go back to the first case I discussed, with the unmatched parenthesis, in Friendly-traceback, I rely on the location of the error shown by Python to indicate where the problem arose and, when appropriate, I look \*back\* to also show where the potential problem started.  Unfortunately, I cannot do that in this case with CPython.

  

Why is this case handled differently by CPython?
------------------------------------------------

While I have some general idea of how the CPython interpreter works, I absolutely do not understand well enough to claim with absolute certainty how this situation arise.  Please, feel free to leave a comment to correct the description below if it is incorrect.

  

 My understanding is the following:

  

After breaking down a file into tokens, parsing it according to the rules of the Python grammar, an abstract syntax tree (AST) is constructed if no syntax error is found.  The nonlocal/global problem noted is not picked up by CPython up to that point - which also explains why flake8 would not find it as it relies on the AST, and does not actually executes the code.  (I'm a bit curious as to how Pylint does ... I'll probably have to look into it when I have more time).

  

Using the AST, a control flow graph is created and various "frames" are created with links (GOTOs, under a different name...) joining different parts.  It is at that point that relationships between variables in different frames is examined in details.  Pictorially, this can be represented as follows:

  

  

(This image was taken from

[this blog post by Eli Bendersky](https://eli.thegreenplace.net/2010/09/20/python-internals-symbol-tables-part-2)

)  In terms of the actual code, it is in the

[CPython symtable.c file](https://github.com/python/cpython/blob/master/Python/symtable.c)

. At that point, errors are not found by scanning lines of code linearly, but rather by visiting nodes in the AST in some deterministic fashion ... which leads to the oddity mentioned previously: CPython consistently shows the first of two statements as the source of the problem, whereas Pypy (which relies on some other method) shows the second, which is consistent with the way it shows the location of all SyntaxError messages.

  

Conclusion
----------

For Friendly-traceback, this likely means that for such cases, and unlike the mismatched parenthesis case, I will not attempt to figure out which two lines are problematic, and will simply expand slightly on the terse one liner given by Python (and in a way that can be translated into languages other than English).

  

  
  
from Hacker News https://ift.tt/2RTiRiX