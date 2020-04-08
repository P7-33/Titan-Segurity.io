---
title: 'C++ Value Categories'
date: 2019-11-07T08:42:00+01:00
draft: false
---

In C++, all expressions have two properies: a type and a value category. Value categories are a little complicated to understand and have gone through a few changes with time.

lvalue and rvalue
-----------------

Lvalue stands for `locator value`. An lvalue is something that occupies a memory location. But… doesn’t everything occupy a memory location? Not necessarily. Let’s look at a simple expression:

There are two values in this expression. On the left of the `=` sign we have `number`. On the right, we have `7`. `number` has a memory location associated to it, and it will be filled with the value 7. The `7` on the right doesn’t have a memory address associated to it. It is part of the program, but we can’t really get its memory address.

An expression like the one above, expects the left side of the `=` sign to be an lvalue. That’s the reason something like this doesn’t work:

An `rvalue` can be defined as anything that is not an `lvalue` (At least it could be defined like this in the past).

Non-modifiable lvalue
---------------------

In the beginning of C++ there were only `lvalues` and `rvalues`. Lvalues could be modified and rvalues couldn’t. When C++ introduced the `const` keyword, this changed.

```
1 2 
```

```
const int number \= 7; number \= 8; 
```

The code above fails because number is a `non-modifiable lvalue` and the `=` operator expects an `lvalue` on the left side.

References
----------

References were later added to the standard, and with it, new rules. A reference (now called `lvalue reference`) binds to an lvalue like this:

```
1 2 3 
```

```
int number \= 7; int &rnumber \= number; rnumber \= 8; 
```

If you’ve been writing or reading C++ code for a while, you have probably noticed functions that receive arguments as const references:

```
1 
```

```
void func(const int& num); 
```

In order to make the use of references look similar to the use of primitive types, References to `const` behave differently that normal `lvalue references`. The standard allows us to do:

7 is an rvalue, and `func` expects an lvalue reference. What happens in this scenario is, the compiler will create a temporary variable and will assign 7 to it. It will then pass a reference to this temporary to the function. Because the argument is const, we don’t have to worry about the program trying to modify the value 7. This conversion to a temporary will happen any time the compiler can find a way to convert the given argument to the argument expected by the function.

rvalue references
-----------------

To help achive better performance for some applications, C++ introduced rvalue references. This allows the compiler to take an rvalue and convert it to an lvalue.

A function can receive an rvalue reference by using the `&&` operator. This function can also be called with an `rvalue`:

The interesting thing here is that `func` is not receiving a constant argument, so it can actually modify `num`.

This works similarly as with lvalue references. In this scenario the compiler will actually create a temporary an pass a reference to this temporary to the function. The function can then modify this temporary as it desires.

xvalue
------

An xvalue is a value that is about to expire. A temporary is an xvalue as well as an object that has been moved with `std::move`. Xvalues can be passed to functions that expect an rvalue reference (`&&`) and can be [polymorphic objects](https://ncona.com/2019/10/virtual-functions-in-cpp/).

When a function receives an expiring value it takes ownership of it and extends its lifetime to the lifetime of the new function.

glvalue
-------

Stands for `generalized lvalue`. It can be an `lvalue` or an `xvalue`.

prvalue
-------

Stands for `pure rvalue`. It refers to the original rvalue definition above.

Conclusion
----------

After reading a few articles about the different categories, I still find it a little difficult to identify which category a value belongs to. This knowledge might not be useful very often, but it helps understand how compilers might implement some features and why certain ways of handling values can have better performance that others.

  
  
from Hacker News https://ift.tt/32svPpf