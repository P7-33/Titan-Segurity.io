---
title: 'Tiny Drones Navigate Like Real Bugs'
date: 2019-11-07T07:08:00+01:00
draft: false
---

When it comes to robotic navigation, the usual approach is to go as technically advanced and “smart” as possible. Yet the most successful lifeforms that we know of follow a completely different approach. With limited senses and cognitive abilities, the success of invertebrates like ants and honeybees lie in cooperation in large numbers. A join team of researchers from TU Delft, University of Liverpool and Radboud University of Nijmegen, decided to try this approach and experimented with [a simple navigation technique to allow a swarm of tiny flying robots to explore an unknown environment.](https://www.tudelft.nl/en/2019/tu-delft/swarm-of-tiny-drones-explores-unknown-environments/)

The drones used were of-the-shelf [Crazyflie 2.0](https://www.bitcraze.io/crazyflie-2/) micro quadcopters with add-on boards. Sensors consisted of it’s onboard IMU, simple range finding sensors on a [Multi-ranger deck](https://www.bitcraze.io/multi-ranger-deck/) for obstacle detection, and a down pointing optical flow sensor, on a [Flow deck](https://www.bitcraze.io/flow-deck-v2/), to keep track of the distance travelled.  To navigate, the drones used a “swarm gradient bug algorithm” (SGBA).  Each drone in has different preferred direction of travel from takeoff. When an obstacle encountered, it follows the contour of the obstacle, and then continues  in the preferred direction once the path is clear.  When the battery drops to 60%, it returns to a wireless homing beacon. While this technique might not be the most efficient, it has the major advantage of being “lightweight” enough to implement on a cheap microcontroller, an STM32F4 in this case. The [full research article](https://robotics.sciencemag.org/content/4/35/eaaw9710) is available for free, and is a treasure trove of information.

The main application researchers have in mind is for search and rescue. A swarm of drones can explore an unstable or dangerous area, and identify key areas to focus rescue efforts on.  This can drastically reduce wasted time and risk to rescue workers. It is always cool to see complex problems being solved with simple solution, and we are keen to see where things go. Check out the video after the break.

We’ve covered [Crazyflie](https://hackaday.com/2011/04/29/mini-quadrocopter-is-crazy-awesome/) hacks a [number](https://hackaday.com/2012/04/16/tiny-quadcopter-gets-an-update-on-the-virge-of-flying-without-pc/) of [times](https://hackaday.com/2015/07/15/controlling-quadcopters-with-wireless-mouse-dongles/) over the [years](https://hackaday.com/2013/08/22/crazyflie-control-with-leap-and-kinect/), and this time will probably not be the last.

Thanks \[Qes\] for the tip!

  
  
from Hackaday https://ift.tt/2pNafyw  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)