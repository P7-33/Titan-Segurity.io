---
title: 'Security Flaws & Fixes - W/E - 1/24/20'
date: 2020-01-24T17:01:00+01:00
draft: false
---

**Cisco Mitigates Vulnerabilities in FMC and Other Products** (01/22/2020)  
To address security issues across multiple product lines, [Cisco](http://www.cisco.com/) released more than 25 [advisories](https://tools.cisco.com/security/center/publicationListing.x?product=Cisco&sort=-day_sir#~Vulnerabilities) on January 22. The most critical of these is an authentication bypass flaw in the vendor's Firepower Management Center and updates have been released.

  

**Citrix Begins Patching Zero-Day Hole in ADC, Gateway** (01/22/2020)  
[Citrix](http://www.citrix.com/) began rolling out [patches](https://www.citrix.com/blogs/2020/01/19/vulnerability-update-first-permanent-fixes-available-timeline-accelerated/) for a critical bug in its Application Delivery Controller (ADC) and Citrix Gateway. Permanent fixes for ADC versions 11.1 and 12.0 are available. Further fixes for this bug, which is being actively exploited, are being prepared by the vendor. In addition, Citrix [warned](https://www.citrix.com/blogs/2020/01/17/citrix-updates-on-citrix-adc-citrix-gateway-vulnerability/) that this vulnerability also affects certain deployments of two older versions of Citrix SD-WAN WANOP, product versions 10.2.6 and version 11.0.3. Other SD-WAN products are not impacted.

  

**DoS Bug Identified in AMD Driver Receive****s Security Patches** (01/22/2020)

[Cisco](http://www.cisco.com/) [warned](https://talosintelligence.com/vulnerability_reports/TALOS-2019-0913) that an exploitable out-of-bounds read vulnerability exists in [AMD](http://www.amd.com/)'s Radeon line of graphics cards, specifically ATIDXX64.DLL driver, version 26.20.13001.50005. A specially crafted pixel shader can cause a denial-of-service. An attacker can provide a specially crafted shader file to trigger this vulnerability which can be triggered from the [VMware](http://www.vmware.com/) guest, affecting the VMware host. Patches have been released.

  

**DoS Condition Possible in Schneider Electric Modicon Controllers** (01/22/2020)  
Schneider Electric's Modicon Controllers are impacted by a vulnerability that can lead to a denial-of-service condition. Multiple versions are affected, according to an [advisory](https://www.us-cert.gov/ics/advisories/icsa-20-016-01) released by the [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/). The vendor has released some firmware patches.

  

**Freely Available Tool Scans for Indicators of Compromise Related to Citrix Bug** (01/22/2020)  
[FireEye](http://www.fireeye.com/) and [Citrix](http://www.citrix.com/) have created a free tool that searches for indicators of compromise (IoC) associated with attacker activity resulting from a zero-day vulnerability in Citrix Application Delivery Controller (ADC), Citrix Gateway, and two older versions of Citrix SD-WAN WANOP. This tool is accessible in both the Citrix and FireEye GitHub repositories.

  

**Google Says Apple's Privacy Software Tracks Users** (01/23/2020)  
In a [report](https://amp.ft.com/content/916a766a-3d27-11ea-a01a-bae547046735?__twitter_impression=true) published by the Financial Times ([FT](https://www.ft.com/)), [Google](http://www.google.com/) warned of flaws in Safari's Intelligent Tracking Protection (ITP) which could allow third parties to track people's browsing habits. The research team identified five possible attack scenarios on the issues it uncovered in ITP. Apple says it has already released an update for the flaws. In a December [blog post](https://webkit.org/blog/9661/preventing-tracking-prevention-tracking/), Apple stated, "We'd like to thank Google for sending us a report in which they explore both the ability to detect when Web content is treated differently by tracking prevention and the bad things that are possible with such detection. Their responsible disclosure practice allowed us to design and test the changes detailed..."

  

**Google Swats 11 Bugs in Latest Chrome Release** (01/22/2020)  
[Google](http://www.google.com/) [updated](https://chromereleases.googleblog.com/2020/01/stable-channel-update-for-desktop_16.html) Chrome to 79.0.3945.130 for Windows, Mac, and Linux. This update includes 11 security fixes, including a critical use-after-free bug in speech recognizer.

  

**Honeywell Maxpro VMS & NVR Vulnerable to Attacks** (01/22/2020)  
[Honeywell](http://www.honeywell.com/)'s MAXPRO VMS & NVR are vulnerable to both SQL injection and deserialization of untrusted data issues. Successful exploitation of these vulnerabilities could result in elevation of privileges, cause a denial-of-service condition, or allow unauthenticated remote code execution. An [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-20-021-01) provides information on the affected products, which are video management systems. Patches are available via the vendor.

  

**IE Scripting Engine Zero-Day Gets Micropatched Until Microsoft Issues Fix**(01/22/2020)

A remote code execution vulnerability exists in the way that the scripting engine handles objects in memory in Internet Explorer. The vulnerability could corrupt memory in such a way that an attacker could execute arbitrary code in the context of the current user and eventually gain the same user rights as the current user. In a Web-based attack scenario, an attacker could host a specially crafted Web site that is designed to exploit the vulnerability through Internet Explorer and then convince a user to view the Web site. [Microsoft](http://www.microsoft.com/) is working on a patch and has listed remediation techniques in an [advisory](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV200001). In the meantime, third-party vendor [ACROS Security](https://www.acrossecurity.com/) [released](https://blog.0patch.com/2020/01/micropatching-workaround-for-cve-2020.html) micropatches until the updates are issued. Micropatches are small patches of code that fix software vulnerabilities.

  

**Samba Issues Updates to Plug Security Holes** (01/22/2020)

[Samba](http://us4.samba.org/samba/) has received security [updates](https://www.samba.org/samba/history/security.html) to mitigate vulnerabilities and risks. Users should read the advisories and apply all updates.1/22/2020)

[Samba](http://us4.samba.org/samba/) has received security [updates](https://www.samba.org/samba/history/security.html) to mitigate vulnerabilities and risks. Users should read the advisories and apply all updates.