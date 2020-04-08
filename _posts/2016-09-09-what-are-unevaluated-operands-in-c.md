---
title: 'What are unevaluated operands in C++?'
date: 2019-10-24T02:51:00+01:00
draft: false
---

You know, the C++ standard is amazing sometimes. It contains hidden gifts for the most careful readers. One of these gifts is buried in the definition of _unevaluated operands_, both succinct and important:

> In some contexts, unevaluated operands appear \[...\].  
> An unevaluated operand is not evaluated.

Let's try to dissect it and understand what the standard offers us by means of this often-underrated tool.

Introduction
------------

To be honest, I've cheated a little. The full quote contains another statement that should make it clearer what an _unevaluated operand_ is:

> An unevaluated operand is considered a full-expression.

In other words, the _unevaluated operands_ are the operands of some operators of the language. They are expressions in all respects, but such that they are never evaluated. The reason is because those operators are there just to query the compile-time properties of their operands.

If this still doesn't seem interesting to you, note that not being evaluated means not giving rise to side effects. Right now, the term SFINAE is probably showing up in your thoughts along with many other fancy things, and unevaluated operands are getting more and more interesting.

What are these operators then? Up to C++17, there are four operators the operands of which are unevaluated: `typeof`, `sizeof`, `decltype`, and `noexcept`.  
C++20 will add a few other operators like them, but we have to wait a little longer for that.

So, why are these operators so special and what can we do with them?

### decltype

If you've ever worked in modern C++, it's likely that you used `decltype` at least once. This is probably the most used operator when doing SFINAE.  
To sum up and to avoid speaking _standardese_ too much, its goal is to inspect the declared type of an element or of an expression. Let's take a look at an example of use:

```
template<typename T> auto inspect(int, T &&item) -> decltype(item.func(), void()) { } template<typename T> void inspect(char, T &&item) { } template<typename T> void inspect(T &&item) { inspect(0, std::forward(item)); } inspect(std::string{"example"}); 
```

Here we are exploiting the _tag dispatching_ idiom to literally _select_ the right function to execute. As you can see, `decltype` is used to probe a compile-time feature of `item`, or better yet, of the type `T` that has a member function named `func`. The _best_ part is that `func`isn't actually executed in this context because (**remember**!) the whole expression is an unevaluated operand of `decltype`.  
In other words, this trick can be used to favor an overload when a given type has a member function named `func`. In all other cases, the fallback is executed. A bit of templates, the deduction rules, and our beloved SFINAE do the rest.

### noexcept

So far, so good. `decltype` is used in many codebases and you've probably already seen enough examples of it.  
What about `noexcept` instead? Can we do something similar with it? Actually, yes. As an example, consider the case in which we want to provide two different implementations of the same function: the former throws exceptions in case of errors; the latter doesn't make use of exceptions and returns error codes instead. The way we decide what function to use is by probing a given member and its `noexcept`\-ness from the type we receive:

```
template<typename T> auto inspect(int, T &&item) -> std::enable_if_t<noexcept(item.func())> { throw; } template<typename T> int inspect(char, T &&item) { return 0; } template<typename T> auto inspect(T &&item) { return inspect(0, std::forward(item)); } 
```

Because of how `std::enable_if_t` works, the first function is selected only if `T::func` has the `noexcept` qualifier, and in this case the return type is `void`. Otherwise, the second function is picked up and the return type is `int`; that is our error code.

Again, remember that the operands of the `noexcept` operator are unevaluated and therefore the function call `item.func()` is only taken in consideration to probe its compile-time feature, and we have no actual side effects at runtime when entering the function.

### sizeof

`sizeof` isn't as good as the two operators above to do SFINAE. However, one can imagine some interesting uses for it, in particular when it comes to working with something like the small buffer optimization.  
In this case, we can exploit the properties of this operator to provide different implementations of a class template when the size of the type we use to specialize it fits that of a `void *`:

```
template<typename, typename = std::bool_constant<true>> struct can_sbo { }; template<typename T> struct can_sbo> { /* ... */ }; 
```

I used `sizeof(T)` in the example, but we aren't constrained to it. In fact, we can use any expression we want. As an example `sizeof(T::member)`. Of course, it won't be evaluated.

### typeid

