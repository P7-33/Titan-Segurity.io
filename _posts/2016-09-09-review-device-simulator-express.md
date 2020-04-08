---
title: 'Review: Device Simulator Express emulates a Circuit Playground
Express #CircuitPlaygroundExpress @MSFTGarage @Adafruit'
date: 2019-10-02T15:46:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-5.png)

Last month, Microsoft Garage, in collaboration with Adafruiit, created  [Device Simulator Express,](https://aka.ms/GetDSX) a Visual Studio Code extension that enables developers to program the Adafruit Circuit Playground Express in CircuitPython, with or without a physical device.

The initial [Adafruit blog post is here](https://blog.adafruit.com/2019/08/29/meet-device-simulator-express-pythonsim-a-msftgarage-project-built-by-garage-interns-that-makes-it-easier-to-program-the-adafruit-circuit-playground-express-in-python-with-or-without-a-physica/) describing the initial availability.

Here we’ll quickly outline the installation and use of the simulator.

The software consists of a download available through the [Visual Studio Marketplace](https://marketplace.visualstudio.com/). It is open source under an MIT license. The prerequisite software needed is quite extensive:

> The following dependencies are required to install before launching Device Simulator Express.  
> You will be prompted to install the Python dependencies during the first use.
> 
> *   _**[Visual Studio Code](https://code.visualstudio.com/)**_
> *   _**[Node](https://nodejs.org/en/download/)**_
> *   _**[Python 3.7.4](https://www.python.org/downloads/)**_: Make sure you’ve added python and pip to your PATH in your environment variables.
> *   _**[Python VS Code extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python)**_: This will be installed automatically from the marketplace when you install Device Simulator Express.

The following dependencies can be installed for you by the extension by clicking yes when you are prompted to (**except** `pywin32` which is needed only on Windows platform).

*   _**Playsound**_  
    install by typing the following commands in a console: `pip install playsound`
*   _**Pywin 32**_  
    install by typing the following commands in a console (only for Windows computers, you must run it manually): `pip install pywin32`
*   _**Python-Socketio**_  
    install by typing the following commands in a console: `pip install python-socketio`
*   _**Requests**_  
    install by typing the following commands in a console: `pip install requests`
*   _**Application Insights**_  
    install by typing the following commands in a console: `pip install applicationinsights`

It would be nice if all this software were bundled into a Docker container or similar. Experience using the command shell/console is needed to use pip. Adding pip and python to ones PATH is explained in a footnote.

Running the Simulator
---------------------

After installation,  there is a code window on the left for CircuitPython and a simulated device on the right. This is somewhat similar to Microsoft MakeCode but with code and simulator flipped.

!["New File" animation](https://www.microsoft.com/en-us/garage/wp-content/uploads/sites/5/2019/08/newFile.gif)

The Ctrl-shift-P then type the command is not as straightforward as a menu selection. Perhaps this could be integrated into the VSC menu system at some point?

Use is great, you can paste in some example code and watch it work. And with the growing popularity of Visual Studio Code as an open framework for programming in a wide array of languages, adding CircuitPython support and simulation is an impressive step.

Conclusion
----------

Device Simulator Express is powerful software providing simulation of CircuitPython and Circuit Playground Express together.

The software installation is time consuming and use requires some time and multiple packages. The Visual Studio framework makes for powerful workflows but could be daunting for beginners.

For advanced students and professionals, Device Simulator Express may be the way to work with embedded devices and Python without having to have the actual device available. The ability to leverage VSC’s advanced features could save a great deal of time.

For beginners, I still recommend an actual device. That coupled with a good text editor or preferably the Mu editor (open source) provides an excellent experience with little to no software installation and immediate feedback on the device.