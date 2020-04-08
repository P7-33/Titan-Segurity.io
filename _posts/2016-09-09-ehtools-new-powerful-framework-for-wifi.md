---
title: 'EhTools - A New Powerful Framework For WiFi Penetration Testing'
date: 2019-12-18T00:12:00+01:00
draft: false
---

**EhTools - A New Powerful Framework For WiFi Penetration Testing**  

[![](https://1.bp.blogspot.com/-DOMrrgq3DPk/XflgwgGLdxI/AAAAAAAACCg/5Ond0H9SCUsgvg7NKv8XvaTHbjsl8FmhACNcBGAsYHQ/s640/EhTools--A-New-Framework-of-Wifi-Penetration-Testing-Tools.png)](https://1.bp.blogspot.com/-DOMrrgq3DPk/XflgwgGLdxI/AAAAAAAACCg/5Ond0H9SCUsgvg7NKv8XvaTHbjsl8FmhACNcBGAsYHQ/s1600/EhTools--A-New-Framework-of-Wifi-Penetration-Testing-Tools.png)

Wifi Penetration Testing.  
  
Wifi is maybe one of the best technologies gifted to us. Wifi helps us to upgrade our messy wired devices to a clean, well-organized way.  
  
But as all technologies do, wifi also has some security issues, especially for the public wifi networks. Any intruder can attack our devices by accessing our Wifi networks silently.   
  
We must analyze our wireless network from time to time to prevent hacking attacks. There are a lot of tools already to do wifi penetration testing but the tool we are going to discuss here is a little different from others.  
  
Ehtools. A framework of serious wifi penetration testing tools developed by the entynetproject.  
  
What makes Ehtools framework different from others?  
  
When we go for wifi penetration testing, we have to use different tools for different tasks. That's becomes very irritating sometimes.   
  
Ehtools just organizes and links the tools used for wifi penetration testing that already exists so that we can control them from one place. Examples of such tools are Aircrack-ng, Airdump-ng, WPS Pixie- Dust, etc.  
  
Let's see how we can configure Ehtools on the Linux Platform.  
**Note: You must be logged in as 'root' in order to run the tool error-free.**  
**Configuring EhTools on Linux**  
Fire up your Linux machine and download Ehtools from Github. Now navigate to the directory where you've downloaded it and expand it. Here you will see a shell script named '**install.sh**'. You need to launch it in order to install the tool. Before launching you must give root permission to it. Just type the commands one by one as you can see in the screenshot below.  

[![](https://1.bp.blogspot.com/-6OFbg04HF24/XflgLNjRjfI/AAAAAAAACCM/lDvMVuiseHQq7OUEVNoHcYES5rJ3KjlIQCNcBGAsYHQ/s640/11.png)](https://1.bp.blogspot.com/-6OFbg04HF24/XflgLNjRjfI/AAAAAAAACCM/lDvMVuiseHQq7OUEVNoHcYES5rJ3KjlIQCNcBGAsYHQ/s1600/11.png)

Now it will ask for the version of Ehtools you want to install. It offers two versions- pro and lite. You can buy the tools pro version from here but if you don't want to, you can continue installing the lite version.  
As most will prefer going with the lite for testing purposes, we are choosing the lite as well.  

[![](https://1.bp.blogspot.com/-O0Wxq8V_n4w/XflgCrmF8SI/AAAAAAAACB4/IGDw8yUlbJUA4p03x_IkLWyaHf5fzbmbQCEwYBhgL/s640/22.png)](https://1.bp.blogspot.com/-O0Wxq8V_n4w/XflgCrmF8SI/AAAAAAAACB4/IGDw8yUlbJUA4p03x_IkLWyaHf5fzbmbQCEwYBhgL/s1600/22.png)

Now hit enter. At the next step, it will ask you to install the modules. type 'yes' and hit enter.  

[![](https://1.bp.blogspot.com/-TjT08_KsEEc/XflgCnrBY9I/AAAAAAAACCQ/4CeNBt1V1QofRB76Q-QNd65awTcSd5HzgCEwYBhgL/s640/33.png)](https://1.bp.blogspot.com/-TjT08_KsEEc/XflgCnrBY9I/AAAAAAAACCQ/4CeNBt1V1QofRB76Q-QNd65awTcSd5HzgCEwYBhgL/s1600/33.png)

Now you have to set a username and password to protect ehtools from unauthorized access. type 'yes' and hit enter.  

[![](https://1.bp.blogspot.com/-Zhz3uvnYRw4/XflgClXE5hI/AAAAAAAACCA/pd2SDLp4syoc9-P8bW32RYpeulOss3a9gCEwYBhgL/s640/44.png)](https://1.bp.blogspot.com/-Zhz3uvnYRw4/XflgClXE5hI/AAAAAAAACCA/pd2SDLp4syoc9-P8bW32RYpeulOss3a9gCEwYBhgL/s1600/44.png)

The last step is creating a config key. Type the key you want to set and hit enter.  

[![](https://1.bp.blogspot.com/-UwkUXIlR8QA/XflgDqO-aTI/AAAAAAAACCU/gPHTqH-LLq0Ts3y8Rfdo6FbmaoGjSrkPQCEwYBhgL/s640/55.png)](https://1.bp.blogspot.com/-UwkUXIlR8QA/XflgDqO-aTI/AAAAAAAACCU/gPHTqH-LLq0Ts3y8Rfdo6FbmaoGjSrkPQCEwYBhgL/s1600/55.png)

Here we go! we have successfully configured the tool.  

[![](https://1.bp.blogspot.com/-IAdG7wOaQLI/XflgDyACsCI/AAAAAAAACCY/7d1SQwCiDOUJ3O-1v6k95OWG5N3DsZmigCEwYBhgL/s640/66.jpg)](https://1.bp.blogspot.com/-IAdG7wOaQLI/XflgDyACsCI/AAAAAAAACCY/7d1SQwCiDOUJ3O-1v6k95OWG5N3DsZmigCEwYBhgL/s1600/66.jpg)

**Conclusion**  
  
Many developers working on these types of tools. They do not create new tools but link the tools that already exist and used for the same category of penetration testing. It helps us to control different tools from one place with a single line of commands.