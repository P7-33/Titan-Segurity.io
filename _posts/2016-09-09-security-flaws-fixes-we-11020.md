---
title: 'Security Flaws & Fixes - W/E - 1/10/20'
date: 2020-01-10T15:09:00+01:00
draft: false
---

**Arbitrary Code Execution Flaw Found in Citrix Application Delivery Controller, Gateway** (01/08/2020)  
A vulnerability has been [identified](https://support.citrix.com/article/CTX267027) in [Citrix](http://www.citrix.com/) Application Delivery Controller (ADC) formerly known as NetScaler ADC and Citrix Gateway formerly known as NetScaler Gateway that, if exploited, could allow an unauthenticated attacker to perform arbitrary code execution. Citrix strongly urges affected customers to immediately apply the provided mitigation. Customers should then upgrade all of their vulnerable appliances to a fixed version of the appliance firmware when released.

  

**Cisco Plugs Various Holes in Data Center Network Manager** (01/06/2020)  
[Cisco](http://www.cisco.com/) released six [advisories](https://tools.cisco.com/security/center/publicationListing.x) to alleviate bugs in its Data Center Network Manager product. Some of the flaws, including authentication bypass bugs, have been rated critical by the vendor.

  

**Cybercriminals Exploit Pulse Secure VPN in REvil Ransomware Attacks** (01/08/2020)  
Security researcher Kevin Beaumont has [warned](https://doublepulsar.com/big-game-ransomware-being-delivered-to-organisations-via-pulse-secure-vpn-bd01b791aad9) that a bug in Pulse Secure's VPN is being used to deliver ransomware with targeted delivery to delete backups and disable endpoint security controls. The vendor patched the vulnerability in April 2019 but exploits for the bug appeared in August. Beaumont said the vulnerability "allows people without valid usernames and passwords to remotely connect to the corporate network the device is supposed to protect, turn off multi-factor authentication controls, remotely view logs and cached passwords in plain text (including Active Directory account passwords)." Adversaries have unleashed the REvil (also known as Sodinokibi) ransomware to attack systems running unpatched versions of Pulse Secure's VPN. Travelex is among the companies victimized by these ransomware attacks.

  

**Drupal Fixes Security Holes in Multiple Versions** (12/23/2019)  
Security updates have been released to mitigate security issues in [Drupal](https://www.drupal.org/) 7.x, 8.7.x, and 8.8.x. Users should read the [advisories](https://www.drupal.org/sa-core-2019-012) and apply the updates

  

**Firefox 72 Turns on Fingerprinting Scripts by Default** (01/08/2020)  
[Mozilla](http://www.mozilla.org/) [released](https://www.mozilla.org/en-US/firefox/72.0/releasenotes/) version 72 of Firefox with at least 10 bug fixes on January 7. Additionally, Firefox 72 offers an enhanced tracking protection feature that blocks fingerprint scripts by default to preserve user privacy. A day later, Mozilla [updated](https://www.mozilla.org/en-US/security/advisories/mfsa2020-03/) both Firefox and Firefox ESR to remedy a zero-day hole allowing for IonMonkey type confusion with StoreElementHole and FallibleStore Element.

  

**Four Vendors Patch Security Bug Found in 2009** (01/06/2020)  
Four security vendors have issued patches for a type of vulnerability that was initially [discussed](https://blog.zoller.lu/2009/04/case-for-av-bypassesevasions.html) by researcher Thierry Zoller in 2009. Zoller [revisited](https://blog.zoller.lu/) the class of vulnerabilities in 2019 and stated that "most AV Vendors haven't appropriately reacted and in some cases I even found the very same vulnerabilities that were patched and disclosed years ago." The vulnerability affects multiple archive formats and involves the user's ability to alter a compressed archive so that the antivirus software cannot access it. [Kaspersky](http://www.kaspersky.com/), [ESET](http://www.eset.com/), [Bitdefender](http://www.bitdefender.com/), and Avira have released fixes.

  

**Google Changes Bug Disclosure Policy** (01/08/2020)  
[Google](http://www.google.com/)'s Project Zero announced a year-long trial change to its bug disclosure policy: full 90 days by default, regardless of when the bug is fixed. Earlier disclosure of a bug will only be made if both the affected vendor and Google agree upon it. The goals of the policy include faster and more thorough patch management and improved patch adoption. Further information is available from a Project Zero [blog post](https://googleprojectzero.blogspot.com/2020/01/policy-and-disclosure-2020-edition.html).

  

**Google Patches Audio Flaw in New Version of Chrome** (01/08/2020)  
[Google](http://www.google.com/) [released](https://chromereleases.googleblog.com/2020/01/stable-channel-update-for-desktop.html) Chrome 79.0.3945.117 for Windows, Mac, and Linux. This update includes three security fixes, one a use-after-free flaw in audio.

  

**Google's First Android Bulletin for 2020 Swats Critical RCE Bug** (01/08/2020)  
[Google](http://www.google.com/) [addressed](https://source.android.com/security/bulletin/2020-01-01.html) seven high and critical flaws with its January release of patches for Android. Among the issues resolved is a critical remote code execution in the Media framework.

  

**Many Apple Devices Vulnerable to Arbitrary Code Bug** (12/23/2019)  
The Cybersecurity and Infrastructure Security Agency ([CISA](https://www.dhs.gov/CISA/)) issued an [alert](https://kb.cert.org/vuls/id/941987/) that some [Apple](http://www.apple.com/) devices are vulnerable to arbitrary code execution at the boot ROM level (called "SecureROM" by Apple) by exploiting a use-after-free vulnerability. SecureROM, which is located within the processor, contains the first code executed by the processor upon booting the device. Because SecureROM is read-only, it cannot be patched with a firmware update. Apple devices that implement processing chips A5 through A11 are vulnerable. This corresponds to iPhone models 4S through X; additionally, certain models of iPad, Apple Watch, iPod Touch, and Apple TV are vulnerable. At this time, there is not a definitive solution.

  

**MDB Leaker Flaw Exposes Data from Microsoft Access Database** (01/07/2020)  
[Mimecast](https://www.mimecast.com/) [identified](https://www.mimecast.com/blog/2020/01/mimecast-discovers-mdb-leaker-microsoft-access-vulnerability-cve-2019-1463/) a bug dubbed "MDB Leaker" in [Microsoft](http://www.microsoft.com/)'s Access database application that could leak sensitive data from 85,000 companies. The vulnerability is related to improperly-managed system memory in the Access application. Mimecast researchers determined that there were code fragments in what should be a data-only file type, an Access MDB file. Microsoft patched this [issue](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2019-1463) in December.

  

**Over 80,000 Companies Vulnerable to Attacks Via Citrix Bug** (12/23/2019)  
A security researcher at [Positive Technologies](https://www.ptsecurity.com/) [discovered](https://www.ptsecurity.com/ww-en/about/news/citrix-vulnerability-allows-criminals-to-hack-networks-of-80000-companies/) a critical vulnerability in [Citrix](http://www.citrix.com/) Application Delivery Controller and Citrix Gateway. If the vulnerability is exploited, attackers obtain direct access to the company's local network from the Internet. This attack does not require access to any accounts and can be performed by any external attacker. At least 80,000 companies in 158 countries are potentially at risk. Citrix has released an [advisory](https://support.citrix.com/article/CTX267027) with mitigation steps to take to secure the devices.

  

**Philips Medical Devices Compromised by Insufficient Encryption, Updates Available** (12/23/2019)  
Philips released a security [advisory](https://www.usa.philips.com/healthcare/about/customer-support/product-security) due to vulnerabilities in Veradius Unity, Pulsera, and Endura medical devices. These products all ship with a dual WAN router. The affected routers have inadequate encryption strength, which may allow an unauthorized user to compromise the router management interface. The vendor has released updates.

  

**Security Issues Found in Telos Automated Message Handling System** (12/23/2019)  
An [advisory](https://kb.cert.org/vuls/id/873161/) from the Cybersecurity and Infrastructure Security Agency warns that Telos Automated Message Handling System (AMHS) contains multiple cross-site scripting vulnerabilities and a database information disclosure vulnerability. Telos AMHS is a Web-based messaging system that supports Department of Defense and intelligence community security marking requirements. AMHS versions prior to version 4.1.5.5 are affected. These issues are addressed in AMHS version 4.1.5.5.

  

**TikTok Vulnerabilities Result in Exposure of User Data, Content Manipulation** (01/08/2020)  
Researchers at [Check Point Software](http://www.checkpoint.com/) [identified](https://research.checkpoint.com/2020/tik-or-tok-is-tiktok-secure-enough/) multiple vulnerabilities, including cross-site scripting, SMS link spoofing, and cross-site request forgery, in the TikTok application. According to the research team, third parties can gain access to TikTok accounts to manipulate content; delete videos; upload unauthorized videos; make private "hidden" videos public; and reveal personal information saved on the account. Check Point notified TikTok of the vulnerabilities, which have since been remedied.

  

**Twitter App Gets Patch for Flaw that Could Enable Attackers to Control Accounts** (12/23/2019)  
A bug has been [fixed](https://privacy.twitter.com/en/blog) in [Twitter](http://twitter.com/) for Android that could allow a threat actor to see nonpublic account information or to control of user accounts. The flaw enabled third parties to insert malicious code into restricted storage areas of the Twitter app,