Let's go further and see what can offer us `typeid`. As you know, it's purpose is to return information about types, nothing less and nothing more.  
Unfortunately, this operator isn't very _SFINAE-friendly_ and it's not worth it to show an example, although one can perhaps build something ad hoc with it.

The Choice Trick
----------------

We have seen how some operators whose operands are not evaluated can be useful in some cases. Now it's time to see one of them in action in a real-world case that I've faced more than once.  
In particular, have you ever worked with templates and found yourself wanting to execute a function if the type has a given property, another function if it has a different property, or a third function as a fallback? Quite common indeed.  
The hard way is something that looks like the following:

```
template<typename T> std::enable_if_t> invoke() { } template<typename T> std::enable_if_t and !has_h> invoke() { } template<typename T> std::enable_if_t and !has_h and has_f> invoke() { } template<typename T> std::enable_if_t and !has_g and !has_h> invoke() { } 
```

where `has_FUNC` is the typical detection idiom:

```
template<typename T, typename = void> struct has_f: std::false_type {}; template<typename T> struct has_f().f())>> : std::true_type {}; 
```

Pretty annoying indeed, and the conditions become more and more complex in order to avoid ambiguities every time we want to add a switch to our cascade.  
Fortunately, C++17 introduced `if constexpr` that clears this a bit:

```
template<typename T> void invoke() { if constexpr(has_h) { } else if constexpr(has_g) { } else if constexpr(has_f) { } else { } } 
```

Umm, does it? We still have to define a lot of classes to detect properties (note that `has_f` serves only the purpose of probing a type for the member function `f`, but we want to also detect `g` and `h` in our example). Moreover, now we have to put everything in the body of the same function; that can be confusing and isn't desired in all cases.  
How can we simplify this using one of the operators above?

First, let's introduce the `choice` class:

```
template<std::size_t N> struct choice: choice-1> {}; template<> struct choice<0> {}; 
```

The class is defined in such a way that `choice` inherits from `choice`and so on until `choice<0>`. It means that we can use `choice` as an argument to a function that requires `choice` as long as `M < N`.  
We can now rewrite the first group of functions in a smarter way by means of this tool and using `decltype` as shown in the previous sections to probe (but not to evaluate!) our types and their compile-time properties:

```
template<typename T> auto invoke(choice<3>) -> decltype(std::declval().h(), void()) { } template<typename T> auto invoke(choice<2>) -> decltype(std::declval().g(), void()) { } template<typename T> auto invoke(choice<1>) -> decltype(std::declval().f(), void()) { } template<typename T> void invoke(choice<0>) { } template<typename T> void invoke() { invoke(choice<100>{}); } 
```

How does it work? Because of the rules of the language, the first function that matches the given arguments is as follows:

```
template<typename T> auto invoke(choice<3>) -> decltype(std::declval().h(), void()) { } 
```

Here we use `decltype` to probe a compile-time property for the type `T`. Probe, not evaluate. Therefore, we have no side effects here.  
SFINAE does the rest for us. In case the type `T` has a member `h`, we enter the first function. Otherwise, we receive a soft error, but the compiler continues to probe the other functions to turn it into a hard error and return to us. This isn't even an option actually because of our fallback that will accept everything that doesn't match one of the previous cases:

```
template<typename T> void invoke(choice<0>) { } 
```

Another important thing that perhaps doesn't immediately catch our attention is that there is no need to resort to the detection idiom to test our types, which relieves us from having to write a lot of code.  
Finally, we have as many functions as there are rules, something that is definitely easy to maintain and to reason on.

Conclusion
----------

We have seen how the C++ language offers a few very interesting operators. Some aren't very useful when you want to do SFINAE; others can be used within certain limits, but one in particular seems to be good enough for most of the cases: `decltype`.  
The _choice trick_ is instead widely used and combines different aspects of the language. It may seem complicated initially, but it's really simple and allows us to solve a common problem with a very compact code. You've probably already encountered it in a simpler form, where the overload is solved by a combination of `int` and`char`, but the way it works is exactly the same. We just walked through an _extended version_ of it.

Obviously the uses and abuses of `decltype` aren't limited to this example, but I'll leave the rest for future articles, hoping that you enjoyed what you've read so far.

  
  
from Hacker News https://ift.tt/2or8l5z