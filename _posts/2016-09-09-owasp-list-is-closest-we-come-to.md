---
title: 'OWASP list is the closest we come to product security commandments'
date: 2019-10-13T10:24:00+01:00
draft: false
---

![OWASP top 10 vulnerabilties ](https://content.cdntwrk.com/files/aHViPTcyNTE0JmNtZD1pdGVtZWRpdG9yaW1hZ2UmZmlsZW5hbWU9aXRlbWVkaXRvcmltYWdlXzViZGFiMjcxOGViYzIuanBnJnZlcnNpb249MDAwMCZzaWc9ODAzMTY3NTZmZDBjNDhlN2QwZjI0ZjJjOTBjYTA1MWQ%253D)

What is the OWASP Top 10 Vulnerabilities list?
----------------------------------------------

First issued in 2004 by the Open Web Application Security Project, the now-famous [OWASP Top 10](https://www.owasp.org/index.php/Top_10-2017_Top_10) Vulnerabilities list (included at the bottom of the article) is probably the closest that the development community has ever come to a set of commandments on how to keep their products secure.

[WHITESOURCE A LEADERIN THE FORRESTER WAVE SCA REPORT Q2, 2019 Download Free  
Report](https://resources.whitesourcesoftware.com/research-reports/the-forrester-wave-software-composition-analysis-2019)

This list represents the most relevant threats to software security today according to OWASP, to the forehead-smacking of many who wonder how SQL injections are still such a concern after all these years. They judge vulnerability types based on [four criteria points](https://www.owasp.org/index.php/Top_10-2017_Details_About_Risk_Factors): ease of exploitability, prevalences, detectability, and business impact. Interestingly enough, OWASP states that they [do not actually factor](https://www.owasp.org/images/f/f8/OWASP_Top_10_-_2013.pdf) into their equation the likelihood that attackers will try to exploit a certain vulnerability.

When it began, the writers decided that the best way to cover the most ground was to put [similar vulnerabilities](https://www.owasp.org/index.php/Background_OWASP_Top_Ten_2004_Project) that they believed to be the most concerning into groupings. They recognized that lacking the proper statistics there could always be a question over which vulnerabilities were necessarily the top worries, especially as this can be a subjective questions as per each organization’s threat model.

However after much debate, they offered their list of what they believed to address the widest set of organizations, albeit not in any particularly order.

With time, the OWASP Top 10 Vulnerabilities list was adopted as a standard for best practices and requirements by numerous organizations, setting a standard in a sense for development. One well known adopter of the list is the payment processing standards of PCI-DSS.

Unfortunately, as the OWASP Top 10 Vulnerabilities list has reached a wider audience, its real intentions as a guide have been misinterpreted, hurting developers instead of helping. So how should we understand the purpose of this list and actually encourage developers to code more securely?   

Understanding Updates To The 2017 List
--------------------------------------

In the years since, they have refreshed and reordered the entries, adding some new vulnerability types as they become relevant, even as others were dropped from the list. New versions have been issued in 2010, 2013, and 2017. The new list was assembled after a long and arduous study that looked at more than 50,000 applications and analyzed some 2.3 million vulnerabilities.

Regular followers of the list will have noticed that along with some changes in the order — despite the fact that injection attacks remain on top — there are some newcomers to the 2017 updated version of the OWASP Top 10 Vulnerabilities family.

Beating out the [competition](https://resources.infosecinstitute.com/owasp-2017-top-10-vs-2013-top-10/#gref) to inch its way onto the field by kicking off unvalidated redirects and forwards is the issue of unprotected APIs. Its inclusion on the list at the number A10 spot  is likely the result of the fact that developers are simply far more dependent on APIs than they used to, interacting with far more components and external products than before. Coming in at the A7 spot is insufficient attack protection, which knocks developers for not being comprehensive enough in adding protections for detecting, logging, and of course responding to attempts to harm their products.

The other major change here in the 2017 version is the combining of A4’s insecure direct object references and A7 missing function level access control, creating a unified broken access control vulnerability and highlighting the necessity of properly establishing controls for who can and cannot access the accounts and data.

Misinterpreting The OWASP Top 10 Vulnerabilities List
-----------------------------------------------------

A force for good, this list has unfortunately turned into a tool for shaming developers who fail to follow its teachings, used as a club to berate them for not being perfect when it comes to security. This approach is counterproductive and misses OWASP’s mission of encouraging and equipping developers to code more securely. Moreover, it fails to recognize the accomplishments of the scores of developers who are pushing out massive amounts of new software at a never before seen rate.

In a [recent interview](https://www.theregister.co.uk/2018/07/07/owasp_chairman_interview/), OWASP’s chairman Martin Knobloch voiced his disappointment at the list being used as a sort of checklist for a final run through before a release, serving more as a validation mechanism than a guide.

As someone who believes strongly in a shift-left approach to security, I am unsurprisingly in overwhelming agreement with Knobloch’s frustration of how many have taken the OWASP Top 10 list as an instrument of FUD, and not the set of guiding principles that it was intended to be.

Challenging Industry Approaches To Security
-------------------------------------------

Organizational security strategies that depend on expecting failure from the human elements in how they secure software in favor of shiny tools are bound to fail.

In recent years the messaging from far too many vendors, especially in the network side, has been that “the perimeter is dead” and that companies need to seek security at depth to find the bad guys who are already inside their network. Far too many headlines at conferences have tried to convince CISOs that teams of elite hackers are gunning for them with rarified 0-day exploits that will leave them defenseless unless they buy their product which somehow will make them impregnable to these otherwise unstoppable attacks.  

This outlook on the state of security is unnecessarily fatalistic, dripping with marketing hype, and misses some of the basic concepts of how security professionals should think about risk.

A comprehensive approach to security should not preach removing the human developers from the process, just to bring in a vendor’s security tools to fix after they have finished their work. This assumes that the developers cannot be trusted, is insulting, and does nothing to make your team stronger when it comes to security and risk management.

What The OWASP Top 10 Vulnerabilities List Is And Is Not
--------------------------------------------------------

A few times a year there is the obligatory [blog post](https://www.hpe.com/us/en/insights/articles/the-owasp-top-10-is-killing-me-and-killing-you-1710.html) asking how it is possible that in 2017 we are still talking about script kiddie level attacks. I have probably written a few of those myself, for which I apologize.

The OWASP Top 10 is not set up to resolve every attack in the book, but to help teams avoid the common mistakes which are far more likely to get their applications breached. A determined attacker can find many avenues to breach their target. However, the smart risk management advisories do not focus on the minority of cases but instead seek to address the issues facing the widest audience.

To draw from the concepts of physical security field, the average risk manager should be far more worried about her client getting into an accident on the road than ninjas trained by SEAL Team 6 coming through the windows, guided by AI (and blockchain).  

Real security is about training people on how to work securely and giving them the technologies, knowledge, and processes to make it easier for them to stay secure. While it is always important to run QA and final security checks before a release, security needs to start at the earliest stages of how your team works, running throughout the process of developing the product. Mistakes will happen, but it is far more cost-effective and downright smarter to try and avoid as many issues as possible in the first place.

For many developers, the driving goal centers around getting the product to work, focusing less on whether or not it is secure. This is not their fault.

Throughout their education, they learned that if they produce a product with a minimal amount of bugs, then they got an A. Security would be handled by another department anyways. Instead, managers need to take the opportunity to show them a better way to work that includes considering how they code, and the components that they are working with, impact the security of their product.

[GET 451 RESEARCH'S REPORTON SECURING OPEN SOURCE SOFTWARE Download Free](https://resources.whitesourcesoftware.com/white-papers/451report-securing-open-source)

Practical Steps To Enable Better Security Practices
---------------------------------------------------

A common pitfall that came out of the days of waterfall development was to wait until the tail end of the development cycle to perform security checks, wherein the developers would receive a laundry list of vulnerabilities to fix, delaying the release and increasing friction between them and the security team.

In hopes of greasing the gears and keeping pace with the speed of DevOps, organizations are looking for new ways to secure their code from the start and maintain harmony between their departments.

One increasingly popular method for bringing security into the earlier stages of product development is in cross-pollinating teams with a mixture of developers and security folks, allowing each side to give input and learn from each other. This can be an excellent opportunity for security experts to bring up many of the issues that the OWASP Top 10 attempts to address in a less confrontational environment, at a stage that could actually have an impact.

When it comes to tools that can help promote better security implementation, we need to think not only about how technology can catch our mistakes or breaches after the fact, but help us work smarter and more securely from the earliest stages. This perspective is part and parcel of the shift-left mentality, looking for opportunities to address issues before they become expensive problems.

Integrating Technologies To Augment Developer Capabilities
----------------------------------------------------------

A clear example of how technologies for shifting left can help developers utilize the OWASP Top 10 comes with the number 9 entry that warns against [using components with known vulnerabilities](https://resources.whitesourcesoftware.com/blog-whitesource/owasp-a9-and-why-you-can-t-ignore-it). One of the most common problems that arise in this space is in gaining visibility over what is in the [open source components](https://resources.whitesourcesoftware.com/blog-whitesource/5-tips-for-using-open-source-components-more-wisely) that they have added to their product.

Developers almost always turn to open source components to help them build their product faster and more efficiently, adding powerful features without the need to write the new code themselves.

In most cases, they are unlikely to check if the component has any known vulnerabilities before adding it to their product. Even if they do perform a cursory check to see if it has any specific issues, they are unlikely to be aware of any issues in the component’s dependencies.

However, if they are using a [Software Composition Analysis tool](https://resources.whitesourcesoftware.com/blog-whitesource/software-composition-security-analysis), they can actually receive useful information about whether an open source component has any known vulnerabilities associated with it throughout the software development lifecycle (SDLC), saving them time that might otherwise be spent tearing and replacing the component after a check from the security team later down the line before release after it was committed to their code.   

Be A Security Enabler Within Your Organization
----------------------------------------------

Based on my reading of the OWASP Top 10 and Knobloch’s comments, the list should be taken as a tool for empowering teams to include security in their thought process of how they code, configure, and ship out their products.

Security teams that do not engage with their developers, making the effort to understand how they can empower them to have security be an inherent element of their workflow, will quickly find themselves sidelined.

If you want to stay relevant, become an enabler, and use the OWASP Top 10 list as a way to start conversations, not to threaten. In the end, you might find that you catch more (O)WASPS with honey than vinegar.

The Official OWASP Top 10 Vulnerabilities List
----------------------------------------------

**A1. Injection** - Injection flaws, such as SQL, NoSQL, OS, and LDAP injection, occur when untrusted data is sent to an interpreter as part of a command or query. The attacker's hostile data can trick the interpreter into executing unintended commands or accessing data without proper authorization.

**A2. Broken Authentication** - Application functions related to authentication and session management are often implemented incorrectly, allowing attackers to compromise passwords, keys, or session tokens, or to exploit other implementation flaws to assume other users' identities temporarily or permanently.

**A3. Sensitive Data Exposure** - Many web applications and APIs do not properly protect sensitive data, such as financial, healthcare, and PII. Attackers may steal or modify such weakly protected data to conduct credit card fraud, identity theft, or other crimes. Sensitive data may be compromised without extra protection, such as encryption at rest or in transit, and requires special precautions when exchanged with the browser.

**A4. XML External Entities (XXE)** - Many older or poorly configured XML processors evaluate external entity references within XML documents. External entities can be used to disclose internal files using the file URI handler, internal file shares, internal port scanning, remote code execution, and denial of service attacks.

**A5.Broken Access Controls** - Restrictions on what authenticated users are allowed to do are often not properly enforced. Attackers can exploit these flaws to access unauthorized functionality and/or data, access other users' accounts, view sensitive files, modify other users' data, change access rights, etc.

**A6. Security Misconfiguration** - Security misconfiguration is the most commonly seen issue. This is commonly a result of insecure default configurations, incomplete or ad hoc configurations, open cloud storage, misconfigured HTTP headers, and verbose error messages containing sensitive information. Not only must all operating systems, frameworks, libraries, and applications be securely configured, but they must be patched/upgraded in a timely fashion.

**A7.Cross Site Scripting (XXS)** - XSS flaws occur whenever an application includes untrusted data in a new web page without proper validation or escaping, or updates an existing web page with user-supplied data using a browser API that can create HTML or JavaScript. XSS allows attackers to execute scripts in the victim's browser which can hijack user sessions, deface web sites, or redirect the user to malicious sites.

**A8. Insecure Deserialization** - Insecure deserialization often leads to remote code execution. Even if deserialization flaws do not result in remote code execution, they can be used to perform attacks, including replay attacks, injection attacks, and privilege escalation attacks.

**A9. Using Components with Known Vulnerabilities** - Components, such as libraries, frameworks, and other software modules, run with the same privileges as the application. If a vulnerable component is exploited, such an attack can facilitate serious data loss or server takeover. Applications and APIs using components with known vulnerabilities may undermine application defenses and enable various attacks and impacts.

**A10. Insufficient Logging & Monitoring** - Insufficient logging and monitoring, coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, maintain persistence, pivot to more systems, and tamper, extract, or destroy data. Most breach studies show time to detect a breach is over 200 days, typically detected by external parties rather than internal processes or monitoring.

  
  
from Hacker News https://whitessource.com/owasp-top-10-vulnerabilities