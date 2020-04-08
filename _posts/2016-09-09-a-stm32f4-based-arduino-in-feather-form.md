---
title: 'A STM32F4 Based Arduino in the Feather Form Factor'
date: 2019-12-01T22:06:00+01:00
draft: false
---

\[minh7a6\] loves the Adafruit Feather, but sees some [room for improvement](https://hackaday.io/project/163853-minhf4-an-stm32f4-arduino-compatible-board).

First is the matter of 5V tolerance. While just about everything is available in a 3.3v range these days, sometimes it’s just nice not to have to care. The main controller on the Feather is plenty powerful, but its intolerant pins just wouldn’t do so it was swapped for a chip from the ever popular STM32F4 line.

Then he wanted better energy efficiency when running from battery. In order to achieve this he switched from a linear regulator to a buck-boost converter. He also felt that the need for a separate SWD adapter for debugging seemed unnecessary, so he built a [Black Magic Probe](https://github.com/blacksphere/blackmagic) right in.

He’s just now finishing up the Arduino IDE support for the board, which is pretty cool. There’s no intention to produce this souped up Feather, but all the files are available for anyone interested.

The [HackadayPrize2019](https://prize.supplyframe.com) is Sponsored by:

[  
![Supplyframe](https://hackaday.com/wp-content/uploads/2018/03/sponsor-supplyframe.png?w=300)  
](https://supplyframe.com/)

[  
![Digi-Key](https://hackaday.com/wp-content/uploads/2016/04/sponsor-2016-digikey21.png?w=300)  
](https://hackaday.io/digikey)

[  
![Microchip](https://hackaday.com/wp-content/uploads/2018/07/sponsor-2016-microchip.png?w=300)  
](https://hackaday.io/microchip)

  
  
from Hackaday https://ift.tt/2Rb4ciC  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)