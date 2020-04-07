---
title: 'A Sliding Puzzle for the PyBadge written in
CircuitPython #Gaming #PyBadge @hobby_robotics'
date: 2020-02-17T16:24:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-38.jpg)

The Aspiring Roboticist ([@hobby\_robotics](https://twitter.com/hobby_robotics/status/1228520055228555267)) posts their sliding puzzle Valentine’s Day project using an Adafruit PyBadge programmed in CircuitPython.

> The sliding puzzle has a long history. The first one, a 4×4, 15 tile puzzle, was made in 1890.  The puzzles may have letters forming words or have pictures instead of, or in addition to, numbers. Basically, the tiles are randomized, and then must be returned, by sliding adjacent tiles into the open space one at a time, until the puzzle is returned to the original arrangement.  
> ![15 tile sliding puzzle](https://www.mcgurrin.info/robots/wp-content/uploads/2019/12/15-Puzzle-300x300.jpg)

This is a sliding puzzle game written in [CircuitPython](https://circuitpython.org/) for the [Adafruit](https://www.adafruit.com/) [PyBadge and PyBadge LC](https://learn.adafruit.com/adafruit-pybadge/). It uses pictures for the puzzle, with numbers superimposed to make the puzzles easier to solve. It is configurable so that different images can be used, and it supports both 3×3 (8 tile) and 4×4 (15 tile) puzzles. The tiled graphics approach used in the Adafruit [displayio](https://learn.adafruit.com/circuitpython-display-support-using-displayio/introduction) library is ideally suited for a sliding puzzle game.

The puzzle images are interchangeable.

[See this blog post for all the details](http://www.mcgurrin.info/robots/642/). Well done!

![PyBadge showing scrambled puzzle](https://www.mcgurrin.info/robots/wp-content/uploads/2019/12/IMG_20191224_183112-300x225.jpg)