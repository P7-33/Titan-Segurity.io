---
title: 'The IBM Pentium 4 64-Bit CPU'
date: 2019-10-02T03:11:00+01:00
draft: false
---

#### [![](http://www.cpushack.com/wp-content/uploads/2019/10/001_chip_big-300x200.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/001_chip_big.jpg)Introduction

This time we will talk about one unique Intel processor, which did not appear on the retail market and whose reviews you will not find on the Internet. This processor was produced purely by special order for one well-known manufacturer of computer equipment. Also in the framework of this article I will try to assemble one of the most powerful retro-systems with this processor.

From the title of the article, I think many people understand that we will talk about the Socket 478 Intel processor

[![](http://www.cpushack.com/wp-content/uploads/2019/10/002_x64_big-300x200.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/002_x64_big.jpg)Most people are familiar with the Socket 478 that replaced Socket 370 at the end of 2001 (we omit Socket 423 due to its short lifespan of less then a year) and allowed the use of single-core, and then with Hyper Threading technology “pseudo-dual” processors that can perform two tasks in parallel. All production Intel processors within Socket 478 were 32-bit, even a couple of representatives from the Pentium Extreme Edition server segment on the «Gallatin» core. But as always there are exceptions. And this exception, or to be more precise, two exceptions, were two models of Pentium 4 processors with the Prescott core, which had 64-bit instructions (EM64T) at their disposal.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/003_sl7qb_big-281x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/003_sl7qb_big.jpg)

Intel Pentium 4 SL7QB 3.2GHz: 64-bits on S478

This pair of processors were commissioned by IBM for its eServer xSeries servers. These processors never hit the retail market and their circulation was not very large, so finding them now is very problematic. It is interesting that the fact that if you want and naturally have the right amount of money, or a large enough order, you can count on a special order of the processor that is needed for the specific needs, with characteristics that will be unique and will not be repeated in standard production products. And it should be noted that not a few such processors have been released, in fact, in the 70’s and early 80’s this was the very purpose of the now ubiquitous ‘sspec.’ Chips with an Sspec (Specification #) were chips that had some specification DIFFERENT from the standard part/datasheet.  A chip WITHOUT a sspec was a standard product.  By the late 1980’s all chips began to receive sspecs as a means of tracking things like revisions, steppings, etc.  I will talk about some a little later.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/016_cpuz-300x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/016_cpuz.jpg)

hat’s how the processor looks through the eyes of the CPU-Z utility. In the “Instructions” field after SSE3, the EM64T proudly shows off! Link to popular CPU-Z [Validation](http://valid.x86.fr/cutmxa).

Special processors made for IBM belonged to the Prescott core and were based on E0 stepping with support for 64-bit instructions, which is not typical for Socket 478! The first 64-bit CPUs for “everyone” appeared only with the arrival of the next LGA775 socket, and even then it wasn’t right away; some Pentium 4 models in LGA775 version were 32-bit. I specifically pointed out that the Pentium 4 Socket 478 model with EM64T support belonged to the E0-stepping, although later the more advanced stepping G1 was released, which did not have such innovations. The first model worked at a frequency of 3.2 GHz and had a SPEC code – SL7QB, the second was slightly faster with a frequency of 3.4 GHz and the SPEC code – SL7Q8.

For the rest, these were the usual «Prescott». But the presence of 64-bit instructions made these processors unique, capable of working with 64-bit operating systems and the same applications, allowing them to do what their 32-bit comrades simply could not do.

#### IBM

[![](http://www.cpushack.com/wp-content/uploads/2019/10/004_ibm_big-300x174.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/004_ibm_big.jpg)Not many companies were able to place their order with Intel, but the «Blue Giant» or IBM could do it, and all in order to defeat HP and Dell in a fierce struggle for the server market share for small and medium-sized businesses. And for one, in order to extend the life of their servers with Socket 478. For these purposes, these two processors were released, capable of executing 64-bit instructions. Another advantage of such processors in conjunction with 64-bit operating systems can be called support for a large amount of RAM, but interestingly, in the age of DDR1 with its small amounts of memory of this standard and chipsets of that time, operating more than four gigabytes of RAM was physically not possible even with 64-bits.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/005_server_big-300x218.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/005_server_big.jpg)So the whole point of using these processors was precisely in supporting 64-bit operating systems and the same software, behind which IBM saw a promising future, as it once was when changing from 16-bit software to 32-bit back in the days of the i386 . And it should be noted they guessed (correctly), that the sunset is approaching the 32-bit era.

I managed to find a processor running at 3.2 GHz with a SPEC code – SL7QB in Canada, so its journey was not close to me. This processor was part of the IBM eServer xSeries 306 server. This server is a regular single-processor 1U blade server that can be installed in a rack. Inside the server, a single Socket 478 was used to hold the Pentium 4 processor, which had support for up to 4 gigabytes of RAM (and the chipset couldn’t see more RAM), two Gigabit network controllers, a pair of 64-bit / 66 MHz PCI-X expansion slots and the ability to support not very sophisticated RAID arrays from SATA-150 or SCSI drives.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/007_306_big-300x246.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/007_306_big.jpg)

Initially, such IBM servers supported conventional 32-bit Pentium 4 processors with Prescott cores, and then the option of using 64-bit Pentium 4 was added. These processors are [listed](https://www.ibm.com/support/pages/system-service-parts-ibm-eserver-xseries-306) under the part number 26K8430 for the server models using the IBM spare parts database (FRU) (41x and 45x).

[![](http://www.cpushack.com/wp-content/uploads/2019/10/008_screen_big-300x221.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/008_screen_big.jpg)

If you look at the motherboard of this server, you can see that it is the simplest solution. In fact, this is dictated by the use of the Intel E7210 chipset, which is a close relative of the desktop Intel 875P, but lacking an AGP port, it uses a pair of PCI-X slots instead.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/006_board306_big-300x255.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/006_board306_big.jpg)

Windows Server 2003, x64 Edition, or various types of Linux were installed on the IBM eServer xSeries 306 server with a 64-bit Pentium 4. Subsequently, IBM expanded the range of its servers, where it was possible to install SL7QB or SL7Q8, among them were models: x206, x226 and x236.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/010_tab1_big-300x264.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/010_tab1_big.jpg)

Thanks to its pricing policy, the cost of new 64-bit servers was very affordable compared to competitors. At the time the updated servers were released (2nd half of 2004), prices for the xSeries 206 model started at $909 for a system with a 3.2 GHz processor and 256 MB of memory, the cost of a more advanced xSeries 306 started at $1,409 for a system with a 3.2 GHz processor and 512 MB of memory.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/009_x206m-150x150.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/009_x206m.jpg)In the server lineup there are also similar models, but with the letter “m” added to the model name. Do not pay attention to them, as these are completely [different](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?infotype=an&subtype=ca&htmlfid=897/ENUS105-415) machines, which are based on processors in a different – LGA775 version.

#### Squeeze everything to the last drop.

In assembling such a system, I wanted to squeeze everything out of it possible! and even more. But I ran into a number of problems both hardware and software. My goal was: 8 GB RAM + Windows 10 x64. But here a number of nuances arose.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/043_direct-150x150.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/043_direct.jpg)Let’s start with the hardware problems. 4 GB of RAM are easily supported by all the boards, even with DDR1 you can get 4 GB on four slots with four sticks of one gigabyte each. But it is boring and not interesting. DDR2 opens up much more promising horizons, but here a problem arises, often suitable motherboards offer only 2 memory slots. A simple solution to install 2 strips of 4 GB. But the creator (Intel) introduced its limitations, I will dwell on them a little more in detail.

Often questions arise about installing more than 4 GB of memory on the relatively “recent” Intel chipsets with an external memory controller (Memory Controller Hub, MCH). Here we briefly consider the necessary conditions for this, since it is not always that the maximum possible amount is written in the manual for the board. Perhaps many believe that it is necessary to have an x86 processor with support for 64 bit expansion (EM64T), and a board that, in principle, allows you to install more than 4 GB of memory (supporting a sufficient number of slots and memory densities, this depends not only on the chipset, but also on specific board). And of course, a BIOS that can initialize this memory, correctly configure the mapping of PCI devices, and so on. Not all motherboards have a BIOS capable of doing this, but all because there were no 64bits on Socket 478 and all of the above motherboards from which the choice was made are transitional models, since their chipsets existed in LGA775 as well, and were already familiar with the 64-bit CPU architecture from Intel.

**CPU:** In fact, for addressing more than 4 GB of memory, a 64-bit x86 processor is generally not required, since starting with Pentium Pro, the ability to expand the physical address (PAE) to 64 GB has been introduced (address lines A32 # – A35 # have been added), but at the same time each task can address no more than 4 GB. However, a processor with 64-bit mode allows you to get the most benefits from RAM over 4 GB, and there will be much less problems with the operating system and drivers than in PAE mode. Note that the width of the address lines for 64-bit processors under LGA775 and even Xeon under LGA771 remained the same (36 bit), that is, they still have a maximum of 64 GB of memory, like Pentium Pro. Isn’t it true that the potential laid down in 1995 is impressive?

**Chipset:** The chipset must be able to address the address space abroad 4 GB, and this feature is not directly related to the supported DRAM organizations, since memory is understood in the broad sense here – this is all the address space available to the processor, in particular, the memory of PCI devices, BIOS, APIC etc. To do this, you must have at least one additional address line on the chipset. That is, the presence of the HA32 # line will provide addressing up to 8GB, HA33 # up to 16GB, HA34 # up to 32GB, and HA35 # up to 64GB.  
And if the server chipsets from Intel (for S603/604/771) have no special problems with addressing, then a study of datasheets for Intel’s desktop chipsets showed that Intel’s first desktop chipset with support for advanced addressing is 955x . Earlier 865, 915, 920, 945 have an older address line HA31 #, that is, physically impossible to install more than 4 GB of RAM in the motherboards on these chipsets.

To summarize, the success of the whole undertaking in the hardware implementation consists of the correct BIOS that “understands” all available RAM + 64-bit Processor + Chipset no older than Intel 955x. But, there is one more nuance, this is the manufacturer of the final motherboard, which, even with a good combination of all circumstances, decided to save money and simply did not route the necessary lines from the chipset, and the lower the cost of the motherboard, the higher the risk. And the boards under consideration are from this lower cost range.

Is there a way out? It seems that there is (but to the end I’m not sure due to the lack of the necessary board) and it lies in Socket 478 motherboards based on the Intel G31 / G41 chipset. There are [enough](https://www.youtube.com/watch?v=YZKm9bRhvC0&feature=youtu.be) examples of working with 8 GB of RAM on motherboards based on the G31 chipset performed by LGA775, but I haven’t seen Socket 478, but as they say there’s a chance =) I’ll leave this for the near or distant future.

**[![](http://www.cpushack.com/wp-content/uploads/2019/10/048_soft-300x237.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/048_soft.jpg)Software problem:** As I wrote above, the ultimate task was to launch Windows 10 x64. At the moment, I have not been able to do this, one cannot cope here, but theoretically it is possible. Windows 7 x64 ran with a bang, no problems arose. But already with the installation of Windows 8.1 there were problems, or rather, there was only one problem – the lack of the NX-bit’s processor, and without this «feature» installation of a modern OS is impossible.

The fact is that NX-bit support is very different for x86 in 32-bit mode, x86 in 64-bit mode and PAE mode. For 32-bit mode, the good old PAE and NX bits via CPUID. That is, basically, you just need to change the value returned to EDX after CPUID with EAX = 80000001h (for example, delete the CPUID check and change the value in EDX to the desired one). NX bit functions are not supported in normal 32-bit mode, and you just need to “calm” the OS. There are software PAE patches for the kernel of the OS where everything works, including Windows 8.1 and early builds of Windows 10.

For 64-bit mode, NX bits are already in use and the NX bit value is located in the 64-bit record of page tables and catalogs (PTE and PDE). The difficulty is that even if you manage to trick the OS by deleting its check of NX bits, then the kernel (and all other drivers / programs) will try to switch the NX bit each time instructions are stored in the page table. This will cause the system to crash. I have, so far, found no confirmation of running Windows 10 x64 on the Pentium 4 Socket 478: SL7QB or SL7Q8, possibly due to the specificity of these processors and their low prevalence, but I want to believe that it will still be possible to do it, not for nothing that I tried out dozens of early builds of Windows 10.

#### We assemble Super Socket 478/x64 PC.

Having such a unique processor at your disposal, it’s absurd not to build a powerful x64-retro system on it. One of the options for using such a system in general can be to build a universal “PC-harvester” that supports all Microsoft operating systems from DOS to Windows 10. And here the most interesting part begins – the selection of components and software. The main component is of course the processor – the heart of the system, it remains to choose a motherboard where it can be installed.

The selection criterion has shifted towards building the fastest system with the fastest interfaces, so there are no AGP slots, only a PCI-Express x16 graphic port, and another PCI-Express x1, and preferably a couple, several PCI, support for DDR2 memory at least, as a variant of DDR3 and the more memory, the better. The list of candidates was as follows:

*   **ASUS P4GD1** (Intel 915P/ DDR1 4Гб DDR-400/ PCI-Express x16, 2x PCI-Express x1, 3x PCI)
*   **Biostar G31-M4** (Intel G31/ DDR2 4Гб DDR2-800 / PCI-Express x16, 2x PCI)
*   **AsRock P4i945GC** (Intel 915P/ DDR1 4Гб DDR2 4Гб DDR2-667/ PCI-Express x16, 1x PCI-Express x1, 2x PCI).

[![](http://www.cpushack.com/wp-content/uploads/2019/10/012_p4gd1_big-300x240.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/012_p4gd1_big.jpg)

ASUS P4GD1

ASUS P4GD1 looks the best in terms of the number of available PCI-Express connectors and configuration flexibility, there is one drawback – this is the first generation DDR memory, all SATA connectors also support only 150 Mb/s.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/013_biostar_big-269x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/013_biostar_big.jpg)

Biostar G31-M4

Biostar G31-M4 looks like a winner due to the support of 800MHz DDR2 memory, the presence of 4 300Mb/s SATA2 ports, but the board is completely devoid of PCI-Express x1 ports and, most importantly, processors with 95 Watt TDP Max are supported, and that means goodbye to “Prescott” which needs more then 95W.  This minus crosses out all available advantages, one of which is support for all operating systems, the presence of appropriate drivers up to Windows 10 x64!

[![](http://www.cpushack.com/wp-content/uploads/2019/10/014_asrock_big-300x250.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/014_asrock_big.jpg)

AsRock P4i945GC

AsRock P4i945GC – the best solution, one additional PCI-Express x1 slot, a pair of PCI, four SATA2 ports. Supported DDR2 memory with a frequency of 667 MHz. After weighing the pros and cons, I settled on the AsRock P4i945GC, also due to the fact that it is much easier to find these days on sale, but finding the ASUS P4GD1 is already a problem.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/044_sys1_big-300x238.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/044_sys1_big.jpg)

For such a system, the use of an SSD is a prerequisite and it is better that it is installed in a PCI-Express slot. The memory capacity is 4 GB, as a video card I decided to use the  GeForce GTX 980 Ti with 6GB, a memory capacity larger than that of the system itself. In a couple of free slots, you can install a couple of 3Dfx Voodoo 2 in SLi, or something “cool” in the PCI version, for example the same 3Dfx Voodoo 5500. The final assembly I got was as follows:

*    Intel Pentium 4, 3.2GHz, Socket 478, «Prescott», SL7QB “64-bit Edition”
*   Thermaltake Big Typhoon
*   AsRock P4i945GC, Intel 945GC + ICH7, Socket 478, PCI-Express , DDR2-667 MHz, SATA-2
*   4 GB (2x 2GB) DDR2 800MHz
*   GeForce GTX 980 Ti, 6GB, KFA2 8Pack Edition
*   SSD HyperX Predator PCIe 240GB
*   Zalman ZM1000-EBT 1000W PSU

[![](http://www.cpushack.com/wp-content/uploads/2019/10/045_sys2_big-276x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/045_sys2_big.jpg)

To the start, let’s go!

[![](http://www.cpushack.com/wp-content/uploads/2019/10/017_bios_big-300x235.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/017_bios_big.jpg)

But first, let’s go into the BIOS of the motherboard.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/018_bios2_big-300x159.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/018_bios2_big.jpg)

The photo shows that the processor is correctly recognized in the BIOS, indicating its 64-bit capacity. And this is how a 240 GB HyperX Predator PCIe x4 drive installed in the PCI-Express x1 slot is displayed in the BIOS.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/019_ssd_big-300x159.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/019_ssd_big.jpg)

I like this solution more than options with SATA options. cables do not get tangles and the appearance of the system becomes more «serious». Let’s see how using just one, instead of the recommended four lanes, PCI-Express will affect the performance of this SSD.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/020_crystal-300x269.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/020_crystal.jpg)

If this result is considered in relation to modern systems, then it is clearly better than any HDD, but loses to modern SSD. But considering that such numbers are available on Pentium 4 on Socket 478!, you can only rejoice at the old man, the responsiveness of the system turned out at a very high level. But you can still connect it to the PCI-Express x4 slot, though you will have to install either a PCI video card or the video card will work in a PCI-Express x1 slot. Another PCI-Express x4 slot is needed on the motherboard =)

[![](http://www.cpushack.com/wp-content/uploads/2019/10/023_cpuzsys_big-300x295.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/023_cpuzsys_big.jpg)

(CPU-Z info – click to enlarge)

I really want to try this monster in practice, but before the test results I will dwell a little on the «not for everyone» processors, this should be interesting.

#### Not like everyone else.

Before starting the tests, I would like to dwell on some processor models, which, let’s say, appeared due to the «efforts» of other companies, and not at the direct initiative of Intel/AMD. First, look into the distant past.

Let’s start with the a Socket 7 AMD processor, which belongs to the K6-2 line on the «CXT» core. A processor with a non-traditional AMD K6-2 38L3054 model name. This processor operates at a frequency of 337 MHz, which is obtained by multiplying the multiplier 4.5 by the system bus 75 MHz. The solution, to put it mildly, is not standard, if you look at the official AMD datasheet, then for the K6-2 processor line you can see different models,

[![](http://www.cpushack.com/wp-content/uploads/2019/10/024_k62docs_big-300x270.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/024_k62docs_big.jpg)

but the 337 MHz model is missing, because it was commissioned by IBM. This is what a processor made for IBM branded PCs looks like:

[![](http://www.cpushack.com/wp-content/uploads/2019/10/025_k62337_big-300x256.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/025_k62337_big.jpg)

AMD K6-2 38L3054 337MHz

As you can see, there is no clock marking on the processor cover. In place of this information there is a marking AMD K6-2 38L3054 (apparently Part number IBM). Below in the photo is a close AMD K6-2 model with a frequency of 333 MHz (3.5 x 95 MHz).

[![](http://www.cpushack.com/wp-content/uploads/2019/10/026_k62333_big-300x254.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/026_k62333_big.jpg)

AMD K6-2 333MHz

[![](http://www.cpushack.com/wp-content/uploads/2019/10/027_x5698_big-292x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/027_x5698_big.jpg)

Xeon X5698

In this case, everything is in place, including information about the frequency of the model.

The following example applies to the LGA1366 socket. The Intel Xeon processor model with the X5698 index, belonging to the «Westemere» microarchitecture, has at its disposal only two cores, while all the other representatives of this server socket have at least four. But then these two cores work at a record clock frequency of 4.4 GHz! and their speed does not decrease under any circumstances, the processor also retained 12 MB of the third-level memory cache. Intel Xeon X5698 was released on special order in limited quantities.

The processor in fact is a 6-core Xeon model, where 4 cores are disabled, but the remaining two are selected at the production stage and are able to operate at that frequency 24/7 at full load. According to one version, these processors were manufactured for the New York Stock Exchange, where at that time the highest core performance was needed, so that multi-billion dollar banking transactions from Wall Street would instantly reach the addressee. The cost of such a processor was set at $ 20,000 apiece. You can find such a processor now, but the cost of a used version will be at the level of the fastest Ryzen 3 R9.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/028_bops44-258x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/028_bops44.jpg)

Intel Black Ops

These processors were installed in pairs, resulting in a workstation with four cores operating at 4.4 GHz, and all this at the beginning of 2011. Each processor had a TDP of 130 watts, and water cooling was clearly assumed. It would be nice to find two of these processors and install them in the EVGA SR-2 motherboard.

Continuing the story of Wall Street, it is worth mentioning an even more interesting processor that replaced the Intel Xeon X5698. A special processor model belonging to the «Ivy Bridge» microarchitecture got its own name, immortalized on the lid of the heat distributor, this is not often seen. The name of this processor is Intel “BLACKOPS”. By special order, Intel has released two “BLACKOPS” models. The first worked at a frequency of 4.4 GHz and had at its disposal 4 cores, but at the same time, all 25 MB of the third-level cache was available.

Finding photos in decent quality of this processor is not so easy. But I managed to find a screenshot of the CPU-Z of this processor. It can be seen below.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/029_bops44z-300x238.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/029_bops44z.jpg)

The x44 multiplier, four cores and a TDP of 250 W, not every VRM motherboard can handle such a processor.

The older model worked at a frequency of 4.6 GHz with six active cores and 25 MB of L3 cache. Both processors have disabled Hyper-Threading Technology. The processors were installed in motherboards with an LGA2011 socket and had a TDP of 250 W, which naturally implied the use of a factory-built VRM. The presence of 25 MB of L3 cache  indicates that these processors were selected from the most successful 10 core die. I could not find information about the cost of processors, but I think it is not far from the cost of the Xeon X5698, in any case it was clearly 4-digit. More information about these processors, and others of Intel’s special ‘Everest’ series can be found in the [CPU Shack’s Everest article](http://www.cpushack.com/2018/07/03/cpu-of-the-day-the-intel-everest-series/).

[![](http://www.cpushack.com/wp-content/uploads/2019/10/031_p43_big-297x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/031_p43_big.jpg)

Dual marked Pentium 4 3GHz, or 3.4GHz (one would hope it would also run at 3.2GHz)

At the time of the LGA775 Pentium, Core2 Duo and Quad, Intel made some of its processor models specifically for Dell, IBM, and Apple. Since the Intel Pentium 4 550 model was available for all markets, according to SPEC, the SL8BY and SL8BM variants were intended for Dell. In the first case, the frequency from 3.4 GHz was underestimated to 3.2, in the second to 3.0 GHz. This allowed a single processor to be used in multiple build configurations, simplifying the supply chain and logistics for the builder.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/IntelXeonX5570-293GHZ-8M-640-SLBFX-279x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/IntelXeonX5570-293GHZ-8M-640-SLBFX.jpg)

Intel Xeon X5557 SLBFX – Made specifically for Apple for use in the Mac Pro without a heatspreader.

To some extent, the Core 2 Duo E8290 model may be interesting, the model number itself already looks unusual. This 2-core processor operates at a frequency of 2833 MHz and a system bus frequency of 1333 MHz and is based on the Wolfdale core. This processor differs from the usual Intel Core 2 Duo E8300 in the absence of Virtualization technology and Intel Trusted Execution security technology, otherwise they are completely identical. Like its predecessor, the Core 2 Duo E8190 was used in the Apple iMac. This list also includes the Core 2 Quad Q9700 and Core 2 Quad Q9705, which are 167 MHz faster than the well-known Core 2 Quad Q9650, but have only half the level 3 cache, 6 MB instead of 12 for the core 2 Quad Q9650.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/033_9900xe-300x289.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/033_9900xe.jpg)

i9-9900XE

There are still a lot of other processors that came through OEM channels and which it is practically impossible to meet in retail, the most modern processor of this kind can be considered Intel Core i9-9990XE, which Intel did not even set the selling price, since the circulation obviously does not reach 1000 pieces. (the typical minimum order qty)

After a short digression, it’s time to press the «Power» button and launch the slowest x64 Monster.

#### Tests

Tests are a good thing, especially when there is something with what to compare. As part of this experiment, I would not want to compare Prescott with Prescott, I just don’t see the point, and it was not for nothing that I installed the GTX 980 Ti. Below I will give the results of those tests that are sharpened by 64 bits, and also try to play modern games.

Testing was conducted in Windows 7 x64 SP1 using the following software:

*   WinRAR x64 v. 5.40
*   WinRAR x32 v. 5.40
*   Cinebench 11.5 x64
*   Cinebench R15
*   Cinebench R20
*   3DMark 2006 v.1.1.1
*   3DMark 2011 v.1.0.132.0
*   3DMark (2013) v.2.9.6631
*   Far Cry
*   Battlefield 4
*   Crysis 3
*   Rise of the Tomb Raider

**WinRAR v. 5.40 (32/64-bit version)**  
Kb/s (more is better)

[![](http://www.cpushack.com/wp-content/uploads/2019/10/021_winrar-300x254.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/021_winrar.jpg)

The percentage difference is not significant, only 2% faster, but it is also in favor of the 64-bit version

[![](http://www.cpushack.com/wp-content/uploads/2019/10/036_winrar-300x112.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/036_winrar.jpg)

It also gives you a reminder that the 64-bit version is better

**Cinebench 11.5 (32/64-bit version);**  
points (more is better)

[![](http://www.cpushack.com/wp-content/uploads/2019/10/022_cib115-300x254.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/022_cib115.jpg)

Everything here is similar to the previous result, around 2%

**Cinebench R15**  
points (more is better)

[![](http://www.cpushack.com/wp-content/uploads/2019/10/042_r15-300x254.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/042_r15.jpg)

Here it’s already more interesting, since Cinebench R15 exists only in the 64-bit version, so we can say the increase was 100% compared to the usual «Prescott». Therefore, I decided to add some competitors close in importance.  Interesting that the performance rated Athlon 64 3200+ is identical in performance (for once the PR rating is correct it seems)

**Cinebench R20**  
I will not give graphs, I’ll just say that while the test was “spinning”, I managed to drink coffee twice =) I will give only a screenshot with the final result.  This test really rewards multi-core CPUs, so being limited to one core, and a small cache, really hinders it.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/034_cibr20-178x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/034_cibr20.jpg)

**HWBOT x265 Benchmark v.2.2.0 – 1080p**  
FPS (more is better)  
All the difference is visible in the screenshot.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/035_x265_big-272x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/035_x265_big.jpg)

**Geekbench 4 v.4.2.3, Single/Multi-Core Score**  
points (more is better)

[![](http://www.cpushack.com/wp-content/uploads/2019/10/049_geekb4-300x254.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/049_geekb4.jpg)

We pass now to 3D tests =) Will the giant GeForce GTX 980 Ti be able to help? Between them the difference in age is as much as 11 years. Although during the «honeymoon» month, when they were together in a system of serious quarrels between them, it wasn’t a trifle 😉 It’s scary to think if the GeForce RTX 2080 Ti was installed instead of the GeForce GTX 980 Ti.

3Dmark 2006 v.1.1.1, Score

[![](http://www.cpushack.com/wp-content/uploads/2019/10/037_3dm2006_big-298x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/037_3dm2006_big.jpg)

Although the Pentium 4 tried its best, it couldn’t «satisfy» the GeForce GTX 980 Ti. The final result is 4666 3DMarks. In the heart of the HWBOT test I found a similar result on points – 5155, which was obtained on Intel Pentium 4 3.2 GHz Northwood and GeForce GTX 9800GT @ 850/1102 MHz.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/038_3dm2006w_big-300x233.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/038_3dm2006w_big.jpg)

Despite the difference of at least 10 generations, a more powerful video card without processor support could not «pull out» the final result. By the way, the balance of components must be observed under any conditions and at any time, and the GeForce RTX 2080 should not be mixed with four or, God forbid, dual-core CPU.

**3DMark 2011 v.1.0.132 – Performance 720p/ Extreme 1080p**

[![](http://www.cpushack.com/wp-content/uploads/2019/10/039_3dm2011_big-241x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/039_3dm2011_big.jpg)

The final numbers of the result have not changed much, and FPS in a number of subtests froze in place, the video card is clearly experiencing processor hunger. Under equal conditions, the GeForce GTX 980 Ti on modern systems is gaining ~ P20123 and X9123. It’s not difficult to calculate the difference.

**3DMark (2013) Fire Strike/ Extreme**  
In fact, I wanted to launch Fire Strike most of all, the very feeling that «this» works already instills pride and confidence in the future.

[![](http://www.cpushack.com/wp-content/uploads/2019/10/040_fslogo_big-241x300.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/040_fslogo_big.jpg)

Yes, the result, as in the previous case, is extremely small, but it is still there! I think many more users are armed with the GeForce GTX 980 Ti, so you can check the results with your own and be glad how much your system bypasses mine =)

[![](http://www.cpushack.com/wp-content/uploads/2019/10/041_fsrez_big-300x262.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/041_fsrez_big.jpg)

What about the games? Easy, let’s start with the “heavy.”

**Battlefield 4 (Tashgar)**  
Frames/sec (Medium / min / max)

[![](http://www.cpushack.com/wp-content/uploads/2019/10/050_bf4-300x254.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/050_bf4.jpg)

Even despite the high-speed SSD, loading took longer than on a modern PC, but as a result the Tashgar card was chosen, where you can ride a jeep with a breeze. All graphics settings in both resolutions were set to Medium. Although looking at the graph, we can say: Yes, what is the difference 😀 It’s a pity that the FPS did not reach 30 frames per second, I hope that the future overclock will help to reduce the gap.

**Rise of the Tomb Raider**  
An unpleasant surprise awaited me here, the game did not want to start, even despite a couple of reinstallations. After clicking on the shortcut on the desktop, only an error warning appeared What I did not understand the reason for, I can only assume that the launch requires a set of any processor instructions that are not physically available for this processor.

**Crysis 3**  
Here the situation is a little better, it was possible to go to the main menu, select the settings, but they could not advance further the menu, neither the “new” game, nor the loading of existing saves, showed a 3D screen, only a black screen, frozen forever. Why didn’t 3D rendering begin? Perhaps for the same reason as with Rise of the Tomb Raider.

Far Cry (1024×768/1280×1080, Max Quality, demo 3DNews – Research, 2x loop)  
Average result, frames/sec

[![](http://www.cpushack.com/wp-content/uploads/2019/10/051_fc1-300x254.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/051_fc1.jpg)

In higher resolution, greater FPS? It’s just that the video card is tired of working in low resolutions =)

What can be summarized by the 3D component? There is a lack of processor power for this video card. From here it does not matter what settings and what resolution is set. You can tighten up the performance by replacing the RAM with a faster one, by setting timings instead of fives – fours, or even all three. It is possible at such a frequency, but miracles cannot be expected from my “Chinese” kit. It’s better to overclock the processor to at least 3.8 GHz, of course, all 4 GHz, but I don’t know how the motherboard will behave, but I have a desire to try it.

By pure processor power, you need to understand that this is an ordinary “Prescott”, albeit with a tremendous zest under the hood.

#### Conclusion

[![](http://www.cpushack.com/wp-content/uploads/2019/10/047_sys4_big-300x250.jpg)](http://www.cpushack.com/wp-content/uploads/2019/10/047_sys4_big.jpg)

As for the first impressions of the resulting 64-bit system on Socket 478, they are the most positive, even despite the fact that the processor was unable to swing the video card. But as I wrote at the beginning of the article, this assembly claims to be a «for all» role and even for launching DOS games or GLIDE from 3Dfx.

_This article is part of The CPU Shack’s continued partnership with guest author max1024, hailing from Belarus. I have provided some minor edits/tweaks in the translation from Belorussian to English._

  
  
from Hacker News https://ift.tt/2ojImgE