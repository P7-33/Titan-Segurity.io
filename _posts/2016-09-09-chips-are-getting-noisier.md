---
title: 'Chips Are Getting Noisier'
date: 2019-12-30T06:55:00+01:00
draft: false
---

In the past, designers only had to worry about noise for sensitive analog portions of a design. Digital circuitry was immune. But while noise gets worse at newer process nodes, staying at 28nm does not mean that it can be ignored anymore.

[![](https://i1.wp.com/semiengineering.com/wp-content/uploads/2019/06/Airwaves-iStock-477025960.jpg?resize=300%2C165&ssl=1)

<img src="https://i1.wp.com/semiengineering.com/wp-content/uploads/2019/06/Airwaves-iStock-477025960.jpg?resize=300%2C165&ssl=1" alt="" />

](https://i1.wp.com/semiengineering.com/wp-content/uploads/2019/06/Airwaves-iStock-477025960.jpg?ssl=1)

With [Moore’s Law](https://semiengineering.com/knowledge_centers/standards-laws/laws/moores-law/) slowing, designs have to do more with less. Margins are being squeezed, additional concurrency is added, and attempts are made to optimize designs so that they can run at higher frequencies than in the past. All of these factors potentially raise a variety of noise concerns, any of which can degrade a chip’s performance or cause it to fail.

[Noise](https://semiengineering.com/knowledge_centers/eda-design/noise-2/) is any unwanted, unexpected or unplanned signal that has been introduced into a design.

“As you follow Moore’s law, the voltage levels keep getting closer to the threshold level, which means that the amount of room you have to buffer your signal from the noise ripple gets smaller and smaller as the signal-to-noise ratio goes up,” says Marc Swinnen, product management director at [Cadence](https://semiengineering.com/entities/cadence-design-systems/). “From the digital side there are three principal sources of noise that people deal with. First is signal integrity (SI) noise, which is essentially [crosstalk](https://semiengineering.com/knowledge_centers/eda-design/noise-2/crosstalk/). The second is glitch noise, which is also a form of crosstalk. In SI noise, you are dealing with switching of the victim. The victim is being slowed down or sped up by crosstalk. With glitch, we are talking about a quiescent victim. There is supposed to be no signal on this line and yet there is a bump. The mechanism is very similar. There is a neighboring line that through capacitive coupling is transferring energy onto another wire. If it slows down or speeds up, we call it SI. If it just creates a bump that should not be there, we call it glitch.”

The good news is that both of those are fairly well understood and contained. “It is the third principle source of noise that is really exciting people today, and that is the IR drop problem,” Swinnen said.

One of the biggest sources of noise is voltage variation. “People have talked about process variation for a long time, but we actually see more voltage variation,” adds Jerry Zhao, product management director in the Digital and Signoff Group at Cadence. “This is noise on the [power grid](https://semiengineering.com/soc-power-grids-challenges/). [Power integrity](https://semiengineering.com/2-5d-3d-power-integrity/) will cause more degradation of chip performance. That is not only for the advanced nodes, but we have seen that more and more on the legacy nodes — 28nm and 40nm are having the same problem.”

Some issues are shared between advanced and legacy nodes. “[Analog](https://semiengineering.com/knowledge_centers/eda-design/definitions/analog/)/RF circuits are generally more sensitive to noise than digital circuits,” says Zhimin Li, solutions architect for analog/mixed-signal verification in [Mentor, a Siemens Business](https://semiengineering.com/entities/mentor-a-siemens-business/). “However, with the reduction of supply voltage for advanced nodes or higher density of switching activities, even digital circuits are becoming more sensitive to power and ground noise. Managing the noise in a mixed-signal IC at advanced nodes is becoming even more challenging.”

**Activity increasing**  
These problems historically did not really affect the older nodes. “In the older nodes, you just can’t run at multi-GHz,” says Mo Faisal, CEO of Movellus. “In addition, the distance between two wires that can be switching at those speeds was larger, so you didn’t have to worry about coupling. In 7nm, the distance between two wires can be 10nm and those wires are switching at 3 to 4GHz. There is a lot of coupling.”

But as chipmakers push to do more at older nodes, noise is becoming more of a problem even there. The culprit is an increase in switching activity.

“With the slowing of Moore’s Law, more and more multicore processors have been deployed, each operating wider and wider vector units,” explains James Myers, director of devices and circuits research at [Arm](https://semiengineering.com/entities/arm/). “This means more opportunity to run into power supply noise, which dramatically limits system performance. Stepping suddenly from lower to higher power, such as when a cache is missed or a new core turns on, causes a large current step and parasitic package/board inductance, which means a correspondingly large voltage drop. Processors must be designed to detect and mitigate such events, usually by frequency or instruction throttling. Otherwise, large voltage margins will be required, which could degrade both performance and efficiency. Designing processors with noise in mind will become increasingly important as advanced packaging technologies such as [2.5](https://semiengineering.com/knowledge_centers/packaging/advanced-packaging/2-5d-ic/)/[3D](https://semiengineering.com/knowledge_centers/packaging/advanced-packaging/3d-ics/) continue to pack more compute into a smaller area.”

Agreement is widespread on that point. “Designs are pushing things more,” says Cadence’s Zhao. “You are switching more, which means you are drawing more current. Where does that current go when it gets to the transistor? All the metals, the power grids. That is where the noise comes from. We have to consider how activity on the grid will impact performance or even result in a failed chip.”

That means more care has to be taken with the power delivery network. “The lower levels of metal are just so thin that they are very resistant,” says João Geada, chief technologist at [ANSYS](https://semiengineering.com/entities/ansys/). “This is making timing unpredictable unless you have the ability to have timing be aware of the voltage conditions. You have to perform multi-physics, multi-domain simulation with the ability to co-simulate the behavior of the power grid together with timing.”

What’s becoming apparent is the methodologies of the past are beginning to fail. “In the past, individual paths were of concern,” says Swinnen. “The power grid always has been something that was margined, but as we moved into the low planar technologies all the way down to 28nm, we still looked at things as Vdd – Vss and we could look at where the worst-case simultaneous switching would be.”

That doesn’t work anymore. “\[Chip designers\] over-designed it,” said Zhao. “They had very conservative grids. They would examine the critical timing paths, but it is the voltage-sensitive paths that are the problem. These will cause timing to fail. These are new problems. This problem exists at 7nm, but when we talk to our customers, they are asking the same questions at 28nm. With the existing tools and methodologies, they have been unable to understand what is going on.”

It also becomes more problematic as as reduced, which impacts tolerances. “Large bandwidths and fast data processing are pushing the frequency limits of such SoCs,” said Joao Marques, group manager at [Adesto Technologies](https://semiengineering.com/entities/adesto-technologies-corp/). “At the same time, battery-operated handheld equipment keeps pushing down the power consumption. Such limits are reducing the design margins, and noise coupling from on-die digital processing must be minimized.”

**New approaches**  
The failures being found in chips are often not functional failures. “What is happening is they are getting very low yield at fmax, and that is the surprise,” says Scott Johnson, principal technical product manager at ANSYS. “These are teams that traditionally led the way for their company’s flagship products. These are the best of the best in the biggest design houses and almost everyone of them has had an fmax surprise – either a complete fmax fail or a yield fail at fmax.”

This is not an easy problem to deal with. “On the clock cycle side, there has been the practice of binning,” says Swinnen. “Microprocessors have used that for years. But with voltage it is more difficult, because while you can have multiple clock speeds for your processors, it is more difficult to specify the required voltage that the chip must operate at. IR-drop failures are not new. We have seen them since 90nm, but they are increasing. The worrying thing to focus on is these failures went through the standard signoff procedures for IR drop analysis and failure analysis, passed all the tests, and yet fail in the field. The methodologies we have in place are insufficient or unreliable.”

Dealing with power noise requires a [methodology](https://semiengineering.com/knowledge_centers/eda-design/verification/methodology/) change. “It is no longer a decoupled problem,” says Geada. “You cannot design the power grid independent of the rest of the design, and in particular, the power grid and timing are certainly no longer decoupled. This is not something that can safely be engineered by having timing margins. You have to analyze the behavior of the power grid at the critical timing corners rather than analyzing the power grid and power just from the perspective of what is my peak power for this design and what is my large di/dt events. You also have to analyze the behavior of the power grid with respect to timing, and timing with respect to the power grid.”

Existing tools require an iterative approach. “People are aware that timing depends upon IR drop,” explains Swinnen. “If you have IR drop, your transistors will slow down. But IR drop is also dependent on timing. When you are switching will determine the IR drop and where it occurs. You have a chicken and egg problem, and this has been ignored. Traditionally people run an IR drop analysis tool and they get the IR drop for every cell. Then they do timing with IR drop, and apply these IR drops to every cell and run timing with the de-rated delays on the cells and see if it still works. The problem is this ignores the fact that this time would not have occurred with that IR drop. You have to converge on the solution. It typically takes four or five cycles of looping between STA and IR analysis to converge on a solution where the timing matches the IR drop and the IR drop matches the timing.”

IR drop is dependent on activity. “The obvious answer is that you have vectors that exercise the circuit, which sounds great in theory, but in practice it has proven difficult,” continues Swinnen. “You need a lot of vectors to get good coverage. It is the same thing with IR drop. Do the vectors cover every possible combination and deal with all of the aggressors in every possible way? Of course not. The vectors not only have to be large in number, but we are talking about real operating vectors. The functional test vectors that people typically use are useless. That is not how the circuit will work.”

While new products that take care of these issues are coming to market, others are looking at updating their processes. “If you know which circuits are sensitive to noise, you try to take extra care of them using isolation techniques,” says Movellus’ Faisal. “If you have a high-performance noise-sensitive piece of design, you can put guard rings and trenches around it to isolate substrate noise, and you can isolate the supply so that the digital switching noise is not coming through. Then there are architectural techniques that we provide by using digital circuitry rather than analog.”

Another approach is to deal with the problem as it occurs, rather than trying to design it away. “In-chip sensing solutions support the semiconductor design community’s demands for increased device reliability, lifetime and enhanced performance optimization,” says Stephen Crosher, CEO of [Moortec](https://semiengineering.com/entities/moortec-semiconductor-ltd/). “We see the emergence, within the design community, of circuit control and management to optimize device lifetime, which is able to take into account regional supply and temperature throughout the SoC design.”

Noise has multiple sources and types that significantly impact a chip’s performance. “Not considering noise throughout the design flow, from architecture to final verification, can result in unexpected degradation or failures in silicon,” says Mentor’s Li. “Starting from the system level, noise specifications and budgeting are primarily driven by the application. Here you must also account for the various modes and environments the chip will operate in. Next, an architecture must be chosen based on tradeoffs among noise, linearity, power, area, and other factors. Then, noise budgeting across the sub-blocks are addressed by creating optimal noise targets for each of the sub-blocks. Proper frequency planning for different blocks, for example, can help alleviate noise issue for critical blocks.”

[Advanced packaging](https://semiengineering.com/knowledge_centers/packaging/advanced-packaging/) adds another dimension to the problem. “Noise is a consideration in all aspects of design,” said Olivia Slater, operations and logistics manager at Adesto Technologies. “For example, there is noise coupling from on-die digital processing, as well as in the integration process. When it comes to [systems in package](https://semiengineering.com/knowledge_centers/packaging/advanced-packaging/system-in-package/), there are additional physical considerations that need to be managed, such as noise caused by die stress or the substrate material causing antenna effects. That can lead to issues in RF devices.”

This adds a whole new challenge to designs. “You must consider the frequencies that all of the devices/dies are switching at and ensure that they do not interfere with each other,” says Faisal. “If the processor is in 7nm and runs at 2.4GHz, and there is a WIFI radio that also runs at 2.4 GHz, then you are creating a problem. There will be EM radiation that will go from one device to the other.”

Li provides another example: “EMI can significantly impact the noise performance because it will propagate through either conductive layers in the package or via the air. If you put two LC-tank VCOs on adjacent chips that oscillate at close frequencies, pulling can cause one VCO to oscillate at the same frequency as the other and the phase noise could be degraded. Or even worse, the functionality could deteriorate.”

**Conclusion**  
IR drop is a noise problem that affects many nodes. Even if design teams did not have issues in the past, attempting to cram more functionality into the same die area or increasing the levels of concurrency can result in unexpected behavior.

Most existing tools will fail to identify these problems. Thankfully, new tools are emerging that deal with timing and power noise simultaneously.

_**Related Articles**  
[New Design Approaches At 7/5nm](https://semiengineering.com/new-design-approaches-at-7-5nm/)  
Smaller features and AI are creating system-level issues, but traditional ways of solving these problems don’t always work.  
[Noise Killed My Chip](https://semiengineering.com/noise-killed-my-chip/)  
Which kind of noise is likely to give your next project a headache, and what you can do about it.  
[Power Budgets At 3nm And Beyond](https://semiengineering.com/power-budgets-at-3nm-and-beyond/)  
Research is heating up at 3nm, and things are going to be very tight.  
_

  
  
from Hacker News https://ift.tt/32cXgVu