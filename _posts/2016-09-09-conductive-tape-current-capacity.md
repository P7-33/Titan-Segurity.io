---
title: 'Conductive Tape Current Capacity Comparison'
date: 2019-12-09T10:32:00+01:00
draft: false
---

The world of DIY circuits for STEM and wearables has a few options for conductors. Wire with Dupont connectors is a standard, as is adhesive copper tape. There’s also conductive nylon/steel thread or ribbon. Which you choose depends on your application, of course, but as a general rule wire is cheap and ubiquitous while making connections is more challenging; copper tape is cheap and simple to use, but delicate and rips easily, so is best used for flat surfaces that won’t see a lot of stress or temporary applications; and conductive nylon thread or tape is better for weaving into fabrics.

The Brown Dog Gadgets team wanted to respond to a frequent question they are asked, what are the current limits for their Maker Tape (nylon/steel ribbon), so [they ran some experiments to find out](https://www.browndoggadgets.com/blogs/news/conductive-tape-experiment-in-great-detail#_). In the name of Science you’ll see some flames in the video below, but only under extreme conditions.  

You may already have bits of each of these options lying around in your bins, and if you don’t it may be worth it. Each connection option has its benefits.

Wire

Copper Tape

Nylon/Steel Tape

Insulation

Yes, must be removed to connect

None, and adhesive backing is sometimes conductive

None

Solderability

Usually great (not for some wires)

Great

Not at all

Resistance

<.1ohms/ft

<.1ohms/ft

5-15ohms/ft

Reusability

Yes

No

Yes

Flexibility

Yes

No

Yes

Ease of connecting

Crimp, solder, twist, spring, press

Solder, adhesive, press

Twist, tie, spring, press

Cost

Cheap

Less cheap

Least cheap

Application

Any electronics

Temporary delicate projects

Fabrics, less delicate projects

Their scientific process yielded sound results. While not as capable as copper tape, which could easily handle 5A (the limit of their power supply), their Maker Tape endured 3A before the adhesive started to struggle, and at 3.5A the tape acted like a fuse and burned itself out. It was only under very specific unusual conditions that took them a long time to recreate that they were able to get flames. For them this was a huge success, as most of their users are powering their circuits with coin cell batteries and only driving a motor or some LEDs, and this current consumption was at least an order of magnitude greater than most of their use cases. Anyone trying to use the nylon/steel tape at the level that can fry the tape likely knows what they’re doing enough to avoid the potential problem.

Incidentally, if you’re wondering why wire rating is measured in amps and not watts, here’s some physics. `Power = Current * Voltage`, and `Voltage = Current * Resistance`. These are the two formulas we all learn from the beginning of electronics lessons. When it comes to wires, resistance is measured as ohms per length. What we’re interested in is not the power that can flow through the wire, but the amount of power that the wire can safely dissipate before failing as it heats up through its own resistance.

Doing some algebra, `Power dissipated by the wire as heat = Current*Current*Wire Resistance*Length`. We don’t need the voltage. But also notice that if the length doubles then the power dissipated by the wire doubles but so does the amount of surface area of the wire to dissipate that heat. If you were to rate a wire by power, you’d have to include the length. To simplify things and keep the length out of the rating, and relate the rating back to how much energy is transferred across the wire (and not dissipated by it), and since source voltage doesn’t matter, the wire is thus rated with the amount of current.

  
  
from Hackaday https://ift.tt/33ZCo3v  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)