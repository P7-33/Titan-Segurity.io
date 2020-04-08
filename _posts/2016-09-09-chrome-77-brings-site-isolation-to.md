---
title: 'Chrome 77 Brings Site Isolation to Android to Protect Sensitive Data,
Passwords'
date: 2019-10-18T15:24:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/10/Google-Chrome-Android.jpg)

One of the most widely used browsers, Google Chrome has been updated to version 77, which finally introduces [‘Site Isolation’](https://beebom.com/chrome-now-uses-over-10-more-ram-thanks-to-spectre-vulnerability/) on Android and delivers improvements to further protect sensitive data from being stolen on its desktop counterpart.  

Before we talk about Site Isolation on Android, it’s essential to note that our phones are resource-constrained. You cannot launch multiple processes on mobile in the blink of an eye, thus, Chrome on Android employs a slimmer form of Site Isolation. The feature has been enabled for few websites as compared to the desktop version to not bog down the mobile device.  

In its official blog post, the Chromium team says _“Site Isolation is turned on only for high-value sites where users log in with a password. This protects sites with sensitive data that users likely care about, such as banks or shopping sites, while allowing process sharing among less critical sites.”_ This means whenever Chrome sees password interaction on a website, it will protect the same with Site Isolation to keep malicious users at bay.  

> Site Isolation in Chrome 77 on Android is password-triggered and has been enabled for 99% of the users (that own mobile devices with at least 2GB RAM).

  

If you’re not familiar with Site Isolation, it’s a feature that was introduced with Google Chrome 67 last year to prevent malicious sites from stealing passwords, cookies, and additional data from open browser tabs. The browser now uses a dedicated process to render the content of each website, thus, isolating it from the rest of the websites that users may have open in other tabs.  

Turning our attention to improvements on desktop, the feature was initially debuted to protect users against hackers who may use a Spectre-like vulnerability to secretly gain sensitive data access from a web process. It’s now being upgraded to protect the users against “_significantly stronger attacks”_ for a variety of different compromised renderer processes.  

You can check out the complete list of compromised renderer processes that Chrome 77 will protect using Site Isolation [right here](https://blog.chromium.org/2019/10/recent-site-isolation-improvements.html). However, it’s now looking to improve this by protecting CSRF defenses, additional data types with Cross-Origin Read Blocking, and a wider reach by removing exceptions from the mix.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/chrome-77-brings-site-isolation-to-android-to-protect-sensitive-data-passwords/)  
\[the\_ad id='1307'\]