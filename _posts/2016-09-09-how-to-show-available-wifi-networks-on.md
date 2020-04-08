---
title: 'How to Show Available WiFi Networks on Linux from the Command Line'
date: 2019-12-08T07:10:00+01:00
draft: false
---

![](https://1.bp.blogspot.com/-NabJ6y3PntM/Xc6oVn1thCI/AAAAAAAADkk/fffdog6GYdgZTiTllQ5mPRZnRdLvKSsjwCLcBGAsYHQ/w1200-h630-p-k-no-nu/nmcli-wifi-scan.png " How To Show Available WiFi Networks, Their Channels, Signal Strength And More From The Command Line - Linux Uprising Blog ")  

**This article explains how to view available WiFi networks, list their channels, link quality, security, signal strength, and more on Linux using the command line.**

This can be useful to scan available WiFi networks to quickly see their signal strength, see their channels to know which WiFi channel to use for less interference, and so on.

There are multiple ways / tools to scan for available WiFi networks and list their details, but in this article I'll only list 2 which are easy to use and provide enough information for this task.

Option #1: Scan and list available WiFi networks using nmcli
------------------------------------------------------------

[nmcli](https://developer.gnome.org/NetworkManager/stable/nmcli.html)

, a command line tool for controlling and reporting the network status, can scan and list available WiFi networks regardless of the WiFi being connected to a network or not. This should already be installed on your Linux distribution, it doesn't require specifying the interface name, and can work without super user (sudo) privileges by default or at least that's the case in my test on both Fedora and Ubuntu.

**Use nmcli to show the available wireless networks SSID, mode, channel, transfer rate, signal strength, bars and security used using:**```
nmcli dev wifi
```

This is how the command output looks:

I've seen some users saying that they had to run nmcli with sudo to get it to show available wireless networks, but that wasn't the case when trying this on Fedora 31 and 30, or on Ubuntu 19.10 or 18.04. Still, in case nmcli doesn't show anything, try running it with sudo:

```
sudo nmcli dev wifi
```**To get nmcli to show some extra information about the scanned WiFi networks, including the SSID-HEX, BSSID, frequency, and more, run it like this:**```
nmcli -f ALL dev wifi
```

Screenshot:

This shows the scanned WiFi details in a tabular view. In case you want to switch to multiline view, so you don't have to expand the terminal window width to see all the details, use

`-m multiline`

, like this:

```
nmcli -m multiline -f ALL dev wifi
```**For usage in scripts**

, use the terse (

`-t`

) output mode:

```
nmcli -t -f ALL dev wifi
```**In case you want to force nmcli to rescan the available WiFi networks**

, use the

`rescan`

option:

```
nmcli dev wifi rescan
```

Option #2: Get a list of available WiFi networks using wavemon
--------------------------------------------------------------

[wavemon](https://github.com/uoaerg/wavemon)

is terminal user interface (TUI) that uses ncurses, which monitors wireless signal and noise levels, packet statistics, device configuration and network parameters. Use this instead of nmcli, if you're not using NetworkManager, or if you simply prefer this over nmcli.

Using it you can get a list of available Wifi access points, regardless if you're connected to a WiFi network or not. The tool requires super user permissions (e.g. run it with sudo) to scan for available Wifi networks by default.

wavemon can show the following information for available (scanned) WiFi networks: SSID, BSSID (access point mac address), signal quality, signal strength, WiFi channel, and frequency.

**wavemon is not installed by default, but it's available in the repositories for many Linux distributions. Install it as follows:**```
sudo dnf install wavemon
```

*   Debian, Ubuntu, Linux Mint, Pop!\_OS, Elementary OS and other Debian or Ubuntu based Linux distributions:

```
sudo apt install wavemon
``````
sudo zypper install wavemon
``````
sudo pacman -S wavemon
```

Now

**launch wavemon:**```
sudo wavemon
```

To scan for available WiFi networks press

`F3`

to switch to the scan tab.

**Looking for a more advanced WiFi scanner with extra features? Check out [Kismet, a command line tool that got a web UI](https://www.linuxuprising.com/2019/04/wireless-sniffer-kismet-2019-04-r1-adds.html)**

back in April, 2019.

  
  
from Hacker News https://ift.tt/2Qjqb6F