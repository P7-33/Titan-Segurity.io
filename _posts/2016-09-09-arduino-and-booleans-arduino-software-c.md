---
title: 'Arduino and Booleans #Arduino #Software #C @Device_Plus_en'
date: 2019-11-11T16:02:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-29.png)

[Lasse Efrayim Jespersen writes](https://www.deviceplus.com/how-tos/arduino-and-booleans-the-truth-is-greater-than-zero/) on the use of boolean logic in programming Arduino microcontrollers.

> Binary and boolean sometimes seem like buzzwords, particularly “binary,” but that’s just because people become so fond of this mode of thinking once they get into it. Hint: They’re the cool geeks with Ferraris.
> 
> At the heart of things, binary is a machine thing, and if you want to control machines, especially microcontrollers, then you have to dig into binary once in a while. Especially the Arduino Uno (atmega328p), which has only 2KB SRAM. It’s a lean system that requires you to be clever if you want it to run large programs. Storing large arrays in PROGMEM and EEPROM (flash) will only get you so far.

The post goes into detail on binary numbers, logical operators in programming, and a simple state machine which remembers where it is in doing things.

![prettyStateMachine](https://www.deviceplus.com/wp-content/uploads/2019/10/boolean-arduino-prettyStateMachine_diagram.png)

[See the full post here](https://www.deviceplus.com/how-tos/arduino-and-booleans-the-truth-is-greater-than-zero/).

!['true' && 'false' can coexist](https://www.deviceplus.com/wp-content/uploads/2019/10/boolean-arduino-dual-relay.jpg)