---
title: 'Security Flaws & Fixes - W/E - 10/11/19'
date: 2019-10-11T16:03:00+01:00
draft: false
---

**Android Receives Security Updates from Google, Qualcomm** (10/09/2019)  
Three critical flaws in Android's Media framework, which could result in remote code execution, have been fixed in [Google](http://www.google.com/)'s October release of [patches](https://source.android.com/security/bulletin/2019-10-01). Nine bulletins comprise this release from Google and [Qualcomm](http://www.qualcomm.com/), which supplies the chips for Android devices, has also released patches for 18 vulnerabilities - eight of which have been deemed critical bugs.

  

**Apple Releases New Versions of iCloud, iTunes, macOS Catalina** (10/09/2019)  
[Apple](http://www.apple.com/) released [iCloud for Windows 7.14](https://support.apple.com/en-us/HT210637), [iCloud for Windows 10.7](https://support.apple.com/en-us/HT210636), [iTunes 12.10.1 for Windows](https://support.apple.com/en-us/HT210635), and [macOS Catalina 10.15](https://support.apple.com/en-us/HT210634). All updates mitigate vulnerabilities in prior versions.

**Cisco Publishes Bundled Security Advisory for ASA, FMC, and FTD Software** (10/07/2019)  
[Cisco](http://www.cisco.com/) released an [advisory collection](https://tools.cisco.com/security/center/viewErp.x?alertId=ERP-72541) to address 18 vulnerabilities in ASA Software, FMC Software, and FTD Software. Successful exploitation of the vulnerabilities could allow an attacker to gain unauthorized access, gain elevated privileges, execute arbitrary commands, or cause a denial-of-service condition on an affected device. Cisco posted updates to mitigate these vulnerabilities.

  

**Cobham EXPLORER 710 Satcom Terminals Could Leak Data** (10/09/2019)  
The CERT Coordination Center [warned](https://kb.cert.org/vuls/id/719689/) that the Cobham EXPLORER 710, a portable satellite terminal, contains multiple vulnerabilities affecting both the device and the firmware, some of which could allow an unauthenticated, local attacker to gain access to sensitive information or complete control of the device. The affected firmware version is 1.07. The vulnerabilities have not yet been patched.

  

**D-Link Says to Replace Outdated Routers Impacted by DoS Bugs** (10/09/2019)  
The National Vulnerability Database issued an [advisory](https://nvd.nist.gov/vuln/detail/CVE-2019-16920) for an unpatched remote code execution condition in [D-Link](http://www.dlink.com/) routers such as DIR-655C, DIR-866L, DIR-652, and DHP-1565. The issue occurs when an attacker sends an arbitrary input to a "PingTest" device common gateway interface that could lead to common injection. An attacker who successfully triggers the command injection could achieve full system compromise. D-Link [responded](https://supportannouncement.us.dlink.com/announcement/publication.aspx?name=SAP10124), saying that the impacted devices are considered end-of-life and replacement of the devices is recommended.

  

**DoS Vulnerabilities Patched in Beckhoff TwinCAT PLC Environment** (10/09/2019)  
[Rapid7](http://www.rapid7.com/) researcher Andreas Galauner [discovered](https://blog.rapid7.com/2019/10/08/r7-2019-32-denial-of-service-vulnerabilities-in-beckhoff-twincat-plc-environment-fixed/) two vulnerabilities affecting the TwinCAT PLC environment - a denial-of-service (DoS) condition resulting from a divide-by-zero error when processing a malformed UDP packet and a DoS condition by removing a routing table after processing an empty UDP packet. TwinCAT is a PLC runtime from Beckhoff that runs on top of Windows and extends the Windows kernel with real-time capabilities. This runtime is used to perform typical industrial control tasks for use in machines or other industrial processes. Beckhoff has addressed both vulnerabilities.

  

**GE Mark VIe Controller Impacted by Two Critical Bugs** (10/09/2019)  
An [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-281-02) states that all versions of the [GE](http://www.ge.com/) Mark VIe Controller are affected by an improper authentication or use of hard-coded credential vulnerabilities. Some versions are affected by both. Successful exploitation of these vulnerabilities could allow an attacker to create read/write/execute commands within the Mark VIe control system. Mitigations are available.

  

**Google Addressing Re-Emergence of "Zero-Day" Flaw on New Devices** (10/07/2019)  
[Google](http://www.google.com/) is [addressing](https://bugs.chromium.org/p/project-zero/issues/list?q=label:CCProjectZeroMembers) a number of reported instances of a re-emerging Android "Zero-Day" flaw. The recently uncovered vulnerability, which is being called "Issue 1942," deals with the binder driver and can be used to give an outsider root access. The renewed "Zero-Day" is believed to affect Android 8 and newer units from - per [reports](https://www.zdnet.com/article/google-finds-android-zero-day-impacting-pixel-samsung-huawei-xiaomi-devices/) - Google, [Samsung](http://www.samsung.com/), [Huawei](http://www.huawei.com/), and [Xiaomi](https://www.mi.com/global). As noted in particular by [ZDNet](http://www.zdnet.com/), Google had previously patched the flaw in "older Android OS versions."

  

**Intel Release Security Updates** (10/09/2019)  
Advisories for [Intel](http://www.intel.com/)'s [Active System Console](https://www.intel.com/content/www/us/en/security-center/advisory/intel-sa-00261.html). [Smart Connect Technology for Intel NUC](https://www.intel.com/content/www/us/en/security-center/advisory/intel-sa-00286.html), and [NUC](https://www.intel.com/content/www/us/en/security-center/advisory/intel-sa-00296.html). Issues include escalation of privilege and denial-of-service. Intel released updates for the products except for Smart Connect Technology for Intel NUC, which has been discontinued.

  

**Legacy Sunny WebBox Firmware Vulnerable to CSRF Condition** (10/09/2019)  
A cross-site request forgery impacts SMA Solar Technology's Sunny WebBox firmware and may allow an attacker to generate a denial-of-service condition, modify passwords, enable services, achieve man-in-the-middle, and modify input parameters associated with devices such as sensors. SMA recommends deactivation of port forwarding as it is not required for monitoring PV systems via the SMA Sunny Portal. The product is considered end-of-life. An [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-281-01) illustrates all details regarding this vulnerability.

  

**Microsoft Patches Close to 60 Holes in Windows, Office, Other Products** (10/09/2019)  
At least fifty-nine security issues have been resolved thanks to [Microsoft](http://www.microsoft.com/)'s [batch](https://portal.msrc.microsoft.com/en-us/security-guidance/releasenotedetail/28ef0a64-489c-e911-a994-000d3a33c573) of fixes released on October 8. Among the products updated are Windows, Internet Explorer, Edge, ChakraCore, Office, and Dynamics 365. Microsoft patched a Remote Desktop Client flaw that could have enabled a malicious server to take over a Windows machine that was connected to it. Included in the compilation of patches is an emergency update for Internet Explorer that was originally released earlier but caused printer errors for some users. The latest release of that patch remedies those issues.

  

**Microsoft Posts Out-of-Band Mandatory Fix for Internet Explorer** (10/07/2019)  
[Microsoft](http://www.microsoft.com/) issued an out-of-band [bulletin](https://support.microsoft.com/en-us/help/4524147/windows-10-update-kb4524147?ranMID=43674&ranEAID=je6NUbpObpQ&ranSiteID=je6NUbpObpQ-L8ZsF_FDt_Z6QqIjOXt3aw&epi=je6NUbpObpQ-L8ZsF_FDt_Z6QqIjOXt3aw&irgwc=1&OCID=AID2000142_aff_7795_1243925&tduid=(ir__s9qawxtctokfrjhxkk0sohzn0n2xgkjwahzf1qla00)(7795)(1243925)(je6NUbpObpQ-L8ZsF_FDt_Z6QqIjOXt3aw)()&irclickid=_s9qawxtctokfrjhxkk0sohzn0n2xgkjwahzf1qla00) to complete a patch that was released earlier and remedies a critical scripting engine flaw in Internet Explorer. This bulletin corrects an issue that was experienced by users in the September release. Microsoft warned, "This is a required security update that expands the out-of-band update dated September 23, 2019."

  

**Multiple VPN Products Exploited by Threat Groups** (10/07/2019)  
The UK's National Cyber Security Center ([NCSC](http://www.ncsconline.org/)) is [investigating](https://www.ncsc.gov.uk/news/alert-vpn-vulnerabilities) the exploitation, by advanced persistent threat actors, of known vulnerabilities affecting virtual private network (VPN) vendors [Pulse secure](https://kb.pulsesecure.net/articles/Pulse_Security_Advisories/SA44101), [Palo Alto Networks](https://kb.pulsesecure.net/articles/Pulse_Security_Advisories/SA44101), and multiple [Fortinet](http://www.fortinet.com/) products. This activity is ongoing, targeting both UK and international organizations. Affected sectors include government, military, academic, business, and healthcare.

**NVIDIA Plugs Holes in SHIELD TV** (10/10/2019)  
[NVIDIA](http://www.nvidia.com/) released a software [update](https://nvidia.custhelp.com/app/answers/detail/a_id/4875) for SHIELD TV. This update addresses issues that may lead to information disclosure, denial-of-service, code execution, or escalation of privileges.

**Patched Drupalgeddon 2 Bug Spews Malware in Latest Campaign** (10/07/2019)  
The Drupalgeddon 2 zero-day vulnerability was [seen](https://blogs.akamai.com/sitr/2019/10/drupalgeddon2-still-used-in-attack-campaigns.html) in an attack campaign by [Akamai](http://www.akamai.com/)'s Larry Cashdollar, even though the remote code execution bug was patched in March 2018. The attack is designed to run code that is embedded inside a .gif file and although not widespread, is targeting high-profile Web sites.

**Previously Disclosed vBulletin Zero-Day Seen in Active Exploits** (10/09/2019)  
[Palo Alto Networks](http://www.paloaltonetworks.com/) researchers have [identified](https://unit42.paloaltonetworks.com/99727/) active exploitation of a zero-day vBulletin bug in the wild. By exploiting this vulnerability, an unauthenticated attacker can gain privileged access and control over any vBulletin server running versions 5.0.0 up to 5.5.4, and potentially lock organizations out from their own sites. To mitigate risks, the Web administrator should update vBulletin to version 5.5.2/3/4 Patch Level 1 or disable PHP, Static HTML, and Ad Module rendering setting in the administration panel. This critical vulnerability was [disclosed](https://seclists.org/fulldisclosure/2019/Sep/31/) in September.

**RCE Condition Possible in iTerm2 with tmux Integration** (10/09/2019)  
A security [audit](https://blog.mozilla.org/security/2019/10/09/iterm2-critical-issue-moss-audit/) funded by the [Mozilla](http://www.mozilla.org/) Open Source Support Program ([MOSS](https://mozilla.org/moss)) discovered a critical security vulnerability in the macOS terminal emulator iTerm2. The remote code execution vulnerability lies in the tmux integration feature of iTerm2 and has been present for at least 7 years. After finding the vulnerability, Mozilla, Radically Open Security (ROS, the firm that conducted the audit), and iTerm2's developer George Nachman worked to develop and release a patch. All users of iTerm2 should update immediately to version 3.3.6. The vulnerability lies in the tmux integration feature of iTerm2 and has been present for at least 7 years. The CERT Coordination Center released its own [advisory](https://kb.cert.org/vuls/id/763073/) regarding the iTerm bug.

  

**SAP Squashes Critical Bugs in October Security Day Release** (10/10/2019)  
As part of its October [Security Patch Day](https://wiki.scn.sap.com/wiki/pages/viewpage.action?pageId=528123050), [SAP](http://www.sap.com/) released seven security notes to address vulnerabilities and flaws within its products. The two most important issues addressed include a missing authentication check in the AS2 Adapter of B2B Add-On for NetWeaver and an information disclosure in Landscape Management Enterprise.

  

**Siemens Advises on Vulnerabilities in Various Industrial Products** (10/07/2019)  
[Siemens](http://www.siemens.com/) released 15 [advisories](https://new.siemens.com/global/en/products/services/cert.html#SecurityPublications), informing the public of security issues in its product lines. Several advisories discuss denial-of-service conditions in its industrial products and a code upload bug is possible in SIMATIC WinCC and SIMATIC PCS 7