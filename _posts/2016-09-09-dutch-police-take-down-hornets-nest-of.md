---
title: 'Dutch police take down hornets'' nest of DDoS botnets'
date: 2019-10-03T07:46:00+01:00
draft: false
---

![DDoS botnet internet globe map](https://zdnet3.cbsistatic.com/hub/i/2019/10/02/9be7f25b-d4a8-4277-86cc-96ecc6af40e2/47b0bdd2622859c686321b15247a7fb9/ddos-internet-globe-map.jpg)

Dutch police have taken down this week a bulletproof hosting provider that has sheltered tens of IoT botnets that have been responsible for hundreds of thousands of DDoS attacks around the world, _ZDNet_ has learned.

Servers were seized, and two men were arrested yesterday at the offices of KV Solutions BV (KV hereinafter), a so-called bulletproof hosting provider, a term used to describe web hosting providers that ignore abuse reports and allow cybercrime operations to operate on their servers.

For two years, the company has provided hosting infrastructure to internet criminals, and has been one of the most serious offender at that, hosting all sorts of badies, from phishing pages to vulnerability scanners, and from crypto-mining operations to malware repositories.

But above all, the company has made a reputation in cyber-security circles for being a hotspot for DDoS botnets, with cyber-criminals renting KV servers to host their bot scanners, malware, and command-and-control (C&C) servers, knowing they'd be safe from "harm."

### KV hosted all sorts of botnets

This year alone, KV hosted tens of these DDoS botnets, most of which have been compiled in this Twitter mega-thread by threat intelligence firm Bad Packets LLC.

The botnets have been created using so-called "IoT malware," which is malware designed to infect Linux-based operating systems that run on routers and other "smart" (Internet of Things) devices.

In an interview with _ZDNet_, Bad Packets said the botnets operating from KV's infrastructure had been observed in the past year scanning the internet and looking to infect a wide range of devices, such as:

*   ASUS routers
*   AVTECH IoT devices
*   GPON routers
*   Fritz!Box routers
*   Huawei routers
*   JAWS web servers (generic IoT)
*   MikroTik routers
*   Netgear routers
*   ZTE cable modems

While the vast majority of DDoS botnets operating on KV's infrastructure had been seen running a version of the Mirai IoT malware, the hosting firm has also harbored botnets built with all sorts of other IoT malware, encompassing almost all IoT malware variants seen in the past year:

*   Fbot
*   Gafgyt
*   Hakai
*   Handymanny
*   Mirai
*   Moobot
*   Tsunami
*   Yowai

The vast majority of these botnets were operated by "script kiddies," or "skidz," a term meant to ridicule untalented hackers who use ready-made or automated tools to build botnets.

However, some were also operated by some of today's most talented hackers. For example, [Subby](https://www.zdnet.com/article/hacker-takes-over-29-iot-botnets/), a notorious IoT malware coder and botnet operator, was known to use KV infrastructure.

In addition, some of these botnets also reached huge sizes, accounting for tens of thousands of infected devices; eventually drawing the attention of cyber-security firms, notably [Trend Micro](https://blog.trendmicro.com/trendlabs-security-intelligence/thinkphp-vulnerability-abused-by-botnets-hakai-and-yowai/) and [Qihoo 360's Netlab](https://blog.netlab.360.com/the-botnet-cluster-on-185-244-25-0-24-en/), which spent time and resources in digging into their operations.

### KV hosted DDoS booter services

Furthermore, KV also served as a hosting provider for some botnets that were part of DDoS-for-hire (DDoS booter) services, according to Troy Mursch, co-founder of Bad Packets.

"We've been monitoring malicious activity originating from their network for a year now," Mursch told _ZDNet_ in an interview today.

"The vast majority of malware samples hosted by them were used for DDoS attacks. This goes hand-in-hand with them hosting the botnet command-and-control (C2) servers as well. It was a one-stop shop for DDoS/booter services," Mursch added.

All in all, Mursch said that "in 2019, Bad Packets detected 440,261 exploit attempts originating from and/or referencing malware payloads hosted by KV Solutions."

Victims of DDoS attacks that originated from KV-hosted botnets include Ubisoft, Wish.com, and about every major cloud and web hosting provider you can name, such as AWS, Microsoft Azure, OVH, AT&T, Comcast, Cox, Charter, and China Unicom; just to name a few.

### KV never took action against bad customers

But this high concentration of DDoS firepower on the infrastructure of one single company couldn't have gone unnoticed forever.

Several security researchers and sources in the web hosting community have told _ZDNet_ that the company "had it coming."

KV administrators sarcastically ignored abuse reports from everyone and allowed their customers to run rampant.

Complaints to Dutch authorities started coming in last year, and many fellow web hosting providers and security researchers have been gagged to silence this whole year, as Dutch cyber police slowly gathered the evidence they needed to take down the company.

### Two arrested

Dutch police finally stepped in and raided the company's offices yesterday, Tuesday, October 1, at about the time the company posted a message on its Facebook page, announcing "a malfunction," a coded message to customers to wipe their servers.

![kv-facebook.png](https://www.zdnet.com/article/dutch-police-take-down-hornets-nest-of-ddos-botnets/)

<span><img src="https://zdnet3.cbsistatic.com/hub/i/r/2019/10/02/61f806d5-e319-4f9d-aaa4-b2adb1a2b623/resize/370xauto/694651cd3e000455220055a07b2ad1ef/kv-facebook.png" alt="kv-facebook.png" /></span>

Dutch authorities made the raid public today, [in a press release](https://www.politie.nl/nieuws/2019/oktober/2/11-servers-botnet-offline.html), which also mentioned the arrests of two suspects, a 24-year-old from Veendam, and a 28-year-old from Middelburg.

The two -- Marco B., 24, from Veendam, and Angelo K., 28, from Middelburg -- are believed to be the founders of a network of five interconnected companies. Dutch privacy laws do not permit revealing a suspect's full name, so we honored this requirement for our reporting.

Marco B. and Angelo K. are listed as the owners of two web hosting firms, namely [KV Solutions BV](https://drimble.nl/bedrijf/middelburg/38201984/kv-solutions-bv.html) and [Lifehosting BV](https://drimble.nl/bedrijf/veendam/38195275/lifehosting-bv.html), but also three IT companies, [Bos IT Holding BV](https://drimble.nl/bedrijf/veendam/38187396/bos-it-holding-bv.html), [Kreikamp IT Holding BV](https://drimble.nl/bedrijf/middelburg/38187515/kreikamp-it-holding-bv.html), and [KBIT Holding BV](https://drimble.nl/bedrijf/middelburg/38190524/kbit-holding-bv.html), all having controlling rights in each other, according to public information from the Dutch Chamber of Commerce.

All the websites and domains of the five companies listed above are now down. Phone calls to contact numbers listed on cached versions of these sites were not answered.

While the Dutch police statement published today only mentions "the hosting of IoT botnets," KV's infrastructure hosted a lot of other malware as well. KV's public IP block was 185.244.25.0/24. Any malware operation that had servers in this address space saw some unfortunate downtime today.

As it happened in other raids of bulletproof hosting providers, the data from the seized servers will most likely lead to other arrests, such as botnet operators and malware authors.

![kv-snitch.png](https://www.zdnet.com/article/dutch-police-take-down-hornets-nest-of-ddos-botnets/)

<span><img src="https://zdnet2.cbsistatic.com/hub/i/2019/10/02/d7989b7c-fd4e-448c-9588-b7e42bf34e67/74736866992991ae3d2e112de9dbf5cc/kv-snitch.png" alt="kv-snitch.png" /></span>

  
  
from Hacker News https://ift.tt/2nOOrBU