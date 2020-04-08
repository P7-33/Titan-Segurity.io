---
title: 'Cloud flaws expose millions of child tracking smartwatches'
date: 2019-12-18T18:03:00+01:00
draft: false
---

Parents buy their children GPS-enabled smartwatches to keep track of them, but security flaws mean they’re not the only ones who can.

This year alone, researchers have found [several vulnerabilities](https://blog.rapid7.com/2019/12/11/iot-vuln-disclosure-childrens-gps-smart-watches-r7-2019-57/) in a number of [child-tracking smartwatches](https://blog.avast.com/unsecure-child-trackers). But new findings out today show that nearly all were harboring a far greater, more damaging flaw in a common shared cloud platform used to power millions of cellular-enabled smartwatches.

The cloud platform is developed by Chinese white-label electronics maker Thinkrace, one of the largest manufacturers of location-tracking devices. The platform works as a backend system for Thinkrace-made devices, storing and retrieving locations and other device data. Not only does Thinkrace sell its own child-tracking watches to parents who want to keep tabs on their children, the electronics maker also sells its tracking devices to third-party businesses, which then repackage and relabel the devices with their own branding to be sold on to consumers.

All of the devices made or resold use the same cloud platform, guaranteeing that any white-label device made by Thinkrace and sold by one of its customers is vulnerable.

Ken Munro, founder of [Pen Test Partners,](https://crunchbase.com/organization/pen-test-partners) shared [the findings](https://www.pentestpartners.com/security-blog/kids-tracker-watches-cloudpets-exploiting-athletes-and-hijacking-reality-tv/?=pen-test-partners) exclusively with TechCrunch. Their research found at least 47 million vulnerable devices.

“It’s only the tip of the iceberg,” he told TechCrunch.

Smartwatches leaking location data
----------------------------------

Munro and his team found that Thinkrace made more than 360 devices, mostly watches and other trackers. Because of relabeling and reselling, many Thinkrace devices are branded differently

“Often the brand owner doesn’t even realize the devices they are selling are on a Thinkrace platform,” said Munro.

Each tracking device sold interacts with the cloud platform either directly or via an endpoint hosted on a web domain operated by the reseller. The researchers traced the commands all the way back to Thinkrace’s cloud platform, which the researchers described as a common point of failure.

The researchers said that most of the commands that control the devices do not require authorization and the commands are well documented, allowing anyone with basic knowledge to gain access and track a device. And because there is no randomization of account numbers, the researchers found they could access devices in bulk simply by increasing each account number by one.

The flaws aren’t just putting children at risk, but also others who use the devices.

In one case, Thinkrace provided 10,000 smartwatches to athletes [participating](https://web.archive.org/web/20191217145621/http://www.thinkrace.net/news/company/1344.cshtml) in the Special Olympics. But the vulnerabilities meant that every athlete could have their location monitored, the researchers said.

Child voice recordings found exposed
------------------------------------

One device maker bought the rights to resell one of Thinkrace’s smartwatches. Like many other resellers, this brand owner allowed parents to track the whereabouts of their children and raise an alarm if they leave a geographical area set by the parent.

The researchers said they could track the location of any child wearing one of these watches by enumerating easy-to-guess account numbers.

The smartwatch also allows parents and children to talk to each other, just like a walkie-talkie. But the researchers found that the voice messages were recorded and stored in the insecure cloud, allowing anyone to download files.

![](https://techcrunch.com/wp-content/uploads/2019/12/audio-recording.gif)

A recording of a child’s voice from a vulnerable server of a smartwatch reseller. (We’ve removed the audio to protect the child’s privacy.)

TechCrunch listened to several recordings picked at random and could hear children talking to their parents through the app.

The researchers likened the findings to CloudPets, an internet-connected teddy bear-like toy, which, in 2017, left their cloud servers unprotected, exposing [two million](https://www.vice.com/en_us/article/pgwean/internet-of-things-teddy-bear-leaked-2-million-parent-and-kids-message-recordings) child voice recordings.

Some five million children and parents use the smartwatch sold by the reseller.

Disclosure whack-a-mole
-----------------------

The researchers disclosed the vulnerabilities to several white-label electronics makers in 2015 and 2017, including Thinkrace.

Some of the resellers fixed their vulnerable endpoints. In some cases, the fixes put in place to protect vulnerable endpoints [later became undone](https://0x0.li/trackmageddon/). But many companies simply ignored the warnings, prompting the researchers to go public with their findings.

Rick Tang, a spokesperson for Thinkrace, did not respond to a request for comment.

Munro said that while the vulnerabilities are not believed to have been widely exploited, device makers like Thinkrace “need to get better” at building more secure systems. Until then, Munro said owners should stop using these devices.

> [Many smart home device makers still won’t say if they give your data to the government](https://techcrunch.com/2019/12/11/smart-home-tech-user-data-government/)