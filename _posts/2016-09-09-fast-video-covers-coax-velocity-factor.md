---
title: 'Fast Video Covers Coax Velocity Factor'
date: 2019-10-12T03:04:00+01:00
draft: false
---

We once saw an interview test for C programmers that showed a structure with a few integer, floating point, and pointer fields. The question: How big is this structure? The correct answer was either “It depends,” or “sizeof(struct x).” The same could be said of the question “What is the speed of light?” The flip answer is 186,282 miles per second, or 299,792,458 metres per second. However, a better answer is “It depends on what it is traveling in.” \[KB9VBR\] discusses how [different transmission lines have different velocity factors](https://www.youtube.com/watch?v=SCF15sDD2IM) and what that means when making RF measurements. A cable with a 0.6 velocity factor sees radio signals move at 60% of that 186,282 number.

This might seem like pedantry, but the velocity factor makes a difference because it changes the actual measurements of such things as dipole legs and coax stubs. The guys make a makeshift time domain reflectometer using a signal generator and an oscilloscope.

Working with more manageable imperial units than miles per second, they compute the speed of light is also 11.78 inches per nanosecond. Using that number and their scope, they can use the time a pulse takes to travel its length to compare the cable’s length to the measurement. A 25 foot piece of coax read out as 24.96 feet. A commercial instrument read out 24.87 feet. Pretty good. A time domain reflectometer can also find problems in coax and also tell you about where the problem is.

Keep in mind that these guys are ham radio operators and probably not physicists. So for example, when he casually says that electrons and subatomic particles travel at the speed of light, you might want to fact check that. However, from the radio perspective they know what they are talking about. For the record, we aren’t physicists either, but we are pretty sure anything with mass  such as an electron can’t quite get up to light speed.

The key to building a good time-domain reflectometer by the way lies in fast rise times on the signal injection. We’ve seen quite a few [designs](https://hackaday.com/2015/07/27/hackers-measure-cable-lengths-with-time-domain-reflectometers/) over time. If you think the speed of light measurement is part of the “round Earth conspiracy” feel free to [make your own measurements](https://hackaday.com/2016/09/29/testing-the-speed-of-light-conspiracy/).

  
  
from Hackaday https://ift.tt/2nD5RkD  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)