---
title: 'Security Flaws & Fixes - W/E - 12/13/19'
date: 2019-12-13T15:26:00+01:00
draft: false
---

**Adobe Products Receive Updates** (12/10/2019)  
[Adobe](http://www.adobe.com/) issued updates for [ColdFusion](https://helpx.adobe.com/security/products/coldfusion/apsb19-58.html), [Brackets](https://helpx.adobe.com/security/products/coldfusion/apsb19-58.html), [Photoshop CC](https://helpx.adobe.com/security/products/photoshop/apsb19-56.html), and [Acrobat and Reader](https://helpx.adobe.com/security/products/acrobat/apsb19-55.html). Users are encouraged to apply all updates.

  

**Chrome 70 Mitigates More than 50 Vulnerabilities** (12/10/2019)  
[Google](http://www.google.com/) rolled out [Chrome 79](https://chromereleases.googleblog.com/2019/12/stable-channel-update-for-desktop.html) with a total of 51 bug fixes. Two of the vulnerabilities, a use-after-free in Bluetooth and a heap buffer overflow in password manager - have been deemed critical by the vendor.

  

**Intel Advises on NUC Firmware Bugs, Data Leak Issue in Processors** (12/10/2019)  
Multiple [advisories](https://www.intel.com/content/www/us/en/security-center/default.html) have been released by [Intel](http://www.intel.com/) to notify users of vulnerabilities. The highest severity issue pertains to escalation-of-privilege vulnerabilities in NUC firmware. In addition, Intel [warned](https://www.intel.com/content/www/us/en/security-center/advisory/intel-sa-00289.html) of a data leakage bug affecting some of its processors. This vulnerability, dubbed "Plundervolt," can enable attackers to extract full RSA encryption keys. While a Software Guard Extension TCB key recovery is planned for early 2020, Intel suggests immediately updating the BIOS version for mitigation purposes.

  

**Microsoft Plugs Zero-Day Windows Flaw in Patch Tuesday Security Release** (12/11/2019)  
[Microsoft](http://www.microsoft.com/)'s [Patch Tuesday release](https://portal.msrc.microsoft.com/en-us/security-guidance/) of security bulletins for the month of December remedied at least 36 vulnerabilities across Windows, Internet Explorer, Office, SQL Server, and more products. The most critical of these fixes is a patch for a zero-day privilege escalation hole in Windows that [Kaspersky](http://www.kaspersky.com/) researchers [found](https://securelist.com/?p=95432) and warned had been exploited by the WizardOpium threat group. Microsoft also released a patch for an information leakage bug in Windows Remote Desktop Protocol.

  

**Mitigation Techniques Bolster Security of Weidmueller Industrial Ethernet Switches** (12/09/2019)  
According to an [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-339-02) from the [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/), industrial Ethernet switches from Weidmueller are impacted by multiple vulnerabilities. Successful exploitation of these vulnerabilities could allow a remote attacker to gain unauthorized access to the device, affecting the confidentiality, integrity, and availability of the device the attacker is targeting. The advisory details mitigation techniques.

  

**More Systems Vulnerable to Interpeak IPnet TCP/IP Stack Bugs** (12/11/2019)  
The Cybersecurity and Infrastructure Security Agency ([CISA](https://www.dhs.gov/CISA/)) released a follow-up [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-274-01) regarding vulnerabilities found in the Interpeak IPnet TCP/IP stack, which were first reported in Wind River VxWorks. These vulnerabilities have expanded beyond the affected VxWorks systems and affect additional real-time operating systems. Some of the vendors, including [Microsoft](http://www.microsoft.com/), [Avaya](http://www.avaya.com/), and [Rockwell Automation](http://www.rockwell.com/), have released their own alerts in response to the vulnerabilities.

  

**Password Managers Found with Various Bugs Including Plaintext Credentials** (12/10/2019)  
[Pen Test Partners](https://www.pentestpartners.com/)' Phil Eveleigh [assessed](https://www.pentestpartners.com/security-blog/hacking-hardware-password-managers-the-reczone/) three password managers - RecZone Password Safe, PasswordFast, and Vault Password Keeper - and discovered vulnerabilities in each one. Among the issues he discovered were credentials stored in plaintext, credentials that remain after a hardware reset, and encryption that can be reversed. Eveleigh said, "However one thing I did find consistent across all devices is the keyboard is hard to use and doesn't encourage strong, complicated passwords."

  

**Samba Receives Multiple Updates** (12/10/2019)  
The [Samba](http://us4.samba.org/samba/) Team has issued [updates](https://www.samba.org/samba/history/security.html) for Samba. All users are instructed to update immediately to mitigate a denial-of-service condition, among other vulnerabilities.

  

**SAP Issues Patches for Product Vulnerabilities** (12/11/2019)  
[SAP](http://www.sap.com/) released five [security notes](https://wiki.scn.sap.com/wiki/pages/viewpage.action?pageId=533660397) as part of its monthly batch of security fixes for December. Two additional notes are updates to previously released advisories.

  

**Security Issue Found in Thales DIS SafeNet Sentinel LDK License Manager** (12/09/2019)  
An [ICS-CERT](http://www.us-cert.gov/control_systems/ics-cert/) [advisory](https://www.us-cert.gov/ics/advisories/icsa-19-339-01) discusses a link following bug in Thales DIS' SafeNet Sentinel LDK License Manager. The affected product is vulnerable when configured as a service. This vulnerability may allow an attacker with local access to create, write, and/or delete files in system folder using symbolic links, leading to a privilege escalation. Thales recommends upgrading to Version 7.101 or later.

  

**Siemens Posts Multiple Security Advisories for Products** (12/10/2019)  
[Siemens](http://www.siemens.com/) posted more than a dozen [advisories](https://new.siemens.com/global/en/products/services/cert.html#SecurityPublications) to address vulnerabilities and other issues within its products. Among the issues are a denial-of-service bug in the Web server of its industrial products, a vulnerability in the SIMATIC suite, and multiple bugs in the bootloader of RUGGEDCOM ROS devices. Users should immediately apply any available updates.

  

**Updates for Apple's iOS, Other Products Are Available** (12/11/2019)  
[Apple](http://www.apple.com/) has [addressed](https://support.apple.com/en-us/HT201222) vulnerabilities across multiple products including watchOS, tvOS, Safari, and iOS. Users have been instructed to update immediately to mitigate risks.

  

**VMware ESXi and Horizon DaaS Receive Security Updates** (12/09/2019)  
[VMware](http://www.vmware.com/) has [addressed](https://www.vmware.com/security/advisories/VMSA-2019-0022.html) an OpenSLP remote code execution vulnerability in the ESXi and the Horizon DaaS appliances. The vendor considers this bug a critical issue and has released updates for mitigation.

  

**Vulnerable Smart Locks Open Doors to Attackers** (12/11/2019)  
The security team at [F-Secure](http://www.f-secure.com/) [discovered](https://labs.f-secure.com/blog/digital-lockpicking-stealing-keys-to-the-kingdom) an exploitable design flaw with the KeyWe Smart Lock that attackers can use to pick the device. The lock's inability to receive firmware updates means the flaw cannot be fully fixed. KeyWe Smart Lock, a remote-controlled entry device primarily used in private dwellings, allows users to open and close doors with an app on their mobile phones. F-Secure determined how to exploit improperly designed communication protocols and intercept the secret passphrase that controls the lock while it's exchanged between the physical device and the mobile app.