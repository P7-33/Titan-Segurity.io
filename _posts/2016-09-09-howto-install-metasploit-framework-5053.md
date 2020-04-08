---
title: 'HOWTO : Install Metasploit Framework 5.0.53 on Ubuntu Desktop 19.04'
date: 2019-10-08T02:28:00+01:00
draft: false
---

**Install dependencies :**  
  
  
  
`sudo apt -y install curl`  
  
  
  
**Download the installer :**  
  
  
  
`curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall  
  
  
  
chmod +x msfinstall`  
  
  
  
**Run the installer :**  
  
  
  
`./msfinstall`  
  
  
  
**Initialize the msfdb :**  
  
  
  
`msfdb init`  
  
  
  
or  
  
  
  
`msfdb reinit`  
  
  
  
You may need to answer two questions about setting up web version of Metasploit Framework.  
  
  
  
**Run the Metasploit Framework :**  
  
  
  
`msfdb start`  
  
  
  
or  
  
  
  
`msfdb restart`  
  
  
  
`msfconsole`  
  
  
  
**Stop database :**  
  
  
  
`msfdb stop`  
  
  
  
That's all! See you.