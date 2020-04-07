---
title: 'Security Flaws & Fixes - W/E - 1/31/20'
date: 2020-01-31T11:47:00+01:00
draft: false
---

**Apple Security Releases Include Alleviation of 4 RCE tvOS Bugs** (01/28/2020)  
[Apple](http://www.apple.com/) released multiple updates to mitigate vulnerabilities within its products, including Safari, iOS, watchOS, and iTunes. Four of the bugs remedied are remote code execution flaws in tvOS - all are considered severe. Users should apply all updates or visit the vendor's [update page](https://support.apple.com/en-us/HT201222) for manual application.

  

**Attackers Come Knocking on Meeting Doors Thanks to Zoom Flaw** (01/28/2020)  
[Check Point Software](http://www.checkpoint.com/) researchers [identified](https://unit42.paloaltonetworks.com/the-fractured-statue-campaign-u-s-government-targeted-in-spear-phishing-attacks/) a technique which could allow a threat actor to potentially identify and join active [Zoom](http://www.zoom.com/) meetings. Zoom Meeting IDs are composed of 9, 10, or 11 digits and if either the "Require meeting password" option or Waiting Room feature are not enabled, the digits are the only capability preventing an unauthorized person from joining the meeting. Check Point determined that the Zoom Meeting IDs could be brute-forced. Zoom was notified about the issue on July 19 and has since rolled out changes to eliminate this attack scenario.

  

**CacheOut, L1DES: New Side-Channel Attack Method Impacts Intel's CPUs** (01/29/2020)  
[Intel](http://www.intel.com/) released an [advisory](https://www.intel.com/content/www/us/en/security-center/advisory/intel-sa-00329.html) after it was determined that another speculative execution attack method can be used to target systems running its processors. This method was first identified in 2018 when the Spectre and Meltdown zero-day vulnerabilities came to light. The attack has been dubbed [CacheOut ](https://cacheoutattack.com/)and [L1D Eviction Sampling](https://mdsattacks.com/#ridl-nng) and is capable of leaking data. Intel plans to release microcode updates to mitigate these issues and provided more details in a [blog post](https://blogs.intel.com/technology/2020/01/ipas-intel-sa-00329/#gs.vhee9s) and a [guidance document](https://software.intel.com/security-software-guidance/software-guidance/l1d-eviction-sampling).

  

**Check Point Finds Security Issues in Microsoft Azure** (01/30/2020)  
[Check Point Software](http://www.checkpoint.com/) shared [details](https://blog.checkpoint.com/2020/01/30/check-point-research-partners-with-microsoft-azure-to-create-a-safer-better-secured-cloud-infrastructure/) about vulnerabilities and attack vectors it found in [Microsoft](http://www.microsoft.com/) Azure Stack and Azure platforms. Using a chain of issues, the researchers could obtain screenshots and information about tenants and infrastructure machines in Azure Stack. Critical bugs were also uncovered in Azure App Service. Microsoft has since [mitigated](https://blog.checkpoint.com/2020/01/30/check-point-research-partners-with-microsoft-azure-to-create-a-safer-better-secured-cloud-infrastructure/) these issues.

  

**Cisco Fixes Critical Bugs in Products** (01/28/2020)  
A vulnerability in the Web-based management interface of [Cisco](http://www.cisco.com/) Small Business Smart and Managed Switches could allow an unauthenticated, remote attacker to conduct a cross-site request forgery attack on an affected system. The vendor has issued [updates](https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-20191016-sbss-csrf) to mitigate this bug. In a separate [advisory](https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-20200124-webex-unauthjoin), the vendor patched critical bug in Webex Meetings Suite sites and Webex Meetings Online sites. This vulnerability could enable an unauthenticated, remote attendee to join a password-protected meeting without providing the meeting password.

  

**Flaws, Misconfigurations Can Leave LoRaWAN Networks Exposed to Cyber Attacks** (01/28/2020)  
Cyber vulnerabilities in LoRaWAN, a wireless, low-power WAN protocol that is used for Internet of Things devices, could enable attacks, the research team at [IOActive](http://www.ioactive.com/) has [warned](https://act-on.ioactive.com/acton/attachment/34793/f-87b45f5f-f181-44fc-82a8-8e53c501dc4e/1/-/-/-/-/LoRaWAN%20Networks%20Susceptible%20to%20Hacking.pdf). The researchers noted that while usage of LoRaWAN is increasing and that it contains two layers of encryption, the protocol can be misconfigured, exposing it to attacks. Hard-coded keys can be culled from the devices using the protocol. The team said in its paper, "Once the keys are compromised, the LoRaWAN network becomes vulnerable, as the keys are the source of the network's only security mechanism, encryption. After reviewing vendor documentation, one may quickly realize that it is not difficult to obtain credentials for devices that are physically accessible."

  

**GE's Healthcare Products Vulnerable to Cyber Attacks** (01/28/2020)  
Multiple vulnerabilities have been detected in GE's CARESCAPE Telemetry Server, ApexPro Telemetry Server, CARESCAPE Central Station and Clinical Information Center systems, and CARESCAPE B450, B650, B850 Monitors. An [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsma-20-023-01) discusses mitigation processes. GE is developing software updates.

  

**In Spite of Protections, "Memory Lane" DMA Attacks Still Impact Devices** (01/29/2020)  
[Eclypsium](https://eclypsium.com/) [research](https://eclypsium.com/wp-content/uploads/2020/01/DMA-Attacks-A-Walk-Down-Memory-Lane.pdf) shows that enterprise laptops, servers, and cloud environments continue to be vulnerable to Direct Memory Access (DMA) attacks, even in the presence of protections such as UEFI Secure Boot, [Intel](http://www.intel.com/) Boot Guard, [HP](http://www.hp.com/) Sure Start, and [Microsoft](http://www.microsoft.com/) Virtualization-Based Security. DMA attacks enable a potential attacker to read and write memory off a victim system directly, bypassing the main CPU and operating system. By overwriting memory, attackers can gain control over kernel execution to perform malicious activity. The researchers refer to these attacks as "Memory Lane." A [blog post](https://eclypsium.com/2020/01/30/direct-memory-access-attacks/) discusses mitigations and vendor releases to prevent these attacks.

  

**New Version of OpenSMTPD Mitigates Critical Flaw** (01/29/2020)  
[Qualys](http://www.qualys.com/) [discovered](https://www.qualys.com/2020/01/28/cve-2020-7247/lpe-rce-opensmtpd.txt) a vulnerability in OpenSMTPD, OpenBSD's mail server. This vulnerability, exploitable since May 2018, allows an attacker to execute arbitrary shell commands. OpenBSD has issued an [advisory](https://www.mail-archive.com/misc@opensmtpd.org/msg04850.html) along with updates and recommends users immediately apply the patches.

  

**NSA Delivers Guide to Combat Cloud Vulnerabilities** (01/28/2020)  
The National Security Agency ([NSA](http://www.nsa.gov/)) released [guidance](https://media.defense.gov/2020/Jan/22/2002237484/-1/-1/0/CSI-MITIGATING-CLOUD-VULNERABILITIES_20200121.PDF) on mitigating cloud vulnerabilities. The guide divides cloud vulnerabilities into four classes (misconfiguration, poor access control, shared tenancy vulnerabilities, and supply chain vulnerabilities) and provides descriptions of each vulnerability class along with the most effective mitigations to help organizations lock down their cloud resources.

  

**Outdated SCPI Protocol Widely Used for Test and Measurement Highly Insecure** (01/29/2020)  
[Trend Micro](http://www.trendmicro.com/) [analyzed](https://blog.trendmicro.com/trendlabs-security-intelligence/security-analysis-of-devices-that-support-scpi-and-visa-protocols/) the Standard Commands for Programmable Instruments (SCPI) legacy protocol, which was first released in 1990, and determined that although it is in wide use, its lack of authentication leaves it exposed to possible cyber attacks. SCPI is used in test and measurement devices and is considered simple to use but because it connects devices to the Internet, it can leak data.

  

**Updates for Magento Alleviate 30+ Security Bugs** (01/29/2020)  
Magento 2.3.4 has been [released](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-4-open-source.html) to patch more than 30 security issues. The update closes cross-site scripting and remote code execution vulnerabilities.

  

**Vulnerable E-Scooters Pose Security Risk to Rider's Private Data** (01/29/2020)  
New research from the University of Texas at San Antonio ([UTSAA](https://www.utsa.edu/)) finds micromobility vehicles, such as e-scooters, have security and privacy risks as a result of their software services and applications. Hackers can cause a series of attacks, including eavesdropping on users and spoofing of GPS systems to direct riders to unintended locations. Vendors of e-scooters can suffer denial-of-service attacks and data leaks. Some e-scooter models communicate with the rider's smartphone over a Bluetooth Low Energy channel. Someone with malicious intent could eavesdrop on these wireless channels and listen to data exchanges between the scooter and riders' smartphone app.