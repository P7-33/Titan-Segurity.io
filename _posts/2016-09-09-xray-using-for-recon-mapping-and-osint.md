---
title: 'XRay - Using For Recon Mapping And OSINT Suite'
date: 2019-11-11T12:02:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-7sLGGq3Zgew/XckvbaiXhoI/AAAAAAAAGe0/mAl83KGaKngfD-Y8qUhQ29OSiLudmsRGgCLcBGAsYHQ/s640/XRAY.png)](https://1.bp.blogspot.com/-7sLGGq3Zgew/XckvbaiXhoI/AAAAAAAAGe0/mAl83KGaKngfD-Y8qUhQ29OSiLudmsRGgCLcBGAsYHQ/s1600/XRAY.png)

  
XRay is a software for recon, mapping and OSINT gathering from public networks.  
  
XRay for network OSINT gathering, its goal is to make some of the initial tasks of information gathering and network mapping automatic.  

### How Does it Work?

**XRay is a very simple tool, it works this way:**  

1.  It'll bruteforce subdomains using a wordlist and DNS requests.
2.  For every subdomain/ip found, it'll use Shodan to gather open ports and other intel.
3.  If a ViewDNS API key is provided, for every subdomain historical data will be collected.
4.  For every unique IP address, and for every open port, it'll launch specific banner grabbers and info collectors.
5.  Eventually the data is presented to the user on the web ui.

  

### Grabbers and Collectors

*   HTTP Server, X-Powered-By and Location headers.
*   HTTP and HTTPS robots.txt disallowed entries.
*   HTTPS certificates chain ( with recursive subdomain grabbing from CN and Alt Names ).
*   HTML title tag.
*   DNS version.bind. and hostname.bind. records.
*   MySQL, SMTP, FTP, SSH, POP and IRC banners.

  

### Notes

**Shodan API Key**  
  
The shodan.io API key parameter ( \-shodan-key KEY ) is optional, however if not specified, no service fingerprinting will be performed and a lot less information will be shown (basically it just gonna be DNS subdomain enumeration).  
  
**ViewDNS API Key**  
  
If a [ViewDNS](http://viewdns.info/) API key parameter ( \-viewdns-key KEY ) is passed, domain historical data will also be retrieved.  
  
**Anonymity and Legal Issues**  
  
The software will rely on your main DNS resolver in order to enumerate subdomains, also, several connections might be directly established from your host to the computers of the network you're scanning in order to grab banners from open ports. Technically, you're just connecting to public addresses with open ports (and there's no port scanning involved, as such information is grabbed indirectly using Shodan API), but you know, someone might not like such behaviour.  
  

### Building a Docker image

To build a Docker image with the latest version of XRay:  
  
git clone https://ift.tt/2XcBrmV  
cd xray  
docker build -t xraydocker .  
  
Once built, XRay can be started within a Docker container using the following:  
  
docker run --rm -it -p 8080:8080 xraydocker xray -address 0.0.0.0 -shodan-key shodan\_key\_here -domain example.com   
  

### Manual Compilation

Make sure you are using Go >= 1.7, that your installation is working properly, that you have set the $GOPATH variable and you have appended $GOPATH/bin to your $PATH.  
  
**Then:**  
  
go get github.com/evilsocket/xray  
cd $GOPATH/src/github.com/evilsocket/xray/  
make  
  
You'll find the executable in the build folder.  
  

### Usage

Usage: xray -shodan-key YOUR\_SHODAN\_API\_KEY -domain TARGET\_DOMAIN  
  
Options:  
  -address string  
        IP address to bind the web ui server to. (default "127.0.0.1")  
  -consumers int  
        Number of concurrent consumers to use for subdomain enumeration. (default 16)  
  -domain string  
        Base domain to start enumeration from.  
  -port int  
        TCP port to bind the web ui server to. (default 8080)  
  -preserve-domain  
        Do not remove subdomain from the provided domain name.  
  -session string  
        Session file name. (default "\-xray-session.json")  
  -shodan-key string  
        Shodan API key.  
  -viewdns-key string  
        ViewDNS API key.  
  -wordlist string  
        Wordlist file to use for enumeration. (default "wordlists/default.lst")  
  
**Example:**  
  
\# xray -shodan-key yadayadayadapicaboo... -viewdns-key foobarsomethingsomething... -domain fbi.gov  
  
\_\_\_\_  \_\_\_  
\\   \\/  /  
 \\     RAY v 1.0.0b  
 /    by Simone 'evilsocket' Margaritelli  
/\_\_\_/\\  \\  
      \\\_/  
  
@ Saving session to fbi.gov-xray-session.json  
@ Web UI running on http://127.0.0.1:8080/  
  
[Download XRay](https://github.com/evilsocket/xray)

  
  
from Hackers Online Club (HOC) https://ift.tt/34HnxLY