---
title: 'Intel Has PCIe 4.0 Optane SSDs Ready, but Nothing to Plug Them Into'
date: 2020-01-06T04:08:00+01:00
draft: false
---

![Intel Alder Stream second-gen Optane SSD. Image taken by Nathan Kirsch, Legit Reviews, during Intel demonstration](https://vanilla.futurecdn.net/tomshardware/media/img/missing-image.svg)

Intel Alder Stream second-gen Optane SSD. Image taken by Nathan Kirsch, Legit Reviews, during Intel demonstration (Image credit: Nathan Kirsch / Legit Reviews)

In an interesting revelation that could give us some insight into how Intel's processor and storage roadmaps converge, even if forcibly, the company's Technical Marketing Performance Engineer Frank Ober [recently posted to Twitter](https://twitter.com/fxober/status/1209277330067058688) that the next-gen Optane SSDs would support the PCIe Gen 4.0 interface.

Intel teased us with its new "Alder Stream" second-gen Optane SSDs a few months ago but didn't share many details about the new drives, like what type of interface the SSDs would use. We do know the SSDs will come with second-gen Optane media ([details here](https://www.tomshardware.com/news/optane-dimm-workstation-qlc-flash-144-layers-penta-level-roadmap-ssd-665p,40481.html)), which is an important step forward for Intel in the wake of its split with its [ex-manufacturing partner Micron](https://www.tomshardware.com/news/micron-intel-close-imft-deal-october-31,39279.html).

From what we can glean from the posts, Ober has already sampled the drives on one Linux developer, meaning the drives are likely in the final stages of development, and is actively sampling the drives to others. 

These initial Optane SSDs are destined for the data center, but this new revelation also gives us an indication of when we can expect to see new PCIe 4.0 Optane SSDs with second-gen [3D XPoint](https://www.tomshardware.com/news/micron-intel-3d-xpoint-memory,29690.html) for the consumer market.

Image 1 of 3

![](https://vanilla.futurecdn.net/tomshardware/media/img/missing-image.svg)

(Image credit: @fxober on Twitter)

Image 2 of 3

![](https://vanilla.futurecdn.net/tomshardware/media/img/missing-image.svg)

(Image credit: Intel)

Image 3 of 3

![](https://vanilla.futurecdn.net/tomshardware/media/img/missing-image.svg)

(Image credit: Intel)

Given that Intel doesn’t have any processors (aside from the Stratix 10 FPGAs) that support the PCIe 4.0 interface, the developers obviously don't have access to an Intel-driven PCIe 4.0 test platform, so they could be testing with either AMD's EPYC or Ryzen processors to use the new drives at their full potential, or connecting them to Intel platforms with the PCIe 3.0 interface, which should still unlock extra performance from the next-gen SSDs controller and media. 

Given that the drives appear nearly ready for market, that could present a conundrum for Intel as any current sales of its next-gen Optane products would only benefit its rivals (AMD chief among them) that do support the interface. Logically, that means the company might keep its next-gen Optane products off the market, even if they're ready, until it has processors that support the new faster interface.

According to [Intel's latest statements to Tom's Hardware](https://www.tomshardware.com/news/intel-refutes-reports-of-further-roadmap-delays), the company plans to begin production of its PCIe 4.0-equipped 10nm Ice Lake processors in H2 2020, which means we might not see significant volume until several months later. In the interim, Intel will begin production of its 14nm Cooper Lake processors in the first half of 2020, and those chips almost [certainly come with the PCIe 3.0 interface.](https://www.tomshardware.com/news/intel-server-ddr5-pcie-5.0-roadmap-leaked-granite-rapids,39403.html) As a result, it's logical to expect the company to launch the Alder Stream SSDs with the Ice Lake chips in the latter half of 2020 (provided it remains on schedule).

If Intel follows its normal cadence, the consumer desktop SSDs in M.2 and PCIe add-in-card form factors should arrive shortly after the data center models, and that would slot into the expected timeline for Intel's PCIe 4.0-compatible desktop processors.

According to Intel's latest desktop announcements, Tiger Lake ([rumored to have PCIe 4.0](https://www.tomshardware.com/news/intel-gen12-graphics-tiger-lake,40292.html)) lands in 2020, [but those chips appear to be destined for the laptop market](https://www.tomshardware.com/news/intel-tiger-lake-10nm-2020,39299.html). Intel's first PCIe 4.0 chips for the desktop are thought to be [Rocket Lake](https://www.tomshardware.com/news/intel-roadmap-10nm-14nm-gpu-cpu,39163.html), which are rumored to arrive in early 2021.

AMD moved forward to PCIe 4.0 earlier this year with the arrival of its EPYC and Ryzen processors for the data center and desktop markets, respectively, giving the company a big advantage in terms of I/O throughput. 

Meanwhile, Intel has been mired on the PCIe 3.0 interface due to its next-gen architectures being locked behind its transition to the 10nm node. The company does plan to make future architectures portable between nodes, but for now, the company doesn’t have any PCIe 4.0-capable chips, and barring any big unexpected announcements this week at CES, it doesn’t appear the company will support the interface until late 2020 or early 2021.

That’s because supporting PCIe 4.0 on a processor, at least in a meaningful way, isn’t just as simple as bolting on a PCIe 4.0 controller: The internal pathways have to be built to accommodate the increased throughput. There is the odd chance that Intel could support the PCIe 4.0 interface through external means only, such as only through devices connected to the chipset, but that doesn't seem likely. 

In either case, Intel's Alder Stream second-gen Optane drives are apparently ready for sampling to partners, but due the long qualification cycles in the enterprise, particularly when Intel is plowing ahead with a new media, it will likely be quite a while before the company launches the new drives. Regardless if the drives are ready or not, there is very little doubt that Intel would not release the drives until its own PCIe 4.0-capable processors are ready as well. 

  
  
from Hacker News https://ift.tt/37Ct4ES