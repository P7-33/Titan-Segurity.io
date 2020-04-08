---
title: '#SecTorCa: Millions of Phones Leaking Information Via Tor'
date: 2019-10-11T09:37:00+01:00
draft: false
---

#SecTorCa: Millions of Phones Leaking Information Via Tor
=========================================================

![](https://assets.infosecurity-magazine.com/webpage/rss/3c81e77e-9f14-4672-be39-68371b397126.jpg)

There is a privacy threat lurking on perhaps hundreds of millions of devices, that could enable potential attackers to track and profile users, by using information leaked via the Tor network, even if the users never intentionally installed Tor in the first place.

In a session at the [SecTor](https://sector.ca/) security conference in Toronto, Canada on October 10, researchers Adam Podgorski and Milind Bhargava from [Deloitte Canada](https://www2.deloitte.com/ca/en.html) outlined and demonstrated previously undisclosed research into how they were able to determine that personally identifiable information (PII) is being leaked by millions of mobile users every day over Tor.

The irony of the issue is that [Tor](https://www.torproject.org/) is a technology and a network that is intended to help provide and enable anonymity for users. With Tor, traffic travels through a number of different network hops to an eventual exit point in the hope of masking where the traffic originated from. Podgorski said that there are some users that choose to install a Tor browser on their mobile devices, but that’s not the problem. The problem is that Tor is being installed by mobile applications without user knowledge and potentially putting users at risk.

The researchers explained that they set up several Tor exit nodes, just to see what they could find, and the results were surprising. The researchers found that approximately 30% of all Android devices are transmitting data over Tor.

“You’re probably scratching your head now, like we were a couple of months ago, because that doesn’t make any sense,” Podgorski said. “There's no way a third of Android users know what Tor is and are actually using it.”

What the researchers determined is that Tor is being bundled, embedded and installed in other applications and users are not aware of its existence. It was not entirely clear to the researchers why Tor was being bundled with so many applications. Podgorski said that it could be due to a misunderstanding of the technology and how it can be used. Tor was also found on Apple IOS devices, but the numbers were smaller with only approximately 5% of devices sending data.

**Tracking Users**

In a series of demonstrations, including live dashboards shown by Bhargava, the researchers showed what data they had collected from mobile users that were inadvertently using Tor. The data included GPS coordinates, web addresses, phone numbers, keystrokes and other PII.

“This data can be used to build a robust profile of an individual,” Podgorski said.

Bhargava explained that the exit nodes the researchers set up intentionally attempted to force browsers to not use encrypted versions of websites, forcing the devices to regular HTTP when possible. With data coming to the exit node without encryption, it was possible for the researchers to see the user data. Bhargava noted that for sites that force HTTPS encryption and do not offer any fallback option to regular un-encrypted HTTP, they wouldn’t be able to see the users data.

Also of note, Bhargava admitted that he found his own phone number in the data, which was a surprise to him, as he had not installed Tor on his device. The only applications on his phone were applications installed by the carrier.

There are several things that need to happen to fix the issue. Podgorski said that the first is awareness that there is a problem, which is what the research is intended to highlight for legislators, government and organizations. For users, Podgorski emphasized that good operational security practices need to be employed, by using encryption everywhere.

In Podgorski's view, there is already a legal compliance risk that the mobile application PII data leaks expose.

“We’re pretty sure what we found breaches GDPR on multiple levels,” he said, “but the issue is that governments can’t enforce the law if they’re not aware.”

  
  
from Infosecurity - Latest New... https://ift.tt/2MuJgPP