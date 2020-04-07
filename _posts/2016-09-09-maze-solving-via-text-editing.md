---
title: 'Maze Solving Via Text Editing'
date: 2020-01-12T16:18:00+01:00
draft: false
---

Linux scripters usually know about sed — the stream editor. It has a simple job: transform text as it whizzes from input to output. So if you wanted to solve a maze, this wouldn’t be the tool you’d think to use, right? Well, if you were \[xsot\], [you’d disagree](https://devpost.com/software/sed-pathfinder).

You build a maze using spaces for empty space and # for walls. There’s an S to mark the start position and an E to mark the end. Of course, the maze can also contain newlines. The sed script does an amazing job of solving the problem.

As the author points out:

> The main difficulty lies in the lack of the luxuries usually provided in a regular programming language such as:
> 
> *   arithmetic
> *   data types other than strings
> *   more than 2 “variables”
> 
> Also, sed regex lacks features present in other regex systems such as PCRE (non-greedy matching, lookaheads, etc).

We will confess, we didn’t pull the whole [122 line script](https://gist.github.com/xsot/99a8a4304660916455ba2c2c774e623a) apart to understand it, but it looks like it replaces spaces with special marker characters that relate to the direction from the end to the start. The characters U, D, L, and R indicate the direction. Then it is able to select the closest character and replaces them with arrows (well, a letter v, a caret, and the less than and greater than signs).

A very unusual hack of using sed, we think. The output is even colorized and animated. Amazing.

We can’t say we’ve ever done anything this bizarre with a scripting command. We have looked at [scripting](https://hackaday.com/2019/12/30/linux-fu-leaning-down-with-exec/) many times, though, if you want to brush up. Probably the closest we’ve come is using bash scripts to process [binary files](https://hackaday.com/2018/06/29/linux-fu-scripting-for-binary-files/).

  
  
from Hackaday https://ift.tt/2NkmF9F  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)