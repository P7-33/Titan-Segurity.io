---
title: 'Microsoft warns users to stay alert for more BlueKeep attacks'
date: 2019-11-08T04:58:00+01:00
draft: false
---

Reverse engineering of BlueKeep patch reveals how dangerous it is Researchers develop a proof-of-concept attack after reverse engineering the Microsoft BlueKeep patch. ![](https://zdnet4.cbsistatic.com/hub/i/r/2019/07/09/33970abf-5012-4274-b2cd-247562f0acd8/thumbnail/570x322/590f71e959e415eb6edca43eae771cd2/bluekeep-researchers-show-how-dangerous-5d1ca6aa2f64e300c2bf415b-1-jul-09-2019-12-05-08-poster.jpg)

Microsoft's security team believes that more destructive BlueKeep attacks are on the horizon and urges users and companies alike to apply patches if they've been lagging.

The company's warning comes after security researchers detected [the first-ever malware campaign](https://www.zdnet.com/article/bluekeep-attacks-are-happening-but-its-not-a-worm/) that weaponized the BlueKeep vulnerability.

The attacks, which were detected last weekend, used BlueKeep to break into unpatched Windows systems and install a cryptocurrency miner.

Many security researchers considered the attacks underwhelming and not living up to the hype that was built around BlueKeep for the past six months.

This was because Microsoft said BlueKeep could be used to build wormable (self-spreading) malware. However, the attacks that happened over the weekend did not deploy malware that could spread on its own.

Instead, attackers scanned the internet for vulnerable systems and attacked each unpatched system, one at a time, deploying a BlueKeep exploit, and then the cryptocurrency miner.

This was far from the self-spreading malware outbreak that Microsoft said BlueKeep could trigger. Furthermore, in many cases, the BlueKeep exploit failed to work, crashing systems.

But Microsoft says this is just the beginning, and that attackers will eventually refine their attacks, and that the worst is yet to come.

"While there have been no other verified attacks involving ransomware or other types of malware as of this writing, the BlueKeep exploit will likely be used to deliver payloads more impactful and damaging than coin miners," Microsoft said today. "We cannot discount enhancements that will likely result in more effective attacks."

Now, Microsoft is warning and urging users to apply patches -- for the third time this year.

"Customers are encouraged to identify and update vulnerable systems immediately," the company said. "Many of these unpatched devices could be unmonitored RDP appliances placed by suppliers and other third-parties to occasionally manage customer systems. BlueKeep can be exploited without leaving obvious traces, customers should also thoroughly inspect systems that might already be infected or compromised."

### The BlueKeep lowdown

Because there's been a flood of BlueKeep-related coverage this year, below is a summary of what you need to know. Just the essentials:

*   BlueKeep is a nickname given to CVE-2019-0708, a vulnerability in the Microsoft RDP (Remote Desktop Protocol) service.
*   BlueKeep impacts only: Windows 7, Windows Server 2008 R2, Windows Server 2008.
*   Patches have been available since mid-May 2019. [See official Microsoft advisory](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2019-0708).
*   On the same day it released patches, Microsoft published a blog post [warning about BlueKeep being wormable](https://msrc-blog.microsoft.com/2019/05/14/prevent-a-worm-by-updating-remote-desktop-services-cve-2019-0708/).
*   [Microsoft issued a second warning](https://blogs.technet.microsoft.com/msrc/2019/05/30/a-reminder-to-update-your-systems-to-prevent-a-worm/) about orgs needing to patch BlueKeep, two weeks later, at the end of May.
*   The [US National Security Agency](https://www.nsa.gov/News-Features/News-Stories/Article-View/Article/1865726/nsa-cybersecurity-advisory-patch-remote-desktop-services-on-legacy-versions-of/), the [US Department of Homeland Security](https://www.us-cert.gov/ncas/alerts/AA19-168A), [Germany's BSI](https://www.bsi.bund.de/DE/Presse/Pressemitteilungen/Presse2019/Windows-Schwachstelle-RDP-150519.html) cyber-security agency, the [Australian Cyber Security Centre](https://www.cyber.gov.au/news/protect-against-BlueKeep), and the [UK's National Cyber Security Centre](https://www.ncsc.gov.uk/report/weekly-threat-report-31st-may-2019) have all issued their own security alerts, trying to get companies to patch outdated computer fleets.
*   Many security researchers and cyber-security firms developed fully-working BlueKeep exploits over the summer; however, nobody published the code after realizing how dangerous the exploit was, and fearing that it could be abused by malware authors.
*   In July, a US company started [selling a private BlueKeep exploit](https://www.zdnet.com/article/us-company-selling-weaponized-bluekeep-exploit/) to its customers, so they could test if their systems were vulnerable.
*   In September, the developers of the Metasploit penetration testing framework [published the first public BlueKeep proof-of-concept exploit](https://www.zdnet.com/article/metasploit-team-releases-bluekeep-exploit/).
*   In late October, malware authors started using this BlueKeep Metasploit module in a real-world campaign. Microsoft has an article about this malware campaign [here](https://www.microsoft.com/security/blog/2019/11/07/the-new-cve-2019-0708-rdp-exploit-attacks-explained/).
*   According to BinaryEdge, there are roughly 700,000 internet-connected Windows systems that are vulnerable to BlueKeep, and have yet to receive patches.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2CkWie5