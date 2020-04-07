---
title: 'How to Use Windows 10 Apps on Chromebook Using Wine'
date: 2020-01-06T07:05:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Many argue that [Chromebook](https://beebom.com/what-is-a-chromebook/) is not a complete machine and it panders to people who have limited use-case. Frankly, that is true to some extent. However, with the support of [Android and Linux apps](https://beebom.com/best-chrome-os-apps-install-chromebook/), the gap has closed significantly. Having said that, lack of Windows app support is still the bottleneck for many users who want to move from a Windows PC to Chromebook. But that is also changing. Now, you can use Windows 10 apps on Chromebook thanks to the Linux support. In this article, I am going to show you how to install a majority of Windows apps on [Chrome OS](https://beebom.com/best-chrome-os-tips-tricks/) without a hitch. So, let’s get started.  

Install Windows 10 Apps on Chromebook Using Wine
------------------------------------------------

  

Before we begin, make sure you have [set up Linux](https://beebom.com/how-use-linux-chromebook/) on your Chromebook properly. Having done that, here we will begin by installing Wine on our Chromebook. In case, you are wondering what is Wine, well, **it’s a compatibility layer that allows you to use Windows apps in a Linux environment.** To cut things short, you will be using Windows applications through a compatibility layer called [Wine](https://en.wikipedia.org/wiki/Wine_(software)) which will run inside the Linux container. That seems a mouthful, but don’t worry the performance remains quite good and more than usable for light applications. Now having said all of that, let’s begin and learn how to use Windows 10 apps on Chromebook.  

1\. First of all, **open the Linux Terminal** and run the below command to install Wine.  

```
sudo apt-get install wine
```  

![How to Use Windows 10 Apps on Chromebook Using Wine 1](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-1.jpg)

2\. Next, **execute the below commands one by one**. It will finally install the necessary libraries which will allow you to use both legacy and modern [Windows apps](https://beebom.com/best-windows-10-apps/) on Chromebook.  

```
sudo su  
  
sudo dpkg --add-architecture i386  
  
sudo apt update && apt install wine32
```  

![How to Use Windows 10 Apps on Chromebook Using Wine 2](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-2.jpg)

3\. Now that you have set up Wine successfully, it’s time to download a Windows application. Here, as an example, I am going to show you how to install IrfanView– a popular image viewer– on Chrome OS. All you have to do is **[download the 64-bit EXE](https://www.fosshub.com/IrfanView.html) file of any Windows program and move it to the Linux files section**. Make sure to rename the file to something easier to type.  

_**Note:** As a thumb rule on Linux, rename files and folders to one word which can be easily typed on Terminal. It will immensely help you while dealing with files on the Linux Terminal._  

![f](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-3.jpg)

  
  

  

4\. Now, open Terminal again and type the below command. **Make sure to replace _irfanview.exe_** with the filename of your chosen application, in case you are installing a different application. Instantly, a setup wizard will open up and you will be able to install the application just like Windows programs.  

```
wine irfanview.exe
```  

![a](https://beebom.com/wp-content/uploads/2020/01/a-1.jpg)

*     
    
    ### Create Shortcut for Windows Programs on Chrome OS
    
      
    
  

5\. After you have installed the program, the next part is to run it. While Wine creates a shortcut in the App Drawer, the shortcuts don’t work because of the incorrect file path. So to fix it, you will have to find the correct path and modify the shortcut appropriately. Here is how you can do it. Open the native File Manager and move to the Linux Files section. Here, **click on the 3-dot menu and enable “Show Hidden Files”.**  

![How to Use Windows 10 Apps on Chromebook Using Wine 4](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-4.jpg)

6\. After that, open the `.wine` folder and navigate to `drive_c`. Here, you will get a file-directory system similar to Windows 10. Now, check where the program has been installed, either in `Program Files` or `Program Files (x86)` folder. Once, you have located the correct folder, open it and **find the final .EXE file**. That’s the program you will have to run through the Terminal.  

![How to Use Windows 10 Apps on Chromebook Using Wine 5](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-5.jpg)

7\. Now, this is how your file path will look like. Here, you will have to change `yourusername` to the actual username assigned to your Chromebook. For example, if your email ID is `[[email protected]](http://beebom.com/cdn-cgi/l/email-protection)` then your username will be `abc123`. Similarly, change `Program Files/IrfanView/i_view64.exe`to the file path shown on your File Manager.  

```
/home/yourusername/.wine/drive\_c/Program Files/IrfanView/i\_view64.exe
```  

![d](https://beebom.com/wp-content/uploads/2020/01/d.jpg)

8\. Finally, this is how your complete file path will look like. Add `wine` in the beginning and thereafter space and the file path under inverted commas. **You can also run the below command in Terminal** to check if your file path is correct or not. If correct, the Windows application will open up.

  
  

  
```
wine "/home/yourusername/.wine/drive\_c/Program Files/IrfanView/i\_view64.exe"
```  

![How to Use Windows 10 Apps on Chromebook Using Wine 7](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-7-1.jpg)

9\. Now that you have finally created the file path, let’s find the shortcut. Open File Manager and move to Linux files section with Hidden Files turned on. This time, **navigate to .local folder -> share -> applications -> wine -> Programs**. Here, you will find the folder for the installed Windows application. Open it and then you will get a file with .desktop extension. Right-click on it and open it with Text ([Install](https://chrome.google.com/webstore/detail/text/mmfbcljfglbokpmkimbfghdkjmjhdgbg/related?hl=en)).  

![How to Use Windows 10 Apps on Chromebook Using Wine 1](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-1-1.jpg)

10\. On Text, **replace the file path that follows after `Exec=`**with the complete file path you have created in step #8. Repeating again, make sure to change the username and actual file path of the program that you have installed. After that, press Ctrl + S to save the changes and close Text.  

![How to Use Windows 10 Apps on Chromebook Using Wine 2](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-2-1.jpg)

11\. Now, go ahead and **open the Windows app from the App Drawer**. It will work like a charm. You can also pin Windows apps to the Chrome OS shelf without any issue.  

![How to Use Windows 10 Apps on Chromebook Using Wine 3](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-3-1.jpg)

12\. Here is another Windows application, [IDM](https://beebom.com/free-idm-alternatives/) running on Chrome OS. I have mentioned the file path below for you to take note of. **Once you learn how to create the file path**, running a Windows application becomes a breeze on Chrome OS.  

```
wine "/home/yourusername/.wine/drive\_c/Program Files (x86)/Internet Download Manager/IDMan.exe"
```  

![How to Use Windows 10 Apps on Chromebook Using Wine 4](https://beebom.com/wp-content/uploads/2020/01/How-to-Use-Windows-10-Apps-on-Chromebook-Using-Wine-4-1.jpg)

Enjoy a Legion of Windows Apps on Chromebook
--------------------------------------------

  

So that was our deep dive into how you can use Windows 10 apps on Chromebook using Wine. As it’s evident in this tutorial, Windows apps work really well through the Linux container on Chrome OS. Among other apps, we tried Skype, Notepad++ and VLC as well. I would say go ahead and try your favorite Windows apps on your Chromebook. Anyway, that is all from us. In the coming days, we will bring more in-depth guides about [gaming on Chromebook](https://beebom.com/best-chromebook-games/) using the popular Let’s Play Linux tool. So, stay tuned with us and until then, go through our list on the [best Linux apps](https://beebom.com/best-linux-apps-chromebook/) you can install on your Chromebook.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-use-windows-10-apps-chromebook-using-wine/)  
\[the\_ad id='1307'\]