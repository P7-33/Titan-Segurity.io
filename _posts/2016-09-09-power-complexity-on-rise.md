---
title: 'Power Complexity On The Rise'
date: 2019-11-17T01:49:00+01:00
draft: false
---

![](https://semiengineering.com/wp-content/uploads/2018/11/iStock-532174758.jpg "   Power Complexity On The Rise 		    	")  

New chip architectures and custom applications are adding significant challenges to chip design and verification, and the problems are becoming much more complex as low power is added into the mix.

Power always has been a consideration in design, but in the past it typically involved different power domains that were either on, off, or in some level of sleep mode. As hardware architectures shift and hardware becomes more tightly intertwined with software — in part due to the reduced benefits of device scaling and in part to meet new market demands, the number of possible states, potential interactions, and possible variables is exploding.

“When we add low power into the requirements, we’re basically modifying the operation of the entire chip’s functionality for a completely orthogonal purpose, saving power, and the best power-saving algorithms are quite intrusive,” said Gordon Allan, product manager at [Mentor, a Siemens Business](https://semiengineering.com/entities/mentor-a-siemens-business/). “They modify the behavior in multiple ways at multiple levels, so that whenever some piece of the chip is unused, we can turn it off or we can stop its clock or we can reduce its frequency. All of those different techniques are available to squeeze the low power out of our devices.”

The problem is this interferes with the regular operation of the device, and it creates [verification](https://semiengineering.com/knowledge_centers/eda-design/verification/functional-verification/) issues that never existed before.

“It adds another dimension to our design verification from the stimulus viewpoint,” Allan said. “We want to create interesting stimulus that can flush out the bugs. This means taking our existing stimulus for the main functionality of the device, adding some additional stimulus for what can change in the low power setup of the device going into the low power modes — going to sleep, waking up, turning clocks on and off, turning voltage on and off — all of those things that can happen on the side. Now we need to modulate our main stimulus with additional input with the goal to flush out where the bugs are often deeply buried in in a hierarchy or deeply buried in a pipeline somewhere.”

It’s not sufficient just to run the test with the clock on and then off. For example, what happens when low-power events are used to disrupt the operation of a device?

“Low power design techniques are exponentially growing, and they are becoming necessary for all the top semiconductors for the devices around us,” said Namit Gupta, group director for application engineering at [Synopsys](https://semiengineering.com/entities/synopsys-inc/). “If you look at, for example, a conversation on a mobile phone, or when we use a mobile phone for audio, after a few seconds or a minute you will notice that the screen will either dim or turn off. That is where the low power design techniques are working. The devices are becoming smarter. As more things are being packed into designs, we need to deal with the complexity these low-power design techniques are bringing for the original design functionality.”

The result is that every design team needs to take power much more seriously than in the past, and they need to revisit it throughout the design flow.

“There is obviously the part about low power designs, and how they impact the functionality of the chip in terms of, for example, [clock gating](https://semiengineering.com/knowledge_centers/low-power/techniques/clock-gating-2/) as a technique,” said Preeti Gupta, director of RTL product management at [ANSYS](https://semiengineering.com/entities/ansys/). “There are challenges when you insert a clock gate as it can cause glitching if not handled properly. Or there is [power gating](https://semiengineering.com/knowledge_centers/low-power/techniques/power-gating/) as a technique where you’re adding switches to your design, and how those switches and isolation strategies and retention strategies work. All of these add to the total verification cycles, and when you have [voltage islands](https://semiengineering.com/knowledge_centers/low-power/techniques/voltage-islands/) and [dynamic voltage and frequency scaling](https://semiengineering.com/knowledge_centers/low-power/techniques/dynamic-voltage-and-frequency-scaling/), all of these add to the total verification requirements for a particular chip. There’s no doubt that you need to do more for low power design.”

**Different markets, different challenges**  
What’s changed is that power is touching more designs in more places, and it’s no longer just a matter of performance versus power. It’s both all the time.

“For example, everything you do with memory today in an [IoT](https://semiengineering.com/knowledge_centers/iot-iiot/internet-of-things/) device is driven by an MCU,” said Paul Hill, director of marketing at [Adesto Technologies](https://semiengineering.com/entities/adesto-technologies-corp/). “The MCU has to sit there in idle mode checking it every couple of nanoseconds to see if it’s ready. Reducing [power consumption](https://semiengineering.com/knowledge_centers/low-power/low-power-design/power-consumption/) in the memory is one thing. But if you can reduce the amount of work the MCU has to do, you can save significantly more power.”

That requires much tighter integration with more levels of the software stack because partitioning of data, interoperability and [hardware-software co-design](https://semiengineering.com/knowledge_centers/eda-design/methodologies-and-flows/hardware-software-co-design/) can have a big impact on both performance and power.

“You can’t do any of this without software,” said Hill. “We can add IP to the memory to tell the MCU when a particular process is completed. Then the MCU can go to sleep. When the memory completes the task it wakes up the MCU. That allows the memory to be a bit more intelligent, but the MCU software has to acknowledge that and react accordingly. It’s a mixture of hardware and software.”

Add [AI](https://semiengineering.com/knowledge_centers/artificial-intelligence/)/[ML](https://semiengineering.com/knowledge_centers/artificial-intelligence/machine-learning/) into the mix and that complexity can grow in multiple dimensions. In some of these applications, algorithms are so tightly integrated into the hardware that it is hard to separate one from the other. This has been one of the key tradeoffs in machine learning. The more specialization that is added, the more algorithms can be pruned and tied to specific functionality, the greater the energy savings. Current research is focused on designing algorithms differently to begin with, allowing room for both flexibility and greater efficiency.

“You can get 1,000 times improvement in performance per watt,” said Kunle Olukotun, professor of electrical engineering and computer science at Stanford University, in a recent presentation. “Sparsity can get a model that is just as accurate with less data. The key is how to train a sparse model. In the future, more and more models will become sparse.”

**New use cases**  
These issues become significantly more intertwined when multiple chips are packaged together, because power now needs to be considered across multiple chips. This is particularly true with [chiplets](https://semiengineering.com/knowledge_centers/packaging/advanced-packaging/chiplets/), where much more detailed characterization needs to be included up front so design teams can determine how the various components will work together.

“Compute power is not just one chip, it’s separate chips working together,” said Andy Heinig, group manager for system integration in [Fraunhofer’s](https://semiengineering.com/entities/fraunhofer-iis-eas/) Engineering of Adaptive Systems Division. “This is a good approach for automotive because you have a lot of heterogeneous integration of both analog and digital parts. Automotive today uses many configurations that are available for different chips, but if you can standardize the chiplets, you can have a basic configuration or a mid-range or high-end. That becomes more economical.”

It’s also more power-efficient, because in the past many blocks used in automotive chips were not best of breed. That affects the partitioning of processing power, because a particular block can only perform as well as its design. However, those designs can be much more targeted and granular with chiplets.

“It’s not always clear how many objects you will need to track with technology,” Heinig said. “This is important to understand because the more objects you have, the more power it takes. So in a city you can’t predict how many people are in front of you. But on a highway, you can say how many objects you have to deal with.”

Granularity of designs is one of the big changes, regardless of whether it is inside a chip or a package, and it has a big impact on power. “Let’s say you have a chip that needs to conform within a 10 watt budget,” said ANSYS’ Gupta. “You’re designing and bringing [IP](https://semiengineering.com/knowledge_centers/intellectual-property/) from several different third parties, and you’re designing your own in-house IP, and then you assemble the SoC together. How do you make sure you’re within that 10-watt budget across all modes of operation? I’m looking at, ‘Am I doing enough clock gating? Am I gating my data enough? Do I have enough power gated domains? Do I need more? Do I need less? What do I need to hit my target?’”

**New players, new problems**  
Those targets vary greatly by application, but they also vary by company and by process node.

“One of the ways this has changed over recent years is that a lot of the major semiconductor companies and vertically integrated systems houses are getting more and more into designing high-performance chips, and they’re going onto deeper submicron nodes,” said Pete Hardee, director of product management in the system and verification group at [Cadence](https://semiengineering.com/entities/cadence-design-systems/). “Here, as soon as we got to the [finFET](https://semiengineering.com/knowledge_centers/integrated-circuit/transistors/3d/finfet-3/) nodes, the problem changed and actually moved back to being more about dynamic power than about leakage power.”

Fortunately, the [UPF power standard](https://semiengineering.com/knowledge_centers/standards-laws/standards/unified-power-format/) allows control over components that need to be inserted into the design to manage power gating. “That’s basically switching off various power domains when you don’t need them, which is primarily about controlling leakage power,” Hardee said. “Leakage power became a bigger and bigger issue for planar [CMOS](https://semiengineering.com/knowledge_centers/materials/cmos/) because it gets impossible to fully turn off the transistors. There’s always leakage running through the transistor even when the gate is turned off. That problem actually is addressed by the finFET quite well in that the transistors behave themselves a lot better. You can turn them fully off and leakage is not such a big issue.”

For dynamic power, there are a bunch of different clock domains with separate processing.

“We’re trying to run each sort of calculation or each sort of sub-processing element on these big chips,” Hardee said. “We’re trying to run them at the most efficient clock frequency possible, so we’re seeing an enormous explosion of clock domains in designs in order to be more efficient for dynamic power. This means the whole area of [clock domain crossing](https://semiengineering.com/knowledge_centers/eda-design/verification/clock-domain-crossing/) verification is growing, but it’s also moving from an implementation problem, and often an implementation afterthought, into low power verification. It’s becoming an active concern for [low power verification](https://semiengineering.com/knowledge_centers/low-power/low-power-verification/) currently.”

**Dealing with more variables**  
Taken together, this has a big impact on the whole backend of the design flow.

“We have the traditional verification methods, using [UVM](https://semiengineering.com/knowledge_centers/eda-design/verification/methodology/uvm/) random stimulus sequences, that let us build up libraries of interesting stimuli, and we can add low power into the mix there,” said Mentor’s Allan. “We’ve also have seen success with the [Portable Stimulus](https://semiengineering.com/knowledge_centers/languages/portable_stimulus/) standard, and the use of graph-based verification to create that interesting stimulus in a way which is more efficient.”

These are just some of the approaches being used today to handle a growing number of low-power features that are being added into designs of chips for everything from mobile phones to server chips. On top of that, low power design creates a need for more complex stimuli. There are tools available to bring that added complexity down to size so the engineering team is not suddenly needing to do 10X as much stimulus to add low power into the mix.

The next piece of the puzzle is measuring the effectiveness of the verification.

“Traditionally we refer to being coverage-driven,” said Allan. “So we’re adding a new element to [coverage](https://semiengineering.com/knowledge_centers/eda-design/verification/coverage/) here as well to say, ‘Have we covered all the possible power states in conjunction with operating the design in the way it was intended to?’ We already had a complex coverage plan just for device normal operation. Now we are adding that new orthogonal thing into the mix here so we’re saying we want to cover these traffic states alongside these low power states.”

Tools in this area identify what a low power design looks like based on standards such as UPF, UPF 3.x, which lets designers define very precisely what the low power architecture of their design looks like. In the simulator, this can be interpreted in order to create coverage models and checks from that description that will help to answer that question of whether all of the low power states have been covered, and those can then be crossed with regular coverage points for normal operation of the design. The trick is to verify both the regular functionality and the low power functionality together and not to treat them as separate problems.

As far as the need for checks, these are created automatically from the UPF description, and really do help with verification, Allan said. “There are two kinds of checks that we create: static and dynamic, i.e., runtime in the simulation. Static checks can help to flush out any verification of the design that is just not implemented correctly according to the low power spec, and that can deal with a subset of the potential design errors that can creep into these complex designs. Dynamic checks build upon good stimulus and good coverage models to create a set of assertions that watch for correct operation in the specific areas of low power. A typical low power flow will insert pieces of logic here and there in the chip at the boundaries between clock domains and power domains. There are certain elements that we want to automate the insertion of, so there’s also a need to automate the verification of those. That’s where automated low power checks and coverage come into play. Although these elements were inserted automatically, the designers and the verification engineers shouldn’t ignore their existence because they didn’t design them in manually by hand. They were inserted by the tool, so we want to make them aware of this additional logic so they can debug it.”

To ensure full confidence and thoroughness in low-power design verification, two main challenges exist and must be considered. The first is power intent-based verification for power modes with UPF. The second involves multiple domains changing multiple operating modes simultaneously along with clock-gating and external events.

“Power intent affects implementation as well as modeling,” said John Biggs, senior principal research engineer at [Arm](https://semiengineering.com/entities/arm/). “So in the old days, you had global power and ground. These days you have a network of power and ground, and UPF is a standardized way to describe power intent. You can create a model for a simulator, and you have the same semantics as the implementation, and you can have a soft macro of the intent you’ve already implemented.”

It can be extremely challenging to represent the inter-and intra-power domains with the right set of power domains and power ports. Additionally, the insertion of isolation/level shifters at the right boundary is critical to verification, but challenging. To mitigate these challenges, it is important to incrementally develop and enhance UPF files for power intent, and to verify power intent of the design hierarchically at the start of the design and throughout all levels of design.

Further, for power management functional features with respect to operating modes, the challenge is to cover all aspects of simultaneous domain state changes crossed with external events such as interrupt etc., and clock gating. Random stimulus for simultaneous operating mode changes and stressful internal events, such as simultaneous memory access and swipe of external events and clock gating, provides 100% coverage giving high confidence for power management feature quality.

And all of this begs the question as to why low power techniques like clock gating make verification difficult. ANSYS’ Gupta said that adding logic to the clock path is always a challenge due to the impact on timing particularly for high performance designs. “While AND/OR-based clock gates are prone to glitches and need additional checks, latch-based designs eliminate glitches but add more complexity in static timing analysis.”

**Conclusion**  
With so many considerations and options to approach low power verification, there is one thing designers should keep in mind when approaching a new project.

“One of the most important things about low power design is not to overdo it,” she said. “We recently met with a vice president of engineering for one of the semiconductor companies who said his team added 16 power-gated domains onto the chip. He wanted to know if he actually needed that many because it was impacting the verification cycles. As such, when low power designs are being crafted, it’s important to know what the application is, what the target is, and then design to that, rather than create the most power-efficient design. That can be a good goal, but it may not be necessary.”

**—Ed Sperling contributed to this report.**

Related Stories  
[Using Emulators For Power/Performance Tradeoffs](https://semiengineering.com/using-emulators-for-power-performance-tradeoffs/)  
Chip design’s big iron is moving further forward in the design cycle.  
[3D Power Delivery](https://semiengineering.com/3d-power-delivery/)  
The design of the power delivery network just got a lot more complicated, and designers can no longer rely on margining when things become vertical.

  
  
from Hacker News https://ift.tt/33LeIR8