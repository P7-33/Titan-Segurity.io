---
title: 'Are All Edge Devices “Servers?”'
date: 2020-03-04T11:23:00+01:00
draft: false
---

Over the weekend, a discussion broke out on Twitter between leading experts in the field of servers, IoT, gateways and single-board computers over the future of “edge computing.” This post is meant to summarize what was talked about for a broader audience because it is relevant to how we, as an industry, think and talk about “The Edge.”

The topic? What are the differences between an edge device and a server, should the industry consider these as being “The same thing” or are they different. Should devices which are meant to be deployed in fleets be treated differently than those meant to be deployed as servers?

Lets find out what key developers from the ecosystem said:

According to Red Hat Chief Arm Architect and current [Nuvia](https://nuviainc.com/) VP of Software Jon Masters:

> Edge devices are all servers. All of them. Some folks disagree. They are wrong in my opinion. [https://t.co/97eU8LpT6f](https://t.co/97eU8LpT6f)
> 
> — Jon Masters 🏴‍☠️ (@jonmasters) [February 29, 2020](https://twitter.com/jonmasters/status/1233817927209480192?ref_src=twsrc%5Etfw)

Edward Vielmetti, who manages special projects at [Packet](https://www.packet.com/) (a Bare Metal Server and On Premise Cloud Provider) said this:

> Edge devices are servers (from the kernel point of view) but from an operations and network point of view they emphatically do not always have data-center quality networking.
> 
> You can’t count on 5 9’s uptime, reliable power, separated management networks, on-site staff, &c.
> 
> — Edward Vielmetti (@vielmetti) [March 1, 2020](https://twitter.com/vielmetti/status/1234178307001921543?ref_src=twsrc%5Etfw)

David Tischler, founder of [miniNodes](https://www.mininodes.com/) weighed in:

> Opinion here: Yes. “FleetReady” is needed.
> 
> Two type of devices should be covered, terminology matters:
> 
> IoT: A “final” endpoint, that only sends data upstream.
> 
> Edge: A smaller server, but still a server, in that it sends data to users, customers, devices, etc.
> 
> — miniNodes (@miniNodes) [February 29, 2020](https://twitter.com/miniNodes/status/1233823824803586048?ref_src=twsrc%5Etfw)

You can view and participate [in the full discussion here](https://twitter.com/rexstjohn/status/1233812801765830656).

On a related topic, as has been reported [in other publications](https://www.hackster.io/news/raspberry-pi-4-strides-towards-serverready-status-via-sbbr-compliant-uefi-firmware-effort-a6e390d5f019), a community driven project is now well underway [to certify the Raspberry Pi 4 as being “ServerReady.”](https://rpi4-uefi.dev/about/) Effectively what this would mean is that it is possible to buy $35 single-board computers which have similar software support to enterprise-grade server hardware.

Maintainers of the project recently posted a status update indicating that a comprehensive dashboard of progress is now available. The project is being organized via [Discord](https://discordapp.com/invite/fqRhc8y) currently with source code posted on GitHub.

> [https://t.co/BW3FdBdQTr](https://t.co/BW3FdBdQTr)
> 
> Raspberry Pi 4 UEFI now has a comprehensive status page of what works and what doesn’t
> 
> — It’s an Arm world (virtualized) (@WhatAintInside) [March 1, 2020](https://twitter.com/WhatAintInside/status/1234244877493428229?ref_src=twsrc%5Etfw)

Closing thoughts: What do you think? Is everything a server?

_All opinions written here belong to the author and not those of their employer. Follow [@rexstjohn](https://twitter.com/rexstjohn) on twitter because he posts on many hardware topics like robots, drones and edge computing. _