---
title: 'Security Flaws & Fixes - W/E - 2/7/20'
date: 2020-02-07T17:18:00+01:00
draft: false
---

**Android Receives 25 Mitigations in February's Security Bulletin** (02/05/2020)  
[Google](http://www.google.com/) released the February [Android Security Bulletin](https://source.android.com/security/bulletin/2020-02-01.html) to alleviate 25 vulnerabilities in the operating system. Two bugs, an information disclosure and a remote code execution, have been rated critical and both can be found in Android's System component.

  

**Credential Exposure Possible in AutomationDirect C-More Touch Panels** (02/04/2020)  
AutomationDirect's C-More Touch Panels EA9 Series, a software management platform, can unmask its credentials and leak data, which may allow an attacker to remotely access the system and manipulate system configurations. Users should upgrade to Version 6.53. The [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) issued an [advisory](https://www.us-cert.gov/ics/advisories/icsa-20-035-01) with further information regarding this security issue.

  

**Critical Cisco Discovery Protocol Bugs Expose Routers, Phones, Cameras** (02/05/2020)  
The scientists at [Armis](https://www.armis.com/) [discovered](https://www.armis.com/cdpwn/) five zero-day vulnerabilities in various implementations of the [Cisco](http://www.cisco.com/) Discovery Protocol (CDP) that can allow remote attackers to completely take over devices without any user interaction. This discovery has been dubbed "CDPwn," CDP is a Cisco proprietary Layer 2 (Data Link Layer) network protocol that is used to discover information about locally attached Cisco equipment. CDP is implemented in Cisco switches, routers, IP phones, and cameras. The CERT Coordination Center issued its own [advisory](https://kb.cert.org/vuls/id/261385/) regarding CDPwn.

  

**DHS Directives Require Some Improvement** (02/04/2020)  
The Government Accountability Office ([GAO](http://www.gao.gov/)) was asked to evaluate the Department of Homeland Security's ([DHS](http://www.dhs.gov/)) binding operational directives. These directives require agencies to safeguard federal information and information systems from a known or reasonably suspected information security threat, vulnerability, or risk. In its [analysis](https://www.gao.gov/assets/710/704253.pdf) the GAO found that the agencies and the DHS didn't always complete the directives' actions on time. The DHS also did not consistently ensure that agencies fully complied with the directives. The GAO has made four recommendations, which include that the Secretary of Homeland Security should ensure that the binding operational directive performance metric for addressing vulnerabilities identified by high value asset assessments aligns with the process DHS has established.

  

**DoS, Data Leak Bugs Found in Mini-SNMPD** (02/04/2020)  
[Cisco](http://www.cisco.com/)'s Talos research team [discovered](https://blog.talosintelligence.com/2020/02/vuln-spotlight-mini-snmpd-feb-2020.html) that multiple vulnerabilities exist in Mini-SNMPD, a lightweight implementation of a Simple Network Management Protocol (SNMP) server. An attacker can exploit these bugs by providing a specially crafted SNMPD request to the user. These vulnerabilities could lead to a variety of conditions, potentially resulting in the disclosure of sensitive information and a denial-of-service condition. Mini-SNMPD has released an [update](https://github.com/troglobit/mini-snmpd/releases/tag/v1.5), following notification from Talos.

  

**Google Admits to Accidentally Routing Users' Exported Videos to Strangers** (02/04/2020)  
[Google](http://www.google.com/) has confirmed that a worrisome and embarrassing bug appears to have caused some users' attempts to export their videos to result in those movie files being sent to complete strangers. The blunder, which was verified via an [email](https://twitter.com/jonoberheide/status/1224525738268905477?s=20) sent to account holders, impacted users that attempted to export their media via the Google Takeout tool, an application designed to allow Google Photos users to transport their data elsewhere. Instead of the filed being sent to the correct recipients, the data was instead routed to a random other user. The company noted that the issue continued during a five day period, running from November 21st to November 25th, 2019. While the search giant claims that only 0.01 percent of Photos users were affected, the potential embarrassment and privacy loss that could result for those few unlucky users is immense. Google claims it will directly notify anyone that may have been impacted by the issue. It also warns that backups which were made during the aforementioned period may be incomplete, and suggests that users back their data up again if they believe they may have been impacted.

  

**Google Chrome 80 Resolves 50+ Security Issues** (02/06/2020)  
[Google](http://www.google.com/) [released](https://chromereleases.googleblog.com/2020/02/stable-channel-update-for-desktop.html) Chrome version 80 and includes 56 security fixes. Among the issues rated "high" by the vendor are updates for an integer overflow in JavaScript and fixes for multiple bugs in XML and SQLite.

  

**Medtronic Corrects Vulnerabilities in Cardiac Devices** (02/04/2020)  
Medtronic released [updates](https://global.medtronic.com/xg-en/product-security/security-bulletins.html) to fix some vulnerabilities in its cardiac devices. The bugs were originally disclosed in 2018 and 2019. Issues had been reported in the Conexus Telemetry and Monitoring Accessories and the CareLink 2090 and CareLink Encore 29901 Programmers.

  

**Security Updates Available for Magento** (02/04/2020)  
[Adobe](http://www.adobe.com/) released [updates](https://global.medtronic.com/xg-en/product-security/security-bulletins.html) to mitigate vulnerabilities that could lead to an arbitrary code execution condition in Magento. Updates are available for Magento Commerce and Open Source edition.

  

**Survey Finds Insecure Government Web Sites Leading Up to 2020 Election** (02/04/2020)  
A [McAfee](http://www.mcafee.com/) survey revealed a lack of US government .GOV validation and HTTPS encryption among county election Web sites in 13 states projected to be critical in the 2020 US Presidential Election. The survey found that as many as 83.3% of these county sites lacked .GOV validation across these states, and 88.9% and 90.0% of sites lacked such certification in Iowa and New Hampshire respectively. Such shortcomings could make it possible for malicious actors to establish false government Web sites and use them to spread false election information that could influence voter behavior and even impact final election results.

  

**Vulnerable Version of WhatsApp for Desktop Leaked User Files** (02/05/2020)  
Researcher Gal Weizman [uncovered](https://www.perimeterx.com/tech-blog/2020/whatsapp-fs-read-vuln-disclosure/) vulnerabilities in [WhatsApp](http://www.whatsapp.com/) Desktop when paired with WhatsApp for iPhone that allowed cross-site scripting and local file reading. [Facebook](http://www.facebook.com/) has [patched](https://www.facebook.com/security/advisories/cve-2019-18426) the bugs.