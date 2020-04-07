---
title: 'How to Install iTunes on Chromebook in 2020'
date: 2020-01-15T09:30:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

While the majority of [American classrooms](https://www.nytimes.com/2017/05/13/technology/google-education-chromebooks-schools.html) are filled with Chromebooks, it’s equally true that many users prefer iPhones as their primary device. And eventually, that leads to incompatibility between two distinct ecosystems created by Google and Apple. Yes, I am talking about running iTunes on [Chromebook](https://beebom.com/what-is-a-chromebook/) and how you can get it working. Well, in this article, I bring you a detailed guide on how to install iTunes on Chromebook. We will also discuss the performance of iTunes on Chromebooks so you know what to expect from the app.  

Install iTunes on Chromebook in 2020
------------------------------------

  

Here, we have explained how to get iTunes working on your Chromebook thoroughly. To give you an overview, we are using Wine app which is popular for running [Windows apps](https://beebom.com/best-windows-10-apps/) on Linux systems. In tandem, we will install the Windows version of iTunes on our Chromebook through the Linux container. Now having said all of that, let’s go through the steps without further delay.  

1\. First and foremost, you need to [enable Linux](https://beebom.com/how-use-linux-chromebook/) and then [set up Wine on your Chromebook](https://beebom.com/how-use-windows-10-apps-chromebook-using-wine/). We have written detailed guides separately so **follow the above-linked articles** and you will be all set for the next step.  

![Install iTunes on Chromebook 1](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-1.jpg)

2\. Now, let’s go ahead and download iTunes for Chromebook. Keep in mind, **the 64-bit version does not work properly** on Chromebook and displays a black window. So, download this specific [32-bit version of iTunes](https://drive.google.com/file/d/1XoaZtFL49Q39EDGXyOFCS3oUgiQL5_o4/view) from here. The build is 12.9.3 from August, last year.  

3\. Next, **rename the file to something easier** like “itunes.exe” and move it to the Linux section.  

![itunes](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-2.jpg)

4\. Having done that, open the Terminal and execute the below command to change the Wine architecture to 32-bit. **Make sure to change `yourusername` to the actual username** assigned to your Chromebook. For example, if your email ID is [\[email protected\]](http://beebom.com/cdn-cgi/l/email-protection) then your username will be abc123. If a Wine window opens up, so click on the “Ok” button.  

```
WINEARCH=win32 WINEPREFIX=/home/yourusername/.wine32 winecfg
```  

![Install iTunes on Chromebook 4](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-4.jpg)

  
  

  

5\. Next, run the below command to **install the 32-bit version of iTunes** on Chromebook. Again, make sure to change your username. Instantly, an installation window will open up. Click on “Next” and proceed with the setup.  

```
WINEARCH=win32 WINEPREFIX=/home/yourusername/.wine32/ wine itunes.exe
```  

![chrome os ](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-10.jpg)

6\. After the installation, click on “Finish” and voila, there you have it. iTunes successfully running on Chromebook.  

![Install iTunes on Chromebook 3](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-3.jpg)

Create Shortcut for iTunes on Chromebook
----------------------------------------

  

You have successfully installed iTunes on Chromebook and a shortcut has also been created in the App Drawer inside Linux folder. However, when you click on it, **the shortcut does not open iTunes due to an incorrect file path**. So, to fix this issue, follow these steps.  

1\. Open the native File Explorer and move to the Linux section. Here, click on the 3-dot menu and **enable “Show Hidden Files”**.  

![Create Shortcut for iTunes on Chromebook](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-5.jpg)

2\. Now, navigate to the following path: **.local -> share -> applications -> wine -> Program Files -> iTunes**. Here, you will find iTunes.desktop file which is the shortcut that we need to edit. So, right-click on it and select “Open With”. Here, choose the Text app to open the file. In case, you don’t have the Text app, install it from [here](https://chrome.google.com/webstore/detail/text/mmfbcljfglbokpmkimbfghdkjmjhdgbg?hl=en).  

![chromebook](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-6.jpg)

  
  

  

3\. Having done that, copy the below path and **paste it just after `Exec=`** . Keep in mind, do change `yourusername` to the actual one.  

```
env WINEPREFIX="/home/yourusername/.wine32" wine "/home/yourusername/.wine32/drive_c/Program Files/iTunes/iTunes.exe"
```  

![Create Shortcut for iTunes on Chromebook](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-7.jpg)

4\. Now, save the file and close the Text app. Finally, open iTunes from the App Drawer and this time, it should launch perfectly fine. **You can further pin iTunes to Chrome Shelf as well**.  

![itunes](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-8.jpg)

Our Experience with iTunes on a Chromebook
------------------------------------------

  

While we have managed to install and run iTunes on a Chromebook, the question remains, does it work well? In our testing, iTunes did not perform well despite running on a [powerful (i5, 8th-Gen) Chromebook](https://beebom.com/best-chromebooks-you-can-buy/). It’s quite expected as you are running iTunes inside a Windows container which in turn, is running inside a Linux container. So, **the performance takes a hit significantly**. Further, despite Linux gaining USB support on Chrome OS, [iTunes was unable to detect iPhone](https://beebom.com/how-use-iphone-with-linux/) and could not sync the library. Partly, it’s because Apple does not officially support Linux connectivity for iDevices.  

![Our Experience with iTunes on a Chromebook](https://beebom.com/wp-content/uploads/2020/01/Install-iTunes-on-Chromebook-9.jpg)

Having said all of that, the most disappointing part is that **iTunes crashes every time you try to sign in to your account**. So, neither you can access your media library locally nor through the cloud. All in all, iTunes on Chromebook is not a good experience and you should look for [other options](https://beebom.com/best-itunes-alternatives/).  

Take a Look at iTunes for Chromebook
------------------------------------

  

So that is how you can get iTunes on your Chromebook. While the installation process is not that simple, you can definitely try it on your device. Once you have set up Wine, the process becomes a breeze. Apart from that, on the performance front, iTunes didn’t work well but do give it a shot and see how well it fares on your Chromebook. Anyway, that is all from us. If you are facing some trouble while making it work, do comment down and let us know the issue. We will definitely take a look. And whenever we find a proper build of iTunes working successfully on Chromebooks, we will definitely let you know.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-install-itunes-on-chromebook/)  
\[the\_ad id='1307'\]