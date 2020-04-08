---
title: 'A Counterintuitive Probability Game'
date: 2019-10-03T03:11:00+01:00
draft: false
---

A Counterintuitive Probability Game
-----------------------------------

_posted before 2019-09-15_

I read an interesting [math paper](https://fermatslibrary.com/s/pick-the-largest-number) by Thomas Cover that I struggled to believe at first. I recommend you read it before continuing reading this post (it’s short). Thus, I decided to test out the claim using Python.

The results hold. When the third random number, C, falls in is the same possible range as that of the other two numbers, the win rate is 66%. When C is a fixed number equally between the upper and lower limit of what the other two numbers may be, the win rate is 75%.

Thus, the benefit of using the entire Real number line as the possible range for C is to ensure that you at least sometimes choose a value in between the ranges the other player is selecting numbers from (they don’t have to choose anywhere around 0). If your C is never between their two numbers, your probability of winning is indeed 1/2.

  
  
from Hacker News https://ift.tt/2nPedpG