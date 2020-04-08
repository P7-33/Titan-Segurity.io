---
title: 'Upstreaming multipath TCP'
date: 2019-09-27T05:47:00+01:00
draft: false
---

### Welcome to LWN.net

The following subscription-only content has been made available to you by an LWN subscriber. Thousands of subscribers depend on LWN for the best news from the Linux and free software communities. If you enjoy this article, please consider accepting the trial offer on the right. Thank you for visiting LWN.net!

### Free trial subscription

Try LWN for free for 1 month: no payment or credit card required. [Activate your trial subscription now](https://lwn.net/Promo/slink-trial2-3/claim) and see why thousands of readers subscribe to LWN.net.

By

**Jonathan Corbet**

September 26, 2019

* * *

[LPC](https://lwn.net/Archives/ConferenceByYear/#2019-Linux_Plumbers_Conference)

The

[multipath TCP (MPTCP)](https://lwn.net/Articles/544399/)

protocol (and the Linux implementation of it) have been under development for a solid decade; MPTCP offers a number of advantages for devices that have more than one network interface available. Despite having been deployed widely, though, MPTCP is still not supported by the upstream Linux kernel. At the 2019 Linux Plumbers Conference, Matthieu Baerts and Mat Martineau discussed the current state of the Linux MPTCP implementation and what will be required to get it into the mainline kernel.

MPTCP, described by [RFC 6824](https://tools.ietf.org/html/rfc6824), is built around one fundamental idea: allowing a single network connection to exchange data over multiple physical paths. One obvious use case is a phone handset, which has both WiFi and broadband interfaces. Being able to use both at the same time would give the device greater bandwidth, but also greater redundancy — a connection could continue uninterrupted despite changes to individual paths.

Apple added MPTCP support in 2013, mostly to support easier failover between paths. The "walk-out" use case, where a user working over WiFi leaves the building and must switch to broadband, is prominent here. [![[Matthieu Baerts]](https://static.lwn.net/images/conf/2019/lpc/MatthieuBaerts-sm.jpg "Matthieu Baerts")](https://lwn.net/Articles/800517/) Others, including Samsung and LG, have patched in MPTCP support to gain access to greater bandwidth. MPTCP is also being added to residential network gateways, which have both DSL and LTE interfaces, again for greater bandwidth. The 5G standards also include MPTCP.

The Linux implementation was started in March 2009; over the following ten years it has reached version 0.95. It is already used by millions, Baerts said, but it is not in a condition where it can be upstreamed. The MPTCP developers are working on changing that, but there are a number of constraints they have to work under, the first of which being that the addition of MPTCP cannot affect the existing TCP stack. In particular, there can be no performance regressions, and no increase in code size if MPTCP is disabled. The protocol itself is strictly opt-in; applications must ask for it explicitly. The plan is to proceed in small steps, merging a minimal feature set first.

#### The MPTCP protocol

Baerts then launched into a quick overview of the MPTCP protocol which, he said, looks as much like vanilla TCP as possible. Due to the proliferation of network middleboxes that refuse to pass traffic they don't recognize, the addition of new protocols to the open Internet is a difficult task. There are two approaches that can work; one of which is

[the QUIC way](https://lwn.net/Articles/745590/)

, with all of the protocol details hidden from middleboxes. The other, taken by MPTCP, is to look just like an existing protocol. So the "subflows" used to carry traffic over a specific path are just basic TCP connections.

The new protocol does have to carry some information to tie those connections together, though. That is done in a few ways, starting with the "data sequence number" that is uniform across all connections. There is an MPTCP option in the TCP header, and a set of new SYN flags to indicate MPTCP capability or add a connection to an existing MPTCP session. There is some extra signaling to, for example, announce the availability of additional addresses. Receive windows across the TCP connections have to be coupled to provide a single window at the MPTCP level.

As it turns out, there are two versions of the MPTCP protocol: RFC 6824 and the newer [RFC 6824bis](https://datatracker.ietf.org/doc/draft-ietf-mptcp-rfc6824bis/) draft. The latter has been submitted for publication, and is the version that the MPTCP v1.0 patch will support. The modifications in the newer draft make it easier to implement, and 5G is using that version of the standard as well, so it is to be expected that all users will switch over relatively quickly. Baerts asked whether focusing on just RFC 6824bis would be acceptable to the networking developers; Eric Dumazet replied that it would be fine.

#### Getting it upstream

There was [a patch set](https://lwn.net/Articles/791376/) sent to the lists in June. It creates a new protocol type (IPPROTO\_MPTCP) that applications can use to select multipath. Baerts noted that this patch set does not yet support IPv6; adding that support should not be hard, but the MPTCP developers don't want to focus on it now. A member of the audience quickly suggested that the group should do the opposite: implement IPv6 only, and add IPv4 support later. Dave Miller said that the basic functionality needs to be submitted at the beginning, and that includes IPv6 support. We are, he said, way past the point of allowing IPv4-specific protocol implementations.

The developers are also uncertain about how to set socket options on MPTCP subflows. They don't want to settle on an API at this point, Baerts said, so there will be no user-space access to subflows for now.

Then, there is the question of who should be able to create MPTCP sockets. The first implementation will not be fully hardened; there have been no fuzzing efforts yet, for example. The plan is to include a sysctl knob to control access to the feature; it will be off by default and specific to each network namespace. Miller shot down that idea as well; if the code is to be accepted, he said, it should be functional. It should not be off by default, and in any case there are too many knobs in the system already. Alexei Starovoitov said that the receive path is more worrisome anyway, and that can't be controlled by a sysctl knob. Apple had a remote security issue that could be used to jailbreak phones; he would like to avoid that in Linux.

#### Use cases

The initial use case for MPTCP, Martineau said, is the server role. The path management issues are far simpler; clients, instead, have the complexity of multiple interfaces to deal with. Some of the requisite low-level pieces have already been upstreamed. He mentioned [SKB extensions](https://lwn.net/ml/netdev/20181218161527.2760-1-fw@strlen.de/) in particular; they are a way of attaching additional information to packets in the kernel without bloating the (already too large) sk\_buff structure. SKB extensions have already been used to remove a couple of unrelated pointers from that structure, making things better overall.

Once the initial merge has happened, work on adding more features can begin. Moving beyond the server use case is high on the list at that [![[Mat Martineau]](https://static.lwn.net/images/conf/2019/lpc/MatMartineau-sm.jpg "Mat Martineau")](https://lwn.net/Articles/800518/) point. There is also a need to support a user-space path manager that can add and remove paths while applying whatever policy the system administrator might configure. Work on the user-space side can be found [on GitHub](https://github.com/intel/mptcpd).

Another area for future development is a packet scheduler that can decide which path should be used for each packet. It could be configured to optimize for throughput, latency, or redundancy. This is relatively simple to do on the server side, where it is mostly a matter of acting on requests from the peer on each MPTCP connection. The kernel will feature a "basic" scheduler; the addition of a BPF hook for more complex cases seems nearly inevitable.

As mentioned above, MPTCP will be entirely opt-in; it will not be used unless an application explicitly requests it. But, naturally, there are users who want their unmodified binary programs to start using MPTCP once it's available. There is a working, if inelegant, solution to this problem. A new control-group hook allows the installation of a BPF program that runs when a program calls socket(); it can change the requested protocol to IPPROTO\_MPTCP and the calling application will be none the wiser.

The "break before make" feature would allow the establishment of an MPTCP connection that initially has no subflows at all. It may useful for cases like switching between multiple access points. This feature will be added if the demand for it materializes. There will eventually be a need to be able to set socket options on subflows; this will have to be handled carefully since a number of them could interfere with ordinary TCP.

Finally, Martineau mentioned the problem of [in-kernel TLS support](https://lwn.net/Articles/666509/). Since MPTCP is not TCP, it lacks the upper-level protocol support needed for TLS. With enough work, support could be added, and it would still be possible to split TLS data across flows. That becomes hard, though, when hardware acceleration is involved; it's not clear what the solution there will be.

\[Your editor thanks the Linux Foundation, LWN's travel sponsor, for supporting travel to this event.\]

> **Did you like this article?** Please accept our [trial subscription offer](https://lwn.net/Promo/slink-trial2-3/claim) to be able to see more content like it and to participate in the discussion.

* * *

(

[Log in](https://lwn.net/Login/?target=/Articles/800501/)

to post comments)

  
  
from Hacker News https://ift.tt/2n4Hdc3