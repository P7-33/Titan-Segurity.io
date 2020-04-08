---
title: '5 Tips for OSCP Prep by Mitch Moser'
date: 2019-12-15T19:43:00+01:00
draft: false
---

![](https://miro.medium.com/max/60/1*dTaPMAj_l7iRlv2Y1a14OA.png?q=20)

![](https://miro.medium.com/max/700/1*dTaPMAj_l7iRlv2Y1a14OA.png)

The ominous Offensive Security logo

Introduction
============

Many OSCP write-ups focus on discussing the time spent in the PWK course and labs. I spent a significant amount of time preparing for this course before enrolling and I was able to pass the exam with only 30 days of lab access. Feel free to skip past the following section and check out the 5 tips that prepared me the most for this course!

My OSCP Experience
==================

I first heard about OSCP two years ago and knew it was something I wanted to achieve. There was something unique and fascinating about the format: A 24hr exam. Completely practical — no multiple choice questions. Limited use of automated tools. This all sounded extremely challenging. And it was!

Receiving the coursework was daunting as it all floods in at once: Lab access, the 380 page textbook, and the hours of videos. I was able to knock out the PWK course along with roughly 90% of the exercises within the first week. During the coursework I was reverting boxes in the network and running intensive scans after their services came back up.

After completing the course materials, I proceeded into the lab now having a full list of scanned hosts. I spent the next couple of weeks popping boxes and documenting my processes, refining my workflow, and honestly getting used to interacting with some of the older systems and services. During my last week of lab access, I went over my lab report to ensure I hadn’t missed anything. My final report was 198 pages — primarily due to including large, readable screenshots and code snippets!

Following my 30 days of lab access, I used my exam attempt to assess my readiness to complete this course. My strategy was to start on the buffer overflow machine while I scanned the other 4 hosts then knock out one of the easier boxes. This plan combined with my lab report would give me over half the points to pass with plenty of time left to gain the other points I would need to pass the exam.

I rooted the BOF box, an easier box, and had user on two of the medium boxes within within 9hrs of the exam. I struggled and was unable to follow manual privilege escalation routes on either of my medium boxes which should have pushed me into a passing grade.

Discouraged from the initial exam attempt but overall happy with my performance given the tough selection of boxes, I chose to schedule a second attempt and hope for different medium hosts! I spent the time leading up to my second attempt rooting a couple of retired windows HackTheBox machines and staying sharp on my overall process and workflow.

My second exam attempt went smoothly and I managed to root both medium boxes. After those machines, I had more than enough points to pass including my lab report and I chose to forego the hard machine in order to complete my 39-page exam report while I still had VPN access. I completed the exam and submitted my report within 20hrs.

[

Offensive Security Certified Professional (OSCP) was issued by Offensive Security to Mitchell…


--------------------------------------------------------------------------------------------------

### 

An OSCP is able to research a network, identify vulnerabilities and successfully execute attacks. This often includes…

#### 

www.youracclaim.com









](https://www.youracclaim.com/badges/2977e03d-612c-4006-810f-454f271b512b?source=post_page-----76001cdf4f4f----------------------)

1\. HackTheBox & IppSec
=======================

[

HackTheBox :: Penetration Testing Labs


------------------------------------------

### 

An online platform to test and advance your skills in penetration testing and cyber security. Join today and start…

#### 

www.hackthebox.eu









](https://www.hackthebox.eu/?source=post_page-----76001cdf4f4f----------------------)

[

IppSec


----------

### 

You probably know about my channel. Here's a bunch of other content I enjoy. Patreon Pages of Cool People…

#### 

www.youtube.com









](https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA?source=post_page-----76001cdf4f4f----------------------)

One of many great lists of OSCP-like HTB machines

HackTheBox has been such an amazing resource for hands-on learning and I don’t think I would have been able to prepare or construct a workflow that applied to PWK/OSCP without this. IppSec’s videos on retired boxes are excellent and pair well with the DIY approach to learning that HackTheBox offers. I learn new, invaluable tidbits of information from each of his videos as well as alternative ways to solve some of the problems I had encountered with boxes I had rooted before they were retired.

2\. Georgia Weidman
===================

[

Penetration Testing | No Starch Press


-----------------------------------------

### 

Penetration testers simulate cyber attacks to find security weaknesses in networks, operating systems, and…

#### 

nostarch.com









](https://nostarch.com/pentesting?source=post_page-----76001cdf4f4f----------------------)

[

Free Advanced Penetration Testing Course from Cybrary


---------------------------------------------------------

### 

Our free, online Advanced Penetration Testing course provides you with skills that prepare you to work in one of the…

#### 

www.cybrary.it









](https://www.cybrary.it/course/advanced-penetration-testing/?source=post_page-----76001cdf4f4f----------------------)

Georgia Weidman’s materials are fantastic resources for easing into the material covered in PWK at your own pace. She offers a free course on Cybrary which goes hand-in-hand with her book. This material is highly recommended if you would like to take a step beyond reviewing PWK’s syllabus but don’t feel ready to enroll in the course quite yet.

3\. dostackbufferoverflowgood
=============================

[

justinsteven/dostackbufferoverflowgood


------------------------------------------

### 

Contribute to justinsteven/dostackbufferoverflowgood development by creating an account on GitHub.

#### 

github.com









](https://github.com/justinsteven/dostackbufferoverflowgood?source=post_page-----76001cdf4f4f----------------------)

Like many, I was intimidated by the idea of writing a buffer overflow from scratch which is required in both the course and the exam. I sought out many resources and this one helped me wrap my mind around this topic the most. Justin includes a vulnerable binary as well as reading material which explain his process and workflow which translated perfectly into the buffer overflow portions of the lab and exam.

If there was just one takeaway from his methods that I recommend looking into it is how he **_automated the identification of bad characters using Mona modules in Immunity Debugger_**! This is by far the most sophisticated method I have been able to find and helped keep me sane during the practice sessions leading up to PWK as well as in the course exercises and during the exam.

Georgia Weidman’s coverage of WarFTP and Vulnserver were also great practice tools for getting comfortable with this topic.

[

WarFTP 1.65 — ‘USER’ Remote Buffer Overflow


-----------------------------------------------

### 

CVE-34041CVE-2007-1567 . remote exploit for Windows platform

#### 

www.exploit-db.com









](https://www.exploit-db.com/exploits/3570?source=post_page-----76001cdf4f4f----------------------)

[

stephenbradshaw/vulnserver


------------------------------

### 

Vulnerable server used for learning software exploitation - stephenbradshaw/vulnserver

#### 

github.com









](https://github.com/stephenbradshaw/vulnserver?source=post_page-----76001cdf4f4f----------------------)

4\. Discord Communities
=======================

[

InfoSec Community


---------------------

### 

Step up your game with a modern voice & text chat app. Crystal clear voice, multiple server and channel support, mobile…

#### 

discord.gg









](https://discord.gg/TN3jXaQ?source=post_page-----76001cdf4f4f----------------------)

[

OSCP


--------

### 

Step up your game with a modern voice & text chat app. Crystal clear voice, multiple server and channel support, mobile…

#### 

discord.gg









](https://discord.gg/2G2nap8?source=post_page-----76001cdf4f4f----------------------)

[

PWK/OSCP Prep


-----------------

### 

Step up your game with a modern voice & text chat app. Crystal clear voice, multiple server and channel support, mobile…

#### 

discord.gg









](https://discord.gg/n7ubFqq?source=post_page-----76001cdf4f4f----------------------)

[

The Many Hats Club


----------------------

### 

The Many Hats Club is an information security focused group of individuals from all walks of life. We offer the infosec…

#### 

themanyhats.club









](https://themanyhats.club/invite/?source=post_page-----76001cdf4f4f----------------------)

These are great groups to discussing ideas, find motivation, avoid burnout, get advice on challenges, as well as answer questions regarding the course material. These are not a place for spoilers but are often a platform to talk out an idea or train of thought and communicate with fellow students in near real-time. I gained a lot from these communities.

5\. onetwopunch
===============

A small practical tip I’ll include is a handy tool called onetwopunch which helped knock out a lot of the mundane scanning in the large lab network with impressive accuracy. This tool uses unicornscan to quickly scanning every TCP and UDP port on a host, then passes open ports to nmap which you can specify flags with. I used this to run my scans on both the lab and exam networks with ease and accuracy.

[

superkojiman/onetwopunch


----------------------------

### 

Use unicornscan to quickly scan all open ports, and then pass the open ports to nmap for detailed scans. …

#### 

github.com









](https://github.com/superkojiman/onetwopunch?source=post_page-----76001cdf4f4f----------------------)