---
title: 'My Favorite Programming Problem to Teach: Digit Length'
date: 2019-11-11T01:46:00+01:00
draft: false
---

My Favorite Programming Problem to Teach: Digit Length
======================================================

By [Jacob Strieb](https://jstrieb.github.io)

Published on [November 10, 2019](https://jstrieb.github.io/posts/digit-length/)

* * *

During the Fall 2018 semester, I had the pleasure of being a teaching assistant for [Fundamentals of Programming and Computer Science (15-112)](http://cs.cmu.edu/~112) at Carnegie Mellon University, where I am an undergraduate. 112—as the course is commonly known—uses rigorous problem sets to teach algorithmic thinking and much of the Python programming language. Because it is required for many majors and programs throughout the university, students with widely varying academic backgrounds take the course.

As a TA, my responsibilities included leading weekly “small group” sessions. The course encourages interactive learning through guided practice, and these small, TA-led groups are ideal for hands-on learning.

Besides recursion, my favorite topic to teach in small groups was finding digit length. This deceptively simple task actually provides a surprising number of opportunities to explore deep ideas. The problem is stated as follows.

### Problem

> Write a function `digitLength(n)` that takes a natural number as input (_i.e._, 0, 1, 2, …) and returns as output the number of digits the input has.
> 
> For example: `digitLength(69420) == 5` and `digitLength(1337) == 4`

When this problem is assigned, students have learned about arithmetic operators, variables, conditional statments, and loops. For the vast majority of students (who lack prior programming experience), this can be a particularly difficult time in the course. The first few weeks go quickly, and students are expected to solve problems using multiple programming concepts shortly after learning them. This task is ideal for helping students build confidence, practice basic topics, and learn skills that will be critical for their success in the rest of the course.

Naive Solution
==============

The first solution students come up with typically looks like the following.

After correcting errors, reviewing functionally-equivalent alternatives, and congratulating students on their understanding of loops, functions, variables, and arithmetic, I ask them: does this function always work?

The simple[1](https://jstrieb.github.io/posts/digit-length/#fn1) answer: this solution fails on `n = 0`, returning `0` instead of `1` because it never enters the loop body and thus never increments `count`. Addressing this minor problem provides a good opportunity to review conditionals. It also prompts a discussion about handling edge cases, and the mechanics and merits of returning early. We are left with a valid solution that looks like the following.

Constrained Solution
====================

Expecting to move on, most students are surprised when I pose the problem again, but with a constraint: don’t use any loops.

If the task is framed as a “counting” problem, it seems best accomplished with loops, so I encourage conceptualizing it differently. The first hint is to develop a solution using a composition of functions and operations, rather than a series of instructions given to the computer. The subsequent big hint is to work with a _mathematical_ definition of “digit length in base 10.”

It is natural to form this definition using numerical ranges. For instance, all two-digit natural numbers fall between 9 and 100, all three-digit naturals fall between 99 and 1000, and so on. After some examples it becomes clear that generally, digit length is determined by the bounding powers of 10. Once this connection is made, I introduce Python’s `math.log10` function and do a quick review of logarithms if necessary.

Discussing `math.log10` presents a good opportunity to review the concept of types, and to discuss different methods of conversion between `float` and `int` with consideration given to the method of rounding used for each. Python’s default `round` function behaves unintuitively, so it is important to ensure students understand how to use it properly.

The process of solving this problem is also a chance to emphasize the utility of exploring concepts by doing examples and planning on the chalkboard before beginning to write code.

At this point, students may develop a solution like the following.

As before, after congratulating students on arriving at a clever, unintuitive solution to a difficult problem, I ask: does this function always work?

Once again, the function fails on `n = 0`. This time, rather than returning an incorrect solution, there is an error. This is because `math.log10(0)` raises a `ValueError` exception since 0 is not in the domain of the log10 function.[2](https://jstrieb.github.io/posts/digit-length/#fn2)

When I had this problem for homework as a student, I submitted a variant of `digitLengthClever`. It passed all test cases, and I got full credit. But I discovered a subtle bug only after wasting hours debugging more complex code utilizing the function. The subtle bug causes the function to return incorrect results for powers of 10 (`n = 10**x` for positive values `x` of type `int`). For example, though 102 = 100 has 3 digits, the following is true.

Thus `digitLengthClever(10**2) == 2`, when it should return `3`. I didn’t discover this problem initially, because the autograding test cases did not include a test using a power of 10.

Before concluding the small group session, I work with students to finalize a correct, loop-free solution like the following.

Lessons Learned
===============

With the remaining time in the small group session, I recap fundamental concepts and discuss how the problem relates to deep ideas in programming. Though many of the lessons may be obvious to those with software engineering experience, the conclusions therein can take a long time to reach for students new to the discipline, which is why I make a point to discuss them early in the course.

Testing
-------

Recounting my anecdote about getting full credit for an incorrect `digitLength` solution demonstrates the utility of _good_ test cases, since I may have caught the bug earlier had the tests been more comprehensive. I additionally share my experience to emphasize that unit testing is never sufficient to guarantee a function works correctly in all cases. I hope to illustrate by example that unit testing saves time in the long-run, but is not a panacea for guaranteeing code correctness.

Reviewing the deceptive, almost-correct solutions teach that it is insufficient for a program to _seem_ to work; truly correct code requires stronger guarantees. This mindset prepares students to learn about contracts and formal methods, topics taught in 15-122 and 15-150 (the following courses in the Carnegie Mellon introductory computer science series).

Furthermore, the examples teach that when developing test cases, it is beneificial to include suspected edge case inputs like `0`.

Specification Clarity
---------------------

Initial solutions that fail on input `n = 0` are ideal for highlighting the importance of well-developed specifications. Students are likely to be more focused on solving problem sets correctly than on software engineering best-practices. Thus, they may not consider that the formulation of the problem has important consequences for which solutions are correct.

Specifically, it may not be apparent that the inclusion of 0 in the definition of natural numbers from the problem statement is critical for a correct solution.

Keeping the set of inputs in-mind is an important habit for ensuring that code takes into account edge cases and is provably correct. Discussing specification clarity doubles as an opportunity to encourage students to formalize specifications for all functions they create. Ideally, including specifications as comments makes code more readable, but it also forces students to consider when their functions are well-defined.

If my job is done correctly, students will leave the small group session understanding that clarifying details about the specification before writing code is the difference between unexpected errors and well-defined behavior.

Code and Math
-------------

Working through programming problems that have elegant mathematical solutions is a good way to help students frame their perceptions about the relationship between code and math. Solving coding problems mathematically is a particularly good tactic for decoupling students’ conceptualization of programming from the process of giving instructions to a computer. Though sometimes useful, thinking in terms of instructing a computer can be an impediment to thinking algorithmically. Since algorithmic problem solving is both one of the main facets of the course, and is necessary for students’ continued success in future computer science courses at Carnegie Mellon, problems like finding digit length are handy to broaden students’ minds.

Conversely, problems like finding digit length also demonstrate how to explore mathematical ideas through computation. Evaluating different solutions leads to natural questions about the definitions implicit in the problem statement: mathematically, what is digit length? How many digits does 0 actually have? Can one define natural numbers based on whether they posses digit length,[3](https://jstrieb.github.io/posts/digit-length/#fn3) or is digit length a derivative property of natural numbers? What are the resulting implications for the oft-debated consideration of 0 as a natural number? Though computation may not be able to answer these questions directly, it provides a useful means by which to understand and probe abstract mathematical concepts.

Alternate, Invalid Solution
===========================

By the time this problem is given, strings have not yet been covered in the course. As a result, solutions using strings are disallowed on problem sets and quizzes until they are taught. However, the few students who have prior Python programming experience may be tempted to find digit length without loops using a variant of the following (for our purposes) invalid solution. I include it below for reference.

* * *

1.  The simple answer is not necessarily the correct one; the correct answer depends on how many digits you think 0 has[↩](https://jstrieb.github.io/posts/digit-length/#fnref1)
    
2.  This seems to suggest that depending on how you define “digit length,” the number 0 has an undefined digit length, rather than having 1 digit[↩](https://jstrieb.github.io/posts/digit-length/#fnref2)
    
3.  In other words, define the natural numbers as the domain of the log  function.[↩](https://jstrieb.github.io/posts/digit-length/#fnref3)
    

* * *

Copyright © 2019 Jacob Strieb. All right reserved.

  
  
from Hacker News https://ift.tt/2Q6igJU