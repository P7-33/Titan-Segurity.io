---
title: 'Security Flaws & Fixes - W/E - 1/17/20'
date: 2020-01-17T14:58:00+01:00
draft: false
---

**"Cable Haunt" RCE Bug in Broadcom Chip Impacts Hundreds of Millions of Modems** (01/14/2020)  
Researchers in Denmark [uncovered](https://github.com/Lyrebirds/Cable-Haunt-Report/releases/latest/download/report.pdf) a vulnerability in the firmware of [Broadcom](http://www.broadcom.com/)'s modem firmware that can potentially impact millions of devices. The bug, called "Cable Haunt," is located in a component of the Broadcom chip - the spectrum analyzer - and causes a remote code execution. The researchers said, "The cable modems are vulnerable to remote code execution through a Web-socket connection, bypassing normal CORS and SOC rules, and then subsequently by overflowing the registers and executing malicious functionality. The exploit is possible due to lack of protection proper authorization of the Web-socket client, default credentials and a programming error in the spectrum analyzer." There are approximately 200 million cable modems in Europe that could be potentially affected by this bug and multiple vendors, including [Netgear](http://www.netgear.com/) and Arris are impacted.

  

**Adobe Boots Bugs in Illustrator CC, Experience Manager** (01/14/2020)  
[Adobe](http://www.adobe.com/) released security bulletins for [Illustrator CC](https://helpx.adobe.com/security/products/illustrator/apsb20-03.html) and [Experience Manager](https://helpx.adobe.com/security/products/experience-manager/apsb20-01.html). The Illustrator CC update resolves a memory corruption issue that can lead to an arbitrary code execution. The update for Experience Manager remedies multiple issues, including two reflected cross-site scripting flaws.

  

**Attackers Target Unpatched Pulse Secure VPN Servers to Install Ransomware** (01/13/2020)  
The Cybersecurity and Infrastructure Security Agency ([CISA](https://www.dhs.gov/CISA/)) has [observed](https://www.us-cert.gov/ncas/alerts/aa20-010a) wide exploitation of Pulse Secure's VPN servers due to a remote code execution vulnerability. This bug was addressed by the vendor in April 2019 but many servers worldwide remain unpatched and vulnerable. Cybercriminals are targeting the bug to unleash the REvil (Sodinokibi) ransomware. CISA strongly recommends that users and administrators apply the patches immediately.

  

**Citrix to Release Patches for Zero-Day Bug in ADC, Gateway** (01/14/2020)  
[Citrix](http://www.citrix.com/) is [planning](https://www.citrix.com/blogs/2020/01/11/citrix-provides-update-on-citrix-adc-citrix-gateway-vulnerability/) to release fixes for a zero-day hole in its Application Delivery Controller and Gateway that, if exploited, could allow an unauthenticated attacker to perform arbitrary code execution. The vendor warned of the flaw on December 17 but exploits have since been released. Updates for versions 11.1 and 12 are expected on January 20 while versions 12.1 and 13 will be made available on January 27, and version 10.5 will receive an update on January 31.

  

**GE/Emerson GE PACSystems RX3i Affected by Security Issue** (01/14/2020)  
The [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) has [warned](https://www.us-cert.gov/ics/advisories/icsa-20-014-01) that PACSystems RX3i (previously owned by GE and acquired by Emerson) are vulnerable to an improper input validation flaw. Multiple products and versions are impacted. Details about contacting Emerson are available from the ICS-CERT advisory.

  

**HTTP Cache Poisoning Renders AWS, Akamai, Cloudflare Vulnerable** (01/15/2020)  
Multiple caching service providers are vulnerable to HTTP cache poisoning, according to an [advisory](https://kb.cert.org/vuls/id/335217/) from the ([CISA](https://www.dhs.gov/CISA/)). Once an attacker has successfully injected malicious content, future visitors accessing the compromised site will collect and execute the attacker's injected scripts. The advisory offers suggestions to content delivery network providers to implement to prevent HTTP cache poisoning. [Akamai](http://www.akamai.com/), Amazon Web Services ([AWS](http://www.aws.amazon.com/)), and [Cloudflare](https://www.cloudflare.com/) are all affected by this issue.

  

**Multiple Intel Products Receive Security Updates** (01/14/2020)  
[Intel](http://www.intel.com/) released six security [advisories](https://www.intel.com/content/www/us/en/security-center/default.html) on January 14 to address vulnerabilities in various product lines. Among the issues is an information disclosure bug in the Data Analytics Acceleration Library that has been patched in version 2020 Gold.

  

**Multiple Security Bulletins Posted by Juniper Networks** (01/13/2020)  
[Juniper Networks](http://www.juniper.net/) issued multiple security [bulletins](https://kb.juniper.net/InfoCenter/index?page=content&channel=SECURITY_ADVISORIES) to address vulnerabilities across the vendor's product lines. At least eight of the bulletins pertain to security issues within Junos OS. Juniper product users should review the advisories and apply all updates immediately.

  

**Oracle Shoots Down 334 Vulnerabilities in Massive Batch of Fixes** (01/15/2020)  
Over 330 vulnerabilities have been eliminated following the release of [Oracle](http://www.oracle.com/)'s [Critical Patch Update](https://www.oracle.com/security-alerts/cpujan2020.html) for January. Flaws have been patched across multiple Oracle families, including MySQL, Fusion Middleware, E-Business Suite, Java SE, and more. In total, 334 bugs have been patched and Oracle recommends that users immediately apply the updates.

  

**Over 300K WordPress Sites Exposed to Attacks Thanks to Authentication Bypass** (01/15/2020)  
Two [WordPress](http://wordpress.org/) plugins, InfiniteWP Client and WP Time Capsule, [contain](https://www.webarxsecurity.com/vulnerability-infinitewp-client-wp-time-capsule/) logical flaws in their code that can enable anyone to log into an administrator account without a password. This discovery was made by the research team at [WebArx](https://www.webarxsecurity.com/) who noted that a combined 320,000 Web sites are vulnerable as a result.

  

**SAP Delivers Security Fixes on Monthly Patch Day** (01/15/2020)  
[SAP](http://www.sap.com/) [published](https://bartblaze.blogspot.com/2020/01/satan-ransomware-rebrands-as-5ss5c.html) six security notes and one advisory to cap its January batch of vulnerability patches. Among the most significant remediations is a fix for a cross-site scripting flaw in Rest Adapter of SAP Process Integration and a patch for a denial-of-service condition in NetWeaver Internet Communication Manager.

  

**Scientists Warn of Possible Collisions, Security Failures in SHA-1** (01/13/2020)  
Two researchers have [demonstrated](https://eprint.iacr.org/2020/014.pdf) a collision attack on the SHA-1 hash function which can enable criminals to create fraudulent digital certificates. This is similar to attacks that have been previously conducted on MD5. The scientists, Gaëtan Leurent and Thomas Peyrin, created their fake digital certificates using GNU Privacy Guard and a cluster of GPUs. They said, "This work shows once and for all that SHA-1 should not be used in any security protocol where some kind of collision resistance is to be expected from the hash function."

  

**Siemens Issues Multiple Advisories for Product Lines** (01/14/2020)  
Multiple [Siemens](http://www.siemens.com/) products have received [updates](https://new.siemens.com/global/en/products/services/cert.html#SecurityPublications) to mitigate vulnerabilities. Among the flaws discussed in its batch of advisories are authentication bypass, cross-site scripting, and mirror port isolation bugs in the SCALANCE X switches.

  

**Upgrade Mitigates Security Holes in OSIsoft PI Vision** (01/14/2020)  
OSIsoft's PI Vision, a visualization tool, is vulnerable to several security issues, including improper access control, cross-site scripting, and cross-site request forgery. The vendor recommends users upgrade to PI Vision 2019 to resolve these issues. Further details are available from an [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-20-014-06).

  

**VMware Releases Security Update** (01/14/2020)  
[VMware](http://www.vmware.com/) has released a security [update](https://www.vmware.com/security/advisories/VMSA-2020-0002.html) to fix a bug in VMware Tools. The vulnerability affects VMware Tools for Windows version 10.x.y. Users are instructed to update to version 11.0 or later.