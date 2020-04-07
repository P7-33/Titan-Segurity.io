---
title: 'Uncover, Understand, Own – Regaining Control over Your AMD CPU [video]'
date: 2019-12-29T04:13:00+01:00
draft: false
---

![](https://static.media.ccc.de/media/congress/2019/10942-hd_preview.jpg " media.ccc.de - Uncover, Understand, Own - Regaining Control Over Your AMD CPU  ")  

Uncover, Understand, Own - Regaining Control Over Your AMD CPU
==============================================================

[Robert Buhren](https://media.ccc.de/search?q=Robert+Buhren), [Alexander Eichner](https://media.ccc.de/search?q=Alexander+Eichner) and [Christian Werling](https://media.ccc.de/search?q=Christian+Werling)

Playlists:

['36c3' videos starting here](https://media.ccc.de/v/36c3-10942-uncover_understand_own_-_regaining_control_over_your_amd_cpu/playlist)

/

[audio](https://media.ccc.de/v/36c3-10942-uncover_understand_own_-_regaining_control_over_your_amd_cpu/audio)

The AMD Platform Security Processor (PSP) is a dedicated ARM CPU inside your AMD processor and runs undocumented, proprietary firmware provided by AMD.

It is a processor inside your processor that you don't control. It is essential for system startup. In fact, in runs before the main processor is even started and is responsible for bootstrapping all other components.

This talk presents our efforts investigating the PSP internals and functionality and how you can better understand it.

Our talk is divided into three parts:

The first part covers the firmware structure of the PSP and how we analyzed this proprietary firmware. We will demonstrate how to extract and replace individual firmware components of the PSP and how to observe the PSP during boot.

The second part covers the functionality of the PSP and how it interacts with other components of the x86 CPU like the DRAM controller or System Management Unit (SMU). We will present our method to gain access to the, otherwise hidden, debug output.

The talk concludes with a security analysis of the PSP firmware.  
We will demonstrate how to provide custom firmare to run on the PSP and introduce our toolchain that helps building custom applications for the PSP.

This talk documents the PSP firmware's proprietary filesystem and provides insights into reverse-engineering such a deeply embedded system. It further sheds light on how we might regain trust in AMD CPUs despite the delicate nature of the PSP.

### Download

#### These files contain multiple languages.

This Talk was translated into multiple languages. The files available for download contain all languages as separate audio-tracks. Most desktop video players allow you to choose between them.

Please look for "audio tracks" in your desktop video player.

### Tags

by [Chaos Computer Club e.V](https://ccc.de) –– [Imprint](https://ccc.de/en/imprint) –– [Privacy](https://media.ccc.de/about.html#privacy)

  
  
from Hacker News https://ift.tt/2skuZ2d