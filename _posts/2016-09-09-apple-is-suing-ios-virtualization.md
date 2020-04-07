---
title: 'Apple is suing iOS virtualization vendor Corellium for violating DMCA 1201'
date: 2020-01-03T02:06:00+01:00
draft: false
---

Apple has unleashed their legal juggernaut on an innovative iOS security company, and if they win their lawsuit, the damage will reverberate beyond the security community and into the world of repair and maintenance.

[Corellium’s](https://corellium.com/) software creates virtual iPhones in a web browser, so that app developers and security researchers can tinker without needing a physical device. It’s nerdy stuff that most people will never need, but it’s genuinely useful. So useful, in fact, that Apple tried to [buy the company](https://drive.google.com/file/d/17aLLlA_OqUXg2gZITKu1l1TRpOZL1445/view). When the founders refused, Apple decided to [sue them](https://www.macrumors.com/2019/08/15/apple-corellium-copyright-infringement-lawsuit/) into oblivion.

In a [just-filed revision](https://www.scribd.com/document/441298959/Apple-Versus-Corellium-Amended-Filing) to their lawsuit, Apple has invoked section 1201 of the [DMCA](https://en.wikipedia.org/wiki/Digital_Millennium_Copyright_Act), the infamous and often abused copyright law. This claim dramatically raises the stakes for this lawsuit, and puts Apple squarely in the crosshairs of copyright experts concerned about unintended precedents it could set if Apple is successful.

But before we talk about section 1201, let’s look at Apple’s [original complaint](https://www.scribd.com/document/422014589/Apple-Inc-vs-Corellium-LLC#from_embed). They accuse Corellium of doing exactly what they promise customers: providing virtualized access to iOS. “Corellium has simply copied everything: the code, the graphical user interface, the icons—all of it, in exacting detail,” the lawsuit states.

![](https://valkyrie.cdn.ifixit.com/media/2020/01/02122138/corellium_screen.jpg)

Corellium’s software creates virtual iOS devices that can be jailbroken and security tested from a browser.

This is an annoying thing for Apple to complain about, because they don’t provide a way to license iOS for virtualized purposes. If they did, [loads of developers](https://www.google.com/search?q=virtualized+ios+site:stackoverflow.com&safe=off&sxsrf=ACYBGNSb4wOqQWtOHG7tNeLYlZLaOARcDA:1577915600055&sa=X&ved=2ahUKEwiCqM7WsePmAhVTsp4KHXp4BdkQrQIoBDAEegQIBhAN&biw=1349&bih=790) would be happy to pay. Apple gives iOS away with every device, and doesn’t sue people for pirating iOS the way that [Microsoft has been notorious for](https://www.geekwire.com/2018/microsoft-sues-prolific-distributor-pirated-office-windows-software/). Running virtualized operating systems is a pretty commonplace thing to do these days—a working Windows setup on Amazon’s AWS servers costs about $0.03/hour.

**The Digital Millennium Copyright Act Strikes Back**

Despite a lack of apparent interest in enforcing their copyright to iOS software, in this specific case Apple has decided to exert control over iOS. And they’ve crossed a red line by invoking the most notorious statute in the US copyright act, [section 1201](https://www.law.cornell.edu/uscode/text/17/1201). This is the very law that made it illegal for farmers to [work on their tractors](https://www.wired.com/2015/02/new-high-tech-farm-equipment-nightmare-farmers/) and for you to [fix your refrigerator](https://www.ifixit.com/News/copyright-and-the-end-of-ownership). It’s the same law that we’ve been whacking away at for years, getting [exemptions](https://www.eff.org/deeplinks/2018/10/new-exemptions-dmca-section-1201-are-welcome-dont-go-far-enough) from the US Copyright Office for fixing, jailbreaking, and performing security research on everything from smartwatches to automobiles.

Enter Apple with the latest terrible, awful, no-good application of 1201. Apple claims that in making virtual iPhones for security and development use, Corellium is engaged in “unlawful trafficking of a product used to circumvent security measures in violation of 17 U.S.C. § 1201.”

In other words: Corellium sells a way to use iOS that works around the way Apple intended it to work. Apple knows that you can’t use Corellium’s software to create your own knock-off iPhone. But they can claim that Corellium’s software is illegal, and they might technically be right. That’s terrifying.

**Circumventing Technological Protection Measures**

> Back in 1998, when the law was written, digital locks were very rare—they were really only used to protect movies on DVDs

So how did we get here? Well, 1201 works in two ways: One, it makes it illegal to bypass digital locks. And two, it makes it illegal to distribute tools to bypass locks. Back in 1998, when the law was written, digital locks were very rare—they were really only used to protect movies on DVDs. But nowadays, legitimate cybersecurity needs have driven companies to use digital locks on just about everything, and they are not providing anyone the key. You might have to modify your Samsung refrigerator’s software to [fix its outdated calendar](https://us.community.samsung.com/t5/Kitchen-and-Family-Hub/Google-Calendar-Won-t-Sign-on/td-p/1018229). But in order to do that, you have to jailbreak its Android operating system. And, as the name implies, jailbreaks require breaking digital locks.

> “Anytime someone puts a lock on something you own, against your wishes, and doesn’t give you the key, they’re not doing it for your benefit.” — Doctorow’s Law

VIDEO

Fortunately, Congress built an escape hatch into the law, and allows motivated types like us to apply for specific ‘exemptions’ — permission to pick digital locks that are in the public interest. For the last decade, iFixit has joined EFF and digital activists from around the country to apply for, and win, [numerous exemptions](https://www.ifixit.com/News/1201-copyright-final-rule) for repair and security research every three years. One of those exemptions, most [recently granted](https://www.copyright.gov/title37/201/37cfr201-40.html) last October, is for jailbreaking iPhones. (Notably, Apple did not oppose this exemption request.)

Sounds great! So why can’t Corellium just send the judge a link to the jailbreaking exemption and wave this lawsuit goodbye? Well, there’s a [fatal flaw](https://www.eff.org/deeplinks/2018/02/did-congress-really-expect-us-whittle-our-own-personal-jailbreaking-tools) with 1201. The Copyright Office believes only it has the power to grant exemptions for individuals to bypass their own locks, not for third parties to do it for you. So you can write the code to make your own virtualized iOS container, but you can’t hire Corellium to do it for you. 

This shows how ridiculous the law is. Cory Doctorow [puts it well](https://www.eff.org/deeplinks/2018/02/did-congress-really-expect-us-whittle-our-own-personal-jailbreaking-tools): “Even computer scientists don’t hand-whittle their own software tools for every activity: like everyone else, they rely on specialized toolsmiths who make software.” The Electronic Frontier Foundation vehemently disagreed with the Office on this and requested a tool exemption, but the Copyright Office ignored them and excluded tool distribution from the most recent exemptions.

**Making Tools Should Not Be a Crime**

Apple is upset that Corellium has created a tool that grants access to iOS in an innovative medium that Apple is (so far) unwilling to provide. 

“Corellium, by offering the Corellium Apple Product for sale or license without authorization from Apple, is trafficking in technologies, products, or services that are primarily designed to avoid, bypass, remove, deactivate, or otherwise impair technological measures that effectively control access to Apple’s copyrighted works, in violation of 17 U.S.C.§ 1201(a)(2).”

![](https://valkyrie.cdn.ifixit.com/media/2020/01/02125251/jailbreak2.jpg)

Jailbreaking an iPhone, something allowed under an exception to the DMCA/1201 laws Image via [Wikimedia](https://commons.wikimedia.org/wiki/File:Jailbreaking_iPhone.jpg)

According to Apple, Correllium does this by “disabling loadable firmware validation, disabling self-verification of the FIPS module, adding Corellium software to the ‘trust cache,’ and instructing the restore tool not to contact Apple servers for kernel / device tree / firmware signing.” That allows them to “jailbreak” or otherwise bypass one or more feature of iOS and iOS devices that are designed to prevent access to the software or other material that could be stored on the iOS device.

Of course, Apple includes those copyrighted works for free with every iOS device. Corellium is not enabling piracy of iOS—they’re supporting security research. But because 1201 doesn’t require theft of a copyrighted work, Apple has a chance of succeeding with this ‘tool trafficking’ argument.

**If Apple Wins, We All Lose**

As the world embraces internet-connected hardware, more and more of the devices that we use will integrate digital locks. Apple is arguing that no one else should be able to make tooling for performing security research on their products. What happens if other companies start making the same claims?

This isn’t academic. Last year, GM [sued](https://law.justia.com/cases/federal/district-courts/michigan/miedce/2:2015cv12917/303716/17/) aftermarket parts company Dorman for “overriding the security measures used in \[GM\]’s vehicle control modules” in their transmission repair tool. Dorman’s aftermarket transmissions moved the firmware from an existing transmission into their aftermarket part, so that it would be recognized by the vehicle and work.

John Deere has also been aggressively locking down their products, aiming to monopolize service and prevent farmers from doing repairs themselves. They [opposed a DMCA exemption](https://www.ifixit.com/News/john-deere-ownership) for farmers on the grounds that if owners could fix their own equipment, they might use their newfound freedom to pirate Taylor Swift’s music on their tractors.

This is a massive change from the status quo. For decades, people have used aftermarket car parts and those parts have created competition in the industry. For decades, farmers have been self-reliant and able to fix their own gear without the manufacturer breathing down their neck and squeezing money out of them.

That GM and John Deere can abuse copyright law in this way is terrible. It’s clearly in the public’s interest to have aftermarket parts options for automobiles: it keeps manufacturers competitive on both price and quality. This law has the unintended consequence of giving manufacturers a monopoly on repairs of any product containing software and a digital lock.

VIDEO

Apple knows this. They understand the ethical implications of using a bad law as a cudgel, and they don’t care. Every successful suit that invokes 1201 sets a precedent for further abuse. The purpose of copyright is set out in the US constitution as simply “to promote the progress of science and useful arts.” Apple’s suit does the opposite—it seeks to limit who can make security tools to improve iOS. It’s beyond the pale to abuse copyright to preserve a monopoly position and deter security research.

**It’s Time to Fix the DMCA**

![](https://valkyrie.cdn.ifixit.com/media/2020/01/02125841/copyright-seal.gif)

Seal of the U.S. Copyright Office.

So where do we go from here? The EFF has [sued the Copyright Office](https://www.eff.org/press/releases/eff-lawsuit-takes-dmca-section-1201-research-and-technology-restrictions-violate) arguing that section 1201 is an unconstitutional violation of the First Amendment. If they succeed, it’s possible that 1201 could go away entirely. But that suit has languished on the court’s desk for three years, and it’s unclear when it will be heard.

The more expeditious path would be for Congress to pass something like Rep. Zoe Lofgren’s [Unlocking Technology Act](https://en.wikipedia.org/wiki/The_Unlocking_Technology_Act_of_2013) and fix section 1201 once and for all.

The future of ownership is at stake. If we can’t investigate the security of the software that runs on our devices or make software changes in order to fix them, then we don’t really own our stuff anymore. 

It’s time to decriminalize toolmaking.

_Top image by [Daniel Aleksandersen/Flickr](https://www.flickr.com/photos/aleksandersen/48767755527/in/photolist-2hiruFa-5fWgPV-5fWh4g-5g1Cts-omVpc-7B1U64-czKPHQ-2GYZWs-38mBEQ-8Zp9tQ-fCzbC-9SaBd3-54wvCi-54wsyB-tGhEfT-QMnP1e-HrBVPu-2hZ3m8P-54uNN6-54uNat-8ApxUG-8Amsyp-8AmyxV-8AppqS-8AprTh-8Apnmd-8Amwka-8ApuCW-8AptDJ-dRntTz-dWjNBU-x4MDQB-aoG95n-9UbyFd-2Cwy9G-9UbyNy-2Cwyi1-CuWtrZ-ZoiXMF-6WpeL9-q6a9Hi-bDC2yk-54AGWh-bqH6QQ-54AHp1-2drCPQw-QMnPn6-54AFUU-54wwqx-9UbyVW)_

  
  
from Hacker News https://ift.tt/2SXRUeD