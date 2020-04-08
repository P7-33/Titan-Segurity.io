---
title: 'Ubuntu Remote Desktop: Easy, Built-In, VNC Compatible'
date: 2019-10-19T04:59:00+01:00
draft: false
---

![](https://static.makeuseof.com/wp-content/uploads/2010/03/Ubuntu-Remote-Desktop-Featured.jpg)

Do you need to connect to your computer remotely? Perhaps you’re in a different room and need to grab a file from it. Rather than get up, if you’re on the same network, this should be easy, regardless of the operating system.

Using Ubuntu’s remote desktop tool gives you total control over your desktop from any other computer: Linux, macOS, or Windows. You’ll see what’s on that screen and be able to move the mouse, and even type!

The remote desktop feature supports VNC and is built into Ubuntu by default. Here’s how to use remote desktop software with Ubuntu.

Three Ways to Remote Control Ubuntu
-----------------------------------

Overall you have three options for remote controlling an Ubuntu PC:

*   SSH: Secure Shell
*   VNC: Virtual Network Computing
*   RDP: Remote Desktop Protocol

While many Linux users see [SSH as their remote connection](//www.makeuseof.com/tag/beginners-guide-setting-ssh-linux-testing-setup/) tool of choice, it lacks a graphical user interface (GUI). It’s a popular command line tool, Ubuntu’s built-in remote desktop tool, supports all three options.

Furthermore, you’re not limited to remote control from an Ubuntu or Linux computer. With sharing configured, your Ubuntu PC can be remotely accessed. Linux, Mac, and Windows PCs can use remote desktop tools to control Ubuntu. You’ll also find VNC tools for Android and iOS.

Turning Ubuntu Remote Desktop On
--------------------------------

Enabling the Ubuntu Remote Desktop could not be easier. You don’t need to install a thing: Ubuntu has built in VNC support. However, you will need to move to the Ubuntu PC to set it up the first time.

Click **Search **and enter **desktop sharing**, then click **Sharing**. You’ll be presented with a simple window of options. Along the top edge of the window, click the switch to enable the feature. Next, click the **Screen Sharing** button and again, find the switch on the window and click it to enable.

Ensure that **Allow connections to control the screen** is enabled. For security purposes, you should also set a password here.

As soon as you enable remote connection, the local name of your Ubuntu device will be displayed. This is a VNC address—keep a note of it for remote access later.

Remote Control Ubuntu With VNC
------------------------------

Controlling an Ubuntu PC over VNC is straightforward from another device. Just be sure you have a VNC client or viewer app installed. Here’s how to use VNC from another desktop computer.

### Remote Desktop Ubuntu From Another Linux Device

Ubuntu (and many other Linux distributions) comes with a preinstalled remote desktop viewer. This means that once your Ubuntu PC is configured for remote connection, you can connect to it from whatever Linux distro you’re using.

*   Click **Search** and enter **remote**.
*   Select the first result, **Remmina**.

*   Select **VNC** in the drop-down menu on the left.
*   Enter the VNC address (or IP address) you noted earlier for the Ubuntu PC.
*   Tap **Enter** to commence the connection.
*   When prompted, input the password.

As you add devices, they’ll be saved in the list so you can quickly access them in future.

Use this tool to connect to other Ubuntu desktops on your network, and you’ll be controlling that computer remotely. The tool can also be used to control any computer with a VNC client installed.

### Remotely Connect to Ubuntu From Windows

Want to control your Ubuntu computer from a Windows computer? Using the same VNC address (or your Ubuntu computer’s IP address) you can.

First, however, you’ll need a VNC client, such as VNC Viewer (from VNC Connect) installed on your Windows computer. Then you can connect to your Ubuntu machine by entering the VNC or IP address.

Check our guide about [establishing a remote desktop connection to Ubuntu from Windows](%20https:/www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/) for full details.

### Establish an Ubuntu Remote Desktop From a Mac

Mac users wanting to connect to their Ubuntu machines should use the built-in VNC Viewer tool.

Again, connecting to your Ubuntu machine is a simple matter of entering your IP address or the provided VNC address., Want for some in-depth information about using VNC on a Mac?

Check our tutorial to [easy remote desktop support on the Mac](//www.makeuseof.com/tag/macnifying-os-x-setting-up-remote-help-on-the-mac/).

What About Ubuntu’s RDP Support?
--------------------------------

It’s also possible to connect to an Ubuntu PC over RDP.

Remote Desktop Protocol is a proprietary system developed by Microsoft. It has proven so successful that RDP server and client apps are available on most software platforms.

RDP’s authentication system relies on your computer username and password and is quick and easy to set up.

### Configure Ubuntu RDP

Before connecting to Ubuntu over RDP, you’ll need to know the remote computer’s IP address. The easiest way is to open a terminal and enter

```
ifconfig
```

Be sure to note the inet addr value that corresponds with the connection type. For example, if the Ubuntu computer is on Ethernet, use this IP address.

Next, you’ll need to install xrdp. This is an RDP server for Ubuntu (and other Linux devices) and is required before remote connection.

Install with

```
sudo apt install xrdp
```

Once installed, launch the server with

```
sudo systemctl enable xrdp
```

With xrdp running, you’re ready to use RDP.

Remote Control Ubuntu With RDP
------------------------------

As noted, RDP clients are available for most platforms. For example, you can use Remmina’s RDP function if you’re using a Linux computer to remotely control Ubuntu. Similarly, RDP is built-in to Windows.

If you’re using a standard desktop, use these steps to use RDP to connect to Ubuntu.

*   **Ubuntu/Linux**: Launch **Remmina** and select **RDP** in the drop-down box. Enter the remote PC’s IP address and tap **Enter**.
*   **Windows**: Click **Start** and type **rdp**. Look for the Remote Desktop Connection app and click **Open**. Input the IP address of your Ubuntu computer and click **Connect**.

*   **Mac**: Start by installing the [Microsoft Remote Desktop 10](https://apps.apple.com/us/app/microsoft-remote-desktop-10/id1295203466?mt=12) software from the App Store. Launch the software, click **Add Desktop**, add the IP address under **PC Name**, then **Save**. Simply double-click the icon for the connection in the app window to start a remote desktop session.

Our guide to using [RDP on a Mac](//www.makeuseof.com/tag/microsoft-remote-desktop-access-windows-mac/) will help here. It’s aimed at remote controlling a Windows PC, but the setup is the same for Linux.

Note that RDP will prompt for your Ubuntu PC account credentials when the connection is first established.

Can You Remote Control Ubuntu Away From Home?
---------------------------------------------

Want to connect to your Ubuntu machine while traveling? This is a little trickier, but not totally impossible. You’re going to need a static IP, or a dynamic address from a service such as [DynDNS.](http://www.dyndns.com/)

This basically forwards a web address to a device running DynDNS on your network. Read our tutorial for [using DynDNS to connect to your computer from anywhere](//www.makeuseof.com/tag/connect-home-network-dyndns/) for details and examples.

Read the full article: [Ubuntu Remote Desktop: Easy, Built-In, VNC Compatible](https://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/)

  
  
from MakeUseOf https://ift.tt/2P3qMbV  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)