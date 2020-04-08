---
title: 'A Basic Guide to VOIP Packet analysis through Wireshark'
date: 2019-11-08T15:58:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-SG0ohpWu_FM/XcWCbrUJqPI/AAAAAAAAD6g/i3HjZQpRxgIN0QpeVxgbpkwtLcb8VqpOgCLcBGAsYHQ/s640/wireshark.png)](https://1.bp.blogspot.com/-SG0ohpWu_FM/XcWCbrUJqPI/AAAAAAAAD6g/i3HjZQpRxgIN0QpeVxgbpkwtLcb8VqpOgCLcBGAsYHQ/s1600/wireshark.png)

Wireshark is a packet analysis tool used for analysing services, protocols , data transmission. It is an open source software available freely online.Wireshark is  cross platform which uses pcap to capture packets. It is majorly a GUI based tool which is implemented with the help Qt widget toolkit ( Used for creating GUI  as well as cross-platform applications that run on various software and hardware platforms such as Linux, Windows, macOS, Android or embedded systems ).There is also a terminal-based (non-GUI) version called TShark.  
  
One can download Wireshark from its official website. i.e. https://www.wireshark.org/download.html  
  
Wireshark makes it very easy to analyse packet with the help of filters in order to work efficiently.  
  
It Stands for "Voice Over Internet Protocol," and is often pronounced "voip." VoIP is basically a telephone connection over the Internet. The data is sent digitally, using the Internet Protocol (IP) instead of analog telephone lines. Switching to VoIP might also help you save money on communications services. Long-distance and international calls are generally free with VoIP service. The only charge is for your internet access. This is also one of the major reason corporates are shifting to VOIP services very fast.  
  
**How VOIP data packets are transmitted ?**  

Voice over Internet Protocol, is a method for taking analog audio signals, like the kind you hear when you talk on the phone, and turning them into digital data that can be transmitted over the Internet.For the transmission of VOIP Packets they use several protocols which are SIP, RTP .

SIP : Session Initiation protocol is a protocol which setup an IP communication session.Its is done with the help of 3-way handshake which includes following steps : 

*   The caller sends an INVITE
*   The callee sends an 200 OK to accept the call
*   The caller sends an ACK to indicate that the handshake is done and a call is going to be setup.

![Image result for sip handshake](https://www.voipmechanic.com/images/sip_pics/sip_call_basic.gif)

When SIP executes and is implemented it mainly requires a SIP Account/Services which can be availed online, second it requires SIP Client which can be a soft-phone or software which provides connection through SIP services.

After the establishment done between the clients comes up another protocol i.e. RTP (Real-time Transport Protocol) which is responsible in exchanging data packets. 

You can think of SIP as a stage manager. SIP prepares the stage for RTP by setting up its connection. Once RTP is finished with its stage (call), then SIP comes back to the stage to clean up after it. 

  
Now let's start the Wireshark and start capturing packets. Here the VOIP application used is Zoiper whose packets we will be going to capture including the connection establishment , data transmission and connection termination.  
  
  
**Step 1** : Open Wireshark and select the interface whose packets you want to capture.Here I am going to select Local Area connection.  
  
  

[![](https://1.bp.blogspot.com/-B1b92qNvHok/XZS3FQxq45I/AAAAAAAAASA/JX8RPB5Tg_E1q79vwldhNWAFlbBsLvtnACLcBGAsYHQ/s640/w1.png)](https://1.bp.blogspot.com/-B1b92qNvHok/XZS3FQxq45I/AAAAAAAAASA/JX8RPB5Tg_E1q79vwldhNWAFlbBsLvtnACLcBGAsYHQ/s1600/w1.png)

  
  
You will observe hundreds of packets getting captured.  
  
**Step 2:** Now we will open a VOIP application whose packets we need to capture.( In my case it is Zoiper5 ) .It might seem tough to analyse specific packets as it is going with the collection of many protools so we use filters in which we go for majorly to filters i.e. RTP and SIP .  

  

  

[![](https://1.bp.blogspot.com/-n7G_zD1-E6U/XZS5lPdc3vI/AAAAAAAAASY/ctTdjX0JkFwRd6LsAkvoZT40GC2sY1G2gCLcBGAsYHQ/s640/w2.png)](https://1.bp.blogspot.com/-n7G_zD1-E6U/XZS5lPdc3vI/AAAAAAAAASY/ctTdjX0JkFwRd6LsAkvoZT40GC2sY1G2gCLcBGAsYHQ/s1600/w2.png)

  

  
 **Step 3**: After applying the SIP filter, in the Info column you will see handshake for connection establishment with the services is being made. Let's make a call and start capturing packets.  
  
  

[![](https://1.bp.blogspot.com/-BIy0WB-I7Ak/XZS7JKfns2I/AAAAAAAAASk/RbHAHKKv29kCxFhzVd1CQLtNHnvDS1OPQCLcBGAsYHQ/s640/w3.png)](https://1.bp.blogspot.com/-BIy0WB-I7Ak/XZS7JKfns2I/AAAAAAAAASk/RbHAHKKv29kCxFhzVd1CQLtNHnvDS1OPQCLcBGAsYHQ/s1600/w3.png)

  
In this image notice in the Info. columns the SIP handshake and you will notice a proper connection was established and ended up with Bye with some status codes.This hows up the work of SIP very well which was of connection establishment now lets move on to check for the data packets transferred in between.  
  
**Step 4:** Change the filter from sip to RTP  and you will notice a lot of packets listed in the analysis frame. You will see a whole lot of packets transmitted in the data stream.  
  
  

[![](https://1.bp.blogspot.com/-ZWlm_MTAiT8/XZS82HJrWqI/AAAAAAAAASw/B_vQ5dySnDINCrCCtpKhj8pHlOzT8KpRgCLcBGAsYHQ/s640/w4.png)](https://1.bp.blogspot.com/-ZWlm_MTAiT8/XZS82HJrWqI/AAAAAAAAASw/B_vQ5dySnDINCrCCtpKhj8pHlOzT8KpRgCLcBGAsYHQ/s1600/w4.png)

  
**Step 5**: Go to Telephone tab in the  title bar and click on VOIP .  
  
  

[![](https://1.bp.blogspot.com/-vCMeD78ny9Q/XZS9PW7eN5I/AAAAAAAAAS4/p5VqXCQZbdQGJbBmcEoiTsN9jHJmchygwCLcBGAsYHQ/s640/w5.png)](https://1.bp.blogspot.com/-vCMeD78ny9Q/XZS9PW7eN5I/AAAAAAAAAS4/p5VqXCQZbdQGJbBmcEoiTsN9jHJmchygwCLcBGAsYHQ/s1600/w5.png)

  
You will land up to a new window where you can listen up to the entire conversation been made through VOIP.   
  
  

[![](https://1.bp.blogspot.com/-OtNaF4odOf4/XZS-B7a7fXI/AAAAAAAAATE/iftFK5Dnrcg0CBDT8-Va1N99xBuBCFnhQCLcBGAsYHQ/s640/w6.png)](https://1.bp.blogspot.com/-OtNaF4odOf4/XZS-B7a7fXI/AAAAAAAAATE/iftFK5Dnrcg0CBDT8-Va1N99xBuBCFnhQCLcBGAsYHQ/s1600/w6.png)

  
  
**Step 6** : Click on Play Stream and it will open up a RTP player in which two colour codes are used the blue and black one the blue coloured column is the one in which data was transferred from system itself and the black one is which has been received from the VOIP user whom you have called.  
NOTE : You can go for the better understanding of colour encoding by going to **View Tab -> Coloring Rules.**  
  
  

[![](https://1.bp.blogspot.com/-OgedxQaXc6Q/XZS_R9cEjGI/AAAAAAAAATQ/ld-Y2dSb2BcyT8002XXtQMHTYfPaZ-qxgCLcBGAsYHQ/s640/W8.png)](https://1.bp.blogspot.com/-OgedxQaXc6Q/XZS_R9cEjGI/AAAAAAAAATQ/ld-Y2dSb2BcyT8002XXtQMHTYfPaZ-qxgCLcBGAsYHQ/s1600/W8.png)

  
  
Select any one whose side you want to listen and go for sniffing the VOIP packets.  
  
You can work on such packets and download some for practice purpose from here :  
[https://wiki.wireshark.org/SampleCaptures#Sample\_Captures](https://wiki.wireshark.org/SampleCaptures#Sample_Captures)