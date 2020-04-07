---
title: 'Using Mixed Integer Programming to Assign Air Cargo to Flights'
date: 2020-01-27T08:12:00+01:00
draft: false
---

![](https://miro.medium.com/max/1000/1*Pnlkcp6YmYdKaPP2eh_d-g.jpeg "Using Mixed Integer Programming to Assign Air Cargo to Flights")  

Using Mixed Integer Programming to Assign Air Cargo to Flights
==============================================================

In [a previous post](https://flexport.engineering/air-cargo-supply-and-demand-at-flexport-b7c0f980e2cc) we outlined the basics of supply and demand in the world of air freight forwarding, and described the difficult problem of air cargo consolidation. In this post we’ll look at how Flexport uses math and data science to solve this problem and get shipments delivered on time at their lowest possible cost.

Consider a toy scenario where a freight forwarder has ten shipments, a single flight to assign any shipment to, and the only decision to make is whether to assign each shipment to the flight. (In this toy scenario, if we choose not to assign a particular shipment to the flight, assume we can move it some other way.) Each shipment has a volume and a cost, and the flight has a total available volume that cannot be exceeded. (You may recognize this as a simplified [knapsack problem](https://en.wikipedia.org/wiki/Knapsack_problem).) In this case there are 2¹⁰=1,024 possible solutions (actually 1,023 since we wouldn’t send the plane completely empty).

Maybe you could create a spreadsheet to list out each possible solution and choose the one with the lowest cost. But what if you had the same ten shipments but two flights to choose from? Now you have 3¹⁰=59,049 solutions to calculate. For just ten shipments!

A large freight forwarder will have many more than ten shipments and many more than two flights to choose from, leading to trillions upon trillions of possible solutions. Among these, perhaps mere millions are _feasible_, and maybe the traditional spreadsheet method can find at least one feasible solution. But at Flexport we don’t want just the feasible solutions. We want the best solutions, the _optimal_ solutions. How do we find an optimal solution among the countless possibilities? One answer is to use integer programming.

Integer programming is a subfield of discrete optimization, a field of operations research concerned with minimizing some objective function subject to constraints. In our case, we want to minimize total cost subject to getting shipments to the correct destinations on time and not over-filling ULDs. (If you don’t know what a ULD is, go back and read [part 1](https://flexport.engineering/air-cargo-supply-and-demand-at-flexport-b7c0f980e2cc).) In practice, though we desire the optimal solution, we are sometimes unable to get to optimality, and in this case we are happy with a good or close solution. In the post we’ll limit ourselves to a simple model in which we can achieve optimality.

The first step when tackling a problem like this is to consult the literature. The academic community has addressed the freight forwarding domain for years, and we [found](https://doi.org/10.1016/j.cor.2014.11.015) [several](https://doi.org/10.1016/j.trc.2011.08.001) [papers](https://doi.org/10.1016/j.trc.2015.03.028) that closely resembled our problem. We took many of the following concepts and notation from these papers, and we thank the authors for their contributions to the field.

Objective Function
==================

Let’s start by defining an objective function, which will motivate our notation and constraints. We want to minimize cost, and to minimize cost we need to understand the concept of pivot weight, which we explained in detail in [part 1](https://flexport.engineering/air-cargo-supply-and-demand-at-flexport-b7c0f980e2cc). Briefly, pivot weight is the minimum weight that a freight forwarder commits to paying for, regardless of how much weight the forwarder actually tenders. We have a total weight, a pivot weight, an under-pivot rate, and an over-pivot rate. The pivot weight multiplied by the under-pivot rate is a sunk cost, so we can ignore it, and focus only on the over-pivot weight multiplied by the over-pivot rate.

The objective function is to minimize the total cost, which we define as the total over-pivot weight of all shipments assigned to a ULD, multiplied by the over-pivot rate. For example, if ULD 1 is 100 kilograms over pivot, and the over-pivot rate for ULD 1 is $4/kilogram, then the total cost for ULD 1 is $400.

So to begin, we need some notation for over-pivot weight and for over-pivot cost.

Objective function

The total weight of a ULD of course depends on which shipments are assigned to the ULD, and their individual weights. So we need an expression to calculate it that includes these terms.

Total weight
============

The total weight of a ULD is simply the sum of the weights of the shipments assigned to the ULD. How do we indicate that a particlar shipment has been assigned to a specific ULD? For this we need not a parameter, but a decision variable. A decision variable is something that the solver can control and adjust in its effort to minimize the objective function.

But we’re after the total weight, not the count. To get the weight, we can just multiply each decision variable by the weight parameter, and because the decision variable takes the value 0 if it’s not assigned, then the weight will be zeroed out and not included in the total weight. Let’s say the weights for shipments 1 through 4 are 10, 50, 25, and 5. Then the total weight assigned to ULD 3 would be as follows:

In words one would say “yj is the sum over all i of gi xi,j for all j in J.”

Extra-pivot weight
==================

Now that we have total weight, we can apply our formula for extra-pivot weight:

We’d multiply this by the over-pivot rate to get our total charge, in dollars. At first glance this might seem sufficient, but what about the case when the total weight of all the shipment assigned to the ULD doesn’t actually exceed the pivot weight? In that case, extra-pivot weight would be a negative number if we used the formula as is. For example, if pivot weight is 1650 kilograms, and total assigned weight is 1000 kilograms, then extra-pivot weight = 1000–1650 = -650. The objective function would then multiply this by the over-pivot rate, and we’d get a negative dollar amount back, as is if the carrier would pay us for shipping less than the pivot weight.

What we’ve effectively done is to implement the max() function in mathematical programming. a=max(b, c) is simply a>=b and a>=c.

Let’s review what we’ve defined so far:

Every shipment must fly
=======================

At this point, we could code this up in Python (using [Pyomo](https://pyomo.readthedocs.io/), for example) and send it to a solver. If we did, we’d find the solver would assign zero shipments to any flight, and we can quickly see why: The best way to minimize the objective function is to accrue no costs. This leads us to our next constraint: Every shipment must be assigned to a ULD. (For our purposes we’ll extend this to each shipment must be assigned to one and only one ULD, though in reality Flexport can split a shipment across several ULDs and even across several flights.)

With this constraint in place the solver would actually start assigning shipments to flights, but it would simply spread out shipments among all available ULD until the pivot weights were met. Then it would put every remaining shipment into the single ULD with the lowest extra-pivot cost without regard for that ULD’s volume or weight capacities. So the next two constraints we’ll add are volume and weight.

Volume and weight constraints
=============================

A freight forwarding industry veteran will immediately recognize that this constraint does not actually represent reality. Why? Because it treats the cargo as if it can be poured like water into any volume. In reality, cargo is rigid, some of it comes in large cartons, some of it comes in large pallets, some of it is unstackable. 10 cubic meters of such cargo cannot be packed into an arbitrary volume of exactly 10 cubic meters. The way to handle these cases is to run another type of optimization called bin packing to check whether certain volumes will fit inside another volume, but that is beyond the scope of this post.

With those two additional constraints in place, now the solver will assign shipments to ULD respecting max weight and volume while minimizing total cost. But there’s still one problem: We haven’t said anything about assigning to shipments to ULDs that are going to the right destination, or meeting delivery deadlines. Let’s tackle those next.

Origin and destination
======================

  
  
from Hacker News https://ift.tt/2RV31mj