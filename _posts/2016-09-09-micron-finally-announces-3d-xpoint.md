---
title: 'Micron Finally Announces a 3D XPoint Product: Micron X100 NVMe SSD'
date: 2019-10-25T01:37:00+01:00
draft: false
---

![](https://images.anandtech.com/doci/15029/x100-screenshot_678x452.png "Micron Finally Announces A 3D XPoint Product: Micron X100 NVMe SSD")  

Micron and Intel co-developed 3D XPoint memory as a high-performance alternative to flash, but so far only Intel has brought products to market, under their Optane brand. Despite owning the fab where 3D XPoint memory is produced, the closest Micron has come to commercializing that tech for themselves was their announcement in 2016 that upcoming Micron products using 3D XPoint memory would be branded as [Micron QuantX](https://www.anandtech.com/show/10556/micron-announces-quantx-branding-for-3d-xpoint-memory), their counterpart to Intel's Optane brand. Years later, we finally have a concrete product announcement, and they seem to have abandoned the QuantX name.

The new Micron X100 is a high-end enterprise NVMe SSD to compete against [Intel's upcoming second-generation Optane SSDs](https://www.anandtech.com/show/14903/intel-shares-new-optane-and-3d-nand-roadmap) and any specialized low-latency SLC NAND their competitors can come up with (eg. [Samsung Z-NAND](https://www.anandtech.com/show/13951/the-samsung-983-zet-znand-ssd-review), [Toshiba XL-FLASH](https://www.anandtech.com/show/14707/toshiba-launches-xlflash-3d-slc-nand)). Micron has not yet released full specs for the X100, but the top line performance numbers are 2.5M IOPS for 4kB random reads and around 10GB/s for sequential transfers—both likely to be new records for a single SSD if they can ship it soon enough. A preview video posted by Micron includes a graph that labels the 2.5M IOPS figure as being tested at QD1, which sounds too good to be true: almost 5x the performance of Intel's current Optane SSDs. Micron says the X100 should be good for at least 9GB/s for reads, writes, or mixed workloads, reflecting how much closer 3D XPoint is to symmetrical read/write performance than any flash memory. (And also suggesting that the controller may be the bottleneck for sequential transfers more than the 3D XPoint memory itself.) For QoS, Micron is listing both read and write latencies of 8µs or less, slightly better than the 10µs that Intel's current Optane SSDs promise.

The card Micron is showing off today is a full-height half-length PCIe x16 add-in card, so it should be able to reach full throughput even on PCIe 3.0 systems. Micron says the X100 will be in limited sampling to select customers sometime this quarter, so it's not going to be shaking up the storage market much in the immediate future but it is far enough past the vaporware stage that Micron should be able to deliver the rest of the specs soon—including the range of available capacities. Since Micron hasn't said anything about a second generation of 3D XPoint memory being ready, the density and costs of the X100 shouldn't be drastically different from Intel's Optane offerings.

  
  
from Hacker News https://ift.tt/33WEGRt