---
title: 'How To Hack Any Android Smartphone With just an Tricky SMS - Kali Linux'
date: 2019-12-13T05:57:00+01:00
draft: false
---

**How To Hack Any Android Smartphone With just an Tricky SMS - Kali Linux**  

[![](https://1.bp.blogspot.com/-MKeUgYxKFsc/XfMZFP3vZhI/AAAAAAAAB7g/lI8pnPu-ViYruahtUxb5_QuJtFtRKU1sgCNcBGAsYHQ/s640/Hack-Android-with-a-Tricky-SMS-Using-Venom.png)](https://1.bp.blogspot.com/-MKeUgYxKFsc/XfMZFP3vZhI/AAAAAAAAB7g/lI8pnPu-ViYruahtUxb5_QuJtFtRKU1sgCNcBGAsYHQ/s1600/Hack-Android-with-a-Tricky-SMS-Using-Venom.png)

  
Social Engineering sometimes doesn't work for all.  
Do you agree with it? When I was a noob, I tried a lot of things to trape people but none of them worked! The heading I have given is not a clickbait, it is the solution for the problems newbie attackers face.  
  
But you can't exactly hack an android phone with an SMS but you can make a webpage that has auto-download enabled. Because maximum people do not download payloads manually. That is the biggest problem.  
  
Here I am going to use a tool called Venom which is basically a Metasploit Shellcode generator/compiler script. It was mainly created to test for different purposes. It depends on you how you use it. The tool uses the Apache2 webserver to deliver payloads using a fake web page. You just need to send a tricky SMS so that the victim clicks the link. The payload will be downloaded automatically to the victim's system.  
  
I don't recommend you hack someone's system with his/her permission which is completely illegal. Make use of this information for educational purposes only so that you can protect yourself against these attacks.  
  
Let's get into the installation manual.  
Configure Venom in Kali Linux  
Fire up your Kali Linux machine, open up the terminal, change the directory to the Desktop and clone Venom from Github.  
  
**cd Desktop/**  
**git clone [https://github.com/r00t-3xp10it/venom.git](https://github.com/r00t-3xp10it/venom.git)**  
  
Now change the directory to the venom folder and again change the directory to the aux folder which is inside the venom folder. Here you will see a script named with setup.sh. If you are a root user, you must take permission to run this shell script. Don't worry, just follow the commands.  
  
**cd venom/**  
**cd aux/**  
**chmod +x setup.sh**  
**./setup.sh**  

[![](https://1.bp.blogspot.com/-9Yj_YTLXCyI/XfMZDqsjAxI/AAAAAAAAB7k/XfKcH3yqAgIY0l7j0vSRGpJBX8qFtk84ACEwYBhgL/s640/1.png)](https://1.bp.blogspot.com/-9Yj_YTLXCyI/XfMZDqsjAxI/AAAAAAAAB7k/XfKcH3yqAgIY0l7j0vSRGpJBX8qFtk84ACEwYBhgL/s1600/1.png)

  
  
The script will set up the tool and install all the requirements to run the tool properly. Now go back to the main folder(cd ..) and run the venom.sh script.  
**./venom.sh**  

[![](https://1.bp.blogspot.com/-NXNTEoNgGgs/XfMZDiFDwSI/AAAAAAAAB7o/kpeGcLQXD8Me3XT-6RYeDHfg1x5GeMZogCEwYBhgL/s640/2.png)](https://1.bp.blogspot.com/-NXNTEoNgGgs/XfMZDiFDwSI/AAAAAAAAB7o/kpeGcLQXD8Me3XT-6RYeDHfg1x5GeMZogCEwYBhgL/s1600/2.png)

The tool stated successfully. Here you see we can create payloads for all popular platforms such as Windows, Android, Ios. But I will stick with Android because I want to test it for Android. So I will select No 4.  

[![](https://1.bp.blogspot.com/-gGCKUtimfe8/XfMZDq2pd9I/AAAAAAAAB7s/EfPwK68-mJUvgSDN86ZfwS6h9pqw64obACEwYBhgL/s640/3.png)](https://1.bp.blogspot.com/-gGCKUtimfe8/XfMZDq2pd9I/AAAAAAAAB7s/EfPwK68-mJUvgSDN86ZfwS6h9pqw64obACEwYBhgL/s1600/3.png)

Here I have entered option Agent No 1 and now it showing a popup to enter the localhost IP. If you want to hack over WAN, you can use port forwarding in your router or if you don't have a router you can take the Ngrok tool in use. Which is a  great tool for port forwarding and it is completely free.  

[![](https://1.bp.blogspot.com/-HTdCLR2NpFw/XfMZEWZNf0I/AAAAAAAAB7w/kH4Hepc0OTEKkvc3IKsCV6Bg1NxmiPgwwCEwYBhgL/s640/4.png)](https://1.bp.blogspot.com/-HTdCLR2NpFw/XfMZEWZNf0I/AAAAAAAAB7w/kH4Hepc0OTEKkvc3IKsCV6Bg1NxmiPgwwCEwYBhgL/s1600/4.png)

Now it's asking for the port number. I have entered my port number and in the third popup, it is asking the name I want to give to the payload.  
  
After completing the generating process of the payload, the tool asking me how I want to deliver the payload to the victim. Here I have selected the Apache2 Malicious web server.  

[![](https://1.bp.blogspot.com/-8QAhLb2-Tyk/XfMZE9OpRLI/AAAAAAAAB70/YbH6ynLGVKg26JNY_ja7NH-dv5WRUlCqwCEwYBhgL/s640/5.png)](https://1.bp.blogspot.com/-8QAhLb2-Tyk/XfMZE9OpRLI/AAAAAAAAB70/YbH6ynLGVKg26JNY_ja7NH-dv5WRUlCqwCEwYBhgL/s1600/5.png)

Now it automatically starting the Metasploit MultiHandler.   
**Sending the Link to a victim with a Tricky SMS**  
The web server is running on the localhost so I can open the web page using my local IP(ex: 192.168.43.139). But we can't send a naked IP address to a victim. He will find it suspicious. We must mask it. You can take the bit.ly service in use. The paid service also offers you to create a custom URL.  
  
Now you need to find an online fake SMS service. I have found a website called [SMSGang](http://www.smsgang.com/). I can send text anonymously with a fake name from the website.  

[![](https://1.bp.blogspot.com/-cpeCfB5Voew/XfMZyUDTNPI/AAAAAAAAB74/EGxy85d1yrIEZVMWmcvVIjT1ENm1OUFTQCNcBGAsYHQ/s320/venom%2Bin%2BKali%2BLinux-crackitdown.png)](https://1.bp.blogspot.com/-cpeCfB5Voew/XfMZyUDTNPI/AAAAAAAAB74/EGxy85d1yrIEZVMWmcvVIjT1ENm1OUFTQCNcBGAsYHQ/s1600/venom%2Bin%2BKali%2BLinux-crackitdown.png)

As I have prepared a tricky SMS, you can apply your own trick to make it look more genuine. It depends on you.  
  
Check out the popular commands you can use to control the compromised device after starting the Metasploit listener.  
**Popular Metasploit commands**  
  
1\. shell- Interact with a Shell  
2\. sysinfo- To check system information  
3\. webcame\_ list- Shows the list of connected webcams  
4\. webcam\_snap- To take a Webcam snapshot  
5\. record\_mic -d 20- To record mic. Also phone conversation  
6\. check\_root- To check the device root status  
7\. dump\_calllog- To retrieve call log  
8 dump\_contacts- To retrieve contacts  
9\. geolocate- To locate the device  
10 send\_sms- To send an SMS  
11\. sms\_dump- To download all SMS as a text file  
12\. run- To run any service(set the location of the service after the command).  
**Conclusion**  
Social Engineering completely depends on how you trick people. These tools only help a little to make your trick look more genuine. A Venom is a great tool if you use it in the right way.  
  
I loved the tool. What's your opinion about it? what trick are you gonna use? tell others in the comment box below. We get inspired to produce more tutorials like this when you leave a comment.  
(We offer guest commenting. You don't need to create an account to do comment.)  
  
**Disclaimer**  
  
The tutorial you found on this website is only for educational purposes. Misuse of this information can lead you to jail or punishment. Anything you damage, we are not responsible for that. Do use it on your own property. If you want to test it on other's property, take written permission from them