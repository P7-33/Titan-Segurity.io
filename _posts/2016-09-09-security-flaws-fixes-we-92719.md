---
title: 'Security Flaws & Fixes - W/E - 9/27/19'
date: 2019-09-27T16:52:00+01:00
draft: false
---

**Apple Products Receive Updates** (09/25/2019)  
[Apple](http://www.apple.com/) released [updates](https://support.apple.com/en-us/HT201222) for tvOS, Apple TV, Safari, and iOS. In addition, the vendor announced that a software update to fix a bug with third-party keyboard apps - but not Apple's built-in keyboards is forthcoming but did not give a date when that fix will be issued.

  

**Atlassian Plugs Hole in Jira Service Desk Products** (09/24/2019)  
[Atlassian](https://www.atlassian.com/) released [updates](https://confluence.atlassian.com/jira/jira-service-desk-security-advisory-2019-09-18-976171274.html) for Jira Service Desk Server and Jira Service Desk Data Center following the discovery of an URL path traversal vulnerability that can lead to information disclosure. The vendor rates this bug as critical.

  

**Critical Search Path Bug in Forcepoint VPN Client Can Expose Windows Systems** (09/25/2019)  
[Forcepoint](https://www.forcepoint.com/) has [updated](https://support.forcepoint.com/KBArticle?id=000017525) its VPN Client for Windows versions to mitigate an unquoted search path bug in versions prior to 6.6.1. A researcher at [SafeBreach Labs](https://safebreach.com/) [found](https://safebreach.com/Post/Forcepoint-VPN-Client-for-Windows-Unquoted-Search-Path-and-Potential-Abuses-CVE-2019-6145) the bug and reported it to Forcepoint. According to SafeBreach Labs, the vulnerability "could have been exploited by an attacker during a post-exploitation phase in order to achieve privilege escalation, persistence and in some cases defense evasion by using the technique of implanting an arbitrary unsigned executable which is executed by a signed service that runs as NT AUTHORITY\\SYSTEM."

  

**Further Action Needed to Reduce Cybersecurity Risk to US Electric Grid** (09/25/2019)  
The Government Accountability Office ([GAO](http://www.gao.gov/)) [recommended](https://www.gao.gov/assets/710/701079.pdf) actions that the Department of Energy ([DOE](http://www.energy.gov/)) and the Federal Energy Regulatory Commission ([FERC](http://www.ferc.gov/)) should take to secure components for the electric grid's infrastructure and improve reliability. The report describes the risks facing the grid and provides a list of possible cyber actors that could pose a threat to the grid, among other things. Among its recommendations, the GAO stated that the DOE should develop a plan aimed at implementing the federal cybersecurity strategy for the grid and ensure that the plan addresses the key characteristics of a national strategy, including a full assessment of cybersecurity risks to the grid.

  

**Google: Bad Chrome Update Can Wreak Havoc on macOS** (09/26/2019)  
A Chrome update could damage macOS systems, [Google](http://www.google.com/) warned in an [advisory](https://support.google.com/chrome/thread/15235262?hl=en). "We recently discovered that a Chrome update may have shipped with a bug that damages the file system on macOS machines with System Integrity Protection (SIP) disabled, including machines that do not support SIP. We've paused the release while we finalize a new update that addresses the problem," Google said. It is recommended that users disable SIP. Information about recovering affected machines is available from the advisory.

  

**Hacker Releases Zero-Day RCE Exploit for vBulletin, Vendor Posts Patch** (09/25/2019)  
An anonymous researcher [posted](https://seclists.org/fulldisclosure/2019/Sep/31) an exploit for vBulletin forum software. The zero-day bug results in a remote code execution on all versions from 5.0.0 till 5.5.4. Several security vendors confirmed the legitimacy of the bug. vBulletin released [updates](https://forum.vbulletin.com/forum/vbulletin-announcements/vbulletin-announcements_aa/4422707-vbulletin-security-patch-released-versions-5-5-2-5-5-3-and-5-5-4) to address the exploit on September 25.

  

**Microsoft Issues Out-of-Band Security Update to Fix Zero-Day Hole in IE** (09/24/2019)  
[Microsoft](http://www.microsoft.com/) released out-of-band security updates to notify consumers and businesses of security issues within several products. The first [advisory](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2019-1367) warns of a scripting engine memory corruption vulnerability in Internet Explorer while a second [alert](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2019-1255) discusses a denial-of-service issue in Microsoft Defender. Attackers are actively exploiting the Internet Explorer bug. The vendor also issued a [cumulative security update](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2019-1255) for Internet Explorer.

  

**Out-of-Band Adobe Bulletin Mitigates Three Bugs in ColdFusion** (09/25/2019)  
[Adobe](http://www.adobe.com/) pushed out fixes for ColdFusion versions 2016 and 2018. The [updates](https://helpx.adobe.com/security/products/coldfusion/apsb19-47.html) remedy a path traversal, a command injection via vulnerable component, and security bypass vulnerabilities.

  

**Update VMware Products to Mitigate Code Execution** (09/24/2019)  
[VMware](http://www.vmware.com/)'s ESXi, Workstation, Fusion, VMRC, and Horizon Client contain a use-after-free vulnerability in the virtual sound device. A local attacker with non-administrative access on the guest machine may exploit this issue to execute code on the host. The vendor confirmed that there are no workarounds and an [advisory](https://www.vmware.com/security/advisories/VMSA-2019-0014.html) details which versions are fixed.

  

**Zero-Day Hole in Rich Reviews Plugin Leaves WordPress Sites Vulnerable** (09/26/2019)  
An outdated [WordPress](http://wordpress.org/) plugin called Rich Reviews is under attack due to an unpatched bug and about 16,000 sites that run this plugin are vulnerable, the research team at [Wordfence](https://www.wordfence.com/) [warned](https://www.wordfence.com/blog/2019/09/rich-reviews-plugin-vulnerability-exploited-in-the-wild/). The bug can be used to deliver stored cross-site scripting payloads and attacks that began in April are continuing.