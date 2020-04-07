---
title: 'How to wrap packages with maximum paper efficiency #Math #ProblemSolving'
date: 2020-01-17T16:28:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/Untitled-61.png)

Jason [writes on the Almost Looks Like Work blog](https://jasmcole.com/2019/12/27/wraptimisation-2-the-wrappening/) about the eternal problem in wrapping a package: How to do wo with the least amount of wrapping paper.

The problem:
------------

*   The present is a cuboid of side lengths ![a, b, c](https://s0.wp.com/latex.php?latex=a%2C+b%2C+c&bg=ffffff&fg=333333&s=0 "a, b, c") with ![a > b > c](https://s0.wp.com/latex.php?latex=a+%3E+b+%3E+c&bg=ffffff&fg=333333&s=0 "a > b > c")
*   The wrapping paper is a rectangle of side lengths ![w, h](https://s0.wp.com/latex.php?latex=w%2C+h&bg=ffffff&fg=333333&s=0 "w, h")
*   The wrapping process is to place the present on the centre of the wrapping paper on it’s largest face (of area ![ab](https://s0.wp.com/latex.php?latex=ab&bg=ffffff&fg=333333&s=0 "ab")), optionally rotate the paper by some angle ![\theta](https://s0.wp.com/latex.php?latex=%5Ctheta&bg=ffffff&fg=333333&s=0 "\theta"), then fold the paper up around the present onto the top face
*   The paper must cover all of the surface area of the present
*   The efficiency of the wrap ![\epsilon < 1](https://s0.wp.com/latex.php?latex=%5Cepsilon+%3C+1&bg=ffffff&fg=333333&s=0 "\epsilon < 1") is defined as the ratio of the surface area of the present to the area of the paper:

![\displaystyle{\epsilon = \frac{2(a\cdot b + a \cdot c + b \cdot c)}{w \cdot h}}](https://s0.wp.com/latex.php?latex=%5Cdisplaystyle%7B%5Cepsilon+%3D+%5Cfrac%7B2%28a%5Ccdot+b+%2B+a+%5Ccdot+c+%2B+b+%5Ccdot+c%29%7D%7Bw+%5Ccdot+h%7D%7D&bg=ffffff&fg=333333&s=0 "\displaystyle{\epsilon = \frac{2(a\cdot b + a \cdot c + b \cdot c)}{w \cdot h}}")

Our aim is to find a ![w, h, \theta](https://s0.wp.com/latex.php?latex=w%2C+h%2C+%5Ctheta&bg=ffffff&fg=333333&s=0 "w, h, \theta") which covers the present with maximum efficiency.

[See the post](https://jasmcole.com/2019/12/27/wraptimisation-2-the-wrappening/) for the analytical results and the conclusions.