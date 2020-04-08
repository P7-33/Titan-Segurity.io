---
title: 'Track a Cellphone Without The IP Address Using Trape Tool - Kali Linux'
date: 2019-12-18T12:36:00+01:00
draft: false
---

**Track a Cellphone Without The IP Address Using Trape Tool - Kali Linux**  
The most important topic to discuss for them who lost their cellphone and searching the web for the solution to track the phone.  
  
Second, if someone bullying you then it's become very very important to track him down.  
  
Rex, one of my friends, one day got a call from an unknown number a man spoke to him with very bad language.  
  
He tried to track the phone number but he failed because the service providers do not allow us to do that.  
  
If they don't, then  How can we track a cell phone with our own? This question often comes in our mind when we go to track someone down.   
  
But we forget one thing, i.e. nowadays every single person uses the internet on their mobile. We can track them through the Internet.  
  
Here, we are going to discuss the way using which we can track any cell phone easily using a simple tool and a little social engineering trick. All you need is Kali Linux Installed in your system and an active Internet connection.  
  
The tool we're gonna use here is called Trape. Before begining the tutorial let's know a little about it.  
**A Little About Trape Tool**  

[![](https://1.bp.blogspot.com/-FHXZ0txwdV4/XfoM2etniTI/AAAAAAAACDQ/wF3kLrnKfCUPuNwrmjYkdvPC69gJCC2FgCNcBGAsYHQ/s640/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown.png)](https://1.bp.blogspot.com/-FHXZ0txwdV4/XfoM2etniTI/AAAAAAAACDQ/wF3kLrnKfCUPuNwrmjYkdvPC69gJCC2FgCNcBGAsYHQ/s1600/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown.png)

Trape is a Github script written in python. Using Trape we can generate a tracking URL for the victim. If the victim enters the URL, we will get the IP logs in Trape's control panel.  
  
Basically, the tool performs browser hooking. Once the victim trapped, we can capture credentials, important details, etc. We can get the real-time location too if the GPS is turned on.  
  
Also, we can check the login sessions of the browsers that the victim used. The tool recognizes facebook, twitter, VK, Reddit, Gmail, Github, etc. popular sessions.  
  
**Let's get to the tutorial.**  
  

*   Configure Trape in Kali Linux
*   Fire up your Kali Linux machine and open up the terminal.
*   Clone or download the tool from here. To clone it, use the commands-

  
**cd Desktop/**  
**git clone https://github.com/jofpin/trape.git**  
  

*   It will download the tool on the desktop. You can change the directory to your own choice. 
*   Now go to the downloaded folder by the commands-

  
**cd Desktop**  
**ls**  
**cd Trape/**  
**ls**  
**Step 1: Install The requirements**  
Here, you will see a text file named requirements.txt. This file is needed to install some necessary packages and library files to run Trape properly.  
  
Now proceed to install the requirements, run the file by the command-  
  
**pip install -r requirements.txt**  

[![](https://1.bp.blogspot.com/-95CgEzDzoms/XfoM1REa76I/AAAAAAAACDk/KWZlkPNXLvA_G8rey1nlyDzf19u-XDz_wCEwYBhgL/s640/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown%2B%25281%2529.png)](https://1.bp.blogspot.com/-95CgEzDzoms/XfoM1REa76I/AAAAAAAACDk/KWZlkPNXLvA_G8rey1nlyDzf19u-XDz_wCEwYBhgL/s1600/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown%2B%25281%2529.png)

This command will install all the necessary packages and subfolders automatically. But it's not a thing to worry about. Trape will install the requirements on its own but this step will help to speed up the installation process.  
**Step 2: Load The Tool in The terminal**  
Now, run the command python trape.py -h to see how to use the tool.  
  
 Here it shows the command **python trape.py -u <\> -p <\>**. We can use this command to run the tool.  
  
Now let us demonstrate how we can use the tool.  
  
In the command, we are using the URL https://google.com and the Port 8080 as an example. So our command will look like-  
  
**python trape.py -u https://google.com -p 8080**  
  
(Note: You can take any URL and a Port number you want to use in the command. If you take https://facebook.com in the URL, the browser hooking phishing page will look like the Facebook login page.)  
  
 Now type the command and hit enter. The tool will be loaded successfully.  
  
Here our Trape tool is running. Here we got two links and one access key. The first link is to trape the victim, the second is the control panel link and the access key is to access the control panel.  

[![](https://1.bp.blogspot.com/--KJHL0PPiDs/XfoM1HkfUHI/AAAAAAAACDg/8gZj6kLzblInwDhLe1LP0V67YIhMv-hAQCEwYBhgL/s640/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown%2B%25282%2529.png)](https://1.bp.blogspot.com/--KJHL0PPiDs/XfoM1HkfUHI/AAAAAAAACDg/8gZj6kLzblInwDhLe1LP0V67YIhMv-hAQCEwYBhgL/s1600/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown%2B%25282%2529.png)

**Step 3: Resolve the problems with the IP address**  
All are okay but there is a problem. The link for the victim looks suspicious and if the victim is clever, he's not gonna get trapped.  
  
But there is a solution. Shorten the link using Bitly URL shortener.  

[![](https://1.bp.blogspot.com/-keKAA6GwuU4/XfoM3X2wpsI/AAAAAAAACDs/ZNyEqpdLYP0JUyrMZa3ZTQjsiShCyt23gCEwYBhgL/s640/install-Trape-in-Kali-Linux.png)](https://1.bp.blogspot.com/-keKAA6GwuU4/XfoM3X2wpsI/AAAAAAAACDs/ZNyEqpdLYP0JUyrMZa3ZTQjsiShCyt23gCEwYBhgL/s1600/install-Trape-in-Kali-Linux.png)

Ahha! now, all okay. Send the shortened link to the victim and wait for the victim to fall in the trape.  
  
Note down this point- The IP address 127.0.0.1 which used in the generated link is a local IP address and it will not work outside the local network. It will only work on the devices connected to the same local network.  
  
But don't worry. Ngrok tool can help us in this situation.   
Access localhost over WAN Using Ngrok  
Download [Ngrok](https://github.com/bubenshchykov/ngrok) from here. It will be downloaded as a zip file. Extract it on the desktop and copy the Ngrok executable file from the extracted folder to the Desktop.  
  
Now open up the terminal and change the directory to Desktop by the command-  
**cd Desktop/**  
**ls**  
Now you need to change the permission of Ngrok script. To do that type the command-  
  
**chmod +x ngrok**  
  
In this step, move the ngrok script to bin folder by the command-  
  
**mv ngrok /usr/bin**  
  
Now clear the terminal and simply type the command ngrok http 8080 and hit enter.  
  
Here in the 8080 section, you can choose and forward any port number.  
  
Now you can see our 8080 port is online!  
  
configure ngrok in Kali Linux  

[![](https://1.bp.blogspot.com/-R1iJjtDF2e0/XfoM1b3BnWI/AAAAAAAACDc/HXvCU8UEcUYUhoYXHiP-Y973jbKsOKjYgCEwYBhgL/s640/configure%2BNgrok%2Bin%2BKali%2BLinux-crackitdown.png)](https://1.bp.blogspot.com/-R1iJjtDF2e0/XfoM1b3BnWI/AAAAAAAACDc/HXvCU8UEcUYUhoYXHiP-Y973jbKsOKjYgCEwYBhgL/s1600/configure%2BNgrok%2Bin%2BKali%2BLinux-crackitdown.png)

  
Okay, in the end, our problem with the localhost URL has been solved. Thanks to Ngrok. We can use the ngrok.io URL instead of the localhost.  
  
**Step 4: Login To The Control Panel And Manage the Trapped**  
Now, copy the control panel link and paste & search in a browser.  
  

[![](https://1.bp.blogspot.com/-MRQZm596Gts/XfoM2A0-_YI/AAAAAAAACDg/1seT8i6Gbs4cYMj6pGNXKdSPWg8sAk9LwCEwYBhgL/s640/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown%2B%25283%2529.png)](https://1.bp.blogspot.com/-MRQZm596Gts/XfoM2A0-_YI/AAAAAAAACDg/1seT8i6Gbs4cYMj6pGNXKdSPWg8sAk9LwCEwYBhgL/s1600/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown%2B%25283%2529.png)

  
  
  
And copy the access key from the terminal and paste it to the login page. You will be logged in to the Control Panel Dashboard. Here you can manage the trapped victims.  
  
If someone clicks the link you will get his log in the Dashboard. To test the tool we opened it on another computer and we got the IP log.  

[![](https://1.bp.blogspot.com/-fXsIySQaE78/XfoM27SLjpI/AAAAAAAACDo/JWFbwxMrcVQaLtiNRPet2RvecQJ7NbVVwCEwYBhgL/s640/install-Trape-in-Kali-Linux-crackitdown.png)](https://1.bp.blogspot.com/-fXsIySQaE78/XfoM27SLjpI/AAAAAAAACDo/JWFbwxMrcVQaLtiNRPet2RvecQJ7NbVVwCEwYBhgL/s1600/install-Trape-in-Kali-Linux-crackitdown.png)

Now, look at what you can collect from the trapped IP addresses. Click on 'DETAILS' at the right. You will get the real-time location and the logged-in sessions in the browser.  

[![](https://1.bp.blogspot.com/-_Efn4Vvzz-E/XfoM2GVHpvI/AAAAAAAACDc/_iwYsq9zffsqiMgFlUlUbaxpIWGeq_NkQCEwYBhgL/s640/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown%2B%25284%2529.png)](https://1.bp.blogspot.com/-_Efn4Vvzz-E/XfoM2GVHpvI/AAAAAAAACDc/_iwYsq9zffsqiMgFlUlUbaxpIWGeq_NkQCEwYBhgL/s1600/install%2BTrape%2Bin%2BKali%2BLinux-crackitdown%2B%25284%2529.png)

But the location depends on GPS. If the GPS of the victim is turned on, you will get a real-time location. Also, you will get the details of the device, about the CPU, Operating System, Browser, ISP Name. These details are enough to track someone down.  
  
If the sessions are active then the OFFLINE will become ONLINE. If it comes online click on the session icon to see and use it.  
  
One thing to note down. You can use the trapping link on many people.  
**Conclusion:**  
  

*   We should stop cyberbullies as much as we can. But we can't stay safe every time. In this case, tools like Trape comes into use.
*   Playing with someone's feelings is not a good thing but that's what cyberbullies do. It's not nice mainly for a teenager.
*   If you liked the tutorial let us know and if you have any problem with the installation or use of this tool feel free to comment us below describing your problem. Stay safe and have a joyful hacking journey. 

  
**Disclaimer:**  
  
We do not promote any illegal activity on our blog. Perform it on others at your own risk. We are not responsible for any kind of damage caused by you. It is recommended to use it legally and stay safe. Use it only when you need it for good work. Ethical Hacking doesn't mean applying it to anyone without any legal reason. To do practice use your own property or if you want to use other's take written permission from them.