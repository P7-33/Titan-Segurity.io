---
title: 'A Bug in WhatsApp''s Desktop App Allowed Hackers to Read Local Files'
date: 2020-02-06T10:13:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/02/WhatsApp-Desktop-app-bug-allowed-remote-hack.jpg)

Cyber-security researchers have identified a **critical JavaScript vulnerability in the WhatsApp desktop app** prior to versions 0.3.9309. Originally discovered by Gal Weizman of PerimeterX, the vulnerability affects both the Windows and Mac versions of the app, and could potentially allow cyber-criminals to inject malware or perform remote code execution using seemingly innocuous messages.  

According to the National Vulnerability Database, the vulnerability (CVE-2019-1842) _“when paired with WhatsApp for iPhone versions prior to 2.20.10, allows cross-site scripting and local file reading.”_ In essence, it allows cyber-criminals to execute [phishing](https://beebom.com/india-phishing-attacks/) or ransomware campaigns through notification messages that appear normal at first sight.  

The most critical vulnerability apparently allowed attackers to simply send some malicious JavaScript in a WhatsApp message to take control over a target device remotely and read local files.  

WhatsApp’s desktop applications, which need to be paired with the Android or iOS version of the app to work, are built using web-browser technology with the Electron framework. As it turns out, WhatsApp developers were using an old, out-of-date version of Chromium (version 69), which was already known to have these vulnerabilities. The standard practice is to always update the code with the latest version of Chromium while using Electron, as per Weizman.  

WhatsApp’s desktop apps have more than 1.5 billion users globally, and it isn’t immediately clear as to how many of them are affected by the issue. Facebook has already updated the software with the requisite patches, so the latest version should be free from the problem.  

As mentioned already, WhatsApp Desktop v0.3.9309 and earlier versions are affected by the vulnerability, so you should update to the latest version as soon as possible. You can also learn more about the issue from [Weizman’s report](https://www.perimeterx.com/tech-blog/2020/whatsapp-fs-read-vuln-disclosure/) on the official PerimeterX blog.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/whatsapp-desktop-app-bug-allowed-hacking/)  
\[the\_ad id='1307'\]