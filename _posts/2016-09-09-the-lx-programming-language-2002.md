---
title: 'The Lx Programming Language (2002)'
date: 2019-11-02T01:33:00+01:00
draft: false
---

![](https://avatars1.githubusercontent.com/u/1695924?s=400&v=4 "GitHub - c3d/xl: A super-flexible language based entirely on tree rewrites")  

[](https://github.com/c3d/xl#xl---an-extensible-language)XL - An extensible language
====================================================================================

> **WARNING**: XL is a work in progress. Even if there are some bits and pieces that happen to already work, XL is presently not suitable for any serious programming. Examples given below may sometimes simply not work. Take it as a painful reminder that the work is far from finished, and, who knows, as an idea for a contribution. See [HISTORY](https://github.com/c3d/xl/blob/master/doc/HISTORY.md) for how we came to the present mess, and [Compiler Status](https://github.com/c3d/xl#compiler-status) for information about what is expected to work.

XL is an extensible programming language designed to accomodate a variety of programming needs with ease. Being _extensible_ means that the language is designed to make it very easy for programmers to adapt the language to suit their needs, for example by adding new programming constructs. In XL, extending the language is a routine operation, much like adding a function or creating a class in more traditional programming languages.

As a validation of this bold claim, XL has a single fundamental operator, the [definition operator](https://github.com/c3d/xl#semantics-one-operator-to-rule-them-all), which you write `[Pattern] is [Implementation`, where\] `[Pattern]` is a program pattern, like `X+Y`, and `[Implementation]` explains how to translate that pattern, for example `Add X, Y`.

Everything that is built-in in most other programming languages, from basic data types to arithmetic to conditionals to loops is provided by the standard library in XL. You can replace these constructs if you want, or add your own. Adding a new kind of loop is not more difficult in XL than adding a function, and it uses the same syntax.

For more information, please consult the [XL handbook](https://github.com/c3d/xl/blob/master/doc/HANDBOOK.md).

[](https://github.com/c3d/xl#a-few-simple-examples)A few simple examples
------------------------------------------------------------------------

A program computing the factorial of numbers between 1 and 5 would be written as follows:

```
0! is 1 N! is N * (N-1)! for I in 1..5 loop print "The factorial of ", I, " is ", I! 
```

As a testament to its extensible nature, fundamental operations in XL are defined in the standard library, including operations that would be implemented using keywords in more traditional languages. For example, the `if` statement in XL is defined by the following code:

```
if [[true]] then TrueClause else FalseClause is TrueClause if [[false]] then TrueClause else FalseClause is FalseClause if [[true]] then TrueClause is TrueClause if [[false]] then TrueClause is false 
```

Similarly, the `while` loop is defined as follows:

```
while Condition loop Body is if Condition then Body while Condition loop Body 
```

The standard library also provides implementations for usual operations. For example, if you evaluate `1+3`, this is done through a definition for `+` on `integer` values that looks like the following (where `...` denotes some implementation-dependent code):

```
X:integer + Y:integer is ... 
```

[](https://github.com/c3d/xl#dialects-and-use-cases)Dialects and use cases
--------------------------------------------------------------------------

Two dialects of XL further demonstrate the extensibility of the language

*   [Tao3D](http://tao3d.sf.net) focuses on real-time 3D animations and can be used as a scriptable presentation software, or as someone once described it, a sort of real-time 3D LaTeX Lisp. In Tao3D, you describe a slide with a program that looks like the following code:
    
    ```
    import Slides slide "A simple slide example", * "This looks like some kind of markdown language" * "But code makes it powerful: your mouse is on the " & position position is if mouse_x < 0 then "left" else "right" 
    ```
    
    > The examples above use the new syntax in XL, with `is` as its definition operator. Older variants of the language used `->` instead. If you downloaded a pre-built binary of Tao3D, chances are that you need to replace `is` with `->` for the code above to work as intended.
    
*   [ELFE](http://github.com/c3d/elfe), formerly ELIOT (Extensible Language for the Internet of things) was an experiment on how to write distributed software that looks like a single program, for example to control swarms of devices in the context of the Internet of Things. An example of a simple ELFE program would be:
    
    ```
    WORKER is "worker.mycorp.com" MIN_TEMP is 25 MAX_TEMP is 55 invoke WORKER, every 2s, reply display temperature display Temp:real is print "The temperature of ", WORKER, " is ", Temp 
    ```

> The present branch, `bigmerge`, is an ongoing effort to _reconverge_ the various dialects of XL. At the moment, it should pass most of the ELFE-level tests, although this is not actively tested. Getting it to support Tao3D is somewhat more difficult and may take some time.

[](https://github.com/c3d/xl#if-you-come-from-another-language)If you come from another language
------------------------------------------------------------------------------------------------

If you are familiar with other programming languages, here are a few things that may surprise you about XL.

*   There are no keywords. In C, `if` is a keyword. In XL, it's just a name.
*   The language is designed primarily to be readable and writable by humans. For example, there are [special parsing rules](https://github.com/c3d/xl#subtlety-1-expression-vs-statement) to match how we read the code.
*   The language is _homoiconic_, i.e. programs are data, like in Lisp. This forms the basis of XL extensibility.
*   Evaluation is defined entirely in terms of rewrites of a very simple abstract. syntax tree that represents the program being evaluated.
*   The precedence of all operators is dynamic, in the sense that it's loaded from a [configuration file](https://github.com/c3d/xl/blob/master/src/xl.syntax)
*   The language is primarily defined by its own [standard library](https://github.com/c3d/xl/blob/master/src/builtins.xl), rather than by special rules in the compiler.

### [](https://github.com/c3d/xl#semantics-one-operator-to-rule-them-all)Semantics: One operator to rule them all

XL has one fundamental operator, `is`, the _definition operator_. This operator can be read as _transforms into_, i.e. it transforms the code that is on the left into the code that is on the right.

It can define simple variables```
pi is 3.1415926 
``` It can define lists```
words is "xylophage", "zygomatic", "barfitude" 
``` It can define functions```
abs X is if X < 0 then -X else X 
``` It can define operators```
X ≠ Y is not X = Y 
``` It can define specializations for particular inputs```
0! is 1 N! when N > 0 is N * (N-1)! 
``` It can define notations using arbitrary combinations of operators```
A in B..C is A >= B and A <= C 
``` It can define optimizations using specializations```
X * 1 is X X + 0 is X 
``` It can define program structures```
loop Body is Body; loop Body 
``` It can define types```
type complex is polar or cartesian type cartesian is cartesian(re:number, im:number) type polar is polar(mod:number, arg:number) 
```

Note that types in XL indicate the shape of parse trees. In other words, the `cartesian` type above will match any parse tree that takes the shape of the word `cartesian` followed by two numbers, like for example `cartesian(1,5)`.

It can define higher-order functions, i.e. functions that return functions```
adder N is (X is N + X) add3 is adder 3 // This will compute 8 add3 5 
```

This makes XL a truly functional language.

It can define maps associating a key to a value```
my_map is 0 is 4 1 is 0 8 is "World" 27 is 32 N when N < 45 is N + 1 // The following is "World" my_map 8 // The following is 32 my_map[27] // The following is 45 my_map (44) 
```

This provides a functionality roughly equivalent to `std::map` in C++. However, it's really nothing more than a regular function with a number of special cases. The compiler can optimize some special kinds of mapping to provide an efficient implementation.

It can define templates (C++ terminology) or generics (Ada terminology)\_```
// An (inefficient) implementation of a generic 1-based array type type array [1] of T is Value : T 1 is Value type array [N] of T when N > 1 is Head : array[N-1] of T Tail : T I when I
````It can define variadic functions````
`min X is X min X, Y is { Z is min Y; if X < Z then X else Z } // Computes 4 min 7, 42, 20, 8, 4, 5, 30` 
``` 

``In short, the single `is` operator covers all kinds of declarations that are found in other languages, using a single, easy to read syntax.``

### `[](https://github.com/c3d/xl#syntax-look-ma-no-keywords)Syntax: Look, Ma, no keywords!`

`XL has no keywords. Instead, the syntax relies on a rather simple [recursive descent](https://en.wikipedia.org/wiki/Recursive_descent_parser) [parser](https://github.com/c3d/xl/blob/master/src/parser.cpp).`

`THe parser generates a parse tree made of 8 node types. The first four node types are leaf nodes:`

*   `` `Integer` is for integer numbers such as `2` or `16#FFFF_FFFF`.``
*   `` `Real` is for real numbers such as `2.5` or `2#1.001_001_001#e-3` ``
*   `` `Text` is for text values such as `"Hello"` or `'World'`. Text can be encoded using UTF-8``
*   `` `Name` is for names and symbols such as `ABC` or `**` ``

`The last four node types are inner nodes:`

*   `` `Infix` are nodes where a named operator separates the operands, e.g. `A+B` or `A and B`.``
*   `` `Prefix` are nodes where the operator precedes the operand, e.g. `+X` or `sin X`. By default, functions are prefix.``
*   `` `Postfix` are nodes where the operator follows the operand, e.g. `3%` or `5km`.``
*   `` `Block` are nodes with only one child surrounded by delimiters, such as `(A)`, `[A]` or `{A}`.``

``Of note, the line separator is an infix that separates statements, much like the semi-colon `;`. The comma `,` infix is traditionally used to build lists or to separate the argument of functions. Indentation forms a special kind of block.``

`For example, the following code:`

```
 `tell "foo", if A < B+C then hello world` 
```

``parses as a prefix `tell`, with an infix `,` as its right argument. On the left of the `,` there is the text `"foo"`. On the right, there is an indentation block with a child that is an infix line separator. On the left of the line separator is the `if` statement. On the right is the name `world`.``

`This parser is dynamically configurable, with the default priorities being defined by the [xl.syntax](https://github.com/c3d/xl/blob/master/src/xl.syntax) file.`

`Parse trees are the fundamendal data structure in XL. Any data or program can be represented as a parse tree. Program evaluation is defined as transformation of parse trees.`

### `[](https://github.com/c3d/xl#xl-as-a-functional-language)XL as a functional language`

`XL can be seen as a functional language, where functions are first-class entities, i.e. you can manipulate them, pass them around, etc:`

```
`adder X:integer is (Y is Y + X) add3 is adder 3 add5 is adder 5 print "3+2=", add3 2 print "5+17=", add5 17 print "8+2=", (adder 8) 2` 
```

``However, it is a bit different in the sense that the core data structure is the parse tree. Some specific parse trees, for example `A+B`, are not naturally reduced to a function call, although they are subject to the same evaluation rules based on tree rewrites.``

### `[](https://github.com/c3d/xl#subtlety-1-expression-vs-statement)Subtlety #1: expression vs. statement`

`The XL parse tree is designed to represent programs in a way that is relatively natural for human beings. In that sense, it departs from languages such as Lisp or SmallTalk.`

`However, being readable for humans requires a few special rules to match the way we read expressions. Consider for example the following:`

```
`write sin X, cos Y` 
```

``Most human beings parse this as meaning `write (sin(X),cos(Y))`, i.e. we call `write` with two values resulting from evaluating `sin X` and `cos Y`. This is not entirely logical. If `write` takes comma-separated arguments, why wouldn't `sin` also take comma-separated arguments? In other words, why doesn't this parse as `write(sin(X, cos(Y))`?``

``This shows that humans have a notion of _expressions_ vs. _statements_. Expressions such as `sin X` have higher priority than commas and require parentheses if you want multiple arguments. By contrast, statements such as `write` have lower priority, and will take comma-separated argument lists. An indent or `{ }` block begins a statement, whereas parentheses `()` or square brackets `[]` begin an expression.``

`There are rare cases where the default rule will not achieve the desired objective, and you will need additional parentheses.`

### `[](https://github.com/c3d/xl#subtlety-2-infix-vs-prefix)Subtlety #2: infix vs. prefix`

`Another special rule is that XL will use the presence of a space on only one side of an operator to disambiguate between an infix or a prefix. For example:`

```
`write -A // write (-A) B - A // (B - A)` 
```

### `[](https://github.com/c3d/xl#subtlety-3-delayed-evaluation)Subtlety #3: Delayed evaluation`

`When you pass an argument to a function, evaluation happens only when necessary. Deferred evaluation may happen multiple times, which is necessary in many cases, but awful for performance if you do it by mistake.`

``Consider the following definition of `every`:``

```
`every Duration, Body is loop Body sleep Duration` 
```

``In that case, we want the `Body` to be evaluated every iteration, since this is typically an operation that we want to execute at each loop. Is the same true for `Duration`? Most likely, no.``

`One way to force evaluation is to give a type to the argument. If you want to force early evaluation of the argument, and to check that it is a real value, you can do it as follows:`

```
`every Duration:real, Body is loop Body sleep Duration` 
```

### `[](https://github.com/c3d/xl#subtlelty-4-closures)Subtlelty #4: Closures`

`Like many functional languages, XL ensures that the value of variables is preserved for the evaluation of a given body. Consider for example:`

```
`adder X:integer is (Y is Y + X) add3 := adder 3` 
```

``In that case, `adder 3` will bind `X` to value `3`, but then the returned value outlives the scope where `X` was declared. However, `X` is referred to in the code. So the returned value is a _closure_ which integrates the binding `X is 3`.``

`[](https://github.com/c3d/xl#compiler-status)Compiler status`
--------------------------------------------------------------

`The interpreter / compiler recently went through a rather heavy merge of several incompatible branches. As a result, it inherited the best of the various branches, but is overall quite broken. There are actually several, somewhat incompatible versions of the language, some of which reside in different binaries, some in the primary binary.`

``The primary binary resides in the `src` directory. It is written in C++, and there is currently no real plan to self-compile it, although there are plans to use it as a basis for a self-compiling compiler bootstrap someday.``

``That primary binary contains a single scanner and parser for the XL language, but three different ways to evaluate it, which are instances of the C++ `Evaluator` class. These three ways to evaluate XL are selected using the `-O` option.``

*   `` `-O0` or `-i` selects an interpreter. This interpreter is essentially similar to what used to be the ELFE implementation of the language, i.e. a very small implementation that performs evaluation using parse tree rewrites. It sort of works, passes most tests with `make check`, and is overall sane, if a bit slow (similar to `bash` in my testing). It can be used for example as an extension language for your application, and does not draw much in terms of dependencies. You would add your own vocabulary using simple-to-write "modules". See the `Makefile` for examples. That part is the only one I can advertise as possibly useful. In particular, it correctly runs the examples in the `demo` directory, which are the older ELFE demos, i.e. distributed programming from a single source code.``
    
*   `` `-O1` selects the `FastCompiler`, which is basically an adaptation of the compiler used in the Tao3D program, with the intent to allow the `master` branch of XL to be able to support Tao3D again without major incompatibilities. It generates machine code using LLVM, but the generated code is relatively inefficient because it manipulates the parse tree. For example, an integer value is always represented by an `Integer` pointer, so there is always an indirection to access it. Also, while forward-porting that compiler to a version of the compiler that had dropped it, I broke a number of things. So under repair, and not currently able to support Tao3D yet.``
    
*   `` `-O2` and above select the `Compiler` class, which is an ongoing attempt at implementing XL the way I always wanted to, using type inference to generate efficient code. Presently, the type inference is so badly broken that it's likely to reject a number of very valid programs, including the basic factorial example. I have hope, though. At some point, that implementation was able to compete with C on relatively simple programs, but only with a lot of type annotations. I'm trying to achieve the same result without the type annotations. We're getting there. Like `-O1`, `-O2` output uses LLVM to generate machine code, but that time, it's good machine code.``
    

``If you think 3 implementations is bad, wait. There is more. There is a `Bytecode` class that is yet another evaluator that attempted to generate a bytecode so as to accelerate interpreted evaluation, without having to bring in LLVM and all the risks associated with dynamic code generation (e.g. if you use XL as an extension language). Unfortunately, that bytecode experiment went nowhere. It's slow, ridden with bugs, and has severely damaged other parts of the compiler. I can't wait to expurge it from the compiler.``

`So now that's it, right? Well... No.`

``You see, the current XL started life as a "runtime" language for the "real" XL. The original XL looked more like Ada, and had very different type semantics. See [HISTORY](https://github.com/c3d/xl/blob/master/doc/HISTORY.md) for all the gory details. Suffice it to say here that this compiler resides in the `xl2` directory (because, yes, it was already version 2 of the language). One reason for me to keep it is that it's the only version of the compiler that ever came close to self-compiling it. So I keep it around to remind myself of various neat tricks that XL made possible, like the `translate` instruction.``

`Now, you are really done, right? Well... There's one more.`

``See, I really want the compiler to self-compile. So in order to prepare for that, there is a `native` directory where I store tidbits of what the future compiler and library would look like. Except that this is really an exploratory scratchpad, so the various modules are not even consistent with one another... But ultimately, if everything goes according to plan, the C++ compiler should be able to compile `native` in order to generate a compiler that would compile itself.``

`  
  
from Hacker News https://ift.tt/2Wz4uk5`