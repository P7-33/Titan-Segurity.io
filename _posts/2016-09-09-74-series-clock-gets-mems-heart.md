---
title: '74-Series Clock Gets A MEMS Heart'
date: 2020-01-17T01:17:00+01:00
draft: false
---

\[Erik van Zijst\] has had a long career as a programmer, but lacked an understanding of what was happening at a bare metal level. After building a few logic gates out of transistors to get a feel for electronics, he set out to build a working clock using 74-series logic. [Naturally, it was quite the adventure. ](https://medium.com/@erikvanzijst/a-digital-quartz-clock-from-scratch-a80ec5e427)

The project starts out as many do on the breadboard. The requisite BCD counters and 7-segment displays were sourced, and everything was connected up with a cavalcade of colorful hookup wires. A 32.768 KHz crystal was pressed into service to generate the clock signal, divided down to get a 1Hz output to drive the seconds counter that would then run the entire clock. \[Erik\] then had to learn some more practical electronics skills, to deal with debouncing buttons for the time setting circuit.

With the clock now functional, \[Erik\] decided to take things further, aiming to build something more robust and usable. An automatic brightness control was created using a 555 to run a crude PWM dimmer for the LEDs. Additionally, a PCB was designed to replace the temporary breadboard setup. This led to problems with the oscillator that \[Erik\] couldn’t quite figure out. Rather than continue on the same path, he changed tack, instead replacing the quartz crystal with a modern MEMS oscillator that solved the problem.

It’s a great look at how to construct a working clock from bare logic, and one that serves to remind us just how complex even a seemingly simple device can be. We’ve seen other from-scratch builds before too, [like this 777-transistor clock](https://hackaday.com/2016/06/01/transistor-logic-clock-has-777-transistors/), [or this attractive stacked design.](https://hackaday.com/2018/09/06/transistor-logic-clock-gets-stacked-up/) Video after the break.

  
  
from Hackaday https://ift.tt/2FZ6sTe  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)