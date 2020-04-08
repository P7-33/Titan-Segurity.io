---
title: 'Parsing C++ is literally undecidable (2013)'
date: 2019-10-04T06:05:00+01:00
draft: false
---

Many programmers are aware that C++ templates are Turing-complete, and this was proved in the 2003 paper [C++ Templates are Turing Complete](http://port70.net/~nsz/c/c%2B%2B/turing.pdf).

However, there is an even stronger result that many people are not aware of. The C++ FQA has [a section showing that parsing C++ is undecidable](http://yosefk.com/c++fqa/web-vs-c++.html), but many people have misinterpreted the full implications of this (understandable, since the FQA is discussing several issues over the course of its questions and does not make explicit the undecidability proof).

Some people misinterpret this statement to simply mean that _fully compiling_ a C++ program is undecidable, or that _showing the program valid_ is undecidable. This line of thinking presumes that _constructing a parse tree_ is decidable, but only further stages of the compiler such as template instantiation are undecidable.

For example, see this (incorrect, but top-voted) Stack Overflow [answer](http://stackoverflow.com/a/794116/77070) to the question [What do people mean when they say C++ has “undecidable grammar”?](http://stackoverflow.com/questions/794015/what-do-people-mean-when-they-say-c-has-undecidable-grammar) This answer errs when it says: “Note this has nothing to do with the ambiguity of the C++ grammar.”

In fact, _simply producing a parse tree_ for a C++ program is undecidable, because producing a parse tree can require arbitrary template instantiation. I will demonstrate this with a short program, which is a simplification/adaptation of what is in the FQA link above.

```
struct SomeType {}; template <...> struct TuringMachine { // Insert implementation of a Turing machine here, which we know  // is possible from previous proofs. }; template <typename T> struct S { static int name; }; template<> struct S<SomeType> { typedef int name; }; int x; int main() { S<TuringMachine<...>::output>::name * x; }
```

The parse tree for this program depends on whether `TuringMachine::output` is `SomeType` or not. If it is `SomeType` then `::name` is an integer and the parse tree for the program is multiplying two integers and throwing away the result. If it is _not_ `SomeType`, then `::name` is a typedef for `int` and the parse tree is declaring a pointer-to-int named `x`. These two are completely different parse trees, and the difference between them cannot be delayed to further stages of the compiler.

The parse tree _itself_ depends on arbitrary template instantiation, and is therefore the parsing step is undecidable.

In practice, compilers limit template instantiation depth, so this is more of a theoretical problem than a practical one. But it is still a deep and significant result if you are ever planning on writing a C++ parser.

  
  
from Hacker News https://ift.tt/192kfR1