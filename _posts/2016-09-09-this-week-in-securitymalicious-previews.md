---
title: 'This Week in Security:Malicious Previews, VNC Vulnerabilities,
Powerwall, and The 5th Amendment'
date: 2019-12-01T01:09:00+01:00
draft: false
---

Malware embedded in office documents has been a popular attack for years. Many of those attacks have been fixed, and essentially all the current attacks are unworkable when a document is opened in protected view. There are ways around this, like putting a notice at the top of a document, requesting that the user turn off protected view. \[Curtis Brazzell\] has been researching phishing, and how attacks can work around mitigations like protected view. He noticed that [one of his booby-trapped documents phoned home](https://medium.com/@curtbraz/getting-malicious-office-documents-to-fire-with-protected-view-4de18668c386) before it was opened. How exactly? The preview pane.

The Windows Explorer interface has a built-in preview pane, and it helpfully supports Microsoft Office formats. The problem is that the preview isn’t generated using protected view, at least when previewing Word documents. Generating the preview is enough to trigger loading of remote content, and could feasibly be used to trigger other vulnerabilities. \[Curtis\] notified Microsoft about the issue, and the response was slightly disappointing. His discovery is officially considered a bug, but not a vulnerability.

### VNC Vulnerabilities

Researchers at Kaspersky [took a hard look at several VNC implementations](https://ics-cert.kaspersky.com/reports/2019/11/22/vnc-vulnerability-research/), and uncovered a total of 37 CVEs so far. It seems that several VNC projects share a rather old code-base, and it contains a plethora of potential bugs. VNC should be treated similarly to RDP — don’t expose it to the internet, and don’t connect to unknown servers. The protocol wasn’t written with security in mind, and none of the implementations have been sufficiently security hardened.

Examples of flaws include: Checking that a message doesn’t overflow the buffer _after_ having copied it into said buffer. Another code snippet reads a variable length message into a fixed length buffer without any length checks. That particular function was originally written at AT&T labs back in the late 90s, and has been copied into multiple projects since then.

There is a potential downside to open source that is highlighted here. Open source allows poorly written code to spread. This isn’t a knock against open source, but rather a warning to the reader. Just because code or a project uses an OSS license doesn’t mean it’s secure or hi quality code. [There are more vulnerabilities still in the process of being fixed](https://github.com/TigerVNC/tigervnc/issues/907), so watch out for the rest of this story.

### Powerwall

And since we’re talking about security fails, Tesla’s Powerwall contained a few of them. It’s unclear how many of these have been fixed with firmware updates, but the researchers at Hacker’s Choice [just released the results of their testing](https://github.com/hackerschoice/thc-tesla-powerwall2-hack).

The highlight of of the work is the hard-coded wifi password, set to the unit’s serial number. The problem is that the serial number is a known format: `ST0001`. “YY” is the year of manufacture. So far, that’s only since 2015, meaning there’s only 5 possible options. “L” is the revision, with only 6 seen in the wild so far. The last 7 digits appear to be a linearly incrementing number, with only numbers between 1000 and 2000 being seen. The real kicker is that the wifi network name appears to contain the last 3 digits of the serial number, giving that information away for free. For those keeping track at home, that means that an attacker trying to connect to a Powerwall’s wifi network has only 30 possible passwords to try, given this best case scenario.

How bad could it be, for an attacker to gain access to a Powerwall’s network? There is a web-based management interface that uses the same password as the wifi. This interface has all sorts of useful functions, like inverting the power sensor logic. This option probably exists to work around a hapless electrician that installed the sensor clamp backwards, but different combinations of inversion lead to various interesting results, like charging the grid when the battery should be charging, or pulling power instead. Another fun option is to change the power output to the home to another country’s standard. Doubling the voltage or changing the power frequency could be disastrous.

While this research was just published, the firmware tested appears to be from late 2017, with multiple updates released since then. Tesla hasn’t published details about security fixes in their firmware releases, so it’s hard to know how many of the problems presented here have been fixed.

### Passwords, Freedom, and Self-incrimination

A legal fight has been slowly brewing in the US over the last few years. The central question is this: Does the Constitutionally guaranteed right against self-incrimination apply to passwords? Courts have been testing this issue for years, but so far a case has not come before the US Supreme Court. Prior cases have applied something known as the “Foregone Conclusion Exception”. This essentially means that with a warrant, police can compel an individual to turn over documentation that is known to exist. [The Pennsylvania Supreme Court weighed in on the issue recently](https://arstechnica.com/tech-policy/2019/11/police-cant-force-child-porn-suspect-to-reveal-his-password-court-rules/), and found that the act of giving a password is inherently testimonial, and therefore protected under the 5th amendment.

> No person…shall be compelled in any criminal case to be a witness against himself….

This is yet another case of the difficulty of applying laws and rulings from before the computer revolution. If the password was instead a combination to a safe, it would be easy enough to open that safe through various means, even without the cooperation of the individual. Modern encryption is an entirely different realm, where decryption is impossible without the password. This latest ruling rejects the notion that the forgone conclusion exception can apply to a password. This issue will likely be decided at the US Supreme Court eventually.

We’re running this weekend because of Thanksgiving, but keep your eyes peeled Friday mornings for This Week in Security, and we’ll keep you up to date with these stories and more.

  
  
from Hackaday https://ift.tt/33A1llS  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)