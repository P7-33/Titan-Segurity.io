---
title: 'Multiple Ways to Create Image file for Forensics Investigation'
date: 2020-01-01T06:58:00+01:00
draft: false
---

In this article, we will learn how to capture the forensic image of the victim’s hard drives and systems to get help in the investigation. There are multiple ways to do that work and these tools will help us a lot in the process of an investigation so let’s start this process.

### **Table of Content**

*   **Introduction**
*   **What is a Forensic image?**
*   **FTK Imager**
*   **Belkasoft Acquisition Tool**
*   **Encase Imager**
*   **Forensic Imager**

### **Introduction**

In today’s digital era, the indulgence of devices is increasing more and more and with-it cybercrime is also on the rise. When such a crime occurs, the hard drive becomes an important part as it is crucial evidence. Therefore, during investigation one cannot directly perform various tasks on the hard drive as it is considered tempered. Also, one can lose data by mistake while performing tasks on it. Hence, the necessity of disk image. Now that we have understood the importance and use of disk image, let us now understand that what exactly a forensic image is.

### **What is a Forensic image?**

A Forensic image is an exact copy of hard drive. This image is created using various third-party tools which can easily capture the image of a hard drive bit by bit without changing even a shred of data. Forensic software copies data by creating a bitstream which is an exact duplicate. The best thing about creating a forensic image is that it also copies the deleted data, including files that are left behind in swap and free spaces. Now that we have understood all about the forensic imaging, let us now focus on the practical side of it. We will learn and understand how to create such image by using five different tools which are:

1.  FTK Imager
2.  Belkasoft acquisition tool
3.  Encase imager
4.  Forensic imager

**FTK Imager**

FTK imager can create an image and paging file for windows; along with capturing volatile memory for analysis purpose.

