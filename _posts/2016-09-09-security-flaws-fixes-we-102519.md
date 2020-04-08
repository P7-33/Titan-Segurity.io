---
title: 'Security Flaws & Fixes - W/E - 10/25/19'
date: 2019-10-25T14:05:00+01:00
draft: false
---

**AVEVA Vijeo Citect and Citect SCADA Affected by Buffer Overflow Issue** (10/21/2019)  
The IEC870IP driver for AVEVO's Vijeo Citect and Citect SCADA has a buffer overflow that could cause a server-side crash. Vijeo Citect and Citect SCADA users utilizing the IEC870IP driver v4.14.02 and prior are affected and should upgrade to the IEC870IP driver v4.15.00. Further details have been made available in an [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-290-01).

  

**Google Presents Chrome 78** (10/23/2019)  
[Google](http://www.google.com/) [rolled](https://chromereleases.googleblog.com/2019/10/stable-channel-update-for-desktop_22.html) out Chrome 78 to the stable channel for Windows, Mac, and Linux. This update contains 37 security fixes, including patches for a use-after-free bug in media, a buffer overrun issue in Blink, and an URL spoof in navigation.

  

**Horner Automation Cscape Vulnerable to Arbitrary Code Execution, Data Leakage** (10/21/2019)  
Two vulnerabilities in Horner Automation's Cscape could crash the device being accessed, which may allow the attacker to access information and execute arbitrary code. Cscape is a control system application programming software. The [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) has issued an [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-290-02) regarding these vulnerabilities.

  

**ISC Addresses Security Holes in BIND** (10/21/2019)  
The Internet Systems Consortium ([ISC](http://www.isc.org/)) issued advisories that address vulnerabilities affecting multiple versions of ISC Berkeley Internet Name Domain (BIND). The first [advisory](https://kb.isc.org/docs/cve-2019-6475) addresses a bug that can enable an attacker to replace the mirrored zone (usually the root) with data of their own choosing and bypass protection. In the second [advisory](https://kb.isc.org/docs/cve-2019-6476), ISC explains a condition, which if triggered by an attacker on a server performing recursion, could cause BIND to exit with an assertion failure.

  

**Mozilla Rolls Out Advanced Security Features with Firefox 70** (10/23/2019)  
[Mozilla](http://www.mozilla.org/) [released](https://www.mozilla.org/en-US/firefox/70.0/releasenotes/) Firefox 70 with new protective features, including secure password generation with Lockwise and the Firefox Privacy Protection Report, which shows an overview, with details, of the trackers Firefox has blocked. Enhanced Tracking Protection is on by default and secure password generation enables users to create and save strong passwords for online accounts.

  

**RCE Condition Likely in Certain Legacy D-Link Routers** (10/24/2019)  
The CERT Coordination Center has [advised](https://kb.cert.org/vuls/id/766427/) that multiple [D-Link](http://www.dlink.com/) routers are vulnerable to unauthenticated remote command execution. Several D-Link routers contain CGI capability that is exposed to users as /apply\_sec.cgi, and dispatched on the device by the binary /www/cgi/ssi. This CGI code contains two flaws. By performing an HTTP POST request to a vulnerable router's /apply\_sec.cgi page, a remote, unauthenticated attacker may be able to execute commands with root privileges on an affected device. This action can happen as the result of viewing a specially-crafted Web page. D-Link no longer supports these devices.

  

**Schneider Electric Issues Update to Mitigate ProClima Vulnerabilities** (10/23/2019)  
Multiple vulnerabilities have affected Schneider Electric's ProClima building and automation control products, an [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-295-01) confirms. If exploited, the bugs could enable an attacker to launch arbitrary code. Schneider Electric has released Version 8.0.0 of ProClima and recommends users upgrade to this version or newer.

  

**Trend Micro Bashes RCE Bug in Anti-Threat Toolkit** (10/24/2019)  
[Trend Micro](http://www.trendmicro.com/) [released](https://success.trendmicro.com/solution/000149878) a new version of the Anti-Threat Toolkit after it learned of a vulnerability related to a potential remote code execution in certain versions. Security researcher John Page [found](http://hyp3rlinx.altervista.org/advisories/TREND-MICRO-ANTI-THREAT-TOOLKIT-(ATTK)-REMOTE-CODE-EXECUTION.txt) the bug and contacted Trend Micro in September regarding it.