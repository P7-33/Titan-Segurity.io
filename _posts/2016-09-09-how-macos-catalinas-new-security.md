---
title: 'How macOS Catalina’s New Security Features Work'
date: 2019-10-21T13:12:00+01:00
draft: false
---

![Hands holding a lock over a MacBook](https://www.howtogeek.com/wp-content/uploads/2019/10/img_5da8e3d29cabb.jpg)

[Issarawat Tattong/Shutterstock.com](https://www.shutterstock.com/image-photo/hacker-unlock-key-laptop-335695670)

macOS Catalina introduces new security controls. For example, apps are now required to ask your permission before accessing parts of the drive where documents and personal files are kept. Let’s take a look at what’s new for security in Catalina.

Some Apps Require Permission to Access Your Files
-------------------------------------------------

![macOS Catalina Disk Access Permission Dialog](https://www.howtogeek.com/wp-content/uploads/2019/10/terminal_disk_permission.png)

Apps now have to request permission to access certain parts of your file system. This includes your Documents and Desktop folders, your iCloud Drive, and any external volumes that are currently connected to your Mac (including flash drives, memory cards, and so on). This is the change that’s been getting the most headlines.

Apple has been pushing permission-based access for a while on iOS, and we’re seeing more of these security policies make their way into macOS. When you first upgrade to Catalina, this can result in a blizzard of permission request dialog boxes. This has led some to compare the feature to Windows Vista’s full-screen security prompts (but in reality, it’s nowhere near as egregious).

> Unedited Catalina first-run experience.
> 
> And I haven't even begun to do actual work yet.
> 
> This could be Apple's shining Windows Vista moment. [pic.twitter.com/CxuVhA3BxV](https://t.co/CxuVhA3BxV)
> 
> — Tyler Hall (@tylerhall) [October 7, 2019](https://twitter.com/tylerhall/status/1181321324888776710?ref_src=twsrc%5Etfw)

From a security standpoint, it’s a change to be welcomed, though it can take some time to get used to. Not every app will request access, either. In our tests, we were able to open and save files using markdown editor Typora, but navigating to the Documents folder in Terminal using the `cd ~/Documents/` command prompted a request for permission.

### [Read the remaining 32 paragraphs](https://www.howtogeek.com/443611/how-macos-catalinas-new-security-features-work/)