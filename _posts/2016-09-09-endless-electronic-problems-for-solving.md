---
title: 'Endless Electronic Problems For Solving'
date: 2019-10-16T03:05:00+01:00
draft: false
---

We know not everyone who likes to build circuitry wants to dive headfirst into the underlying electrical engineering that makes everything work. However, if you want to, now is a great time. Many universities have most or all of their material online and you can even take many courses for free. If you want an endless pool of solved study problems, check out [autoCircuits](https://autocircuits.org). It can create many different kinds of electronics problems and their solutions.

You can get a totally random circuit, or choose if you want to focus on DC, AC, two-ports, or several other types of problems. You can also alter the general form of the problem. For example, for a DC analysis, you can have it assign circuit values so that the answer is a value such as 45 ohms, or you can have it just use symbols so that the answer might be i4\=V1/4R. You even get to pick the difficulty level and pick certain types of problems to avoid. Just be fast. After the site generates a problem, you have 10 seconds to download it before it is gone forever.

[![](https://hackaday.com/wp-content/uploads/2019/10/dc1.png?w=400)](https://hackaday.com/wp-content/uploads/2019/10/dc1.png)

The problems range from simple to complex so for example our first screenshot is an easy one.

The program provides the solution, but this one is pretty easy — you just have to combine the parallel and series resistances. With symbolic resistances, the values might have been things like R, 3R, and 9R. Or you can pick to have non-integers like 0.23R or even rational numbers like 22/5 as the multiplying factor.

The program has one other cool feature: you can input a SPICE netlist to plug in your own circuits. There are some restrictions. For example, you can only have 10 nodes and there are some strict naming conventions. In addition, all component values will be selected randomly.

For an example of the SPICE function, try this netlist:

V\_1 1 0 AC  
C\_1 1 2  
C\_2 1 2  
R\_1 2 0  
.TRAN Solve V(2,0)

[![](https://hackaday.com/wp-content/uploads/2019/10/ac.png?w=400)](https://hackaday.com/wp-content/uploads/2019/10/ac.png)

The output looks like the screenshot to the right, although yours will almost certainly have different random values:

If like us, you were too lazy to work it out, the output also shows the answer: _v_4(t)=(-4.111 cos(9.4_t_)-4.092 sin(9.4_t_)). Yeah. That’s what we were thinking.

This would be great if you were teaching electronics, too. You could generate an endless amount of homework or quiz questions. \[Stephano\] offers the service for free and uses software ranging from MATLAB, BLAG, and LaTeX to do its magic.

If you want to brush up on Spice and using it for analysis, we’ve [been there](https://hackaday.com/2016/02/29/spice-power/). By the way, the first analysis tool you generally learn is [nodal analysis](https://hackaday.com/2017/05/25/ohm-dont-forget-kirchhoff/) and that would be a good first step to solving these kinds of problems.

  
  
from Hackaday https://ift.tt/2MiCmht  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)