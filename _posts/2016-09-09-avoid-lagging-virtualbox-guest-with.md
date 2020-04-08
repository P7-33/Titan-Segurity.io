---
title: 'Avoid Lagging VirtualBox Guest With Linux'
date: 2019-10-14T21:43:00+01:00
draft: false
---

You may found Linux VirtualBox guest lagging on audio with video playback and slow performance on the whole guest. The culprit is audio driver that you even do not believe in.  
  
  
  
Set the audio controller to "Intel HD Audio" and driver to "ALSA Audio Driver" to solve the problem on Ubuntu Host. I well tested this setting on the following environments :  
  
  
  
(1) Ubuntu Desktop 19.04 Host with Ubuntu Desktop 19.04 Guest  
  
(2) Ubuntu Desktop 19.04 Host with Kali Linux Rolling Guest  
  
(3) MacOS Catalina Host with Ubuntu Desktop 19.04 Guest (CoreAudio and Intel HD Audio)  
  
  
  
That's all! See you.