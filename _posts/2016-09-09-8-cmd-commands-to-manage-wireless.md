---
title: '8 CMD Commands to Manage Wireless Networks in Windows'
date: 2020-01-22T07:19:00+01:00
draft: false
---

![windows-cmd-wifi](https://static.makeuseof.com/wp-content/uploads/2016/12/windows-cmd-wifi.jpg)

As a Windows user, the Control Panel and the Settings app can feel quite limiting in what they can do. If you want full and absolute control over your network, meaning access to everything the operating system has to offer, then you’ll have to start using Command Prompt.

**Unlock the free "100+ Essential Windows CMD Commands" cheat sheet now!**

This will sign you up to our newsletter

Enter your Email

Unlock

[Read our privacy policy](//www.makeuseof.com/legal/)

Never used Command Prompt before? Don’t worry. Using it is as simple as typing out the commands you’ll see below.

If you’re ready to continue, here are some of the most useful networking commands to know for managing and troubleshooting your home network.

1\. PING
--------

`ping` is one of the most basic yet useful network commands to utilize in the command prompt application. It tells you whether your computer can reach some destination IP address or domain name, and if it can, how long it takes data to travel there and back again.

Sample usage and output:

The command works by sending out multiple data packets and seeing how many of them return. If some of them don’t return, it’ll tell you (“lost”). Packet loss leads to poor performance in games and streaming, and this is a nifty way to test.

By default, it sends 4 packets, each one waiting 4 seconds before timing out. You can increase the number of packets like this:

```
ping www.google.com -n 10
```

And you can increase the timeout duration like this (value is in milliseconds):

```
ping www.google.com -w 6000
```

2\. TRACERT
-----------

`tracert` stands for Trace Route. Like `ping`, it sends out a data packet as a way to troubleshoot any network issues you might have, but it instead tracks the route of the packet as it hops from server to server.

Sample usage:

The command outputs a line-by-line summary of each hop, including the latency between you and that particular hop and the IP address of that hop (plus domain name if available).

Why do you see three latency readings per-hop?

The `tracert` network command sends out three packets per hop to cover packet loss or slowdowns. Just remember that it doesn’t represent your true latency. It’s best practice to average the three.

3\. PATHPING
------------

`pathping` is similar to `tracert` except more informative, which means it takes a lot longer to execute. After sending out packets from you to a given destination, it analyzes the route taken and computes packet loss on a per-hop basis.

Sample usage and output:

4\. IPCONFIG
------------

`ipconfig` often comes up as the most-used networking command on Windows. Not only is it useful for the information it provides, but you can combine it with a couple of switches to execute certain tasks.

Sample usage and output:

The default output shows every network adapter on your system and how they resolve. The **IPv4 Address** and **Default Gateway** details under the Wireless LAN Adapter and Ethernet Adapter sections are the most important to know.

Use this switch to flush your DNS cache:

```
ipconfig /flushdns
```

Flushing the DNS cache can help when your internet is working, but a specific website or server is unreachable for some reason (e.g. a website times out and won’t load). If flushing the DNS cache doesn’t solve your connectivity issues, try these [quick troubleshooting tips to fix your Internet connection](//www.makeuseof.com/tag/no-internet-connection-troubleshooting-tips/).

5\. GETMAC
----------

Every device that’s compliant with IEEE 802 standards has a unique MAC address (Media Access Control). The manufacturer assigns MAC addresses and stores them in the device’s hardware. Some people use MAC addresses to limit which devices can connect to the network.

Sample usage and output:

You may see more than one MAC address depending on how many network-related adapters are on your system. For example, Wi-Fi and Ethernet connections would have separate MAC addresses. If you would like to know more, check out [what your IP and MAC address are good for](//www.makeuseof.com/tag/ip-mac-address/).

6\. NSLOOKUP
------------

`nslookup` stands for Name Server Lookup. It packs a lot of power, but most users won’t need that power. For regular folks like you and me, its main use is finding out the IP address behind a certain domain name.

Sample usage and output:

Note that certain domain names aren’t tied to a dedicated IP address, which means that you may get different IP addresses every time you run the command. This is normal for bigger websites because they spread their workload across many different machines.

If you want to convert an IP address into a domain name, just type it into your browser and see where it leads. Not all IP addresses lead to domain names though, and many IP addresses aren’t reachable over the web.

7\. NETSTAT
-----------

`netstat` is a tool for network statistics, diagnostics, and analysis. It’s powerful and complex but can be simple enough if you ignore the advanced aspects that you don’t need to know about (assuming you aren’t managing a massive business or campus network, for example).

Sample usage and output:

By default, the command shows all “active connections” on your system whether those connections are on LAN or across the internet. An active connection doesn’t mean data moving occurs — it could just mean a port that’s open and ready to accept a connection.

Indeed, `netstat` is mostly useful to regular users for its ability to show port information, and that can come in handy when you need to forward ports.

But the command also has about a dozen switches that change what kind of information is displayed, such as the `-r` switch which shows a routing table instead.

8\. NETSH
---------

`netsh` stands for Network Shell. It’s a cmd command for networking that lets you view and configure pretty much every network adapter on your system in more detail and granularity than any of the preceding commands.

Running the `netsh` command on its own will shift the Command Prompt into network shell mode. There are several different “contexts” within this shell, including one for routing-related commands, one for DHCP-related commands, and one for diagnostics, among others. But you can use it to run individual commands, too.

To see all network shell contexts:

And to see all commands within a context:

You can drill down one more layer to find all of the subcommands within those commands:

So for example, you can run this command to view all of the wireless network drivers on your system and their properties:

```
netsh wlan show drivers
```

Network Shell’s complex enough to deserve an entire article of its own. Just know that if you want to get real technical with your network configuration, you’ll probably need to use this command-line utility.

If Network Shell left you wanting to explore more than cmd network commands for your system, try these [basic cmd commands every user should know](//www.makeuseof.com/tag/15-cmd-commands-every-windows-user-know/).

Network Commands and Other Networking Solutions
-----------------------------------------------

For anyone new to Windows networking commands, a cheat sheet comes in handy. With some reference, you can use a variety of cmd commands for gleaning information on your network, wi-fi, and the Internet. Still, while it’s useful to always know your options, you might want an alternative.

Maybe using cmd commands for your networking aren’t necessary for the specific problem you’re having. You should check out these [diagnostic tricks and simple fixes for network problems](//www.makeuseof.com/tag/4-quick-solutions-windows-network-connection-problems/) to see if there’s a solution for you in there.

Read the full article: [8 CMD Commands to Manage Wireless Networks in Windows](https://www.makeuseof.com/tag/commands-manage-wireless-networks-windows/)

  
  
from MakeUseOf https://ift.tt/38xUJqX  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)