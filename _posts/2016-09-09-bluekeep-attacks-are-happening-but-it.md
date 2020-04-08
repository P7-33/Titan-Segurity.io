---
title: 'BlueKeep attacks are happening, but it''s not a worm'
date: 2019-11-03T04:37:00+01:00
draft: false
---

![us-company-selling-weaponized-bluekeep-e-5d3f4e4709ac9100018ce3cf-1-aug-01-2019-14-06-31-poster.jpg](https://zdnet1.cbsistatic.com/hub/i/2019/08/01/bd49f6c2-afe8-4311-8e36-2b29d90d3508/960fdebf9d6799c9ebb61bff4cb6b8bf/us-company-selling-weaponized-bluekeep-e-5d3f4e4709ac9100018ce3cf-1-aug-01-2019-14-06-31-poster.jpg)

Security researchers have spotted the first mass-hacking campaign using the BlueKeep exploit; however, the exploit is not being used as a self-spreading worm, as Microsoft was afraid it would happen last May when it [issued a dire warning](https://msrc-blog.microsoft.com/2019/05/14/prevent-a-worm-by-updating-remote-desktop-services-cve-2019-0708/) and urged users to patch.

Instead, a hacker group has been using [a demo BlueKeep exploit released by the Metasploit team](https://www.zdnet.com/article/metasploit-team-releases-bluekeep-exploit/) back in September to hack into unpatched Windows systems and install a cryptocurrency miner.

This BlueKeep campaign has been happening at scale for almost two weeks, but it's been [only spotted today](https://twitter.com/GossiTheDog/status/1190654984553205761) by cybersecurity expert Kevin Beaumont.

The British security expert said he found the exploits in logs recorded by honeypots he set up months before and forgot about. First attacks date back to October 23, Beaumont told _ZDNet_.

Beaumont's discovery was [confirmed](https://www.kryptoslogic.com/blog/2019/11/bluekeep-cve-2019-0708-exploitation-spotted-in-the-wild/) by Marcus "MalwareTech" Hutchins, the security researcher who stopped the WannaCry ransomware outbreak, and who's a recognized expert in the BlueKeep exploit -- which impacts the Microsoft RDP (Remote Desktop Protocol) service.

The attacks discovered by Beaumont are nowhere near the scale of the attacks Microsoft was afraid of back in May, when it likened BlueKeep to EternalBlue, the exploit at the heart of the WannaCry, NotPetya, and Bad Rabbit ransomware outbreaks of 2017.

Microsoft engineers were terrified that BlueKeep would trigger another world-spanning malware outbreak that spread on its own, from unpatched system to unpatched system.

However, the first mass-hacking operation didn't turn out to include self-spreading, worm-like capabilities.

> Update: according to netflow it doesn't appear to be self propagating, I assume a list of vulnerable IPs are being fed to a server which performs the exploitation.
> 
> — MalwareTech (@MalwareTechBlog) [November 3, 2019](https://twitter.com/MalwareTechBlog/status/1190802833324462081?ref_src=twsrc%5Etfw)

> I don’t think there’s a worm (or at least anything bad enough to care about). There’s finally generic exploitation tho for sure.
> 
> — Kevin Beaumont (@GossiTheDog) [November 2, 2019](https://twitter.com/GossiTheDog/status/1190761418045448192?ref_src=twsrc%5Etfw)

> FWIW, re:[#BlueKeep](https://twitter.com/hashtag/BlueKeep?src=hash&ref_src=twsrc%5Etfw) we're seeing a small uptick in 3389 related traffic at the [@RenditionSec](https://twitter.com/RenditionSec?ref_src=twsrc%5Etfw) SOC, but not consistent with a worm. I would guess either:  
> 1\. It's not a worm  
> 2\. Enough machines have been patched or the exploit is too unreliable for a worm to reach critical mass
> 
> — Jake Williams (@MalwareJake) [November 2, 2019](https://twitter.com/MalwareJake/status/1190750514713112576?ref_src=twsrc%5Etfw)

Furthermore, these particular BlueKeep attacks don't seem to work. Beaumont told _ZDNet_ that the attacks crashed 10 of the 11 honeypots he was running.

This shows the attacker's exploit code doesn't work as they intend.

This fits right in with what most experts have said about BlueKeep for the past few months. The BlueKeep exploit can have devastating consequences, but it's hard to get an exploit working the correct way, without crashing the OS with a Blue Screen of Death (BSOD) error.

The person/group behind the recent attacks doesn't appear to have the know-how to modify the BlueKeep demo exploit released by the Metasploit team back in September, which is a good thing. However, some attacks are succeeding.

What we are seeing today from this threat actor is the first hacking group that is trying to weaponize this dangerous exploit in an operation at scale, rather than at a specific target.

But ZDNet is also aware that other hackers have used BlueKeep in more targeted attacks, and have used it successfully.

At one point in the future, some low-skilled threat actor will figure out how to run BlueKeep properly, at which point, we'll see it used more broadly. Chances are that it's still going to be used to mine cryptocurrency -- the same thing for which EternalBlue is also used nowadays.

  
  
from Latest Topic for ZDNet in... https://ift.tt/36smkKa