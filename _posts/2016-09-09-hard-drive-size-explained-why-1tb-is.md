---
title: 'Hard Drive Size Explained: Why 1TB Is Only 931GB of Actual Space'
date: 2019-10-22T02:46:00+01:00
draft: false
---

![real-hdd-size](https://static.makeuseof.com/wp-content/uploads/2017/10/real-hdd-size.jpg)

How many times have you opened up a new computer, phone, or external drive, only to be shocked when you realize it doesn’t have as much storage space as it said on the box? That 512GB SSD might actually only hold 477GB, or your 64GB iPhone might only have room for 56GB of files.

There are a few good reasons why this happens. Let’s take a look at why advertised space isn’t usually the same as actual space.

The Operating System and Pre-Installed Apps
-------------------------------------------

The most basic reason that you don’t have all the disk space usable is that there’s already some data present when you buy it. This isn’t the case for removable disks like flash drives or SD cards, but is a major factor with phones and pre-built computers.

When you buy a computer, the operating system (such as Windows or macOS) takes up a large chunk of space. These protected OS files are necessary for the system to run as intended, so there’s no getting around them.

As an example, on my system, the **C:\\Windows** folder takes up 25GB. That’s roughly one tenth of the entire disk space.

However, it’s not just the OS files that take up space out of the box. Most operating systems include extra apps that you may or may not want. This includes everything from Windows 10 bloatware to useful built-in macOS apps like GarageBand.

While they’re not technically part of the OS, they come bundled with it and thus take up room right away. You can usually remove these to regain space; check out [our guide to freeing up storage space on Windows 10](//www.makeuseof.com/tag/low-storage-windows-10/) for some tips.

How Computers Measure Space
---------------------------

While preinstalled apps are definitely a factor, the biggest reason that you don’t get the full amount of advertised space is because computers measure numbers differently than humans do.

### Binary Numbers Explained

Computing uses standard value prefixes, including “kilo” for thousand, “mega” for million, “giga” for billion, “tera” for trillion, and so on. For a primer on these, we’ve looked at [how many gigabytes are in a terabyte](//www.makeuseof.com/tag/memory-sizes-gigabytes-terabytes-petabytes/) and more.

People, including hard disk manufacturers, use the decimal system, which measures numbers with a base of 10. Thus, when we say “500 gigabytes,” we mean 500 trillion bytes.

However, computers use the base 2 binary system, where all numbers are either 1 or 0. If you’re not familiar, below is a list of the numbers 1-10 written out in binary:

```
1  
10  
11  
100  
101  
110  
111  
1000  
1001  
1010  

```

As you can see, in binary, 21 represents the decimal value 1, 22 is equal to 2, 23 equals 4, 24 is the same as 8, and so on. Each new digit’s place in binary increase the number’s value by one power of two. 210, then, equals 1,024.

### Binary and Decimal Measuring

Now we know why computers use 1,024 instead of 1,000 to define these common prefixes. To a computer, one kilobyte is 1,024 bytes, not 1,000 bytes as it is to people. This compounds as you move up the scale, so one megabyte is 1,024 kilobytes, and one gigabyte is 1,024 megabytes.

To see how this affects you, say you buy a 250GB external SSD. That disk contains 250,000,000,000 bytes, but the computer doesn’t display it that way.

Working backwards, we can divide by 1,024 three times (once to convert bytes to kilobytes, again to convert kilobytes to megabytes, and a final time to convert megabytes to gigabytes) to see how much space this actually is:

`250,000,000,000 / (1,024 * 1,024 * 1,024) = 232,830,643,653 bytes, or 232.83GB`

Examining a 250GB drive in Windows shows its maximum space as 232GB, which is exactly what our above calculation found. That’s a difference of about 18GB.

And the larger the disk is, the bigger the difference between measured space and actual space. For example, a 1TB (1,000GB) disk has 931GB of space according to a computer.

### Gigabyte vs. Gibibyte

After walking through this, you might wonder why this disparity exists. Why don’t hard drive manufacturers provide an accurate amount of space on their devices? Well, they technically do.

The correct definition of “giga” is a power of 1,000. There’s another name for a power of 1,024: “gibi.” The International Electrotechnical Commission has published standards for measuring data in binary in order to resolve this confusion.

While a kilobyte (KB) represents 1,000 bytes, a kibibyte (KiB) represents 1,024 bytes. It’s the same for mebibytes (MiB), gibibytes (GiB), tebibytes (TiB), and so on.

For some reason, Windows inaccurately uses the “GB” prefix when it’s really measuring in gibibytes. Other operating systems, like macOS, correctly measure 1GB as one billion bytes. Thus, the same 250GB drive connected to a Mac would show it having 250GB of total space.

Note that this is different than [the difference between megabytes and megabits](//www.makeuseof.com/tag/megabit-vs-megabyte/), which we’ve also explained.

Additional Disk Partitions
--------------------------

Aside from the above, another potential cause for a reduction in the total amount of space a drive has is additional partitions.

In case you weren’t aware, you can separate physical hard disks into different logical sections, which is known as partitioning. [Partitioning a hard drive](//www.makeuseof.com/tag/partition-hard-drive-explained/) allows you to install two different operating systems on one disk, among other uses.

When you buy a computer off the shelf, the manufacturer often includes a recovery partition on the disk. This contains data that allows you to reset your system in case of a serious problem. Like any other files, they take up space on the drive. But because recovery partitions are often hidden from standard view, you might know not they’re around.

To view the partitions on your drive in Windows, type **disk management** into the Start menu and click **Create and format hard disk partitions**. Here you can see each disk on your system and the partitions that make it up. If you see a label of **Restore**, **Recovery**, or similar, that’s your recovery partition.

In most cases, it’s possible to erase these partitions and regain that space. However, it’s usually best to leave them alone. Having them makes recovering your system a lot easier, and the small space gain isn’t worth the hassle of recovering your system manually.

Hidden Features That Also Use Space
-----------------------------------

Finally, most operating systems contain features that take up space but don’t exist as actual files. For example, Windows’s Shadow Copy service is used to power both the Previous Versions and System Restore functions.

System Restore lets you return to an earlier point in time if your system isn’t working properly, while Previous Versions keeps copies of your personal files so you can undo changes. Both of these need space to work, of course.

To see and change how much space features that rely on Shadow Copy services use, press **Win + Pause** to quickly open the **System** Control Panel entry. From here, click **System protection** on the left side. In the resulting window, select your drive from the list and choose **Configure**.

You’ll see a new dialog box that allows you to disable system protection entirely (though we don’t recommend this). Below, you’ll see the **Current Usage** and can adjust the maximum amount that Windows uses. Somewhere around 10 percent is a good amount.

Now You Know How Computers Calculate Space
------------------------------------------

The elements discussed account for the noticeable difference in advertised and actual storage space. While there are some other minor factors, such as special blocks in SSDs, these are the major reasons. Knowing them, it’s wise to plan ahead and make sure you always get the amount of storage you need with new devices.

If you’re low on space, have a look at [how to add more storage to your Mac](//www.makeuseof.com/tag/add-storage-macbook/). Most of the advice applies to other platforms, too.

Read the full article: [Hard Drive Size Explained: Why 1TB Is Only 931GB of Actual Space](https://www.makeuseof.com/tag/1-tb-931-gb-hard-drive/)

  
  
from MakeUseOf https://ift.tt/35UN8T2  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)