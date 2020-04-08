---
title: 'Planting Tiny Spy Chips in Hardware Can Cost as Little as $200'
date: 2019-10-13T08:44:00+01:00
draft: false
---

![](https://media.wired.com/photos/5d9e68a85e69b80009416265/master/w_2560,c_limit/security%2520-%2520feature%2520art%2520-%2520Bloomberg%2520SuperMicro%2520Hack%2520for%2520Cheap%2520-%2520453148685.jpg "Planting Tiny Spy Chips in Hardware Can Cost as Little as $200 | WIRED")  

Elkins programmed his tiny stowaway chip to carry out an attack as soon as the firewall boots up in a target's data center. It impersonates a security administrator accessing the configurations of the firewall by connecting their computer directly to that port. Then the chip triggers the firewall's password recovery feature, creating a new admin account and gaining access to the firewall's settings. Elkins says he used Cisco's ASA 5505 firewall in his experiment because it was the cheapest one he found on eBay, but he says that any Cisco firewall that offers that sort of recovery in the case of a lost password should work. "We are committed to transparency and are investigating the researcher’s findings," Cisco said in a statement. "If new information is found that our customers need to be aware of, we will communicate it via our normal channels."

Once the malicious chip has access to those settings, Elkins says, his attack can change the firewall's settings to offer the hacker remote access to the device, disable its security features, and give the hacker access to the device's log of all the connections it sees, none of which would alert an administrator. "I can basically change the firewall's configuration to make it do whatever I want it to do," Elkins says. Elkins says with a bit more reverse engineering, it would also be possible to reprogram the firmware of the firewall to make it into a more full-featured foothold for spying on the victim's network, though he didn't go that far in his proof of concept.

### A Speck of Dust

Elkins' work follows an earlier attempt to reproduce far more precisely the sort of hardware hack _Bloomberg_ described in its supply chain hijacking scenario. As part of his research presented at the Chaos Computer Conference last December, independent security researcher Trammell Hudson [built a proof of concept for a Supermicro board](https://trmm.net/modchips) that attempted to mimic the techniques of the Chinese hackers described in the _Bloomberg_ story. That meant planting a chip on the part of a Supermicro motherboard with access to its baseboard management controller, or BMC, the component that allows it to be remotely administered, offering a hacker deep control of the target server.

Hudson, who worked in the past for Sandia National Labs and now runs his own security consultancy, found a spot on the Supermicro board where he could replace a tiny resistor with his own chip to alter the data coming in and out of the BMC in real time, exactly the sort of attack that _Bloomberg_ described. He then used a so-called [field reprogrammable gate array](https://www.wired.com/2016/05/googles-making-chips-now-time-intel-freak/)—a reprogrammable chip sometimes used for prototyping custom chip designs—to act as that malicious interception component.

"For an adversary who wants to spend any money on it, this would not have been a difficult task."

Security researcher Trammell Hudson

Hudson's FPGA, at less than 2.5 millimeters square, was only slightly larger than the 1.2-millimeters-square resistor it replaced on the Supermicro board. But in true proof-of-concept style, he says he didn't actually make any attempts to hide that chip, instead connecting it to the board with a mess of wiring and alligator clips. Hudson argues, however, that a real attacker with the resources to fabricate custom chips—a process that would likely cost tens of thousands of dollars—could have carried out a much more stealthy version of the attack, fabricating a chip that carried out the same BMC-tampering functions and fit into a much smaller footprint than the resistor. The result could even be as small as a hundredth of a square millimeter, Hudson says, vastly smaller than _Bloomberg_'s grain of rice.

"For an adversary who wants to spend any money on it, this would not have been a difficult task," Hudson says.

"There’s no need for further comment about false reports from more than a year ago," Supermicro said in a statement.

But Elkins points out that his firewall-based attack, while far less sophisticated, doesn't require that custom chip at all—only his $2 one. "Don’t discount this attack because you think someone needs a chip fab to do it," Elkins says. "Basically anyone who’s an electronic hobbyist can do a version of this at home."

  
  
from Hacker News https://ift.tt/33oxL3f