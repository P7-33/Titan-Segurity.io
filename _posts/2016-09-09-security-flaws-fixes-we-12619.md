---
title: 'Security Flaws & Fixes - W/E - 12/6/19'
date: 2019-12-06T15:13:00+01:00
draft: false
---

**ABB Fixes Vulnerabilities in Relion 650 Series and 670 Series** (11/26/2019)  
A vulnerability in ABB's Relion 650 Series and 670 Series, if exploited, could result in a reboot of the device and lead to a denial-of-service condition. Updates to the products are [available](https://search.abb.com/library/Download.aspx?DocumentID=9AKK107492A9256&LanguageCode=en&DocumentPartId=&Action=Launch). A second bug, a path traversal issue, exists in the Relion 670 Series. An attacker who successfully exploited this vulnerability could retrieve any file on the device's flash drive without authentication on the device or make the product inoperative by deleting files from the device's flash drive. [Updates](https://search.abb.com/library/Download.aspx?DocumentID=9AKK107492A9255&LanguageCode=en&DocumentPartId=&Action=Launch) have been released to mitigate this issue.

  

**Bug in Magento Marketplace Impacted Unknown Number of Accounts** (12/02/2019)  
[Adobe](http://www.adobe.com/) has [advised](https://magento.com/blog/magento-news/magento-marketplace-security-update) that a vulnerability affecting Magento Marketplace may have impacted some of the site's account holders. To address the bug, Adobe took the marketplace offline and delivered a patch. It is unclear how many accounts were breached. Magento is owned by Adobe

  

**GIF Processing Bug Affects Thousands of Android Apps** (11/26/2019)  
[Trend Micro](http://www.trendmicro.com/) [warned](https://blog.trendmicro.com/trendlabs-security-intelligence/patched-gif-processing-vulnerability-cve-2019-11932-still-afflicts-multiple-mobile-apps/) that thousands of Android apps could be impacted by a GIF processing flaw that has been patched in WhatsApp for Android. The underlying problem lies in the library called libpl\_droidsonroids\_gif.so, which is part of the android-gif-drawable package. Many apps continue to use the older version of this library and thus remain at risk. [Facebook](http://www.facebook.com/) patched this issue in its WhatsApp for Android.

  

**Google Bashes Three Critical Android Bugs in Monthly Security Release** (12/03/2019)  
[Google](http://www.google.com/)'s December [Android Security Bulletin](https://source.android.com/security/bulletin/2019-12-01) mitigates at least 20 vulnerabilities including three that have been marked as critical issues. These include a bug in Framework that could enable a remote attacker using a specially crafted message to cause a permanent denial-of-service and two remote code execution vulnerabilities in Media Framework.

  

**HackerOne Discloses Leaked Session Cookie that Led to Account Takeover** (12/04/2019)  
[HackerOne](https://hackerone.com/) was [notified](https://hackerone.com/reports/745324) by a community member in its bug bounty program that the member had accessed a HackerOne Security Analyst's HackerOne account. A session cookie was disclosed due to a human error, which led to the white hat hacker being able to access the account. The individual could then access private customer reports. Upon analysis, the session cookie was revoked and access to the account was blocked. Impacted customers were alerted that their information was viewable to the hacker who submitted the vulnerability.

  

**Kaspersky Finds 37 Vulnerabilities in Virtual Network Computing Systems** (11/26/2019)  
[Kaspersky](http://www.kaspersky.com/) has presented an [analysis](https://ics-cert.kaspersky.com/reports/2019/11/22/vnc-vulnerability-research/) of open-source Virtual Network Computing (VNC) which uncovered memory corruption vulnerabilities that existed in a number of projects for a significant period of time. According to shodan.io, the exploitation of some detected vulnerabilities could lead to remote code execution affecting the users of VNC systems, which amounts to over 600,000 servers accessible from the global network. VNC systems are used in automated industrial facilities enabling remote control of systems and approximately 32% of industrial network computers having some form of remote administration tools, including VNC. Kaspersky researchers studied various VNC systems including LibVNC, UltraVNC, TightVNC1.X, and TurboVNC and found 37 various vulnerabilities. Some bugs were discovered on the client while others were found on the server.

  

**Kaspersky Patches Critical Bugs in Secure Connection** (12/03/2019)  
[SafeBreach](https://safebreach.com/) [discovered](https://safebreach.com/Post/Kaspersky-Secure-Connection-DLL-Preloading-and-Potential-Abuses-CVE-2019-15689) a vulnerability in [Kaspersky](http://www.kaspersky.com/) Secure Connection. The bug can be exploited to allow an attacker to achieve signed code execution, persistence and in some cases defense evasion. It could also enable attackers to implant an arbitrary unsigned executable, executed by a signed service that runs as NT AUTHORITY\\SYSTEM. Secure Connection is deployed with multiple Kaspersky products. SafeBreach notified Kaspersky of the bug in July and it was [patched](https://support.kaspersky.com/13494) on November 21.

  

**Microsoft Advises on Cleaning Up Orphaned Keys Generated on Vulnerable TPMs** (12/05/2019)  
[Microsoft](http://www.microsoft.com/) is aware of an issue in Windows Hello for Business (WHfB) with public keys that persist after a device is removed from Active Directory (AD), if the AD exists. After a user sets up Windows Hello for Business (WHfB), the WHfB public key is written to the on-premises AD. The WHfB keys are tied to a user and a device that has been added to Azure AD, and if the device is removed, the corresponding WHfB key is considered orphaned. However, these orphaned keys are not deleted even when the device it was created on is no longer present. Attacks are possible so Microsoft provided [guidance](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV190026) for cleaning up any orphaned public keys that were generated with an unpatched trusted platform module.

  

**Microsoft Fixes Bug that Could Allow Azure Account Takeover** (12/03/2019)  
[CyberArk](https://www.cyberark.com/) researchers [uncovered](https://www.cyberark.com/threat-research-blog/blackdirect-microsoft-azure-account-takeover/) a vulnerability that allows for the takeover of [Microsoft](http://www.microsoft.com/) Azure Accounts and affects specific OAuth 2.0 applications. The vulnerability allows the creation of tokens with the victim's permissions and could potentially allow a malicious attacker access and control of a victim's account and take actions on his or her behalf. CyberArk calls this bug "BlackDirect" and warned that there are two attack vectors: zero-click and one-click. After reporting the bug, Microsoft issued a fix on November 20.

  

**Moxa AWK-3121 Is No More - Secure Replacement Available** (12/03/2019)  
Multiple product vulnerabilities were identified in Moxa's AWK-3121 Series. This product has since been phased out by the vendor and replaced with model AWK-1131A . Further information is available from an [advisory](https://www.moxa.com/en/support/support/security-advisory/awk-3121-series-industrial-ap-bridge-client-vulnerabilities).

**Mozilla Updates Firefox, Firefox ESR** (12/04/2019)

[Mozilla](http://www.mozilla.org/) released new versions of [Firefox](https://www.mozilla.org/en-US/security/advisories/mfsa2019-36/) and [Firefox ESR](https://www.mozilla.org/en-US/security/advisories/mfsa2019-37/). Firefox 71 alleviates five critical vulnerabilities including a use-after-free bug of SFTKSession object.

  

**Patched SSRF Vulnerability in Jira Servers Continues to Impact Public Cloud Providers** (11/27/2019)  
[Palo Alto Networks](http://www.paloaltonetworks.com/)' researchers [assessed](https://unit42.paloaltonetworks.com/server-side-request-forgery-exposes-data-of-technology-industrial-and-media-organizations/) the Jira server-side request forgery (SSRF) vulnerability on six public cloud service providers (CSPs) and found the following: 7,002 Jira instances exposed to the Internet in public clouds; 3,152 of the vulnerable Jira instances are impacted by the bug; and 1,779 of the vulnerable hosts leak cloud infrastructure metadata. SSRF is a Web application vulnerability that redirects malicious requests to resources that are restricted to the server. The Jira SSRF vulnerability, which can be exploited without authentication, was identified in August and an update was released. However, a scan found that about 25,000 Jira deployments remain exposed. The researchers chose six CSPs, each with a high number of Jira deployments, to study and found 7,002 Jira instances in those six providers.

  

**Timestamp Y2K-Style Bug Leaves Splunk Confused on Dates** (11/27/2019)  
It is [recommended](https://docs.splunk.com/Documentation/Splunk/8.0.0/ReleaseNotes/FixDatetimexml2020) that Splunk administrators update their platforms immediately to mitigate a bug that is unable to recognize timestamps from events where the date contains a two-digit year. This vulnerability will be viable on January 1, 2020 and affects all un-patched Splunk platform instance types, on any operating system. On unpatched Splunk platform instances, the file supports the extraction of two-digit years of "19," up to December 31, 2019. Beginning on January 1, 2020, these un-patched instances will mistakenly treat incoming data as having an invalid timestamp year, and could either add timestamps using the current year, or misinterpret the date incorrectly and add a timestamp with the misinterpreted date. Splunk analyzes machine-generated big data.

  

**Upgrade Boots Security Issue in Reliable Controls LicenseManager** (12/03/2019)  
Reliable Controls' LicenseManager is impacted by a bug that could allow an attacker to crash the system, view sensitive data, or execute arbitrary commands, an [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-337-01) states. An authenticated user may be able to insert malicious code into the system root path, which may allow execution of code with elevated privileges of the application. Reliable Controls has released RC-LicenseManager Version 3.5, which is bundled for use within the latest RC-Studio software.

  

**Zero-Day StrandHogg Bug Abused by Malicious Android Apps** (12/02/2019)  
Norweigan security company [Promon](https://promon.co/) [uncovered](https://promon.co/security-news/strandhogg/) StrandHogg, an Android vulnerability that allows malware to masquerade as legitimate apps. All Android versions are affected, the top 500 most popular apps are at risk, and the bug can be exploited without root access. The vulnerability makes it possible for a malicious app to ask for permissions while pretending to be the legitimate app. An attacker can ask for access to any permission but the victim assumes he or she is giving the app access and is unaware that the attacker has been granted permission. By exploiting this vulnerability, a malicious app installed on the device can attack the device and trick it so that when the app icon of a legitimate app is clicked, a malicious version is instead displayed on the user's screen. When the victim inputs his or her login credentials within this interface, sensitive details are immediately sent to the attacker, who can then login to, and control, security-sensitive apps. [Lookout](https://www.lookout.com/) has identified 36 malicious apps exploiting the vulnerability. Among them were variants of the BankBot banking Trojan observed as early as 2017.