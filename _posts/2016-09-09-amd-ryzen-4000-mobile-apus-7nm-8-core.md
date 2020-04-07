---
title: 'AMD Ryzen 4000 Mobile APUs: 7nm, 8-core on both 15W and 45W, Coming Q1'
date: 2020-01-07T01:38:00+01:00
draft: false
---

At last year’s CES, AMD showcased its then Ryzen 3000 mobile processors as part of the announcements. In what is becoming a trend, at this year’s CES, the company is doing the same in announcing its next generation Ryzen 4000 mobile processors. This year is a little different, with AMD showing off its manufacturing strategy at TSMC 7nm for the first time in the mobile space. There’s a ton of options on the table, both at 15W and 45W, offering some really impressive core counts, frequencies, and most importantly, design wins. Here are all the details.

On AMD’s desktop processor portfolio, the company released a combination package with 7nm and 14nm chips on it – for the new Ryzen 4000 series, codenamed Renoir, it’s a fully integrated monolithic piece of 7nm silicon, containing 8 Zen 2 cores and up to 8 compute units of enhanced Vega graphics. That’s 2x the core count of the previous generation Ryzen Mobile, but 3 fewer compute units, however AMD has reasons for that decrease and emphasized that due to the process node they can get 8 CUs to perform better than 11 CUs.

[![](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-006_575px.jpg)](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-006.jpg)

The new 8 core / 8 CU chip on 7nm is also very small. AMD wouldn’t let us measure it directly, or take pictures before the keynote, but by putting the chip next to a Zen 2 desktop chiplet, I was able to make out that the new APU is pretty much double the size of a single Zen 2 chiplet, and double 74mm2 is 148mm2 or 150mm2 for a round number. Given TSMC’s defect rate of 0.09 per cm2, this would give a yield around 87%.

AMD is going to be launching two variants of Ryzen Mobile 4000, based around two power points. These will both be based on the same 8-core silicon, and be separated into 15 W hardware, traditionally called the U series, and 45 W hardware, traditionally called the H series. There is a special ASUS-only exclusive of the H series based in 35 W, and we’ll cover that as well. The main reason why AMD can offer the same silicon at two different power envelopes is due to transistor scalability, binning, disabling some of the graphics, and base frequency adjustments. It also means that in 15 W mode, there are different power delivery requirements from AMD’s partners.

The 15W hardware is as follows:

AMD Ryzen 4000 15W U-Series CPUs

_AnandTech_

Cores  
Threads

Base  
Freq

Turbo  
Freq

L2

L3

Compute  
Units

IGP  
Freq

Ryzen 7 4800U

8C / 16T

1800

4200

4 MB

8 MB

8 CUs

1750

Ryzen 7 4700U

8C / 8T

2000

4100

4 MB

8 MB

7 CUs

1600

Ryzen 5 4600U

6C / 12T

2100

4000

3 MB

8 MB

6 CUs

1500

Ryzen 5 4500U

6C / 6T

2300

4000

3 MB

8 MB

6 CUs

1500

Ryzen 3 4300U

4C / 4T

2700

3700

2 MB

4 MB

5 CUs

1400

AMD stated that the Zen 2 design in this chips follows the same CCX layout as the desktop hardware, which means the 8 cores are split into two CCX units which communicate over the internal infinity fabric. AMD has also adjusted the L3 amount, to 4 MB per CCX, which is half that of the consumer desktop line.

[![](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-013_575px.jpg)](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-013.jpg)

With the graphics, there’s a bit more of a granular compute unit deficit as we go down the stack, and that’s an important way to differentiate the hardware similar to the CPU side. If you notice, the frequencies are super high – AMD said that this enhanced version of Vega, architected for 7nm, actually responded really well in terms of frequency and power, and so they were able to boost the clocks up a lot. So despite the drop from 11 CUs in the silicon design down to 8 CUs, the 1750 MHz frequency really piles on the performance. AMD is promoting +28% GPU performance in 3D Mark Time Spy against Intel’s Core i7-1065G7, as well as a single threaded performance lead over both Ice Lake and Comet Lake.

These CPUs all support LPDDR4X memory, up to 64 GB, and AMD says that the infinity fabric is not tied to this memory clock. This helps the chip reach even lower power in its idle states, and the company said that they have rearchitected a good portion of the power delivery in the APU in order to be able to power down and power gate more elements of the SoC than was previously possible. AMD said that this decoupling of the infinity fabric and memory support, especially with both CPU and GPU accessing it, was made substantially easier due to the APU being a monolithic solution (with that in mind, it’s likely that AMD might not be going down the chiplet APU route any time soon). Also worthy to note is that AMD is saying that they have reduced the latency for parts of the chip to enter/exit idle states by 80%, and it’s this that helps enable the power gating in such a way to remain responsive. In previous products, certain elements of the design had to remain powered in order to be as responsive as the user required.

[![](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-014_575px.jpg)](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-014.jpg)

In terms of power, AMD is touting a full 2x performance per watt on the new 15 W CPUs, made possible by doubling the cores in the same power envelope and keeping the frequency high. AMD stated that this was possible due to +30% efficiency from the core and the SoC design, and +70% efficiency in the process compared to the previous products. Overall SoC power for the same frequency of the APU is down 20% as well, allowing AMD to push more out of the hardware.

