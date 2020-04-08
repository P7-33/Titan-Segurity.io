---
title: 'Solving Num: A combinatoric math game'
date: 2019-10-04T01:56:00+01:00
draft: false
---

![](http://dangoldin.com/assets/static/images/num-level-68-solution.png "Solving Num: A combinatoric math game")  

I don’t play games on my phone but one game I keep going back to is “[https://apps.apple.com/us/app/num-insanely-hard-math-game/id861791129](https://dangoldin.com/2019/09/14/solving-num-a-combinatoric-math-game/Num)” - an “insanely hard math game.” The premise is pretty simple - you have a few numbers that you need to combine, using the four basic math operations, so it computes to a specific number.

The levels start off simple but it gets more difficult with a lot of trial and error at the higher levels. They’re no longer simple expressions that can be evaluated fairly linearly but instead are solved by using fairly complex intermediate values.

I enjoy the process of solving these problems but decided to challenge myself to write a program that can solve these sorts of problems. Last night I was able to get a crude solution working that’s able to solve a 6-number problem in about 5 minutes on my laptop. The next challenge is speeding this to be even quicker but even the crude solution took a few attempts to get right.

The approach I took was a somewhat intelligent brute force. While it’s still fresh I wanted to share the attempts to highlight my thought process and the difficulties with each failed attempt.

### Attempt 1

Idea here was to simply get all the number permutations and alternate them with all combinations of the operators - for example “1 + 4 - 5 \* 6 / 4 + 1” - and then run them through Python’s eval to see how far I could get. I knew full well this would not solve all types of problems due to not being able to control the order of operations but I just wanted to get a starting point.

### Attempt 2

At this point I wanted to handle the order of operations issue from the first attempt and figured it would be easier to do that if I switched to a [Reverse Polish Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation) (RPN). The intuition here was to simplify the expressions I’d need to generate by not having to worry about the parentheses. This required implementing an RPN evaluator but I found a [simple one online](https://blog.klipse.tech/python/2016/09/22/python-reverse-polish-evaluator.html). Similar to the first attempt, this approach was still not able to represent every type of expression but it was much easier to work with. An example of an expression generated with this approach is “1 2 9 8 17 3 / + \* - \*”.

### Attempt 3

This was an extremely brute force attempt by treating each combination of numbers and operators as its own expression to be permuted. I didn’t worry about validation and instead just relied on evaluating and then ignoring the exceptions. The permutation step was incredibly simple to implement but as expected this was extremely inefficient and I was unable to actually get a solution in a reasonable amount of time. An example of an expression generated (invalid) with this approach was “1 + \* 2 9 8 17 3 / - \*” - it had the right numbers and operators but the RPN order was just invalid.

### Attempt 4

This was simply validating the expressions generated in the third attempt to before running the evaluator. With RPN the approach is incredibly simple since all we need to do is read from left to right and make sure that the number of numbers seen is always greater than the number of operators. This is the current approach and actually results in a working solution in a reasonable amount of time. I tested it on a few problems that have 6 starting numbers and the solutions were all within the 5 to 10 minute range.

### Future

There are some clear deficiencies with the previous approach. The major one is that why validate instead of generating the valid expressions at the beginning? The ideal approach would also do a fair amount of memoization to avoid having to recompute the same sub-expressions over and over. I expect that implementing these ideas will improve the speed by an order of magnitude.

If you’re interested in following along or building your own implementation it’s all available on GitHub: [https://github.com/dangoldin/num-game-solver/blob/master/solve.py](https://github.com/dangoldin/num-game-solver/blob/master/solve.py).

  
  
from Hacker News https://ift.tt/2LukCzm