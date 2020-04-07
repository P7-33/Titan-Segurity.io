---
title: 'The Wireworld computer #TuringMachine #Computers'
date: 2020-01-08T15:25:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/Untitled-30.png)

Via [quinapalus.com](https://www.quinapalus.com/wi-index.html): Wireworld is a cellular automaton on an infinite square grid, invented by Brian Silverman in about 1984. It appeared as part of his ‘Phantom Fish Tank’ program in 1987, but we only found out about it when it was described in _Scientific American_ in January 1990. The automaton has a similar flavour to J. H. Conway’s well-known ‘Game of Life’.

Each cell can be in one of four different states, forming a pattern on the grid. The four states are:

*   blank, shown in the pictures here in black;
*   ‘copper’, shown here as a sort of orange colour;
*   ‘electron head’, or just ‘head’ for short, shown here as white; and
*   ‘electron tail’, or ‘tail’, shown in blue.

![black square on black background](https://www.quinapalus.com/wi-blank.gif)

![orange square](https://www.quinapalus.com/wi-copper.gif)

![white square](https://www.quinapalus.com/wi-head.gif)

![blue square](https://www.quinapalus.com/wi-tail.gif)

Blank

Copper

Head

Tail

### The rules of Wireworld

Time proceeds in discrete steps called _generations_. At each generation the state of each cell may change; whether it changes, and what it changes to, depend on its current state and the state of its eight nearest neighbour cells according to a simple set of rules:

*   a blank square always stays blank
*   an electron head always becomes an electron tail
*   an electron tail always becomes copper
*   copper stays as copper unless it has just one or two neighbours that are electron heads, in which case it becomes an electron head

Signals
-------

As you can see from the illustration below, an electron head-tail pair (which we’ll call an ‘electron’) moves along a row of copper cells (which we’ll call a ‘wire’) at the rate of one cell per generation.

![electron head-tail pair moving on copper wire](https://www.quinapalus.com/wi-wire.gif)

Wires give us a way of transporting a sequence of electrons from one point to another. The pattern of electrons is preserved as they move along a wire and so, if we can represent data using these patterns, we can use the wires to carry data from one place to another.

[See the article](https://www.quinapalus.com/wi-index.html) for how such logic is combined to form logic gates, registers, an instruction set, and the full computer which is able to run programs such as calculating prime numbers

![block diagram](https://www.quinapalus.com/block.gif)