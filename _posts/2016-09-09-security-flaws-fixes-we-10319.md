---
title: 'Security Flaws & Fixes - W/E - 10/3/19'
date: 2019-10-04T13:56:00+01:00
draft: false
---

**CISA: Vulnerable Interpeak IPnet TCP/IP Stack Affects More Medical, Industrial Devices** (10/02/2019)  
The Cybersecurity and Infrastructure Security Agency ([CISA](https://www.dhs.gov/CISA/)) is aware of a public report detailing vulnerabilities found in the Interpeak IPnet TCP/IP stack. The Interpeak IPnet stack vulnerabilities were first reported in Wind River VxWorks but the bugs have expanded beyond the affected VxWorks systems and affect additional real-time operating systems. CISA has reached out to affected vendors of the report and asked them to confirm the vulnerabilities and identify mitigations. CISA issued an [advisory](https://www.us-cert.gov/ics/advisories/icsma-19-274-01) to provide early notice of the reported vulnerabilities and identify baseline mitigations for reducing risks to these and other cybersecurity attacks. The following vendors have issued their own advisories: [BD](https://www.bd.com/en-us/support/product-security-and-privacy/product-security-bulletins), [Drager](https://static.draeger.com/security/download/2019-07-29-WindRiver-VxWorks-Security-Advisory.pdf), [GE Healthcare](https://www.gehealthcare.com/security), [Philips Healthcare](https://www.usa.philips.com/healthcare/about/customer-support/product-security), and [Spacelabs](https://www.spacelabshealthcare.com/products/security/security-advisories-and-archives/urgent-11-vulnerability-in-vxworks-ipnet-service/).

  

**Cisco Addresses Multiple Security Issues with Batch of Advisories** (10/01/2019)  
[Cisco](http://www.cisco.com/) released multiple [advisories](https://tools.cisco.com/security/center/publicationListing.x) to address vulnerabilities and security issues across its product lines. The issues include command injection, buffer overflow, denial-of-service, and unauthorized access vulnerabilities, among others. IOS XE Software, Email Security Appliance, and Catalyst 4000 Series Switches are among the products affected.

  

**Moxa EDR-810 Routers Require Security Update** (10/02/2019)  
Moxa's EDR-810 Series routers are affected by improper input validation and improper access control vulnerabilities. Users should immediately update to version 5.2 to mitigate risks. The vendor posted an [advisory](https://www.moxa.com/en/support/support/security-advisory/edr-810-series-secure-router-vulnerabilities-(1)) with further details.

  

**NSA's Ghidra Tool Vulnerable to Code Execution** (10/02/2019)  
The [NIST](http://www.nist.gov/) posted an [advisory](https://nvd.nist.gov/vuln/detail/CVE-2019-16941) for the National Security Agency's ([NSA](http://www.nsa.gov/)) reverse-engineering Ghidra tool due to a vulnerability that could enable an attacker to launch code in vulnerable systems. All versions are affected and no fix is yet available.

  

**PDFex Attacks Bypass Encryption to Exfiltrate Info from PDF Documents** (10/02/2019)  
Security researchers at Ruhr University Bochum [discovered](https://web-in-security.blogspot.com/2019/09/pdfex-major-security-flaws-in-pdf.html) severe weaknesses in the PDF encryption standard which leads to full plaintext exfiltration in an active attacker scenario. The vulnerabilities, dubbed "PDFex," are explained as: an attacker possessing an encrypted PDF file can manipulate parts of it even without knowing the corresponding password and since PDF encryption uses the Cipher Block Chaining (CBC) encryption mode without integrity checks, self-exfiltrating ciphertext parts using CBC malleability gadgets can be created. Twenty-seven desktop and browser PDF viewers are [affected](https://pdf-insecurity.org/encryption/evaluation_2019.html).

  

**PHP Vulnerability Can Lead to Arbitrary Code Execution** (10/01/2019)  
The Multi-State Information Sharing & Analysis Center ([MS-ISAC](https://www.cisecurity.org/)) released an [advisory](https://www.cisecurity.org/advisory/a-vulnerability-in-php-could-allow-for-arbitrary-code-execution_2019-101/) to warn of a vulnerability in PHP, which could allow an attacker to execute arbitrary code. PHP supports a wide variety of platforms and is used by numerous Web-based software applications. Successfully exploiting this vulnerability could allow for arbitrary code execution in the context of the affected application. It is best to upgrade to the latest PHP version immediately.

  

**Update Exim Email Servers to Alleviate System Crash** (10/01/2019)  
[Tenable](http://www.tenablesecurity.com/)'s researchers [say](https://www.tenable.com/blog/cve-2019-16928-critical-buffer-overflow-flaw-in-exim-is-remotely-exploitable) that a heap-based buffer overflow vulnerability in Exim email servers, could allow remote attackers to crash Exim or potentially execute arbitrary code. Over 3.5 million systems are vulnerable, according to Tenable's analysis. The Exim team released [version 4.92.3](https://exim.org/index.html) on September 29 to address this bug.

  

**Updates for iOS and watchOS Released by Apple** (10/01/2019)  
[Apple](http://www.apple.com/) released [updates](https://support.apple.com/en-us/HT201222) for iOS and watchOS. Users should immediately update to mitigate risks.

  

**WhatsApp Patch Fixes RCE Condition** (10/03/2019)  
A double-free vulnerability in [WhatsApp](http://www.whatsapp.com/) for Android can result in a remote code execution, according to the researcher who [discovered](https://awakened1712.github.io/hacking/hacking-whatsapp-gif-rce/) it. The issue was reported to [Facebook](http://www.facebook.com/) and the bug was patched in WhatsApp version 2.19.244.

  

**Yokogawa Products Prone to Cyber Attacks** (10/02/2019)  
Yokogawa's Exaopc, Exaplog, Exaquantum, Exasmoc, Exarqe, GA10, and InsightSuiteAE products are impacted by an unquoted search path or element, according to an [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-274-02) posted by the Cybersecurity and Infrastructure Security Agency ([CISA](https://www.dhs.gov/CISA/)). The vulnerability may allow a local attacker to execute malicious files by the service privilege. Countermeasures are documented in the advisory.