We can download FTK imager from **[here](https://accessdata.com/product-download/ftk-imager-version-4-2-1)**

After installing the FTK imager we can start by creating an image and to do so, we have to go to the file button and from the drop-down menu, select the Create Disk Image option.

![](https://i0.wp.com/1.bp.blogspot.com/-vI-roBM9zNY/XgwnvCmtDuI/AAAAAAAAiEo/2h3FlUsXEZYmkAD2idyeRS1qef6nhWFnQCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

After selecting the create disk image it will ask you the evidence type whether i.e. physical drive, logical drive, etc. and once you have selected the evidence type then press the next button to move further in the process.

![](https://i1.wp.com/1.bp.blogspot.com/-uI6ZEs0cQ48/XgwnvJenyBI/AAAAAAAAiEs/n68nepooAI83HGyddHI4MOmIMxPoBu-bwCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

Now it will ask for the drive of which you want to create the image. Select that drive and click on Finish button.

![](https://i1.wp.com/1.bp.blogspot.com/-vH6Z4S7mKq4/XgwnvIlxfKI/AAAAAAAAiEw/yH_xInkzWRMpim2Zcb7xQPTolKkOJIiEwCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

Now, we need to provide the image destination i.e. where we want our image to be saved. And to give the path for the destination, click on Add button.

![](https://i2.wp.com/1.bp.blogspot.com/-aBLSdyuLw-M/XgwnwYh5yPI/AAAAAAAAiE4/NmF_9MvEW1Mj9dl291L3iiwczZpRrkOUQCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

Then select the type you want your image to be i.e. raw or E01, etc. Then click on Next button.

![](https://i2.wp.com/1.bp.blogspot.com/-aBLSdyuLw-M/XgwnwYh5yPI/AAAAAAAAiE4/NmF_9MvEW1Mj9dl291L3iiwczZpRrkOUQCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

Further it will ask you to provide details for the image such as case number, evidence number, unique description, examiner, notes about the evidence or investigation. Click on Next button after providing all the details.

![](https://i0.wp.com/1.bp.blogspot.com/-mMPcZ-ix5YI/XgwnwXnpbBI/AAAAAAAAiE8/c-UKtNVR-FQ65DAs8lfDqKs8weEX3HItgCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

After this, it will ask you for the destination folder i.e. where you want your image to be saved along with its name and fragment size. Once you fill up all the details, click on the Finish button.

![](https://i2.wp.com/1.bp.blogspot.com/-xX8X8qnCNg0/XgwnxLqCw2I/AAAAAAAAiFA/kvC3itKmvY43BYAqlukINuFtCqH7XKg9wCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

And now the process to create the image will start and it will simultaneously inform you about the elapsed time, estimated time left, image source, destination and status.

![](https://i0.wp.com/1.bp.blogspot.com/-QxHmJRso4K4/XgwnxfqvLZI/AAAAAAAAiFE/apmMPfzeOtwV6ABhtyKl-4aEtZrlbXeEACLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

After the progress bar completes and status shows Image created successfully then it means our forensic image is created successfully .

![](https://i0.wp.com/1.bp.blogspot.com/-fTDkIY6UsY4/XgwnxnSNkOI/AAAAAAAAiFI/MORiP8FJwlMZQnyHSHYe_DWZLppgWpLdwCLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

And so, after the creation of the image you can go to the destination folder and verify the image as shown in the picture below :

![](https://i0.wp.com/1.bp.blogspot.com/-La2-CeyR3nE/XgwnyIQPDBI/AAAAAAAAiFM/2mzFXMIuPMU_nrsNboB5hi2tTTass5EYQCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

### **Belkasoft Acquisition**

Belkasoft Acquisitiontool formally known as BAT. This tool can create images of hard drives, Removable drives, Mobile devices, Computer RAM memory, cloud data. The acquired image can be analyzed with any third-party tool.

We can download the belkasoft Acquisitiontool from **[here](https://belkasoft.com/bat)**

Once the dialogue box opens, click on Drive option.

![](https://i0.wp.com/1.bp.blogspot.com/-v_Iju29YunQ/XgwnypiRFdI/AAAAAAAAiFQ/mIgi92w2SLwprTFN2jr6OoyzFD8dOQ_0QCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

Now, it will show you all the drives available. From these options select the one drive whose image you want to create and then click on Next button.

![](https://i1.wp.com/1.bp.blogspot.com/-I9dOkeXo2tI/XgwnyxAUdRI/AAAAAAAAiFU/ikXqRHYX54Yk08o3bZe0B0xDbk3HWhVNACLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

After selecting the drive, we need to provide the destination path along with the format of image and hash algorithm for the checksum. We can also choose whether to split image or not. And then click on the Next button.

![](https://i0.wp.com/1.bp.blogspot.com/-cfCgMP_luHA/XgwnzPVClmI/AAAAAAAAiFY/P4fP7dsknjcgONs3uLAVGoZNp8ZaEqA_wCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)

The process of creating the image will start as you can see from the picture below :

![](https://i1.wp.com/1.bp.blogspot.com/-GjUgzmhZ5Qg/Xgwnzmk6gBI/AAAAAAAAiFc/FYg1WC_DfSgw1pd0MCmWArKz7MkgleZOwCLcBGAsYHQ/s1600/23.png?w=687&ssl=1)

Once the process is complete and the image is created, click on the Exit button.

![](https://i1.wp.com/1.bp.blogspot.com/-xb571kY3zq8/Xgwnz2YVvVI/AAAAAAAAiFg/f8_noJs81rYrkJ3cdOFszkLIt6TU-A__ACLcBGAsYHQ/s1600/24.PNG?w=687&ssl=1)

To verify the image, go to the destination folder and access it as shown in the picture below :

![](https://i1.wp.com/1.bp.blogspot.com/-j3-tzAQU5XU/Xgwnz6IJKDI/AAAAAAAAiFk/kCa9OlIsaUgsfQawgeZN_IUwu9oJQfMZwCLcBGAsYHQ/s1600/25.PNG?w=687&ssl=1)

### **Encase Imager**

Another way to capture image is by using Encase tool. We can download Encase imager from **[here](https://www.guidancesoftware.com/)**. 

To start the process, firstly, we need to give all the details about the case. And then click on Finish button.

![](https://i0.wp.com/1.bp.blogspot.com/-N2T4xve_K1Q/Xgwn0alKnBI/AAAAAAAAiFo/OR4TFLFiHq4LZM4R4EU3PYr8yQhvZO85QCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

After that, we need to choose the hard drive whose image we want to create. Once you have selected the drive, click on Next button.

![](https://i1.wp.com/1.bp.blogspot.com/-FqDMaX72f-A/Xgwn04E5EeI/AAAAAAAAiFs/J6U6R8wWAtE7dwRbZQIAsD5HNvtIsJBTgCLcBGAsYHQ/s1600/27.png?w=687&ssl=1)

Now, select the specific drive whose image you want to create as shown in the picture below and click on Next button.

![](https://i0.wp.com/1.bp.blogspot.com/-kI7F06qcRus/Xgwn1Oi4AkI/AAAAAAAAiFw/W7g9XQNYzMkhT6jXf2AxS3MCyvyxKmQXQCLcBGAsYHQ/s1600/28.png?w=687&ssl=1)

Then after selecting all the things it asking us to review all the details which were given. Once review is done, click on Finish Button.

![](https://i0.wp.com/1.bp.blogspot.com/-ViXbGT_2a3w/Xgwn1YWkxzI/AAAAAAAAiF0/9kOk2yezUxUBy6hD8FxMRIuG-gqanTInQCLcBGAsYHQ/s1600/29.png?w=687&ssl=1)

After that, right-click on the chosen driven and then select the Acquire option from the drop-down menu.

![](https://i1.wp.com/1.bp.blogspot.com/-SQUpFlusqzI/Xgwn18_cJBI/AAAAAAAAiF4/5owydH4chwonNAAVyhhnf8jjMDkye9dJQCLcBGAsYHQ/s1600/30.png?w=687&ssl=1)

After this select the add to case option and then click on Next button.

![](https://i1.wp.com/1.bp.blogspot.com/-P18TwFkSG7I/Xgwn10wg-5I/AAAAAAAAiF8/8rVXUk9H804bQQC6NVj70u7J4b9O-1P9QCLcBGAsYHQ/s1600/31.png?w=687&ssl=1)

After this, give the name, number and other details for your image. Then click the finish button.

![](https://i1.wp.com/1.bp.blogspot.com/-NtqEneNMylU/Xgwn2RSb6EI/AAAAAAAAiGA/JXfB8YdYo7MGcr6vyDpd17us0GDZ8HJaQCLcBGAsYHQ/s1600/32.png?w=687&ssl=1)

After clicking on the finish button, you can observe that on the right-hand side, the lower section of the encase window will show the status of the process.

![](https://i1.wp.com/1.bp.blogspot.com/-4W33V-9vjk4/Xgwn2w6MudI/AAAAAAAAiGE/IZ6Vw8LQYksyrIV9fFEO_ZBaTarDh4ApQCLcBGAsYHQ/s1600/33.png?w=687&ssl=1)

After everything is done, it will show you all the details like status, start time, name, process id, destination path, the total time for the whole acquiring image, images hashes. And then at last, you can click on OK.

![](https://i0.wp.com/1.bp.blogspot.com/-xZkRkg7RIng/Xgwn3BpygNI/AAAAAAAAiGI/usT863VEQoIfIgx2lvX4aRiRpD7i2dlIQCLcBGAsYHQ/s1600/34.png?w=687&ssl=1)

Once the image is created, you can see that Encase uses E01 format while creating an image and further splits it into multiple parts as shown in the picture below:

![](https://i1.wp.com/1.bp.blogspot.com/-wmHRQTzBa2o/Xgwn3fmGhAI/AAAAAAAAiGM/gQ3CMeSjybkh-ZKqOuvQOs1d3IoLOBr2wCLcBGAsYHQ/s1600/35.png?w=687&ssl=1)

### **Forensics Imager**

Another way to capture an image is by using forensic imager. We can download Forensic imager from [**here**.](http://www.forensicimager.com/)

To start the process, click on Acquire button as shown in the image.

![](https://i2.wp.com/1.bp.blogspot.com/-HxUtamjFoyM/Xgwn30bJnMI/AAAAAAAAiGQ/535WhTB_f_sr6cWJbBqgAkjIg2lYk1byACLcBGAsYHQ/s1600/36.png?w=687&ssl=1)

Next, it will ask you the source to acquire image.

![](https://i0.wp.com/1.bp.blogspot.com/-5Wyt3Hgecqs/Xgwn39bGDOI/AAAAAAAAiGU/5AIYadgYG0I4kzBTxIrj5J4txBGVVM7bwCLcBGAsYHQ/s1600/37.png?w=687&ssl=1)

As you have given the source for the image, then it will ask you the destination details i.e. the path, format, checksum and other evidence related details. Once you fill all these up, click on Start button.

![](https://i0.wp.com/1.bp.blogspot.com/-txgS4QRYhEU/Xgwn4Q1AFYI/AAAAAAAAiGY/mFD-9HDfAIYn3SQMhdozer13jmlGK5zsQCLcBGAsYHQ/s1600/38.png?w=687&ssl=1)

After clicking on start, you can observe that the process has begun as shown in the picture below :

![](https://i2.wp.com/1.bp.blogspot.com/-kltRQo0YLxs/Xgwn47GuOXI/AAAAAAAAiGc/woea0MXJP8Um1lRYeOgFvdKdq2GhTfJpQCLcBGAsYHQ/s1600/39.png?w=687&ssl=1)

After completing the process, it will show you a pop-up message saying acquisition completed. It means that our forensic image is created. In order to check we need to check the destination path to verify our forensic image.

![](https://i1.wp.com/1.bp.blogspot.com/-IB3DT_GYoyU/Xgwn5JV8WsI/AAAAAAAAiGg/aB9PnqVdp3YJFdjeBUctbV6KyBFTssgqgCLcBGAsYHQ/s1600/40.png?w=687&ssl=1)

We checked at the destination our image is successfully created and ready to be analyzed as a piece of evidence for the forensic investigation.

![](https://i1.wp.com/1.bp.blogspot.com/-3r17fiqUsMA/Xgwn5ezKN8I/AAAAAAAAiGk/b9eQdurVfDI1RQdJC6Rh9aURfLycFXWmQCLcBGAsYHQ/s1600/41.png?w=687&ssl=1)

So, these were the five ways to capture a forensic image of a Hard drive. One should always the various ways to create an image as various times calls for various measures.

**Author:** Shubham Sharma is a Pentester, Cybersecurity Researcher and Enthusiast, contact [**here**](https://www.linkedin.com/in/shubham-sharma-626964153/).

The post [Multiple Ways to Create Image file for Forensics Investigation](https://www.hackingarticles.in/multiple-ways-to-create-image-file-for-forensics-investigation/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/3590Ccc