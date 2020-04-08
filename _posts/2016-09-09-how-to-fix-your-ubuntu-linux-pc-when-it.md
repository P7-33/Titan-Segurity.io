---
title: 'How to Fix Your Ubuntu Linux PC When It Won’t Boot'
date: 2019-12-04T02:51:00+01:00
draft: false
---

![ubuntu-wont-boot](https://static.makeuseof.com/wp-content/uploads/2017/04/ubuntu-wont-boot.jpg)

You’re booting up, preparing to do some work, edit a document, mix a composition, or just play a game… but something goes wrong.

**Unlock the "[Essential Linux Commands](//www.makeuseof.com/tag/linux-commands-reference-pdf/)" cheat sheet now!**

This will sign you up to our newsletter

Enter your Email

Unlock

[Read our privacy policy](//www.makeuseof.com/legal/)

Ubuntu won’t boot.

Sadly, as reliable as Linux is in general, and as popular as Ubuntu is, sometimes it runs into problems, just like Windows 10 or macOS. In most cases, you’ll be able to work around this. Here’s how to fix Ubuntu booting problems.

Ubuntu Not Booting? Try These 5 Tips
------------------------------------

Ubuntu typically works out of the box. But when problems booting arise, Ubuntu probably takes a while or simply does not boot at all.

If Ubuntu is not starting, work through these five steps:

1.  Check for bootable devices
2.  Is the GRUB bootloader working?
3.  Repair the bootloader menu
4.  Reinstall Ubuntu
5.  Replace faulty hardware

While these steps are designed for Ubuntu users, they can be applied to other Linux operating systems. Note, however, that if you’re using disk encryption, some of these fixes will not work.

If your Ubuntu system isn’t booting, it’s time to work through these five steps.

1\. Is a Bootable Device Causing Ubuntu Boot Problems?
------------------------------------------------------

If your computer isn’t booting, could it be because there is a bootable disk attached or loaded?

You’re not alone. One of the most common problems with Ubuntu not booting occurs right after installation. This is because the Ubuntu boot disk (USB device or a DVD) is set as the boot device.

In short, Ubuntu won’t boot after install because the disk is still present. So, eject the disk, and ensure the correct boot device is selected.

Checking the boot device can be done in your system UEFI/BIOS, or if available, the boot order menu. Both can be accessed from the POST screen, which appears when your PC powers up. Take a moment to [change the boot order](//www.makeuseof.com/tag/how-to-change-the-boot-order-on-your-pc-so-you-can-boot-from-usb/), then try rebooting.

(If you run into trouble finding the boot order menu, check the computer’s (or motherboard’s) documentation.)

2\. GRUB Bootloader Issues Might Stop Ubuntu Booting
----------------------------------------------------

GRUB is the bootloader that ensures the selected operating system boots. On a dual booting machine, it will list and boot all installed operating systems, including Windows.

However, installing Windows alongside Ubuntu can lead to the bootloader being overwritten, leading to problems booting Ubuntu.

Other issues can corrupt the bootloader, such as a failed upgrade, or power failure. It isn’t unusual for [a bug to ruin the Linux experience](//www.makeuseof.com/tag/reasons-why-linux-plagued-bugs/).

To check the GRUB bootloader, restart your PC, while holding **Shift**. You should now see a list of the installed operating systems; navigate the menu using the arrow keys.

If not, then the problem is that the GRUB bootloader is broken or overwritten. Repairing the bootloader is the only solution. (If you’re dual booting, you’ll still be able to access Windows).

Note: If you see the GRUB Bootloader, skip down to the next section.

### Repair the GRUB Bootloader to Boot Ubuntu

If GRUB is not loading, then Ubuntu won’t boot. Fortunately, you can repair GRUB using the Ubuntu installation media. Restart the computer with the disc inserted and wait for it to load up.

Again, you may need to change the boot order, as described above. Make a note of the boot order before you change it!

With the installation disc booted into the Live environment, confirm you have a network connection and then open a Terminal. Enter:

```
sudo apt-add-repository ppa:yannubuntu/boot-repair  
  
sudo apt update  
  
sudo apt install -y boot-repair  
  
boot-repair
```

This will install the boot-repair tool and run it after the final instruction. Wait for the system to be scanned, then select **Recommended Repair**. (There is also an **Advanced options** view, where you can select a default OS, default disk or partition, and more.)

Click **Apply** when done. You should now be able to restart your PC and boot into Ubuntu. Alternatively, it will be listed an option in the GRUB bootloader menu.

3\. Ubuntu Still Won’t Boot? Fix the GRUB Bootloader Menu
---------------------------------------------------------

If you can see the bootloader, then you don’t have to do any of the above. There is a built-in recovery tool which you can use to help fix Ubuntu booting problems.

In the bootloader menu, select **Advanced options for Ubuntu**. Next, use the arrow keys to select the entry appended with **(recovery mode)**. Tap **Enter** to continue and wait as Ubuntu is booted into a slimmed down version.

(If you’ve ever [booted Windows Safe Mode](//www.makeuseof.com/tag/boot-windows-10-safe-mode/), this is similar.)

Several repair options can solve situations when Ubuntu won’t boot. The three you should try, in order, are:

1.  `fsck`: This is the file system check tool, which scans the hard disk drive and repairs any errors it finds.
2.  `clean`: Use this to make free space, useful if the reason for Ubuntu not booting is a lack of HDD space.
3.  `dpkg`: With this, you can repair broken software packages. Failed software installations or updates can cause problems with Ubuntu not starting. Repairing them should solve this.

If Ubuntu has never booted previously, you should also try the failsafeX tool. Graphics drivers or a problem with the Xorg graphical server might be the fault if Ubuntu won’t boot after installing. Use failsafeX to overcome this.

Note that the root menu item is for advanced users who have the skills to fix the problem manually.

4\. Ubuntu Not Starting? Time to Reinstall
------------------------------------------

In the event of a dreadful failure that could prove time-consuming to resolve, you might prefer to simply reinstall Ubuntu. This can be done without overwriting your existing files and folders. In fact, it’s one of the easiest fixes if Ubuntu won’t boot.

Again, boot into the Live environment on your Ubuntu CD/DVD or USB drive, and begin the installation. The installer will detect the existing instance of Ubuntu and give you the option to **Reinstall Ubuntu**.

Look for the option with the note “Documents, music, and other personal files will be kept…” In most cases, installed software will be retained too.

Of course, as a precaution, you should already have a backup of all your Ubuntu data. This might have been made manually with a backup utility, or using a [disk cloning tool like dd](//www.makeuseof.com/tag/easily-clone-restore-linux-disk-image-dd/). You might prefer syncing data to the cloud via Dropbox or an [open source cloud solution.](//www.makeuseof.com/tag/10-cloud-solutions-using-linux/)

Once the reinstallation is complete, Ubuntu should be back up and running.

Note: The **Erase Ubuntu and Install** option is not advised unless other options fail and your data is backed up.

5\. Replace Your Faulty Hardware
--------------------------------

Image Credit: [William Warby](https://flic.kr/p/iNmvEe)

Another cause of Ubuntu being unable to boot comes in the shape of faulty hardware. Boot problems can be caused by:

*   Hard disk drive and cabling
*   Motherboard
*   Processor (CPU)
*   Power Supply Unit

Try our guide for [diagnosing a hard disk drive](//www.makeuseof.com/tag/how-to-diagnose-and-fix-a-dead-hard-drive-to-recover-data/). You might also read up on focusing your efforts to diagnose hardware issues that prevent the computer from booting, and [repairing them without breaking the bank](//www.makeuseof.com/tag/6-tips-to-save-money-on-pc-repairs/).

Once a faulty HDD is replaced, you’ll typically need to reinstall Ubuntu from scratch. (Unless you had previously made full disc image backup, in which case this could be restored.)

It’s a scorched earth approach, but will solve problems with Ubuntu not starting.

Say Goodbye to Ubuntu Booting Problems!
---------------------------------------

If Ubuntu won’t boot, it isn’t necessarily going to be easy to get things running again. If the GRUB bootloader cannot be repaired, it could be a long time before you have a usable computer again. Yet another argument in favor of maintaining regular backups, or at least syncing your valuable data with the cloud!

Remember, this can happen with any operating system, not just Ubuntu. Having doubts? Here’s a quick reminder as to [why you should stick with Ubuntu](//www.makeuseof.com/tag/reasons-stick-with-ubuntu/).

Read the full article: [How to Fix Your Ubuntu Linux PC When It Won’t Boot](https://www.makeuseof.com/tag/fix-ubuntu-linux-pc-wont-boot/)

  
  
from MakeUseOf https://ift.tt/2P9lzOm  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)