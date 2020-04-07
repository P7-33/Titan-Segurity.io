---
title: 'How to Install Flatpak and Snap Store in Linux on Chromebook'
date: 2020-01-07T08:17:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

While [Linux support](https://beebom.com/how-use-linux-chromebook/) on Chromebook is a welcome development, it hardly means anything for general consumers. One of the reasons is no graphical user interface (GUI) for Linux App Store which prevents people from discovering and using [Linux apps on Chromebook](https://beebom.com/best-linux-apps-chromebook/). However, there is a way to install a GUI App Store on Linux and here I am going to show you how to get it. In this article, we bring you an in-depth guide on how to install Flatpak and Snap App Store in Linux on [Chromebook](https://beebom.com/what-is-a-chromebook/). Both these app stores are quite popular in the Linux ecosystem so you will be able to access a legion of popular Linux apps on Chrome OS. With all that said, let’s go ahead and learn how to install a GUI app store in Linux on Chromebook.  

*     
    
    Install Flatpak in Linux on Chromebook
    --------------------------------------
    
      
    
  

While Flatpak has a significantly small repository of apps, it’s **supported officially on Chromebooks and the apps run quite well**. And that’s why we have mentioned Flatpak at the beginning of this article. Apart from that, Flatpak comes with its own library of essential packages and sandboxing tools so that is great. Now, let’s go ahead and install Flatpak in Linux on Chromebook.  

1\. Open the Terminal and **run the below commands one by one**. Flatpak will be installed within a few minutes.  

```
sudo apt install flatpak  
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```  

![Install Flatpak in Linux on Chromebook](https://beebom.com/wp-content/uploads/2020/01/How-to-Install-Flatpak-and-Snap-App-Store-in-Linux-on-Chromebook-GUI-3.jpg)

2. In case, **your Chromebook shows some errors or displays “Permission Denied”** then run `sudo su` first to get root access. It’s equivalent to gaining Administrator Privilege on [Windows PCs](https://beebom.com/beginner-tips-for-windows-10/). Following that, execute other commands one by one. Finally, Flatpak will be installed on your Chromebook.  

```
sudo su  
sudo apt install flatpak  
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```  

3\. Now that you have installed Flatpak successfully, **let’s install a GUI application** so you can easily discover, install and manage Linux apps on Chrome OS. Run the below commands and it will install the GUI app store.  

```
sudo su  
sudo apt install gnome-software-plugin-flatpak
```  

4\. After the installation, you will find a “Software” named app inside the Linux folder in the App Drawer. Open it and voila, there you have it. A [GUI store for Linux apps](https://beebom.com/best-linux-apps/) on Chromebook. That’s amazing, right? Here, you can **discover and search for a range of Linux apps and install them in just a click**. All the apps will be installed from the Flatpak repository.  

![How to Install Flatpak and Snap App Store in Linux on Chromebook [GUI] 2](https://beebom.com/wp-content/uploads/2020/01/How-to-Install-Flatpak-and-Snap-App-Store-in-Linux-on-Chromebook-GUI-2.jpg)

5\. While the GUI app store is great, **sometimes it does not work properly**. So here are the command line instructions to help you install Linux apps on your Chromebook through the Terminal. To find apps that you want to install, open [Flathub](https://flathub.org/home) on your browser and discover the Linux apps.

  
  

  

![flathub](https://beebom.com/wp-content/uploads/2020/01/How-to-Install-Flatpak-and-Snap-App-Store-in-Linux-on-Chromebook-GUI-4.jpg)

6\. Now, **open the app that you want to install and scroll down to the bottom.** Here, you will find the command to install the app through the Terminal. Copy it and run the command on the Terminal to install the app. For example, here is how you can install [Spotify](https://beebom.com/spotify-tips-tricks/) through Flatpak.  

_**Note:** Repeating again, run `sudo su` first to gain root access. Following that, execute the flatpak commands._  

```
sudo flatpak install flathub com.spotify.Client
```  

![GUI Linux app store](https://beebom.com/wp-content/uploads/2020/01/How-to-Install-Flatpak-and-Snap-App-Store-in-Linux-on-Chromebook-GUI-5.jpg)

7\. Once installed, **you will find the program in your app drawer** under the Linux folder. Alternatively, you can run it through the Terminal as well using the below command.  

```
sudo flatpak run com.spotify.Client
```  

8\. Here are **some crucial Flatpak commands** that can help you while dealing with Linux apps on Chrome OS.  

*   Search for apps inside the Terminal:
  

```
sudo flatpak search 
```  

*   List all Flatpak Installed Apps:
  

```
sudo flatpak list
```  

*   Uninstall an app installed through Flatpak:
  

```
sudo flatpak uninstall 
```  
```
sudo flatpak update
```  

*     
    
    Install Snap Store in Linux on Chromebook
    -----------------------------------------
    
      
    
  

Snap Store is quite popular in the Linux community and many people choose it over other app packaging platforms because of its massive app repository. So here, I am going to show you how to install Snap Store in Linux on Chromebook. Having said that, **during my testing, I was able to install the majority of apps but they didn’t run quite well.** Nevertheless, you can go ahead and try Snap Store on your Chromebook and see if it works for you.  

1\. Open the [Linux Terminal](https://beebom.com/essential-linux-commands/) and **execute the below commands one by one**. It will install the Snap Store on your Chromebook.  

```
sudo apt update  
sudo apt install snapd
```  

![How to Install Flatpak and Snap App Store in Linux on Chromebook [GUI] 6](https://beebom.com/wp-content/uploads/2020/01/How-to-Install-Flatpak-and-Snap-App-Store-in-Linux-on-Chromebook-GUI-6.jpg)

  
  

  

2\. **If at any stage, you get any error**, run `sudo su` first and then proceed with other commands.  

```
sudo su  
sudo apt update  
sudo apt install snapd
```  

3\. Now, to install any application, **go to [Snap Store](https://snapcraft.io/store) on the web and find your choice of application**. Further, click on the install button at the top-right corner and you will get the command to install the app. Copy it and run the command in the Terminal. Within a few minutes, the application will be installed. For example, here is the command to install VLC.  

```
sudo snap install vlc
```  

![Install Snap Store in Linux on Chromebook](https://beebom.com/wp-content/uploads/2020/01/How-to-Install-Flatpak-and-Snap-App-Store-in-Linux-on-Chromebook-GUI-7.jpg)

4\. After the installation, use the below command to **run the application**.  

```
sudo snap run vlc
```  

5\. If you want to **search for Linux apps right in the Terminal** then you can do so by the below command. After that, you can install the app by its normal name or package name through step #3.  

```
sudo snap find 
```  

![chromebook](https://beebom.com/wp-content/uploads/2020/01/How-to-Install-Flatpak-and-Snap-App-Store-in-Linux-on-Chromebook-GUI-8.jpg)

6\. Also, here are **a few important Snap commands** you will need while dealing with the Terminal.  

*   List all Snap Installed Apps:
  

```
sudo snap list
```  

*   Uninstall an app installed through Snap:
  

```
sudo snap remove 
```  
```
sudo snap refresh
```  

7\. You can also **install the GUI version of the Snap Store** by the below command. It will be much easier for you to discover and install Linux apps on Chromebook. However, in my testing, I was unable to install apps because of a sign-in error. Nevertheless, you can give it a try and see if it works on your Chromebook. After the installation, you will find Snap Store in the App Drawer under the Linux folder.  

```
sudo apt-get install gnome-software-plugin-snap
```  

![How to Install Flatpak and Snap App Store in Linux on Chromebook [GUI] 1](https://beebom.com/wp-content/uploads/2020/01/How-to-Install-Flatpak-and-Snap-App-Store-in-Linux-on-Chromebook-GUI-1.jpg)

Enjoy the GUI App Store in Linux on Chromebook
----------------------------------------------

  

So that was our look into the two most popular app stores and how to install Flatpak and Snap App Store in Linux on Chromebook. While both the app stores are great and reliable, I think Flatpak works better on Chromebook. It installed the apps without any error and we were able to run them right from the App Drawer. So go ahead and install whichever app store you find interesting and reliable. Anyway, that is all from us. If you liked the article, do comment down below and let us know. Also, you can now [enable GPU acceleration](https://beebom.com/enable-microphone-gpu-acceleration-linux-chromebook/) which will make Linux apps much smoother and faster to use on a Chromebook.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-install-flatpak-snap-app-store-linux-chromebook/)  
\[the\_ad id='1307'\]