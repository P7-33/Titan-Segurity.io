---
title: 'Emtombed Secrets Partially Unearthed as Researchers Dissect Clever
Maze-Generating Algorithm'
date: 2019-10-01T06:05:00+01:00
draft: false
---

[![](https://hackaday.com/wp-content/uploads/2019/09/entoumbed-maze-generating-algorithm.png?w=160)](https://hackaday.com/wp-content/uploads/2019/09/entoumbed-maze-generating-algorithm.png)

If you look at enough of another developer’s code, you will eventually say, “What were you thinking, you gosh-darn lunatic?” Now, this exchange can precede the moment where you quit a company and check into a padded room, or it can be akin to calling someone a mad genius and offering them a beer. In the case of \[Steven Sidley\]’s 1982 game _Entombed_, \[John Aycock\] and \[Tara Copplestone\] [found a mysterious table for generating pseudo-random mazes and wrote a whitepaper on how it all works](https://arxiv.org/ftp/arxiv/papers/1811/1811.02035.pdf) (PDF). The table only generates solvable mazes, but if any bits are changed, the puzzles become inescapable.

The software archaeologists are currently in a labyrinth of their own, in which the exit is an explanation of the table, but the path is overgrown with decade-old vines. The programmer did not make the table himself, and its creator’s name is buried somewhere in the maze. Game cart storage was desperately limited so mazes _had_ to be generated on-the-fly rather than crafted and stored. _Entombed_‘s ad-hoc method worked by assessing the previous row and generating the next based on particular criteria, with some PRNG in places to keep it fresh. To save more space, the screen was mirrored down the center which doubles the workload of the table. Someday this mysterious table’s origins may be explained but for now, it is a work of art in its own right.

Aside from a table pulled directly from the aether, this [maze game](https://hackaday.com/2018/12/15/maze-generator-keeps-plotter-and-kids-busy/) leaned on pseudo-random numbers but there is [room for improvement](https://hackaday.com/2018/01/08/entropy-and-the-arduino/) in that regard too.

Via [BBC Future](http://www.bbc.com/future/story/20190919-the-maze-puzzle-hidden-within-an-early-video-game?utm_source=pocket-newtab).

  
  
from Hackaday https://ift.tt/2oQnOMZ  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)