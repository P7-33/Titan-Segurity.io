---
title: 'More Intuitive Calculator Arithmetic'
date: 2019-10-23T04:41:00+01:00
draft: false
---

Early last week, Desmos released a change to the way that basic arithmetic is evaluated in our calculators. The goal of this change is to make the calculators’ answers match people’s intuitions more often by computing numerical answers exactly instead of approximately in more cases where a human would.

Approximate binary arithmetic
-----------------------------

Before this change, all arithmetic in the calculators was evaluated using a system called binary floating point arithmetic. All the numbers this system can represent have the form of an integer multiplied by a power of `$2$`: for example `$3 \times 2^5$` or `$1759 \times 2^{-18}$`.

There are a few different commonly-used versions of binary floating point arithmetic that are distinguished by the range of allowed integer parts and exponents. In the [version we use](https://en.wikipedia.org/wiki/Double-precision_floating-point_format#IEEE_754_double-precision_binary_floating-point_format:_binary64), the integer part (technically called the significand) must be between `$-2^{53}$` and `$2^{53}$`, and the exponent part must be between `$-1022$` and `$1023$`.

There are lots of numbers that can’t be represented exactly in this system, like `$\pi$` or `$\sqrt{2}$`, but also many simple fractions, like `$2/3$` or `$1/7$` or `$3/10$`. The basic rule for knowing if a fraction can be represented exactly is that its denominator must be a power of `$2$` (there are also limits on how large the numerator or denominator can grow). So `$3/8$` can be represented exactly (as `$3 \times 2^{-3}$`) because its denominator is a power of `$2$`, but `$3/10$` can’t be represented exactly because its denominator is not a power of `$2$`.

In binary floating point, when a user inputs a decimal number that cannot be represented exactly, like `$0.3$`, it is immediately converted to the closest number that can be represented. In the case of `$0.3$`, that number is `$5404319552844595\times2^{-54}$`, which is very close to `$0.3$`, but in fact equals (exactly)

```
0.299999999999999988897769753748434595763683319091796875 
```

Similarly, whenever an arithmetic operation on two numbers produces a result that can’t be represented exactly, the result is rounded to the nearest number that can be represented. So `$3$` and `$10$` can be represented exactly, but the result of `$3/10$` must be rounded.

The consequence of all of this rounding is that even very simple arithmetic identities are not exactly obeyed. For example, the rounded result of `$0.1 + 0.2$` is not exactly equal to the rounded result of `$3/10$` (it’s a little larger), and the rounded result of `$1/2 + 1/3 + 1/6$` is a little less than `$1$`.

These slight inaccuracies weren’t always noticeable in the Desmos calculators because the calculators don’t display every digit that they use internally. So even though `$0.1 + 0.2$` comes out to a number a little larger than `$0.3$` internally, it still displayed as `$0.3$`. But the difference could still have observable consequences in some cases. For example, the result of `$1/(0.1 + 0.2 - 0.3)$` displayed as `$1.8014398509\times10^{16}$`, and `$(0.1 + 0.2 - 0.3)\times10^{16}$` displayed as `$0.555111512313$`. And if you used `$0.1 + 0.2 = 0.3$` as the condition in a piecewise, the condition would evaluate to false. For example, `$\{0.1 + 0.2 = 0.3: 1, 0\}$` evaluated to `$0$`.

Binary floating point arithmetic has many excellent properties as a number system for computers (more on this below), and it’s the workhorse of practically all modern scientific computing. But nobody is born knowing all of its rounding rules, and we’ve found that stumbling across their consequences is sometimes a distraction for the teachers and students we aim to serve.

Exact arithmetic for small rationals
------------------------------------

Desmos decided to address some of these rounding issues by adding a second internal number format that we can use in calculations: rational numbers where the numerator and denominator are both integers between `$-2^{53}$` and `$2^{53}$`. Numbers of this form can exactly represent many decimals that binary floating point must round, and the basic arithmetic operations (addition, subtraction, multiplication, and division) are often exact for these numbers.

So now, when you write the decimal `$0.3$` in the calculator, it will be stored internally as the exact representation `{numerator: 3, denominator: 10}`, and when you write `$0.1 + 0.2$`, we will compute `$1/10 + 2/10 = 3/10$` exactly.

This doesn’t mean that _everything_ will be computed exactly. We can still only approximately represent irrational numbers like `$\pi$` or `$\sqrt{2}$` or `$\ln(3)$` (they are represented by the nearest binary floating point number, just as they were before). And even simple arithmetic on exact inputs doesn’t produce exact results when the numerator or denominator of the result would be too large. So even though `$1/2^{30} + 1/(2^{30} + 1)$` is exactly equal to the fraction `$2147483649/1152921505680588800$`, we won’t store it that way, because the denominator is too large. Instead, we’ll convert it to the closest representable binary floating point number, `$2147483647\times2^{-60}$`, and further calculations using this result as an input will use all the usual floating point rounding rules.

The goal isn’t to avoid all approximation—many numbers have to be rounded for display anyway to be represented as finite decimals, and people typically aren’t surprised by this—instead, the goal is to try to compute exactly when people who don’t know about our internal number system expect we would compute exactly.

Considering alternatives
------------------------

Perhaps you are wondering why we ever used binary floating point as our number system in the first place when it has to make approximations to represent numbers as simple as `$0.1$`.

In fact, there are lots of calculators that make this choice differently. Many handheld calculators use decimal floating point instead of binary floating point; in other words, they represent numbers as integers multiplied by a power of `$10$` instead of as integers multiplied by a power of `$2$`. Decimal floating point is able to represent all decimal numbers that have a small enough number of digits, and so user input typically doesn’t need to be rounded immediately before the first calculation can take place.

To some extent, the choice of binary floating point was made for us. Our calculators are built for the web, and so they are implemented in the programming language of the web: Javascript. Javascript only comes with one built in number representation ([for now](https://github.com/tc39/proposal-bigint)): 64-bit binary floating point numbers. And it’s not just Javascript that’s biased towards binary floating point, your computer is too. Pretty much every device that can run a web browser has special circuits designed specifically for doing arithmetic on binary floating point numbers, and this built-in hardware support allows binary floating point arithmetic to be very fast and very efficient. Many handheld calculators, and some old or very special purpose computers have hardware support for decimal floating point, but the device you’re using to read this post almost certainly doesn’t. Hardware-implemented binary floating point has won out over decimal floating point on general purpose computers because it’s more compact and simpler to represent in memory, and the circuits needed for doing arithmetic are simpler. Scientists and engineers have another reason for preferring binary floating point: the spacing between successive representable numbers is more regular, and this means that certain kinds of rounding errors accumulate less rapidly.

We could have implemented our own decimal arithmetic in Javascript (and in fact there are already plenty of [open source implementations](https://www.npmjs.com/search?q=decimal) available). It’s a very reasonable choice for a calculator. But decimal arithmetic only eliminates one source of rounding—it still has to round as soon as you do something like divide by `$3$` (or any number that has a prime factor other than `$2$` or `$5$`). And software-implemented decimal arithmetic will be a lot slower than hardware-implemented binary arithmetic. Speed doesn’t matter so much for displaying a numerical answer to a single calculation, but it starts to matter a lot for plotting, and especially for animating plots. We want the experience of using the graphing calculator to feel like exploring math, and long delays between user input and plot updates completely spoil that feeling.

Alternatively, we could have used rational numbers from the start. But rational numbers have an important downside as a number system for general purpose computations: the numerator and denominator have a tendency to grow larger and larger as you do more arithmetic operations, even for calculations where the quotient is approaching a constant value. For example, the sum `$1 - 1/3 + 1/5 - ...$` approaches `$\pi/4$` as more terms are added. Here are decimal approximations and exact rational representations of a few of the partial sums:

n

approx.

exact

`$1$`

`$1$`

`$1$`

`$2$`

`$0.666667$`

`$\frac{2}{3}$`

`$5$`

`$0.834921$`

`$\frac{263}{315}$`

`$10$`

`$0.76046$`

`$\frac{11064338}{14549535}$`

`$20$`

`$0.772906$`

`$\frac{129049485078524}{166966608033225}$`

`$50$`

`$0.780399$`

`$\frac{850151369116051611488718369170287588082}{1089380862964257455695840764614254743075}$`

As the numerator and denominator grow, the space required to store them grows, and each arithmetic operation becomes slower and slower.

Rational numbers where the numerator and denominator are allowed to grow arbitrarily large are used by computer algebra systems (CAS) like Mathematica and Maple (and also some high-end handheld graphing calculators). Users of these systems are comfortable waiting a while for an exact answer to a complicated computation. But arbitrary-sized rationals aren’t a great choice for things like interactive plotting, where approximations are acceptable and fast execution is required. And no matter how much space you’re willing to let your numbers take up, you _still_ need to have some approximate format to fall back on if you ever want to show a decimal approximation to an irrational number, like `$\sqrt{2}$`. The great advantage of floating point numbers, either binary or decimal, is that they can accurately approximate numbers across many orders of magnitude while requiring only a fixed amount of space to store and a fixed amount of time for each operation.

It took a while for us to settle on the idea of using rationals with limited-sized integers for the numerator and denominator and falling back to binary floating point when we have to. I doubt this idea is original—it’s a combination of a few well-established ideas—but I’m also not aware of any calculator (or programming language) that currently works this way.

So why doesn’t everyone else already do this?

I suspect that handheld calculator makers have largely been satisfied with decimal arithmetic, even though it has to approximate most fractions. When exposing users to the reality of approximations has not been satisfactory, another common strategy has been to pursue [alternative rounding and comparison strategies](http://people.ku.edu/~wzhuang/CAMseminar/CAM06Fall/DirtySecrets.pdf).

For programming languages, I think efficient execution and simple-to-explain rules (even when these rules can have subtle consequences) are more important than matching the pencil-and-paper intuition that simple fraction computations should be done exactly. Expert users probably don’t want to consider the possibility that the number representation and arithmetic model might switch in the middle of a calculation because a denominator somewhere grew too large. If a calculation will end up approximate eventually, it’s simplest to approximate from the start.

But for our users—teachers and students at a variety of grade levels—I think this new system is going to be a really excellent trade-off. I hope it will help them stay focused on interesting math conversations rather than debugging their understanding of calculator technology.

  
  
from Hacker News https://ift.tt/2z8FwNW