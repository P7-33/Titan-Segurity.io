---
title: 'Show HN: A 2d game engine in under 1000 lines of C'
date: 2020-02-02T02:13:00+01:00
draft: false
---

[](https://github.com/ryanpcmcquen/basque#basque)Basque
=======================================================

Basque is a top down 2d game engine.

* * *

[![Basque demo](https://github.com/ryanpcmcquen/basque/raw/master/assets/images/basque_demo.gif "Basque demo")](https://github.com/ryanpcmcquen/basque/raw/master/assets/images/basque_demo.gif) [![Basque demo 2](https://github.com/ryanpcmcquen/basque/raw/master/assets/images/basque_demo_2.gif "Basque demo 2")](https://github.com/ryanpcmcquen/basque/raw/master/assets/images/basque_demo_2.gif)

* * *

#### [](https://github.com/ryanpcmcquen/basque#global-keyboard-shortcuts)Global keyboard shortcuts:

↑: Move player North

→: Move player East

↓: Move player South

←: Move player West

q: Quit

e: Toggle edit mode

#### [](https://github.com/ryanpcmcquen/basque#edit-mode-shortcuts)Edit mode shortcuts:

l: Toggle map library

Mouse button 1 (left click): Place tile

Mouse button 2 (right click): Select tile

* * *

### [](https://github.com/ryanpcmcquen/basque#why-do-this)Why do this?

Why not just use Godot/Unity/et cetera? Basque has a very different priority list than these engines. It is _not_ a generic engine. There isn't much here, but it is a good starting point if you are looking to roll your own engine, here is what it does do:

*   Map editing (with an easy to understand plain text format).
*   Spritesheet animation.
*   Background music.
*   Collision detection.
*   Some frame rate limiting (this should be improved).

At this point the engine will start becoming more specific to the game I am building, which is why I see this as the best time to open source it. Since it could be useful to others, either as a starting point, or just as a guide of how to do some things with SDL2. Note that all of the code is not necessarily the best solution to these problems, but it is _a_ solution.

* * *

### [](https://github.com/ryanpcmcquen/basque#basque-currently-requires)Basque currently requires:

*   SDL2
*   SDL2\_image
*   SDL2\_mixer
*   SDL2\_ttf

* * *

### [](https://github.com/ryanpcmcquen/basque#getting-sdl2-installed)Getting SDL2 installed:

#### [](https://github.com/ryanpcmcquen/basque#linux)Linux:

##### [](https://github.com/ryanpcmcquen/basque#apt)apt:

```
sudo apt-get install libsdl2-dev libsdl2-image-dev libsdl2-mixer-dev libsdl2-ttf-dev 
```

##### [](https://github.com/ryanpcmcquen/basque#dnf)dnf:

```
sudo dnf install SDL2-devel SDL2_image-devel SDL2_mixer-devel SDL2_ttf-devel 
```

Or whatever the equivalent package is for your distro.

#### [](https://github.com/ryanpcmcquen/basque#mac)Mac:

```
brew install sdl2 sdl2_image sdl2_mixer sdl2_ttf 
```

#### [](https://github.com/ryanpcmcquen/basque#windows)Windows:

1.  Download the latest VC development files from: [https://libsdl.org](https://libsdl.org)
    
2.  Place the entire contents of `include` and `lib` under `C:\INCLUDE\SDL2`.
    
3.  Copy all DLLs under `lib` to `C:\Windows\System32` and `C:\Windows\SysWOW64`.
    
4.  Repeat for _SDL2\_image_, _SDL2\_mixer_, and _SDL2\_ttf_.
    
5.  Profit.
    

* * *

  
  
from Hacker News https://ift.tt/2OhXIMC