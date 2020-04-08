---
title: 'Security Flaws & Fixes - W/E - 11/8/19'
date: 2019-11-08T15:18:00+01:00
draft: false
---

**Code Execution, DoS Bugs Patched in LEADTOOLS** (11/07/2019)  
Multiple bugs have been [identified](https://blog.talosintelligence.com/2019/11/vulnerability-spotlight-code-execution.html) in the LEADTOOLS line of imaging toolkits. LEADTOOLS, which is a collection of toolkits designed to perform a variety of functions aimed at integrating documents, multimedia, and imaging technologies into applications, offers prebuilt and portable libraries with an SDK for most platforms. The vulnerabilities could result in denial-of-service conditions and the execution of code remotely. [Cisco](http://www.cisco.com/)'s Talos team notified LEAD Technologies, the producer of LEADTOOLS, and the vulnerabilities have since been [rectified](https://www.leadtools.com/downloads).

  

**Google Squashes Bugs with Release of Fixes for Android** (11/06/2019)  
[Google](http://www.google.com/) released its November version of the [Android Security Bulletin](https://source.android.com/security/bulletin/2019-11-01.html), which contains a number of fixes and updates. The most severe of these issues is a critical security vulnerability in the System component that could enable a remote attacker using a specially crafted file to execute arbitrary code within the context of a privileged process.

  

**Google Updates Chrome to Squash Two Bugs** (11/04/2019)  
The latest [version](https://chromereleases.googleblog.com/2019/10/stable-channel-update-for-desktop_31.html) of [Google](http://www.google.com/) Chrome mitigates two security vulnerabilities. Version 78.0.3904.87, which has been released for Windows, Mac, and Linux alleviates a use-after-free bug in PDFium and a use-after-free issue in audio. [Kaspersky](http://www.kaspersky.com/) [found](https://securelist.com/chrome-0-day-exploit-cve-2019-13720-used-in-operation-wizardopium/94866/) the use-after-free audio vulnerability, which has been used in watering hole-style attacks.

  

**Honeywell Advises on Vulnerabilities in equIP Series and Performance Series Products** (11/04/2019)  
[Honeywell](http://www.honeywell.com/) released multiple [advisories](https://www.security.honeywell.com/resources/eol-and-security-notices) to mitigate risks in equIP series and Performance series IP cameras and recorders. The advisories discuss methods to use to mitigate these vulnerabilities.

  

**Improper Disabling of XLM Macros in Office for Mac Results in Serious Weakness** (11/04/2019)  
The [Microsoft](http://www.microsoft.com/) Office for Mac option "Disable all macros without notification" enables XLM macros without prompting, which can allow a remote, unauthenticated attacker to execute arbitrary code on a vulnerable system. Up to and including Microsoft Excel 4.0, a macro format called XLM was available. XLM macros predate the VBA macros that are more common with modern Microsoft Office systems, however current Microsoft Office versions still support XLM macros. It is unclear if a solution to this issue is available but an [advisory](https://kb.cert.org/vuls/id/125336/) from the Cybersecurity and Infrastructure Security Agency ([CISA](https://www.dhs.gov/CISA/)) offers guidance.

  

**NVIDIA Alleviates DoS, Data Leakage Bugs in GPU Display Driver** (11/06/2019)  
[NVIDIA](http://www.nvidia.com/) has released a software security [update](https://nvidia.custhelp.com/app/answers/detail/a_id/4907/kw/Security%2520Bulletin) for its GPU Display Driver. This update addresses issues that may lead to denial of service, escalation of privileges, or information disclosure.

  

**Two RCE Bugs in rConfig Unpatched as PoC Exploits Released** (11/06/2019)  
Open-source network device configuration management utility rConfig contains two remote code execution bugs, a security researcher has [found](https://shells.systems/rconfig-v3-9-2-authenticated-and-unauthenticated-rce-cve-2019-16663-and-cve-2019-16662/). The first bug affects the ajaxServerSettingsChk.php file while the second was discovered in the search.crud.php file. The researcher, who goes by the name of Askar, released proof-of-concept exploits for both bugs after contacting rConfig's main developer in September and getting no response.

  

**Users of Discontinued Advantech WISE-PaaS/RMM Warned of Vulnerabilities** (11/04/2019)  
Multiple vulnerabilities in Advantech's discontinued WISE-PaaS/RMM Internet of Things device remote monitoring and management platform could result in information disclosure, remote code execution, and system availability compromise. Advantech phased out WISE-PaaS/RMM in July 2019 and replaced this product with EdgeSense and DeviceOn. Users can obtain further information from an [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-304-01).

  

**Vulnerabilities Addressed in Omron Products** (11/06/2019)  
A vulnerability impacts the "Full Development" and "Runtime Only" packages of Omron's SCADA and HMI package "CX-Supervisor." Omron [recommends](https://www.myomron.com/index.php?action=kb&article=1713) users update to CX-Supervisor 3.51 (9). The [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) posted an [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-309-01) with further information. A second ICS-CERT [advisory](https://www.us-cert.gov/ics/advisories/ICSA-19-134-01) pertaining to Omron reflects an update to the vendor's Network Configurator for DeviceNet. A new version has been released to mitigate an untrusted search path vulnerability.