---
title: 'Turn Your Raspberry Pi Into a Media Server With Emby'
date: 2019-09-27T12:55:00+01:00
draft: false
---

![raspi-media-server](https://static.makeuseof.com/wp-content/uploads/2019/09/raspi-media-server.jpg)

Looking for a smart, easy-to-use Raspberry Pi media server solution with a good choice of client apps? Perhaps you looked at Plex or Kodi but found they didn’t seem right. If so, it’s worth giving Emby a go.

Easy to install and set up, Emby is a smart media server alternative. Here’s how to install Emby Server and Emby Theater on the Raspberry Pi.

What Is Emby?
-------------

Emby is a media server. While it isn’t as well-known as other solutions (e.g. Plex, or Kodi), open source Emby has client and server software. This means that you can install the server module on the computer with your media on it, then share to other devices using client apps.

Various plugins can extend the features of Emby. You’ll find IPTV plugins for internet TV, for example. Emby also offers built-in parental controls, to help protect your family from sensitive content. While Emby is less well-known than its competitors, the userbase is growing.

For more information, here’s why you should [forget Plex and Kodi, and try Emby](//www.makeuseof.com/tag/forget-plex-kodi-try-emby/) instead.

What You Need for a Raspberry Pi Emby Media Center
--------------------------------------------------

To build an Emby media server, you will need:

*   Raspberry Pi 2 or later (we used the [Raspberry Pi 4](//www.makeuseof.com/tag/raspberry-pi-4-overview/))
*   microSD card (16GB or more for the best results)
*   PC with a card reader
*   Keyboard and mouse
*   HDMI cable and suitable display

Make sure you have a suitable power connector for your Raspberry Pi.

The process is straightforward: install Emby, connect it to your network, then use it as a media server. Media stored on a USB hard disk drive can be added to Emby, then served to devices on your network.

For example, the Raspberry Pi Emby box could serve your favorite home movies and photos to your TV or mobile.

Install the Emby Media Server on Raspberry Pi
---------------------------------------------

Installing the Emby Server on Raspberry Pi’s default Raspbian Buster is straightforward. Open a terminal and update and upgrade to begin:

```
sudo rpi-update  
  
sudo apt dist-upgrade
```

Next, use wget to download the ARMHF version from the [Linux downloads page;](https://emby.media/linux-server.html) this version is compatible with the Raspberry Pi.

```
wget https://github.com/MediaBrowser/Emby.Releases/releases/download/4.2.1.0/emby-server-deb_4.2.1.0_armhf.deb
```

Install this with

```
dpkg -i emby-server-deb_4.2.1.0_armhf.deb
```

Wait while this completes. Your Raspberry Pi-powered Emby server is installed. All you need to do now is configure it.

Configure Your Emby Media Server
--------------------------------

Access the Emby Server via your browser. It’s easiest using the Raspberry Pi itself—use the address **http://localhost:8096**.

This brings you to the server set up. You’ll need to set the preferred language, username, password, and other options. Setup also gives you the option to link your Emby Connect account. This is a great way to connect to your server from any Emby account, without needing the IP address. However, it’s not necessary.

Following this, you’ll see the Setup your media libraries screen. Here, click **Add Media Library**.

Simply browse for the location, then set the meta information according to the menus.

This is mostly language-based and shouldn’t take long.

When you’re done adding media locations, click **Save**. It’s time to start viewing content on your Emby media server!

Connect Any Device to Your Emby Server
--------------------------------------

An impressive collection of apps is available for Emby. Want to watch on a smart TV? You can! You’ll also find apps for Android TV and Amazon Fire TV, along with Xbox One and PS4. Using Kodi? There’s an Emby add-on available.

Additionally, Emby produce mobile apps for Android and iOS mobile devices. There is even a version for Windows 10 and Windows 10 Mobile, as well as a HTML5 web client.

In short, all devices are covered.

To enjoy content on your Emby server, simply install the app and proceed through the setup. You’ll be asked for the server or device name, and if you set it up, the Emby account credentials.

Once this is all configured, you’ll be ready to enjoy streamed media from your Raspberry Pi Emby server.

Set Up Raspberry Pi as an Emby Client
-------------------------------------

Thanks to the Emby Theater tool for Linux, you can view the media files on your Raspberry Pi Emby server on another Pi.

You have two choices to install the Emby Theater client app on a Raspberry Pi.

1.  Download the DEB file to your Raspberry Pi and install it on Raspbian Buster (or any Debian-based operating system).
2.  Alternatively, download a full disk image, write it to a spare SD card, and boot this.

Use the appropriate download link based on how you plan to install Emby on your Pi.

**Download**: [Emby Theater DEB File for Raspbian Buster](https://github.com/MediaBrowser/emby-theater-electron/releases/download/3.0.9/emby-theater_3.0.9_armhf.deb)

**Download**: [Emby Theater Disk Image](https://github.com/MediaBrowser/emby-theater-electron/releases/download/3.0.9/emby-theater-rpi_3.0.9.zip)

With your chosen download complete, it’s time to install Emby.

### How to Install Emby Theater on Raspbian Buster

Get started with Emby Theater by downloading the DEB file from GitHub. This should be downloaded direct to your Raspberry Pi, or to a location from it can be [copied to the Pi](//www.makeuseof.com/tag/copy-data-raspberry-pi-pc/).

Next, open the terminal and update and upgrade:

```
sudo rpi-update  
  
sudo apt dist-upgrade
```

Next, run the installation command:

```
sudo apt install -f ./emby-theater_3.0.9_armhf.deb
```

Then reboot:

```
reboot
```

Finally, run Emby with

```
emby-theater
```

Want Emby Theater to autostart when you boot your Pi? That’s not a problem. In the terminal, edit the autostart file:

```
sudo nano ~/.config/lxsession/LXDE-pi/autostart
```

Scroll to the end and add:

```
@emby-theater
```

Save and exit (**Ctrl + X**, then **Y**) and restart your Raspberry Pi. Emby should automatically start. Of course, if you want this functionality then it’s smarter to just install the disk image.

### Install Emby Theater From a Disk Image

To turn your Raspberry Pi into a dedicated Emby client, download the zipped disk image to your main PC.

Next, unzip the file. By now you should have your Raspberry Pi’s SD card inserted in your PC’s card reader.

Launch Etcher, then click **Select image** to browse for the IMG file. Ensure that the correct drive is selected (Etcher is good at autodetecting flash media but check regardless) then **Flash**. Etcher will format the media and write the Emby disk image.

A notification will appear when done. Close the software, safely eject the SD card, then replace it in your Raspberry Pi. The computer should boot straight into Emby Theater.

Stream Content on Raspberry Pi With Emby
----------------------------------------

Emby brings a whole new dimension to serving media on a Raspberry Pi. To start off, it’s compatible with the Raspberry Pi 4, and the hardware boost this delivers over its predecessors.

But there’s more to Emby. Don’t want the bells and whistles of a Raspberry Pi Plex server? Find that streaming content on Kodi isn’t as smooth as you would like? Don’t worry. Emby has a clearer focus to sharing media on your network. Sure, you can upgrade to the Emby subscription program for additional features, but you probably won’t need these.

With apps for virtually any device, you’ll find Emby is perfectly suited to the Raspberry Pi and your media files.

Considering alternatives? Here are more ways you can [set up your Raspberry Pi as a media server](//www.makeuseof.com/tag/4-ways-set-up-raspberry-pi-media-server/).

Read the full article: [Turn Your Raspberry Pi Into a Media Server With Emby](https://www.makeuseof.com/tag/raspberry-pi-media-server-emby/)

  
  
from MakeUseOf https://ift.tt/2naVu75  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)