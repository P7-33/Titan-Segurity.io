---
title: 'Updating to Windows 10 for Fun and Profit: Make Those OEM Keys Go
Further'
date: 2019-12-05T16:07:00+01:00
draft: false
---

Microsoft seems to have an every-other-version curse. We’re not sure how much of this is confirmation bias, but consider the track record of releases. Windows 95 was game-changing, Windows 98 famously [crashed during live demo](https://www.youtube.com/watch?v=IW7Rqwwth84). Windows 2000 was amazing, Windows ME has been nicknamed the “Mistake Edition”. XP was the workhorse of the world for years and years, and Vista was… well, it was Vista. Windows 7 is the current reigning champion of desktop installs, and Windows 8 was the version that put a touchscreen interface on desktops. The “curse” is probably an example of finding patterns just because we’re looking for them, but the stats do show a large crowd clinging to Windows 7.

Windows 10 made a name for itself by automatically installing itself on Windows 7 and Windows 8 computers, much to the annoyance of many unexpecting “victims” of that free upgrade. Several years have gone by, Windows 10 has gotten better, and support for Windows 7 ends in January. If you’re tied to the Windows ecosystem, it’s time to upgrade to Windows 10. It’s too bad you missed out on the free upgrade to Windows 10, right?

About that… It’s probably an unintended side effect, but all valid Windows 7 and Windows 8 keys are also valid Windows 10 keys. Activation is potentially another issue, but we’ll get to that later.

What Exactly Do They Mean by OEM License?
-----------------------------------------

Microsoft has finally come to their collective senses: [Windows install ISOs are available for download](https://www.microsoft.com/en-us/software-download/windows10ISO). There are only 2 ISOs, 32 bit and 64 bit. Both images support home and professional versions, and the right version is installed based on the Windows key provided.

Speaking of versions, let’s talk about the different Windows versions. Not the difference between home and professional, but what is meant by an OEM license. Take a look at Windows 10 Pro on Amazon. Right now I see Windows 10 Professional for $184.99, and a Windows 10 Professional OEM for $113. What’s the difference? The packaging may look different, calling Microsoft Support might be a different experience, but the main difference is that an OEM key is locked to the computer it is first installed on.

How do computer upgrades work with an OEM key? The Ship of Theseus is a useful thought experiment. Taken directly from [the Wikipedia article](https://en.wikipedia.org/wiki/Ship_of_Theseus):

> If it is supposed that the famous ship sailed by the hero Theseus in a great battle has been kept in a harbour as a museum piece, and as the years went by some of the wooden parts began to rot and were replaced by new ones then, after a century or so, all of the parts had been replaced. The question then is if the “restored” ship is still the same object as the original.
> 
> If it is then supposed that each of the removed pieces were stored in a warehouse, and after the century, technology developed to cure their rotting and enabled them to be put back together to make a ship, then the question is if this “reconstructed” ship is still the original ship. And if so, then the question also regards the restored ship in the harbour still being the original ship as well.

How much of a computer’s hardware can you upgrade and still consider it the same computer? Rather than wrestle with such a philosophical question for every instance, Microsoft has opted for a simple rule. A new motherboard constitutes a new computer.

So where does that leave us? First, you can go download a Windows 10 ISO, burn it to a DVD, and do a free upgrade right now from Windows 7 or 8. Boot into Windows as normal, and then run the setup executable from the DVD. Follow the prompts to start the upgrade. The installer will copy everything it needs to the hard drive and reboot the machine. After the install finishes, Windows will go through the activation process again, and activation should succeed.

Something about the free upgrade process forces Microsoft to treat this Windows 10 activation as a new computer activation. Because every Windows 7/8 key is eligible for the free upgrade, this means that you can do a full hardware rebuild, motherboard included, and use your Windows 7 OEM key to install Windows 10, and activation should succeed. Do note that this will work only once. Once you’ve used your free upgrade, that Windows key is once again locked, and out of additional activations.

Give Windows The Old Switcheroo
-------------------------------

There is one more trick worth mentioning. You may be familiar with the challenge of upgrading hardware on an existing Windows install. It’s not uncommon for booting with the new hardware to trigger a BSOD before the desktop even loads. The Windows 10 upgrade process has the side-effect of re-installing all the hardware drivers, making it a perfect time for that hardware upgrade. The timing on this is a little tricky. You need to run the setup off the Windows 10 disk and wait for the setup files to finish copying over. When the setup program reboots to start the actual installation, pull the power plug before the drive starts to boot again. You may find it useful to first turn off quiet boot in BIOS. The window for interrupting the process is narrow, but success gives you a hard drive with all your existing data and programs, ready to install Windows 10 on next boot. Rebuild the hardware with all the changes you’d like to make, and boot off that hard drive. Windows 10 will install the proper drivers, just like a fresh install, and the Windows 7 key should activate without any issues.

It’s time to face the music, and upgrade from Windows 7. If you just can’t stomach Windows 10, at least there are options. [Open Shell](https://open-shell.github.io/Open-Shell-Menu/) is the open source successor to Classic Shell, and many find it to smooth the rough edges. Alternatively, maybe it’s time to look at Linux? We’re still holding out hope that the Year of the Linux Desktop![™](https://s.w.org/images/core/emoji/12.0.0-1/72x72/2122.png) is coming. Or for those willing to go over to the dark side, there is that [other Unix derived desktop OS](https://en.wikipedia.org/wiki/MacOS) you could use. In any case, stay secure out there.

  
  
from Hackaday https://ift.tt/2YrC4tm  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)