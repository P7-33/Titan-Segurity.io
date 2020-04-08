---
title: 'A scenario in which the Euler fluid equations fail'
date: 2019-12-19T05:46:00+01:00
draft: false
---

![](https://d2r55xnwy6nx47.cloudfront.net/uploads/2019/12/Vortex-Collision_1200_Social.jpg "Quanta Magazine")  

Mathematicians have suspected for years that under specific circumstances, the Euler equations fail. But they’ve been unable to identify an exact scenario in which this failure occurs. Until now.

The equations are an idealized mathematical description of how fluids move. Within the confines of certain assumptions, they model the way ripples propagate on a pond or how molasses oozes out of a jar. They should be able to describe the motion of any fluid under any circumstances — and for more than two centuries, they have.

But a new proof finds that under certain conditions, the equations fail.

“A year and a half ago I would have said this was something maybe I wouldn’t see in my lifetime,” said [Tarek Elgindi](http://www.math.ucsd.edu/~telgindi/), a mathematician at the University of California, San Diego and author of the new work.

Elgindi proved the existence of the flaw in the Euler equations in two papers posted online this year — [one in April](https://arxiv.org/abs/1904.04795), which he wrote by himself, and [one in October](https://arxiv.org/abs/1910.14071), which he wrote with [Tej-eddine Ghoul](https://nyuad.nyu.edu/en/academics/divisions/science/faculty/tej-eddine-ghoul.html) and [Nader Masmoudi](https://www.math.nyu.edu/faculty/masmoudi/). Together, the papers have upended centuries of assumptions about these famed fluid equations.

“I think it’s a great, wonderful achievement,” said [Peter Constantin](https://web.math.princeton.edu/~const/), a mathematician at Princeton University.

Elgindi’s work is not a death knell for the Euler equations. Rather, he proves that under a very particular set of circumstances, the equations overheat, as it were, and start to output nonsense. Under more realistic conditions, the equations are still, for now, invulnerable.

But the exception Elgindi found is startling to mathematicians, because it occurred under conditions where they previously thought the equations always functioned.

“In general, I think people are quite surprised by Tarek’s example,” said [Vlad Vicol](https://cims.nyu.edu/~vicol/), a mathematician at New York University.

Euler’s Blowup
--------------

Leonhard Euler discovered the fluid equations that now bear his name in 1757. They describe the evolution of a fluid over time, just as Newton’s equations describe the motion of a billiard ball on a table.

More exactly, the equations specify the instantaneous movement of infinitesimally small particles in a fluid. This description includes a particle’s velocity (how fast it’s moving and in which direction) and the related quantity known as its vorticity (how fast it’s spinning, like a top, and in which direction).

Collectively, this information forms a “velocity field,” which is a snapshot of a fluid’s motion at a given moment in time. The Euler equations start with an initial velocity field and predict how it will change at every moment in the future.

The Euler equations are not a literal description of a real-world fluid. They include several nonphysical assumptions. For example, the equations only work if internal currents within a fluid don’t generate friction as they move past each other. They also assume that fluids are “incompressible,” meaning that under the rules of the Euler equations, you can’t squeeze a fluid into a smaller space than the one it already occupies.

“We can think about the model as a certain idealized world and the equations as the rules of motion in this world,” wrote [Vladimir Sverak](http://www-users.math.umn.edu/~sverak/) of the University of Minnesota in an email.

These unnatural provisos led the mathematician and physicist John von Neumann to quip that the equations model “dry water.” To model the motion of a more realistic fluid with internal friction (or viscosity), researchers [use the Navier-Stokes equations instead](https://www.quantamagazine.org/what-makes-the-hardest-equations-in-physics-so-difficult-20180116/).

“The Euler equations are very idealized. Real fluids have friction,” Constantin said.

But the Euler equations still occupy a venerable place in science. Researchers would like to know whether the equations work unequivocally within this frictionless, incompressible, idealized world — that is, whether they can describe all future states of every possible initial velocity field. Or, to put it another way: Are there fluid motions that these supposedly universal equations can’t model?

“The basic question is: Can the equations always do their job?” said Sverak.

In theory, once you plug in values for the current state of a fluid, the equations will produce exact values for a future state. Then you can plug those new values back into the equations and extend your forecast. Typically, the process works, seemingly as far into the future as you care to look.

But it’s also possible that under very rare circumstances, the equations break down. They could be chugging along, producing outputs that work as future inputs, when things start to go awry and the equations eventually produce a value that they can’t continue computing with. In these situations, mathematicians say the equations “blow up.”

If the Euler equations were to blow up, it would be because they’re amplifying a point’s velocity or vorticity in a very unnatural way. The amplification would be so extreme that in a finite amount of time, the velocity or vorticity at a point would become infinite. And once the equations produced an infinite value, they’d crash and be unable to describe any additional future states. This is because generally you can’t compute with infinite values any more than you can divide by zero. (The values would surpass the speed of light along the way, but in this idealized world that’s OK.)

These fatal infinite values are called “singularities.” When mathematicians ask, “Do the Euler equations always work?” they’re really asking, “Are there scenarios under which the Euler equations produce singularities?”

Many mathematicians believe that the answer is yes, but they’ve never been able to find a specific scenario in which the equations actually blow up.

“You feel that Euler is trying to avoid \[a singularity\]. So far it has managed to,” said Constantin.

The new work does not show that the equations produce singularities under the exact conditions that mathematicians care about most. But it is the closest result yet to that goal. To achieve it, Elgindi considered a simplified model of how fluids move.

Reducing Complexity
-------------------

Mathematicians have many different ways of reducing the complexity of the fluid motion they ask the Euler equations to model. Many of the most interesting results, like Elgindi’s, involve demonstrating how far you can simplify a fluid’s behavior — meaning how far you can simplify the data you feed into the equations — while still managing to say something meaningful about the equations themselves.

In a real three-dimensional fluid, like the water in a pond, any particle has three axes along which it can move: the _x_\-axis (left or right), the _y_\-axis (up or down), and the _z_\-axis (backward or forward). That’s a lot of freedom of motion. Furthermore, there’s not necessarily any strong relationship between the movement of particles in different parts of the fluid.

“It’s too much to keep track of,” Elgindi said.

In his new work, Elgindi simplifies the job he asks the Euler equations to handle. He requires that the fluid exhibit symmetry around the _z_\-axis, something you wouldn’t generally find in a real fluid. This symmetry makes it easier to calculate the velocity field, because you know that points on either side of the _z_\-axis are mirror images of one another. So if you know the velocity or vorticity at one point, all you have to do is flip the sign of the values and you’ll know the values at a second point.

He also restricts the range of motion available to points in the fluid. Particles are allowed to move in two general directions, either along the _z_\-axis or toward or away from the _z_\-axis. They’re not allowed to spin around the _z_\-axis. Mathematicians say such a fluid has “no swirl.”

“It reduces the problem basically to a two-dimensional one,” Elgindi said.

Finally, Elgindi puts certain additional stipulations on the initial data he feeds into the Euler equations. The data is rougher, in a sense, than the values that describe real-world fluids, and it makes the formation of singularities more likely.

In real life, if you move a very small distance from one point in a fluid to another, the velocity at the second point is very similar to the velocity at the first. Similarly, the vorticities at the two points should be very similar. Mathematicians say that velocity fields with this property are “smooth,” meaning values vary continuously — smoothly — as you move from one point to the next. There are no rapid changes.

That’s not the case in Elgindi’s descriptions of a fluid.

“The vorticity in Tarek’s data can vary more dramatically,” said Vicol. “Close points have vastly different vorticities.”

Elgindi’s simplifications might seem to stray too far from real fluid behavior to be useful. But they’re much milder than many simplified scenarios under which mathematicians have previously gained insights into the Euler equations.

In fact, Elgindi showed that under these simplified — but not too simplified — conditions, the Euler equations start to produce very unexpected results.

Game Over
---------

To understand Elgindi’s discovery, imagine a tank of water. This is slightly misleading, because Elgindi’s work is about fluids that have no boundary, meaning they float like a blob in space. But for the purpose of visualizing the scenario at the heart of his work, it’s useful to situate the water in a tank. The most important mathematical conjectures — and the hardest to prove — involve fluids without boundaries.

Next, picture two thick rings of water at opposite ends of the tank. The rings form like eddies or whirlpools — organized disturbances within the main body of the fluid. They’re a kind of phenomenon that really does occur in nature, and they look like the rings skilled smokers can produce.

Now imagine the opposing rings moving toward each other.

As they advance, the Euler equations are operating normally in the background, calculating the velocity fields that describe the fluid at each moment in time. But when the rings get close to each other, the equations start to report some wild values.

They show the rings attracting each other with greater and greater intensity — and in particular, they show that the innermost parts of the rings are attracting and pulling each other with even greater force than the outermost parts of the rings. As a result, the rings elongate, stretching out to look more like a pair of funnels. As their centers get closer and closer, their speeds get faster and faster. Then they crash.

And if at that exact moment you look at the velocity field describing the collision, you’ll see something no one has seen under this set of assumptions in the history of the Euler equations: a singularity. Elgindi proved that the Euler equations calculate infinite vorticity at the point of collision. Game over.

“The classical form of the equations breaks down,” said Elgindi. “After that you don’t know what happens.”

The result does have some limitations. Namely, it’s impossible to extrapolate from his proof to the behavior of the Euler equations under the completely “smooth” conditions. This is because mathematicians proved decades ago that under smooth conditions, the scenario Elgindi considers does not produce a singularity.

But in other ways, his result completely changes the way mathematicians look at these old equations.

Prior to Elgindi’s work, mathematicians had never proved the existence of any situation, without a boundary, in which the Euler equations worked for a short period of time (when the rings approach each other) but not forever. In all previous work, mathematicians had found that if the equations worked at all, they worked forever.

“It’s quite a remarkable result because it proves there are singularities under a scenario that is what we call ‘well posed.’ It makes sense, and nevertheless you get this finite-time singularity,” Constantin said.

Many generations of scientists have searched for a soft spot in the Euler equations. At last — with qualification — a mathematician has found one.

  
  
from Hacker News https://ift.tt/38Oaj2Z