---
title: 'Multiple Ways to Mount Raw Images (Windows)'
date: 2020-01-22T17:06:00+01:00
draft: false
---

In this article, we are going to learn how we can mount a forensic image in Windows Machine. There are multiple ways to accomplish this and tools like OSF Mount, Arsenal etc. will help us in this process. So, Let’s Start.

### **Table of Content**

*   **Introduction**
*   **Why Mount an Image?**
*   **Mounting Tools**
    *   **Mount Image Pro**
    *   **OSF Mount**
    *   **Arsenal Image Mounter**
    *   **Access Data FTK Imager**

### **Introduction**

In the Cyber Forensic world, a forensic image is a complete sector by sector copy of a hard drive or external drive. Generally, a forensic image is used as evidence in forensic investigation. These images include unlocated space, slack space and boot records. Some computer forensic tool uses different formats to generate a forensic image.

Some common forensic images formats are RAW, E01, AFF, etc. We can use a variety of tools to analyze and mount that image to get better investigative results.

### **Why Mount an Image?**

Mounting is the process that converts a RAW logical image into a mounted directory. To better examine a forensic image mounting is preferred. There are various tools that can be used to mount a RAW image. Let’s Learn the process of mounting using this variety of tools. Although the basic procedure is the same there are times where an investigator finds himself in a situation where he/she cannot use their preferred tool. Also, Each investigative company uses different tools. So a good investigator should know all the different types of tools to widen their ability and robustness.

### **Tool #1: Mount Image Pro**

Mount Image Pro is a tool, which is quite useful in Forensic investigations. It enables the mounting image across all the forensic image extensions. Some of them are:

*   .RAW
*   .E01 (Encase Image)
*   .A01
*   .dd

This tool is developed by GetData. They are Renowned Provider of User-End software. That provides Data Recovery, File Recovery, Computer Forensics and File Previewing. Their products are designed for getting data back from systems and their hard drives.

