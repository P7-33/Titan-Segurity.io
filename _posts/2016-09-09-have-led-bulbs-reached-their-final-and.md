---
title: 'Have LED Bulbs Reached Their Final (and Cheapest) Form?'
date: 2020-02-16T16:10:00+01:00
draft: false
---

\[electronupdate\] has done a lot of LED light bulb teardowns over the years, witnessing a drive towards ever-cheaper and ever-simpler implementations, and suspects that LED light bulb design has finally reached its ultimate goal. [This teardown of a recent dollar store example](https://electronupdate.blogspot.com/2019/12/dollar-store-led-bulb.html) shows that cost-cutting has managed to shave even more off what was already looking like a market saturated with bottom-dollar design.

The electrical components inside this glowing model of cost-cutting consists of one PCB ([previously-seen dollar store LED bulb examples had two](https://hackaday.com/2017/10/11/dollar-tree-led-bulb-tear-down/)), eleven LEDs, one bridge rectifier, two resistors, and a controller IC. A wirewound resistor apparently also serves as a fuse, just in case.

[![](https://hackaday.com/wp-content/uploads/2020/02/dollar_store_led-0001.jpg?w=400)](https://hackaday.com/wp-content/uploads/2020/02/dollar_store_led-0001.jpg)

Inside the unmarked controller IC. The design is as cheap as it is clever in its cost-cutting.

That’s not all. \[electronupdate\] goes beyond a simple teardown and has decapped the controller IC to see what lurks inside, and the result is shown here. This controller is responsible for driving the LEDs from the ~100 Volts DC that the bridge rectifier and large electrolytic cap present to it, and it’s both cheap and clever in its own way.

The top half is a big transistor for chopping the voltage and the bottom half is the simple control logic; operation is fast enough that no flicker is perceived in the LEDs, and no output smoothing cap is needed. The result, of course, is fewer components and lower cost.

Some of you may recall that back in the early days of LED lighting, bulbs that could last 100,000 hours were a hot promise. [That didn’t happen for a variety of reasons](https://hackaday.com/2019/02/05/what-happened-to-the-100000-hour-led-bulbs/) and the march towards being an everyday consumable where cost was paramount continued. \[electronupdate\] feels they have probably reached that ultimate goal, at least until something else changes. They work, they’re cheap, and just about everything else has been successfully pried up and tossed out the door.

  
  
from Hackaday https://ift.tt/38zmXCd  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)