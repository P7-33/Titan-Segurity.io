---
title: 'Check Point researchers hack an IoT device enabling a local network
attack #IoT #Security @checkpointsw'
date: 2020-02-06T21:49:00+01:00
draft: false
---

Check Point Software Research [posts an article](https://blog.checkpoint.com/2020/02/05/the-dark-side-of-smart-lighting-check-point-research-shows-how-business-and-home-networks-can-be-hacked-from-a-lightbulb/) and [video](https://youtu.be/4CWU0DA__bY) today on their researchers reviewing the market-leading [Philips Hue](https://www2.meethue.com/en-us) smart bulbs and bridge. They found vulnerabilities (CVE-2020-6007) that enabled infiltration into networks using a remote exploit in the [ZigBee](https://en.wikipedia.org/wiki/ZigBee) low-power wireless protocol that is used to control a range of IoT devices.

With the help of the Check Point Institute for Information Security (CPIIS) in Tel Aviv University, the researchers were able to take control of a Hue lightbulb on a target network and install malicious firmware on it. From that point, they used the lightbulb as a platform to take over the bulbs’ control bridge, and attacked the target network as follows:

1.  The hacker controls the bulb’s color or brightness to trick users into thinking the bulb has a glitch. The bulb appears as ‘Unreachable’ in the user’s control app, so they will try to ‘reset’ it.
2.  The only way to reset the bulb is to delete it from the app, and then instruct the control bridge to re-discover the bulb.
3.  The bridge discovers the compromised bulb, and the user adds it back onto their network.
4.  The hacker-controlled bulb with updated firmware then uses the ZigBee protocol vulnerabilities to trigger a heap-based buffer overflow on the control bridge, by sending a large amount of data to it. This data also enables the hacker to install malware on the bridge – which is in turn connected to the target business or home network.
5.  The malware connects back to the hacker and using a known exploit (such as [EternalBlue](https://en.wikipedia.org/wiki/EternalBlue)), they can infiltrate the target IP network from the bridge to spread ransomware or spyware.

The research was disclosed to Philips and Signify (owner of the Philips Hue brand) in November 2019. Signify confirmed the existence of the vulnerability in their product, and issued a patched firmware version (Firmware 1935144040) which is now available on their [site](https://www2.meethue.com/en-us/support/release-notes/bridge).

Additional reporting:

*   [Check Point blog post](https://blog.checkpoint.com/2020/02/05/the-dark-side-of-smart-lighting-check-point-research-shows-how-business-and-home-networks-can-be-hacked-from-a-lightbulb/)
*   [Hacker News](https://thehackernews.com/2020/02/philips-smart-light-bulb-hacking.html)
*   [CVE-2020-6007](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-6007)

Note: In building IoT devices, security can be extremely difficult and should be planned for from the beginning of the concept phase throughout the product design. See [All the Internet of Things – Episode 5: The S in IoT is for Security](https://www.youtube.com/watch?v=ISHqKL1okno) for more information.