We can download the mount image pro from [here](http://www.mountimage.com/).

Once downloaded the mount image pro, then launch tool using the Icon created on the Desktop. After launching the app, we need to press the **Mount** icon to get started.

![](https://i2.wp.com/1.bp.blogspot.com/-Z7IiEUlXsHs/XihqciOCbQI/AAAAAAAAiSI/cr1EUH8t6Mg5CTIhIFIQE00jLI1Nbtv8gCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

We can also click on the File from the Dropdown menu. Go for the “**Mount Image File**” Option to move ahead.

![](https://i2.wp.com/1.bp.blogspot.com/-Z7IiEUlXsHs/XihqciOCbQI/AAAAAAAAiSI/cr1EUH8t6Mg5CTIhIFIQE00jLI1Nbtv8gCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

After this, we need to select our digital image file on our hard drive. After selecting the image file, we need to click on the “**Open**” button to open the image file.

![](https://i0.wp.com/1.bp.blogspot.com/-XJ12SjPSKKg/XihqgxYEpgI/AAAAAAAAiS8/Ok5usT_2h2Y3Y8WRhGhb1-LOzM0Qy6a-ACLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

Now, we need to select a bunch of options to get started. First one is How we want to mount our image? We want the image to be mounted and shown as a partition in our Explorer. Hence we choose the Disk Option. If you want to investigate the image as a Directory choose File System. Followed by this is the location where we want to mount. If we choose the File System Option, we need to specify the Destination Directory. Here we can Choose an Alphabet which would act as Drive Letter (such as Local Disk D: or E: etc.). Next, we get to Disk options panel here, we checked plug and play so that the dismount is easier. Now we select the kind of access that we want to get. We choose the Read-Only Access. We can also customize the Sector Size of the Partition. After giving all the required details press the **OK** button.

![](https://i0.wp.com/1.bp.blogspot.com/-yNmyyP-itD8/XihqhVHCeWI/AAAAAAAAiTA/3S-KwmFKSZchB8FbZvDIye0AUx4bYrr6QCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

After this, mounting will starts and we get a live progression of the process through the status bar as depicted below.

![](https://i0.wp.com/1.bp.blogspot.com/-50TivcHEeIs/XihqhxqXFeI/AAAAAAAAiTE/BaKhcyWrossaEJzpTA93LCaS_rBgpifxwCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

After completion, we will get our mounted image and we can start our investigation.

![](https://i0.wp.com/1.bp.blogspot.com/-7q6p4TWqfi8/XihqiLWlcFI/AAAAAAAAiTI/s5_Zg-FxdCMMUfVYCCmnPpqId57DyUlewCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

As the screenshot suggests it mounted our forensic image as F drive. Now, we can analyze it and get the same view from the files as its user gets in its system.

### **Tool #2:** **OSF Mount**

OSF Mount is the software that allows us to mount local disk image files (sector by sector copies off an entire disk or disk partition) in windows system.  We can then analyze the disk with its other tool which is OS Forensics. By default, the image files are mounted as read-only so that our original image files do not get altered.

This software supports mounting disk images files in any mode, whether we want them in the read-only mode, write mode in write cache mode.

We can download OSF mount from [here](https://www.osforensics.com/tools/mount-disk-images.html).

Let’s Begin with opening the OSF mount after completing its installation process. The developers at PassMark gave us a neat UI to work upon. We have a very minimalistic interface here. To begin with, we will hit the **“Mount New**” Button.

![](https://i1.wp.com/1.bp.blogspot.com/-U5ChZoBvTm0/XihqiQGtsNI/AAAAAAAAiTM/-1I1SS2rjvEd-EolwmIb0IQXh1JshMnmACLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

After that, we follow a series of steps where we fill in the required details.

Step #1: We need to provide the source of the image file to mount for our investigation.

After filling in details, we hit the **Next** button.

![](https://i0.wp.com/1.bp.blogspot.com/-92lTsbuNEp4/Xihqiz8pBWI/AAAAAAAAiTQ/z0nWrFN6v1obM3RRPgLHPm7XMwY5VaDkgCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

Step #2: We need to select if we want a specific partition or we want the entire image mounted for investigation.

![](https://i2.wp.com/1.bp.blogspot.com/-mysuL2Uwq14/Xihqi98qYAI/AAAAAAAAiTU/dQUde4dfp48Vz48mE9M4nfOQcsBLcUr1wCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

After that step, we need to finalize things. In the last step, we need to select a few details regarding our image. These are some additional features that we want to include in our process or not. These features include if we want to mount our image as a removable media or not, the Drive type, the Drive letter, Drive emulations, etc.

After filling all details and completing all steps click on the mount button to start mounting the image file.

![](https://i2.wp.com/1.bp.blogspot.com/-ypNZPetCtxA/Xihqcj5sVTI/AAAAAAAAiSM/2x94yuECVJ0kaxf6BvP1ide9ugO8RVHLACLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

Now as shown in the image given below we have the image successfully mounted and ready for the analysis.

![](https://i1.wp.com/1.bp.blogspot.com/-lNpvQZ1VrMw/XihqcVpGM8I/AAAAAAAAiSE/doAiXj8rJAITbskafeqSjL0FMFnuEvl4QCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

We can also check the working of the mounted image file by opening the mounted image in the File Explorer as shown in the image given below:

![](https://i1.wp.com/1.bp.blogspot.com/-zou3CB5eFWo/Xihqdb9Ov0I/AAAAAAAAiSQ/hnHz5N1g5F8HEta0QqLnI_NlR1GfCUDQgCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

### **Tool #3:** **Arsenal Image Mounter**

Arsenal image mounter handles the disk images as a whole drive. As far as Windows system is concerned, the contents of disk images mounted by AIM are real SCSI disk, which allows its users to take advantage from some disk specific features like Integration with Disk Manager and Access to volume shadow copies and much more.

Many of the image mounting solutions in the market contents of disk images as share and partition rather than complete disk. Which some times limits their usefulness to digital forensics practitioners or investigators. If AIM is running without a license, it will run in free mode and provide core functionalities. If it is licensed, it will run in professional mode with full functionalities enabled.

We can download our Arsenal Image Mounter from [here](https://arsenalrecon.com/products/).

After downloading and completing its installation process, We can open this software and start mounting an image file. After opening that software click on the **“Mount disk image”** button.

![](https://i1.wp.com/1.bp.blogspot.com/-fU4cZ46noUg/XihqdbL1xcI/AAAAAAAAiSU/w7qNW1RQSvA-p2eil3DeqlQAsHmWPtBSQCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

Now we have some details to fill in. We are asked about the mode in which we want to see our mounted image or what type of device it has to be. We can choose Read Only or Writable among other options. We are also required to fill in the Sector Size and Click on the Create “removable” disk device for a better mounting process. After filling up all the details click on the **OK** button to move further.

![](https://i0.wp.com/1.bp.blogspot.com/-fthZ_J6mJJ4/Xihqd_qWtaI/AAAAAAAAiSY/ud4USOPJJa4DHUmGojR1oZh98wNIrHAhACLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

After this our disk is mounted successfully, we will get all the details regarding that with that mounted message.

![](https://i1.wp.com/1.bp.blogspot.com/-febtzHng0KE/XihqeJ6GjHI/AAAAAAAAiSc/xFRhOlc-2Cob1ckvjuM0RbXyklI7Oqp9QCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

Now we check if our image is successfully mounted as a removable device in our system. After checking that, now we can finally start our investigation process.

![](https://i0.wp.com/1.bp.blogspot.com/-Cu-uo0slb6Y/XihqeVRCbbI/AAAAAAAAiSg/ZHWrUv2Sf4k0JISxUu1RU0w1D1gGK9K2gCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

### **Tool #4:** **Access Data FTK Imager**

Access Data believes that zero is on the relevant evidence quickly, conduct faster searches and dramatically increase analysis speed with FTK. FTK uses distributed processing and it is a solution to fully leverage multi-core and multi-thread computers. While other tools waste the usage of modern hardware solutions. Where FTK try to use 100 per cent of its hardware resources for trying to help in the investigation process.

FTK provides faster searching in comparison to other solutions. FTK is truly database-driven, all data is stored securely and centrally, which allows our teams to use the same database that reduces cost creating multiple data sets.

We can download our access data FTK Imager from [here](https://accessdata.com/product-download/ftk-imager-version-4-2-1).

After finishing up the installation process, Open the software to move further ahead.

![](https://i0.wp.com/1.bp.blogspot.com/-MpmZwDwFZdU/XihqeibtE3I/AAAAAAAAiSk/O9ds1R0eU9c4fIMuqmFOznls6HIz0sitwCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

Now, click on the File option from Menu and Select the “**Image Mounting**” option to start the image mounting process.

![](https://i0.wp.com/1.bp.blogspot.com/-1ypcV2d8k0g/XihqfMrRSMI/AAAAAAAAiSo/lCd_81_vt7IAe3pwPMx-9InxHwjtA07ogCLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

Now we explore the Add Image file option. We browse the image file in the system, then fill up the details like image file mount type, its drive letter, and its mount method.

After filling up all mandatory details regarding the process, click on the **Mount** button to start the mounting process.  

![](https://i0.wp.com/1.bp.blogspot.com/-MKiUHIiWQkA/Xihqfev0itI/AAAAAAAAiSs/b3OZEDvAkHIkd-IU4Fif1CLanU6ob7_bQCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

It takes some time to mount an image, but after finishing up the process we will get the details of our mounted image which comes in the mapped images section. It provides us with some basic information regarding Drive, Method, Partition, Image locations, etc.

![](https://i2.wp.com/1.bp.blogspot.com/-MavVloQaK30/XihqgUGd3EI/AAAAAAAAiS0/4kzQz6jQuPc_1bAqRdH27HkkmyLoUsroQCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

If we want we check the integrity information we can do so by checking or monitoring this drive physically by reaching this drive location to validate that data information and start our investigation.

![](https://i1.wp.com/1.bp.blogspot.com/-4tU9aEXMcQ4/Xihqg9zO9pI/AAAAAAAAiS4/_7cbuNtMO7ADSLmp5y16JxQDmoTt-B47wCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

These are different ways in which we can mount a forensic image window to help investigators. For a better analysis of the evidence, it will help them in their investigation process.

**Author:** Shubham Sharma is a Pentester, Cybersecurity Researcher and Enthusiast, contact **[here](https://www.linkedin.com/in/shubham-sharma-626964153/)**.

The post [Multiple Ways to Mount Raw Images (Windows)](https://www.hackingarticles.in/multiple-ways-to-mount-raw-images-windows/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/38z53iL