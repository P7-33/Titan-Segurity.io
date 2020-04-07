---
title: 'Interactive Lorenz Attractor'
date: 2019-12-28T11:10:00+01:00
draft: false
---

![](http://www.malinc.se/m/images/thumbnails/Lorenz200.png "Interactive Lorenz Attractor")  

The positions of the butterflies are described by the Lorenz equations:

\\\[  
\\begin{cases}  
\\dfrac{dx}{dt} = -\\sigma x+\\sigma y \\\\  
\\dfrac{dy}{dt} = -xz+rx-y \\\\  
\\dfrac{dz}{dt} = xy-bz  
\\end{cases}  
\\\]

The red and yellow curves can be seen as the trajectories of two butterflies during a period of time.

For some values of the parameters σ, r and b (like the initial values shown  
above); the butterflies will be attracted to a so-called _strange attractor_ called the Lorenz attractor. Two butterflies  
starting at exactly the same position will have exactly the same path. There is nothing random in the system - it is deterministic.  
Two butterflies that are **arbitrarily close** to each other but not at exactly the same position,  
will diverge after a number  
of times steps, making it impossible to predict the position of any butterfly after many time steps.  
Any approximation, such as approximate measurements of real life data, will give rise to unpredictable motion.  
This behavior can be seen if the butterflies are placed at random positions inside a very small cube, and then watch how they spread out.  
Press the "Small cube" button! Even though the subsequent paths of the butterflies are unpredictable, they don't spread out in a  
random way. It is certain that all butterflies will be on the attractor, but it is impossible to foresee where on the attractor.  
This is an example of _deterministic chaos_.

The Lorenz attractor was first described in 1963 by the meteorologist Edward Lorenz.1 In his book _"The Essence of Chaos"_,  
Lorenz describes how the expression _butterfly effect_ appeared:

> The expression has a somewhat cloudy history. It appears to have arisen following a paper that I presented at a meeting in Washington in 1972,  
> entitled "Does the Flap of a Butterfly's Wings in Brazil Set Off a Tornado in Texas?"  
> ...  
> The thing that has first made the origin of the phrase a bit uncertain is a peculiarity of the first chaotic system I studied in detail. Here  
> an abbreviated graphical representation of a special collection of states known as "strange attractor" was subsequently found to resemble a butterfly,  
> and soon became known as the butterfly.  
> ...  
> Before the Washington meeting I had sometimes used a sea gull as a symbol for sensitive dependence. The switch to a butterfly was actually made by  
> the session convenor, the meteorologist Philip Merilees, who was unable to check with me when he submitted the program titles.  
> ...  
> Perhaps the butterfly, with its seemingly frailty and lack of power, is a natural choice for a symbol of the small that can produce the great.  
>   
> 2

References
----------

1Deterministic Nonperiodic Flow, Edward N. Lorenz, 1963:  
[American Meteorology Society, AMS Journals Online](http://journals.ametsoc.org/doi/abs/10.1175/1520-0469%281963%29020%3C0130%3ADNF%3E2.0.CO%3B2)

2The Essence of Chaos, Edward N. Lorenz, 1993, University of Washington Press, pp 14-15

Made using [three.js](http://threejs.org/)

  
  
from Hacker News https://ift.tt/2t5AhOW