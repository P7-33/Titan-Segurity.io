---
title: 'Security Flaws & Fixes - W/E - 11/1/19'
date: 2019-11-01T14:17:00+01:00
draft: false
---

**Apple Pushes Out Fixes for Bugs Across Multiple Products** (10/30/2019)  
[Apple](http://www.apple.com/) released multiple advisories to address vulnerabilities across its products. Updates are available for [iTunes](https://support.apple.com/kb/HT210726), [iCloud for Windows 11.0](https://support.apple.com/kb/HT210727), [iCloud for Windows 7.15](https://support.apple.com/kb/HT210728), [macOS Catalina](https://support.apple.com/kb/HT210722), [watchOS](https://support.apple.com/kb/HT210724), [Safari](https://support.apple.com/kb/HT210725), [iOS and iPad OS](https://support.apple.com/kb/HT210721), and [tvOS](https://support.apple.com/kb/HT210723).

  

**Arbitrary Code Execution, Other Security Issues Possible in PHP** (10/30/2019)  
The Multi-State Information Sharing and Analysis Center ([MS-ISAC](https://www.cisecurity.org/)) issued an [advisory](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-116/) regarding multiple vulnerabilities in PHP. Successfully exploiting the most severe of these vulnerabilities could allow for arbitrary code execution in the context of the affected application. It is also possible for an attacker to install programs, view, change, or delete data, or create new accounts with full user rights. Failed exploitation could result in a denial-of-service condition.

  

**Configuration File Access Control Bug Detected in Honeywell IP-AK2 Access Control Panel** (10/29/2019)  
A vulnerability was [discovered](https://buildings.honeywell.com.cn/-/media/hbtcn/products-technologies/4security-access-control-system/2win-pak-access-control-solutions/pro3000/sb2018ipak2-eng-pdf.pdf) in [Honeywell](http://www.honeywell.com/)'s IP-AK2 Access Control Panel (version 1.04.07 and prior), that enabled an unauthenticated user to download configuration files. Honeywell recommends that users upgrade to version 1.04.15 to mitigate the vulnerability in any installed and operational system.

  

**End-of-Support Software List Released** (10/30/2019)  
The Multi-State Information Sharing and Analysis Center ([MS-ISAC](https://www.cisecurity.org/)) has released an end-of-support software report [list](https://www.cisecurity.org/blog/end-of-support-software-report-list-2/). The document details products from various vendors including [IBM](http://www.ibm.com/), [Adobe](http://www.adobe.com/), [Microsoft](http://www.microsoft.com/), [Oracle](http://www.oracle.com/), and more.

  

**Mitigation Methods Required to Secure Automation Worx Software Suite** (10/29/2019)  
The [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) has [warned](https://www.us-cert.gov/ics/advisories/icsa-19-302-01) about an improper input validation bug in Phoenix Contact's Automation Worx Software Suite. Successful exploitation of this vulnerability could compromise the availability, integrity, or confidentiality of an application programming workstation. Phoenix Contact is in the process of developing an updated version of this product. Until then, it is strongly recommended that users exchange project files using only secure file exchange services, and that project files not be exchanged via unencrypted email.

  

**Moxa Addresses Bugs in Ethernet Switches** (10/29/2019)  
Multiple product vulnerabilities were identified in [Moxa](https://www.moxa.com/)'s EDS-405A Series, EDS-408A Series, EDS-510A Series, and IKS-G6824A Series Ethernet Switches. In response, the vendor has developed related [solutions](https://www.moxa.com/en/support/product-support/security-advisory/eds-405a-series-eds-408a-series-eds-510a-series-and-iks-g6824a-series-ethernet-switches-vulnerabilities) to address the vulnerabilities.

  

**NGINX Servers Vulnerable to RCE Via PHP Bug** (10/29/2019)  
NGINX servers are affected by a buffer underflow vulnerability in PHP that could allow for a remote code execution but only if the servers have PHP-FPM enabled. While the issue has been [patched](https://bugs.php.net/patch-display.php?bug_id=78599&patch=0001-Fix-bug-78599-env_path_info-underflow-can-lead-to-RC.patch&revision=latest), the bug is being exploited, researchers at Wallarm [warn](https://bugs.php.net/patch-display.php?bug_id=78599&patch=0001-Fix-bug-78599-env_path_info-underflow-can-lead-to-RC.patch&revision=latest)

  

**Philips IntelliSpace Perinatal Vulnerable to Information Exposure** (10/29/2019)  
A bug detected in Philips' IntelliSpace Perinatal, an obstetrics information management system, may enable an unauthorized attacker with physical access to a locked application screen, or an authorized remote desktop session host application user to break-out from the containment of the application and access unauthorized resources from the Windows operating system as the limited-access Windows user. This information was made possible via an [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsma-19-297-01). Risk mitigations are noted.

  

**Samba Releases Updates** (10/29/2019)  
Three [patches](https://www.samba.org/samba/history/security.html) have been released for [Samba](http://us4.samba.org/samba/). The patches mitigate security holes in prior versions and users have been instructed to immediately apply the updates.

  

**Vulnerabilities in Rittal Chiller SK 3232-Series Can Result in Temperature Changes** (10/29/2019)  
Two vulnerabilities in Rittal Chiller SK 3232-Series, which is intended for cooling IT applications, have been described in an [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-297-01). Successful exploitation of these vulnerabilities could disrupt the primary operations of the affected component, shut down cooling to other equipment, and allow changes to the temperature set point. It is not clear if updates have been released for mitigation purposes.