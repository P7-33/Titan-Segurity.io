---
title: 'Tinyland, a Small Dynamicland'
date: 2019-11-17T01:49:00+01:00
draft: false
---

Tinyland is a project I invented in order to explore the ideas behind [Dynamicland](https://dynamicland.org). I’ve been doing a bunch of tiny experiments with a few pals at the [Recurse Center](https://www.recurse.com).

![Pong](https://emmasmith.me/97886829c5f40eafae059a1c73347bae/pong-2.gif)

Tangible UI
-----------

I’m interested to find out what kinds of things we can build when instead of mouse + keyboard + monitor we have physical objects + table.

Instead of looking at a vertical screen, we have a horizontal table. People can sit all around a table. Collaboration is much easier around a table than trying to share a single screen. Monitors divide, tables connect. At least that’s my hypothesis.

Keyboard, mouse, and monitor is really a single user thing. The more people trying to use the same mouse + keyboard + monitor, the worse it goes.

With a table, could this be different? Could you easily have five or six people, all equally engaged, all with the same level of access to the computer?

[![Scientific diagram](https://emmasmith.me/static/627876979b2c7fdf4b6d00850989ef47/b9e4f/diagram.png)](https://emmasmith.me/static/627876979b2c7fdf4b6d00850989ef47/34e8a/diagram.png)

Calibration
-----------

We have an old, cheap webcam and an old, cheap projector pointing downwards at a table, as illustrated by the scientific diagram above. The camera’s image is pretty square, but not nearly square enough to use without some kind of correction. To do this we project markers at the four corners of the projected space. The camera takes a snapshot of the table, projected markers included. [OpenCV](https://opencv.org/) finds the markers — which is semi-easy because they have some distinctive visual characteristics — and captures their coordinates. Now we map the four corners of the raw image to the four corners of our projected space. OpenCV magic helps us out with a function called `findHomography`.

The calibration works best in the dark, so we’re always turning off the lights. 🌜

The objects in our world
------------------------

Tinyland only knows how to recognize objects with an [Aruco marker](http://www.uco.es/investiga/grupos/ava/node/26). When it sees an Aruco marker, it adds it to our current “snaphot” of the world. In the same way that you can get the mouse’s x and y position in an ordinary web app you can get the x and y position of each marker on the table in Tinyland.

These markers are generally printed by a regular printer, but they don’t have to be. Someone here has been making Aruco markers from linotypes! It’s pretty neat, and very crafty. In the apocalypse if we run out of toner we can rest assured that Tinyland will still work. Phew.

🏓 Apps
-------

Tinyland is a programming environment. Or, at least, it aspires to be. And every environment has apps. Right now we have a few apps in our App Store: **Pong**, **A galaxy simulator**, and a sweet **Alchemy game**. Also a **Hello World**, which helps new Tinyland devs get up and running quickly.

We’re pretty close to the point where folks who know nothing about Tinyland can develop their own apps. I’m really excited to see all the different things we can do with this unusual space, this tangible UI.

![Calibration](https://emmasmith.me/58efff8f3de454b90be6eea6fa95f24f/tinyland-03.gif)

Offline mode
------------

To make things easier on ourselves, we created an “offline” mode that allows us to work on Tinyland without being connected to the camera, projector, and table. We have several videos of sample footage of the table with people moving Aruco markers here and there. We feed these into Tinyland in place of the camera footage. It gives us a nice dependable way of testing our ideas before we plug in.

Next
----

So far, Tinyland only runs one app at a time. It’s pretty neat, but I’m interested in doing something other than big flat video games. I want to try to create my own [Realtalk](https://harc.ycr.org/project/realtalk/), the OS that powers Dynamicland. I really know very little about how it works other than the [occasional clue](https://rsnous.com/posts/notes-from-dynamicland-geokit/realtalk-cheat-sheet.png) from folks who’ve travelled to Dynamicland. (That diagram originally appeared in [this post](https://rsnous.com/posts/notes-from-dynamicland-geokit/), which is very good.)

Word on the street is that Realtalk related to Linda, so I’ve been playing around with some of the ideas in [this old paper](https://www.inf.ed.ac.uk/teaching/courses/ppls/linda.pdf).

See you in tuple space! ✨🛰✨

  
  
from Hacker News https://ift.tt/2rOTUtT