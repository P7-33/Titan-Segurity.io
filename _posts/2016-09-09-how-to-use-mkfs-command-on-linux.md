---
title: 'How to Use the mkfs Command on Linux'
date: 2019-10-11T13:10:00+01:00
draft: false
---

![A Linux terminal on a laptop with an Ubuntu-style desktop.](https://www.howtogeek.com/wp-content/uploads/2019/09/stock-lede-linux-see-attribution.png)

[Fatmawati Achmad Zaenuri/Shutterstock](https://www.shutterstock.com/image-vector/linux-interface-screen-notebook-world-map-321627716)

You must create a file system before you can use any data storage device connected to a Linux computer. Learn how to use `mkfs` and other utilities to do just that for all sorts of file systems. We show you how.

 `mkfs` Makes File Systems
--------------------------

The `mkfs` command [makes file systems](http://man7.org/linux/man-pages/man8/mkfs.8.html). On other operating systems, creating a file system is called [formatting](https://en.wikipedia.org/wiki/Disk_formatting). Regardless of its name, it is the process that prepares a partition so that it can store data. The partition needs a way to store files, yes. But it also needs a mechanism to store the names and locations of those files, together with their metadata such as the file creation timestamp, the file modified timestamp, the size of the file, and so on. Once `mkfs` has built the necessary framework for handling and storing file metadata, you can start adding files to the partition.

The syntax is very simple. You just tell `mkfs` the device partition you want the file system created on, and what type of file system you want. That’s on the face of it. Behind the scenes, it’s a little different. For some time now on most Linux distributions `mkfs` has been a [wrapper](https://en.wikipedia.org/wiki/Wrapper_function) for `mke2fs`. The `mkfs` command calls the `mke2fs` command and passes it the options you’ve specified. Poor old `mke2fs` [does all of the work](http://man7.org/linux/man-pages/man8/mke2fs.8.html) but gets none of the glory.

The syntax of `mkfs` has been updated, and the old format has been deprecated. Both forms will work, but we’ll use the modern style in this article.

The Choice of File Systems
--------------------------

The modern way of using `mkfs` is to type “mkfs.” and then the name of the file system you wish to create.

To see the file systems that `mkfs` can create, type “mkfs” and then hit the Tab key twice. There’s no space after “mkfs”, just hit Tab twice.

![List of supported file systems in a terminal window](https://www.howtogeek.com/wp-content/uploads/2019/10/1-5.png)

The list of available file systems is displayed in the terminal window. The screenshot is from Ubuntu 18.04 LTS. Other distributions may offer more or fewer options. We’ll run through these and describe each one briefly. After a quick word about journaling.

Journaling is an important concept in file systems. The file systems records the pending file writes to a journal. As each file is written to, the journal is updated, and the pending write records are updated. This allows the file system to repair broken, partially written files that have occurred due to a catastrophic event such as a power cut. Some of the older file systems do not support journaling. Those that don’t, write to the disk less frequently because they don’t need to update the journal. They may perform faster, but they are more prone to damage due to interrupted file writes.

*   **Ext2**: The very first file system for Linux was the MINIX file system. It was later replaced by the first file system ever written specifically for Linux, which was [Ext](https://en.wikipedia.org/wiki/Extended_file_system). Ext2 was [Ext’s successor](https://en.wikipedia.org/wiki/Ext2). Ext2 is not a journaling file system.
*   **Ext3**: This was the [successor to Ext2](https://en.wikipedia.org/wiki/Ext3), and can be thought of as Ext2 with journaling, which protects your file system from data corruption caused by crashes and sudden power loss.
*   **Ext4**: Ext4 is the standard file system for may Linux distributions. It is a solid, tried, and trusted file system. It has features that [reduce file fragmentation](https://en.wikipedia.org/wiki/Ext4) and can be used with larger drives, partitions, and files than Ext3.
*   **BFS**: This is the [Boot File System](https://en.wikipedia.org/wiki/Boot_File_System), which is designed for one job and one only: to handle the files in the boot partition. It’s rare that you’d be creating a boot file system by hand. Your Linux installation process will do this for you.
*   **FAT**: The [File Allocation Table](https://en.wikipedia.org/wiki/File_Allocation_Table) file system was designed for floppy disks by a consortium of computer-industry heavyweights. It was introduced in 1977. The only reason you’d use this non-journaling file system is for compatibility with non-Linux operating systems.
*   **NTFS**: The [New Technology File System](https://en.wikipedia.org/wiki/NTFS) is a Microsoft journaling file system introduced with Windows NT. It was the successor to FAT. The only reason you’d use this file system is for compatibility with non-Linux operating systems.
*   **MINIX**: Originally created by [Andrew S. Tanenbaum](https://en.wikipedia.org/wiki/Andrew_S._Tanenbaum) as an educational aid, [MINIX](http://www.minix3.org/) is a “mini-Unix” operating system. Nowadays, it is aimed at providing a self-healing and fault-tolerant _operating system_. The MINIX _file system_ was designed as a [simplified version of the Unix File System](https://en.wikipedia.org/wiki/MINIX_file_system). Perhaps if you are cross-developing on a Linux computer and targetting a MINIX platform you may use this file system. Or perhaps you need compatibility with a MINIX computer for other reasons. Use cases for this file system on a Linux computer are not leaping out at me, but it’s available.
*   **VFAT**: [Virtual File Allocation Table](https://en.wiktionary.org/wiki/VFAT), was introduced with Windows 95, and removed the eight-character limit for filenames. File names of up to 255 characters became possible. The only reason you’d use this file system is for compatibility with non-Linux operating systems.
*   **CRAMFS**: The [Compressed ROM File System](https://en.wikipedia.org/wiki/Cramfs) is a read-only file system designed for embedded systems and specialist read-only uses, such as in the boot processes of Linux computers. It is common to have a small, transient, file system loaded first so that bootstrap processes can be launched to prepare for the “real” boot system to be mounted.
*   **MSDOS**: The file system of the [Microsoft Disk Operating System](https://en.wikipedia.org/wiki/MS-DOS). Released in 1981, it’s an elementary file system that is as basic as it gets. The first version didn’t even have directories. It holds a place of prominence in computing history but, beyond compatibility with legacy systems, there is little reason to use it today.

### [Read the remaining 48 paragraphs](https://www.howtogeek.com/443342/how-to-use-the-mkfs-command-on-linux/)