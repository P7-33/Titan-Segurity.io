---
title: 'Show HN: I''ve made a rotary dial number input, because why not?'
date: 2019-10-14T04:44:00+01:00
draft: false
---

[](https://github.com/victorqribeiro/dial#rotary-dial)Rotary Dial
=================================================================

A [Rotary Dial](https://en.wikipedia.org/wiki/Rotary_dial) for input numbers.

[![RotaryDial](https://github.com/victorqribeiro/dial/raw/master/favicon.png)](https://github.com/victorqribeiro/dial/blob/master/favicon.png)

Live version [here](https://victorribeiro.com/dial)

[](https://github.com/victorqribeiro/dial#how-to-use-it)How to use it
=====================================================================

Click / Touch the disc and drag it until the arrow. When the number reaches the arrow, it will turn red, then let go and that's your number.

[](https://github.com/victorqribeiro/dial#how-to-use-it-on-your-web-app)How to use it on your web app
=====================================================================================================

Include the RotaryDial.js file.

```
<script src\="RotaryDial.js"\></script\>
```

Then create a new RotaryDial

```
const rd \= new RotaryDial();
```

Creating a callback is easy, just define what your function will do with the number it recieves from the RotaryDial.

```
const fucn \= function(number){ alert( number ) } const rd \= new RotaryDial({callback: func}); 
```

By default the RotaryDial has the console.log fucntion as the callback.

[](https://github.com/victorqribeiro/dial#documentation)Documentation
=====================================================================

The RotaryDial accepts a configuration object on it's constructor. The most import parts are the size and the callback. The size will determine the size of your rotary dial menu, and the callback detemines which fucntion will be called when a number is selected. Besides that, there are some color cofigurations you can fiddle with.

**size** - The size of the menu. _Default 400px_

**callback** - The function that will be called when a number is selected. _Default console.log_

**discFillColor** - The disc color.

**discStrokeColor** - The disc border color.

**circlesFillColor** - The circles (where the numbers are displayed) color.

**circlesStrokeColor** - The circles (where the numbers are displayed) border color.

**circlesHighlightColor** - The color that a circle will be displayed when a number is selected.

**textFillColor** - The text color.

**textStrokeColor** - The text border color.

**arrowFillColor** - The arrow color.

**arrowStrokeColor** - The arrow border color.

  
  
from Hacker News https://github.com/victorqribeiro/dial