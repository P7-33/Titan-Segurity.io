---
title: 'Show HN: Teapong – A two-player game for fans of Pong and the Utah teapot'
date: 2020-01-25T01:35:00+01:00
draft: false
---

[![](https://github.com/diegomacario/Teapong/raw/master/readme_images/teapong_logo.PNG)](https://github.com/diegomacario/Teapong/blob/master/readme_images/teapong_logo.PNG)

[](https://github.com/diegomacario/Teapong/blob/master/README.md#teapong)Teapong
================================================================================

A two-player game for fans of Pong and the [Utah teapot](https://en.wikipedia.org/wiki/Utah_teapot)!

[![](https://github.com/diegomacario/Teapong/raw/master/readme_images/teapot.png)](https://www.youtube.com/watch?v=qzS9MX50a6k&feature=youtu.be)  
  
_Click on the image above to see a two minute demo of Teapong!_

[](https://github.com/diegomacario/Teapong/blob/master/README.md#technical-details)Technical details
----------------------------------------------------------------------------------------------------

This is the first game that I ever make! 😊

It was written using C++ and OpenGL, and it is currently supported on macOS and Windows.

The external libraries it uses and their purposes are the following:

*   [GLFW](https://www.glfw.org/) is used to interact with the windowing system and to receive inputs.
*   [GLAD](https://glad.dav1d.de/) is used to load pointers to OpenGL functions.
*   [GLM](https://glm.g-truc.net/0.9.9/index.html) is used to perform 3D math.
*   [Assimp](http://www.assimp.org/) is used to load 3D models.
*   [stb\_image](https://github.com/nothings/stb) is used to load textures.
*   [irrKlang](https://www.ambiera.com/irrklang/) is used to play sounds.

The sources of the assets it uses are the following:

*   The 3D models were created using [3ds Max](https://area.autodesk.com/3ds-max-indie/).
*   The textures were created procedurally using 3ds Max and the [Open Shading Language](https://github.com/imageworks/OpenShadingLanguage).
*   The sound effects can be found [here](https://freesound.org/).
*   The background music is Filaments by Podington Bear, and it can be found [here](https://freemusicarchive.org/).

For a more detailed description of this project's code, see [this](https://github.com/diegomacario/Teapong/blob/master/documentation/making_of_teapong.pdf) presentation.

[](https://github.com/diegomacario/Teapong/blob/master/README.md#rules-and-controls)Rules and controls
------------------------------------------------------------------------------------------------------

The rules are simple: the first player to score three points wins!

The controls are as follows:

*   Press Esc to close the game.
*   Press F to toggle between the full screen and the windowed modes. When in the windowed mode, you can manually resize the window using the mouse.
*   Press 1, 2, 4 or 8 to set the number of samples used for anti-aliasing. By default, the game starts with 1 sample. The higher the number of samples, the better the game looks.
*   When in the menu, press Space to start a game.
*   When ready to play, press Space to launch a teapot.
*   The left paddle is controled with G and B, while the right paddle is controlled with Up and Down.
*   Press P to pause the game.
*   Press C to toggle between the fixed and free camera modes. When the camera is free, you can position it using W, A, S, D and the mouse. You can also zoom in and out using the scroll wheel.
*   Press R to reset the camera to its original position.

[](https://github.com/diegomacario/Teapong/blob/master/README.md#running-the-game-without-building-it)Running the game without building it
------------------------------------------------------------------------------------------------------------------------------------------

### [](https://github.com/diegomacario/Teapong/blob/master/README.md#macos)macOS

To run Teapong on macOS, you must follow these steps:

*   Download or clone this repository and open a Terminal window in its root.
*   Execute the following command to install GLFW, GLM and Assimp:

```
$ brew install cmake assimp glm glfw
```

*   Execute the following commands to install GLAD:

```
$ cp dependencies/mac/inc/glad/glad.h /usr/local/include/ $ cp dependencies/mac/inc/KHR/khrplatform.h /usr/local/include/
```

*   Execute the following commands to install irrKlang:

```
$ cp -r dependencies/mac/inc/irrklang /usr/local/include/ $ cp -R dependencies/mac/lib/ /usr/local/lib/
```

*   Download **Teapong\_macOS.zip** from release [1.0.0](https://github.com/diegomacario/Teapong/releases/tag/v1.0.0), open a Terminal in its root directory and execute the following command to launch the game:

### [](https://github.com/diegomacario/Teapong/blob/master/README.md#windows)Windows

To run Teapong on Windows, simply download **Teapong\_Windows.zip** from release [1.0.0](https://github.com/diegomacario/Teapong/releases/tag/v1.0.0) and double click **Teapong.exe**.

[](https://github.com/diegomacario/Teapong/blob/master/README.md#building-the-game)Building the game
----------------------------------------------------------------------------------------------------

### [](https://github.com/diegomacario/Teapong/blob/master/README.md#macos-1)macOS

To build Teapong on macOS, you must follow the same steps listed in the "**Running the game without building it**" section, except for the last one, which you must replace with the following:

*   Execute the following command to build the game:

Thanks to [Daniel Macario](https://github.com/macadev) for writing the Makefile!

### [](https://github.com/diegomacario/Teapong/blob/master/README.md#windows-1)Windows

To build Teapong on Windows, simply download or clone this repository and use the Visual Studio 2019 solution file that is stored in the **VS2019\_solution** directory.

[](https://github.com/diegomacario/Teapong/blob/master/README.md#learning-resources)Learning resources
------------------------------------------------------------------------------------------------------

The following sources of information are the ones that helped me the most while working on this game:

*   The external libraries I used are presented with excellent clarity in [this](https://learnopengl.com/) page.
*   The design pattern I used for game state management was inspired by [this](http://www.ai-junkie.com/architecture/state_driven/tut_state1.html) article.
*   The classes I wrote for resource management were inspired by [this](https://github.com/skypjack/entt/tree/master/src/entt/resource) code.

  
  
from Hacker News https://ift.tt/37ozWpR