---
title: 'Battle of the Boards: Jetson Nano vs Raspberry Pi
4 @Raspberry_Pi @NVIDIAEmbedded @SyonykBlog'
date: 2019-12-16T18:09:00+01:00
draft: false
---

![https://syonyk.blogspot.com/2019/11/battle-of-boards-jetson-nano-vs.html](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-45.png)

[Syonyk’s Blog](https://syonyk.blogspot.com/2019/11/battle-of-boards-jetson-nano-vs.html) features testing the Raspberry Pi 4 against the nVidia Jetson Nano single board computers (SBC).

> I’ve got a collection of broadly similar machines here that I’m benchmarking.  They’re all quad core machines, with various amounts of RAM.  And, by modern desktop standards, they’re all “gutless wonders.”  Despite that, I’ve used them all fairly extensively (except the Pi4, which just showed up).
> 
> I have a thing for gutless wonder ARM desktops.  I’ve talked about doing it with the [Raspberry Pi 3B](https://syonyk.blogspot.com/2018/03/project-pi3desk-building-awesome-pi3.html) (results: Don’t use btrfs on USB), the [Raspberry Pi 3B+](https://syonyk.blogspot.com/2018/09/project-pi3bdesk-making-even-better.html) (works fine, just a bit RAM limited), and the [Jetson Nano](https://syonyk.blogspot.com/2019/04/nvidia-jetson-nano-desktop-use-kernel-builds.html) (an honest desktop replacement for most tasks).
> 
> Finally, I’ve got a new Raspberry Pi 4 with 4GB of RAM.  This is the newest system in the test, and it comes with a set of four Cortex A-72 cores at 1.5Ghz, USB3, and a new GPU architecture.  On paper, this should be a good bit faster than the Nano – but paper and reality often differ.

The post definitely recommends using heatsinks:

> While I’ve done some testing on bare boards, most of the testing was done in a slightly more heatsink-heavy configuration.  The Jetson Nano looks identical to how it ships, because it’s totally fine stock.  The Pi 3B+ has a rather comical heatsink arrangement [I’ve covered before](https://syonyk.blogspot.com/2018/09/raspberry-pi-3b-flirc-case-thermals-and.html) – it lets it run at 1.4Ghz all day long without any issues.  And the Pi4 has a neat little aluminum heatsink on it that does a great job with keeping it cool, even when overclocked quite hard (as long as the fans are turning).

And the results:

> Get the Pi4 and overclock it!
> 
> As much as I like the Jetson Nano, the results are pretty clear – stock for stock, they perform nearly identically and the Pi4 is quite a bit cheaper. But, if you spend a couple bucks on a good heatsink and are willing to push your Pi4 to 2GHz, the Pi4 is significantly faster at the sort of things you care about doing – and also, still cheaper. Just make sure you have a good power supply.
> 
> Plus, the Raspberry Pi 4 is going to have better software support long term. It’s a far more popular board than the Nano. I’m not sure if the Nano will get a kernel update or not, and the Raspberry Pi foundation and developers are working to get a lot of the Pi code into the mainline kernel.

It is well worth [reading the entire article](https://syonyk.blogspot.com/2019/11/battle-of-boards-jetson-nano-vs.html) to see how things were determined.

![](https://1.bp.blogspot.com/-lKKvEAaFuMQ/Xdr-jhpB1MI/AAAAAAAA7V4/MnkYuGuZxbALORG6CyUJZWuiLZfXFZp0ACLcBGAsYHQ/s640/browser_benchmarks.png)