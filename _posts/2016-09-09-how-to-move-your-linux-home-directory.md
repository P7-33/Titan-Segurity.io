---
title: 'How to Move Your Linux home Directory to Another Drive'
date: 2019-10-03T13:08:00+01:00
draft: false
---

![Linux terminal on stylized laptop](https://www.howtogeek.com/wp-content/uploads/2019/09/stock-lede-linux-see-attribution.png)

[Fatmawati Achmad Zaenuri/Shutterstock](https://www.shutterstock.com/image-vector/linux-interface-screen-notebook-world-map-321627716)

Want to move your Linux home folder to another drive? Here’s a straightforward and step by step way to do it that should work on any distribution. Moving your home folder means you can reinstall Linux and not have to worry about your personal files.

Why Keep Your home Folder Separate?
-----------------------------------

If you’re setting up a new machine or adding a hard drive to an existing one, you may want to have your home directory on a different drive than the default location.

An increasingly popular configuration for modern personal computers is to have a medium-sized [Solid State Drive](https://www.howtogeek.com/howto/45359/htg-explains-whats-a-solid-state-drive-and-what-do-i-need-to-know/) (SSD) holding your operating system and a larger [Solid State Hybrid Drive](https://www.howtogeek.com/195262/hybrid-hard-drives-explained-why-you-might-want-one-instead-of-an-ssd/) (SSHD) or traditional hard drive (HD) as your the main storage for data. Or you may have a single traditional hard drive in your system, and you’ve added a new HD for increased storage. Whatever your reasons, here is a simple and blow by blow run-through of moving your home directory.

By the way, if you’re installing a Linux system from scratch, you’ll probably see an option to create a separate home directory in your Linux distribution’s installer. Generally, you’ll just need to go into the partitioning options, create a separate partition, and mount it at “/home”. But, if you’ve already installed a Linux distribution, you can use these instructions to move your current home directory to a new location without losing anything or reinstalling your operating system.

Now, before we start, go and [make a backup](https://www.howtogeek.com/427480/how-to-back-up-your-linux-system/).

**RELATED:** [**_How to Back Up Your Linux System_**](https://www.howtogeek.com/427480/how-to-back-up-your-linux-system/)

Identify the Drive
------------------

If you’ve just fitted a drive to a Linux computer, or installed Linux to one of the drives in a new multi-drive computer, and rebooted, there’s little evidence that the new drive is even present.

The `fdisk` command will [list the drives and their partitions](http://man7.org/linux/man-pages/man8/fdisk.8.html) for us.

```
sudo fdisk -l
```

![sudo fdisk -l in a terminal window](https://www.howtogeek.com/wp-content/uploads/2019/09/1-12.png)

### [Read the remaining 71 paragraphs](https://www.howtogeek.com/442101/how-to-move-your-linux-home-directory-to-another-hard-drive/)