---
title: 'Building a nano current meter #measurement #EE @technoblogy'
date: 2019-10-11T14:34:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-45.png)

The Technoblogy [blog describes](http://www.technoblogy.com/show?2S67) a simple low-current meter to check the sleep current of different microcontroller circuits, such as ones based on AVR microcontrollers. It’s capable of measuring currents of between 10µA and 30nA with reasonable accuracy, using an ATtiny84 and a few other low-cost parts.

> Measuring very small currents accurately is notoriously difficult with normal digital multimeters; they either don’t provide a low current range at all, or if they do, they create a voltage drop referred to as the “burden voltage” which can render the display inaccurate. One way round this is to use a precision current adapter, such as David L. Jones’s [µCurrent](http://alternatezone.com/electronics/ucurrent/uCurrentArticle.pdf), but such circuits are expensive.
> 
> Since I didn’t need high accuracy I decided that an alternative approach would be to calculate the current draw based on the time it takes a capacitor to discharge. A capacitor discharging into a resistive load is exponential, like radioactive decay. The voltage halves for successive fixed time intervals, so if the voltage starts at 5V, after a certain time t it will drop to half this value, 2.5V. After a further time t it will drop to 1.25V, and so on. The time t is called the half life.
> 
> The half life is log(2) of the time constant RC, or 0.693 x RC. So for a fixed capacitor C, by measuring the time taken for the voltage to drop to 50% of its initial value we can calculate R, the effective resistance of the load, and hence the current consumption.
> 
> Using a microcontroller with ADC inputs it’s easy to do this, and few other components are needed apart from the capacitor; the downside is that measurements of currents in the nanoamps may take a few seconds while the capacitor discharges.

![NanoCurrentMeter.gif](http://www.technoblogy.com/pictures/kvm/nanocurrentmeter.gif)

The circuit is based on an ATtiny84 and a 0.28″ three-digit common anode seven-segment LED display.

See [the blog post](http://www.technoblogy.com/show?2S67) for more details and the [code here](http://www.technoblogy.com/list?2SOK).