One question that AMD should be answering about the U series chips this year is if they have succeeded in meeting the 25x20 Goal they set themselves in 2014 - provide 25x more performance over their older Kaveri platform by 2020. As it stands, AMD's main issue with meeting this goal seemed to be idle power, so given that the company is saying it has improved, we should hopefully hear some progress on this. It should be noted that for both U-series and H-series, the chips only support PCIe 3.0 - I suspect that PCIe 4.0 might be too power hungry for these form factors, and for modern graphics PCIe 3.0 is sufficient. As for other features IO features on the chips, the exact SoC SATA/USB/PCIe support will be announced closer to when the products actually ship.

[![](https://images.anandtech.com/doci/15324/Extrapolated%20Linear_575px.png)](https://images.anandtech.com/doci/15324/Extrapolated%20Linear.png)  
_Looking forward to updating this graph with final 2019 data and the new 2020 data_

For each of the U series products, they have a nominal 15W TDP, however AMD states that their customers have a range of configurable TDPs, from 12W to 25W. It’s unlikely that the enhanced performance (or reduced power) modes will be promoted by the OEMs, but it allows them to design chassis to accommodate more performance. AMD says that it is up to the OEM if they want to offer end users the ability to change the TDP, and the end result of a higher TDP is a better sustained performance, but short bursty turbo performance will be the same.

[![](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-018_575px.jpg)](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-018.jpg)

On the H series, these processors are what AMD is going to promote for its high-performance gaming designs. We asked AMD and these 45W parts will have a turbo window up to 54 W, which should be easily capable from the designs we’ve seen using the hardware already. Initially there are two chips available, with a third being ASUS-exclusive for the first six months.

AMD Ryzen 4000 45W H-Series CPUs

_AnandTech_

Cores  
Threads

Base  
Freq

Turbo  
Freq

L2

L3

CUs

IGP  
Freq

TDP

Ryzen 7 4800H

8C / 16T

2900

4200

4 MB

8 MB

7 CUs

1600

45 W

Ryzen 7 4800HS

8C / 16T

2900

4200

4 MB

8 MB

7 CUs

1600

35 W

Ryzen 5 4600H

6C / 12T

3000

4000

3 MB

8 MB

6 CUs

1500

45 W

The 2.9 GHz base frequency is the main beneficiary of the higher TDP here, but some users will notice the lower CU count and the lower integrated graphics frequency. This, according to AMD, is because all the designs currently using this CPU are actually using discrete graphics, so saving power on the integrated GPU front helps. From our perspective, we can think of another reason: there’s room for a Ryzen 9 in this product stack, with a fully enabled IGP as well as a small bump in frequency. When asked, AMD said the typical PR answer: ‘we’re evaluating the market and if we see a need for a Ryzen 9 like product to define our stack, and we see a reason to do it, then we will; however no announcement today’.

[![](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-023_575px.jpg)](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-023.jpg)

The odd-one out here is the Ryzen 7 4800HS, which is our ASUS-exclusive part. From ASUS’ PR, we were told that they worked together with AMD to help bin a super low-leakage part that can offer the full 45 W performance and frequency but in a 35 W envelope. This is the CPU that will appear in ASUS’ Zephyrus G14 notebook, which is a key design win for AMD. The exclusivity part isn’t too clear – the normal H series processors do support a 35W TDP down mode, so any other OEM can use the normal 4800H and put it into 35W mode. What is exclusive is the ‘S’ at the end, which only ASUS can use. Personally I feel that normally when an OEM buys chips from a vendor, each chip has a series of sub-bins for voltage and power, and unless you buy a specific sub-bin, it’s a random allocation. What I think ASUS has done here is work with AMD to secure the initial stock of that best sub-bin, and that’s why ASUS has the exclusive. After that, the 4800HS will be available to anyone.

With these chips, AMD says they will be priced similarly to Intel’s standard H-series processors. When asked about comparisons to the flagship 9980HK hardware, AMD said that the new Ryzen chips still beat those in most areas, single threaded, multithreaded, and on integrated graphics, but the 9980HK is priced above and beyond what AMD is doing, so AMD is aiming to undercut Intel on performance per dollar as well.

[![](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-024_575px.jpg)](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-024.jpg)

AMD H-series will also be getting a feature called SmartShift. This is more a power delivery mechanism than anything else – with H-series designs using the APU and a discrete graphics card (AMD says that all the partners using H have a discrete GPU inside as well), SmartShift will adjust the power budget between the CPU and the discerete GPU for the power budget that the laptop is designed for. In terms of benchmarks with this feature on/off, AMD is quoting 10% better framerates in The Division 2, and 12% faster Cinebench R20 NT. It won’t be obvious which laptop vendors have SmartShift enabled, however, so we’re hoping that AMD gives us an easy way to distinguish those that support it from those that do not.

[![](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-026_575px.jpg)](https://images.anandtech.com/doci/15324/AMD%20CES%202020%20Update_Client_Embargoed%20Until%20Jan.%206%20at%206pm%20ET-page-026.jpg)

Across the 15W and 45W parts, AMD is going to announce that they have secured over 100+ design wins for 2020, with the first devices to come out later in Q1. AMD’s partners have put tentative release dates for their hardware in March, April, and May, some come the end of Q2 we should see a healthy number of AMD Ryzen 4000 designs in the market.

We’ve already seen a few laptops with the new hardware, with ASUS’ Zephyrus G14 being a notable highlight, offering the 35W 4700HS processor and an RTX 2060 GPU in a 14-inch device, making it a powerful portable system. There’s even an LED front dot matrix display, for all the funky gifs.

  
  
from Hacker News https://ift.tt/2sJWqCK