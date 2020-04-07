---
title: 'A hacker rubber ducky payload injector with
CircuitPython #CircuitPython @hacksterio'
date: 2020-02-04T15:49:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-4.jpg)

[Mason posts on hackster.io](https://www.hackster.io/p5g41tmlx/rubber-python-f0d023) an easy way to make a computer USB keystroke injector (commonly called a rubber ducky). This project uses the flexible, affordable [Adafruit Circuit Playground Express](https://www.adafruit.com/product/3333) programmed with your choice of injectables via [CircuitPython](https://circuitpython.org/), the easy to use version of Python for microcontrollers.

> I really love Hak5’s Rubber Ducky. I’ve seen similar projects but none with Adafruit’s CircuitPython. Last year we at India Linux User Group Delhi (ILUG-D) celebrated CircuitPython Day and that was when I first got my hands on Express boards. The best thing about this board is that you got everything on board like Speaker, Mic, Bluetooth, Accelerometer, IR sensor, etc. I really like the fact that it can inject keystrokes via USB, Yea something similar to Rubber Ducky!

Using this device is as easy as eating beans. Just plug it in and it’ll mount itself. Make a new file called `code.py` as CircuitPython will recognize this file as the main file from which it’ll run code. Mason goes on to write a payload text file parser. So a file named payload.txt will be read and the actions taken. Done in just a few lines of modifiable CircuitPython code! And quite a command set.

![](https://cdn-blog.adafruit.com/uploads/2020/02/Capture-1-600x257.jpg)

See the project on hackster.io and [source code on GitHub](https://github.com/nk521/cktpy/blob/master/rubber_python.py).