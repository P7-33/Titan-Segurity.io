---
title: 'The NASA/ESA Solar Orbiter: flying SPARC
processors #Space #Microprocessor #CPUShack @Microchip'
date: 2020-02-12T15:48:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-29.jpg)

Two things about putting computing in space: it takes a long time to do so and all the radiation in space (especially near the sun) can fry regular silicon chips. The [CPUshack Museum writes](http://www.cpushack.com/2020/02/09/esa-solar-orbiter-when-sparcs-fly/) about a new satellite using an old CPU architecture just lifting off:

The [successfully launched](https://www.esa.int/Science_Exploration/Space_Science/Solar_Orbiter), joint NASA/ESA Solar Orbiter mission lifted on a ULA Atlas 5 Rocket out of Florida, USA.  This mission was a long time coming for the ESA: the mission was originally baselined in 2011 and hoped to launch in…2013…then 2017..then 2018 and finally a launch date in 2020.  The original proposal dates to the late 1990’s as a mission to replace the joint NASA/ESA SOHO Solar mission that had launched in 1995.

This is one of the main reasons for it being powered by a computer that by today’s standards is rather dated: using the SPARC architecture!

> The Solar Orbiter is powered by a processor designed by the ESA, the ERC-32SC.  This is the first generation of processors designed by the ESA.  It is a SPARC V7 compliant processor running at 25MHz and capable of 20MIPS.  The ERC-32SC is a single chip version of the original ERC-32 which was a MCM (Multi chip Module) containing 3 dies that made up the processor (the Atmel/Temic TSC691 Integer Unit TSC692 FPU and TSC693 Memory Controller) that was made on a 0.8u CMOS process.  The Single chip version was made possible by a processes shrink to 0.5u.  It was also made by Atmel,  (whom acquired Temic) and is commercially known as the TSC695 as it is designed for space use, is capable of handling a 300krad Total Ionizing Dose of radiation.

![ESA ERC-32SC](http://www.cpushack.com/wp-content/uploads/2020/02/2020-02-09_1552-300x209.png)

The original specifications for this processor were developed back in the 1990’s, which is why it is a SPARC V7, equivalent to the very first Sun SPARC workstations of the late 1980’s!

> The Solar Orbiter caries with is 10 different scientific instruments, and each of them has their own processing subsystem, 9 of which are powered by LEON SPARC processors.  Its common for the main processor of a spacecraft to be the most powerful, but in this case the instruments each possess their own processor more powerful then that of the main spacecraft computer.   This is in large part due to many of these instruments being designed well after the original spacecraft bus and systems were baselined.

For further design details, see the CPUshack Museum’s excellent [article](http://www.cpushack.com/2020/02/09/esa-solar-orbiter-when-sparcs-fly/).

For more information on the Solar Orbiter, [see the ESA website page](https://www.esa.int/Science_Exploration/Space_Science/Solar_Orbiter) on the spacecraft.

![](https://www.esa.int/var/esa/storage/images/science_exploration/space_science/solar_orbiter/20811061-7-eng-GB/Solar_Orbiter_pillars.png)