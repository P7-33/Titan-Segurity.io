---
title: 'Performance variation in ‘identical’ processors'
date: 2020-01-06T01:38:00+01:00
draft: false
---

Every microprocessor is different, random variations in the manufacturing process result in transistors, and the connections between them, being fabricated with more/less atoms. An atom here and there makes very little difference when components are built from millions, or even thousands, of atoms. The width of the connections between transistors in modern devices might only be a dozen or so atoms, and an atom here and there can have a noticeable impact.

How does an atom here and there affect performance? Don’t all processors, of the same product, clocked at the same frequency deliver the same performance?

Yes they do, an atom here or there does not cause a processor to execute more/less instructions at a given frequency. But an atom here and there changes the thermal characteristics of processors, i.e., causes them to heat up faster/slower. High performance processors will [reduce their operating frequency](https://en.wikipedia.org/wiki/Dynamic_frequency_scaling), or [voltage](https://en.wikipedia.org/wiki/Dynamic_voltage_scaling), to prevent self-destruction (by overheating).

Processors operating within the same maximum power budget (say 65 Watts) may execute more/less instructions per second because they have slowed themselves down.

Some years ago I spotted a great example of ‘identical’ processor performance variation, and the author of the example, [Barry Rountree](https://github.com/rountree), kindly sent me the data. In the weeks before Christmas I finally got around to including the data in my [evidence-based software engineering book](http://www.knosof.co.uk/ESEUR/). Unfortunately I could not figure out what was what in the data (relearning an important lesson: make sure to understand the data as soon as it arrives), thankfully Barry came to the rescue and spent some time doing software archeology to [figure out the data.](https://github.com/rountree/s2)

The original plots showed frequency/time data of 2,386 Intel Sandy Bridge XEON processors (in a high performance computer at the [Lawrence Livermore National Laboratory](https://en.wikipedia.org/wiki/Lawrence_Livermore_National_Laboratory)) executing the [EP benchmark](https://en.wikipedia.org/wiki/Embarrassingly_parallel) (the data also includes measurements from the MG benchmark, part of the [NAS Parallel benchmark](https://en.wikipedia.org/wiki/NAS_Parallel_Benchmarks)) at various maximum power limits (see plot at end of post, which is normalised based on performance at 115 Watts). The plot below shows frequency/time for a maximum power of 65 Watts, along with violin plots showing the spread of processors running at a given frequency and taking a given number of seconds ([my code](http://www.coding-guidelines.com/code-data/rapl-final.R), code+data on [Barry’s github repo](https://github.com/rountree/s2)):

![Frequency vs Time at 65 Watts](http://www.coding-guidelines.com/images/rapl-65watts.png)

The expected frequency/time behavior is for processors to lie along a straight line running from top left to bottom right, which is roughly what happens here. I imagine (waving my software arms about) the variation in behavior comes from interactions with the other hardware devices each processor is connected to (e.g., memory, which presumably have their own temperature characteristics). [Memory performance can have a big impact](https://shape-of-code.coding-guidelines.com/2015/11/18/peak-memory-transfer-rate-is-best-specint-performance-predictor/) on benchmark performance. Some of the other maximum power limits have very different, and benchmark, measurements have very different characteristics (see below).

More details and analysis in the paper: [An empirical survey of performance and energy efficiency variation on Intel processors](http://www2.cs.arizona.edu/~amarathe/papers/marathe_e2sc2017.pdf).

Intel’s Sandy Bridge is now around seven years old, and the number of atoms used to fabricate transistors and their connectors has shrunk and shrunk. An atom here and there is likely to produce even more variation in the performance of today’s processors.

A previous [post discussed the impact of a variety of random variations on program performance.](https://shape-of-code.coding-guidelines.com/2015/02/24/hardware-variability-may-be-greater-than-algorithmic-improvement/)

Below is a png version of the original plot I saw:

![Frequency vs Time at all power levels](http://www.coding-guidelines.com/images/rapl-all.png)

  
  
from Hacker News https://ift.tt/37Aktmj