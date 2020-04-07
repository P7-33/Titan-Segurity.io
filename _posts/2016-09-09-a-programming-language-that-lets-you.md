---
title: 'A Programming Language That Lets You Code With Pixels'
date: 2020-01-03T10:36:00+01:00
draft: false
---

This programming language gives you programs that resemble modern art. It’s fortunately a feature of the language, [dubbed Piet](https://www.dangermouse.net/esoteric/piet.html) after the famed abstract painter Piet Mondrian.

The language uses 20 distinct colors, with the colors cycling from red to yellow to green to cyan to blue to magenta and the lightness cycling from light to normal to dark. The code is formed from graphics made of the recognized colors, with individual pixels holding much of the information. Stacks are used for storing data values, that can exist as integers or as Unicode characters with the proper commands applied.

![](https://hackaday.com/wp-content/uploads/2019/12/Screen-Shot-2019-12-30-at-7.48.25-PM.png?w=400)

Numbers in the program are represented by colors, while black blocks indicates edges and white blocks indicate free zones. The interpreter physically slides through blocks in the direction of the Direction Pointer (DP), with hue changes indicating different commands based on the steps of the change.

To execute a program, the Piet language interpreter begins in the upper left codel (or individual code block) of the program, maintaining a DP initially pointed to the right and a Codel Chooser (CC) initially pointed to the left. The DP and CC turn right, left, down, or up depending on the execution.

There is currently a small community of coders developing sample programs, interpreters, IDEs, and compilers for the language. You can check out some of the [sample programs here](https://www.dangermouse.net/esoteric/piet/samples.html).

[![](https://hackaday.com/wp-content/uploads/2019/12/Screen-Shot-2019-12-30-at-7.47.39-PM.png?w=250)](https://hackaday.com/2020/01/03/a-programming-language-that-lets-you-code-with-pixels/screen-shot-2019-12-30-at-7-47-39-pm/) [![](https://hackaday.com/wp-content/uploads/2019/12/Screen-Shot-2019-12-30-at-7.47.58-PM.png?w=250)](https://hackaday.com/2020/01/03/a-programming-language-that-lets-you-code-with-pixels/screen-shot-2019-12-30-at-7-47-58-pm/) [![](https://hackaday.com/wp-content/uploads/2019/12/Screen-Shot-2019-12-30-at-7.48.39-PM.png?w=250)](https://hackaday.com/2020/01/03/a-programming-language-that-lets-you-code-with-pixels/screen-shot-2019-12-30-at-7-48-39-pm/)  
  
from Hackaday https://ift.tt/2QCflHq  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)