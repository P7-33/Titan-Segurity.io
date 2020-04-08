---
title: 'Security Flaws & Fixes - W/E - 12/20/19'
date: 2019-12-20T13:41:00+01:00
draft: false
---

**Critical Vulnerabilities Found in Barco's ClickShare Wireless Presentation System** (12/16/2019)  
[F-Secure](http://www.f-secure.com/) has [discovered](https://labs.f-secure.com/advisories/multiple-vulnerabilities-in-barco-clickshare) several exploitable vulnerabilities in Barco's ClickShare wireless presentation system. Attackers can use the flaws to intercept and manipulate information during presentations, steal passwords and other confidential information, and install backdoors and other malware. While exploiting some of the vulnerabilities requires physical access, others can be done remotely if the system uses its default settings. ClickShare is a collaboration tool that helps groups of people present content from different devices. Barco was notified on October 9 of the vulnerabilities and released firmware updates on December 16 to fix the issues.

  

**Malicious Messages Can Lead to Crash of WhatsApp Group Chat** (12/17/2019)  
[Check Point Software](http://www.checkpoint.com/) [helped](https://research.checkpoint.com/2019/breakingapp-whatsapp-crash-bug) mitigate a new vulnerability in [WhatsApp](http://www.whatsapp.com/) that could allow a threat actor to deliver a malicious group chat message that would crash the app for all members of the group. To regain use of WhatsApp, users would need to uninstall and reinstall it, then delete the group which contains the message. The bug was discovered when Check Point inspected the communications between WhatsApp and WhatsApp Web, the Web version of the app which mirrors all messages sent and received from the user's phone. This enabled researchers to see the parameters used for WhatsApp communications and manipulate them.

  

**Microsoft Advises on SharePoint Server Data Leak Vulnerability** (12/18/2019)  
[Microsoft](http://www.microsoft.com/) issued an out-of-band security [advisory](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2019-1491) and an update to address an information leakage bug in SharePoint Server. An attacker who exploited this vulnerability could read arbitrary files on the server. The update addresses the vulnerability by changing how affected application programming interfaces process requests.

  

**New Version of Advantech DiagAnywhere Server Alleviates Vulnerability** (12/16/2019)  
An [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-346-01) warns of a stack-based buffer overflow in Advantech's DiagAnywhere Server, which is used for remotely monitoring and controlling other Windows based devices. Advantech has phased out DiagAnywhere Server Version 3.07.11 and has released Version 3.07.14 of DiagAnywhere Server to address the reported vulnerability.

  

**Omron Addresses Vulnerabilities in Its CPU Programmable Logic Controllers** (12/16/2019)  
Omron posted an [advisory](http://www.omron-cxone.com/security/2019-12-06_PLC_EN.pdf) regarding its CS, NJ, and CJ series CPU programmable logic controllers due to vulnerabilities in the FINS communication protocol and the FTP function. The advisory details mitigation techniques.

  

**TP-Link Archer Router Bug Gives Attackers Admin Privileges** (12/18/2019)  
A critical vulnerability in the firmware of a router used in both homes and enterprises can enable remote attacker to take control of the router's configuration via Telnet on the LAN and connect to an FTP server through the LAN or WAN. [IBM](http://www.ibm.com/) X-Force Red's Grzegorz Wypych [identified](https://securityintelligence.com/posts/tp-link-archer-router-vulnerability-voids-admin-password-can-allow-remote-takeover/) the bug in TP-Link Archer C5 v4 router firmware. This flaw can grant an unauthorized third-party access to the router with admin privileges, which are the default on the device for all users, without proper authentication taking place. TP-Link has issued patches.

  

**Use-After-Free Bug Squashed in Google Chrome** (12/18/2019)  
[Google](http://www.google.com/) plugged a security vulnerability in Chrome with the release of version 79.0.3945.88 for Windows, Mac, and Linux. The new version fixes a use-after-free bug in media picker.

  

**Vulnerabilities Found in Pre-Installed ASUS, Acer Software** (12/18/2019)  
Security researchers at [SafeBreach](https://safebreach.com/) [discovered](https://safebreach.com/Post/Acer-Quick-Access-DLL-Search-Order-Hijacking-and-Potential-Abuses-CVE-2019-18670) a vulnerability in [Acer](http://www.acer.com/) Quick Access software that can achieve persistence, defense evasion, and, in some cases, privilege escalation by loading an arbitrary unsigned DLL into a service that runs as SYSTEM. Quick Access is a software which is preinstalled on most Acer PCs running Windows. In a separate [advisory](https://safebreach.com/Post/ASUS-ATK-Package-Unquoted-Search-Path-and-Potential-Abuses-CVE-2019-19235), SafeBreach details an unquoted search path bug in [Asus](http://www.asus.com/) ATK Package that comes pre-installed on ASUS computers. This bug can cause persistence and also evade detection. Both Acer and ASUS have released patches for these vulnerabilities.

  

**XSS Vulnerability Resolved in GE S2020/S2020G Fast Switch 61850** (12/16/2019)  
An [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-351-01) recommends that users of [GE](http://www.ge.com/)'s S2020/S2020G Fast Switch 61850 update to Version 07A04 due to a cross-site scripting bug. Successful exploitation of this vulnerability may allow an attacker to inject arbitrary code and allow disclosure of sensitive data.