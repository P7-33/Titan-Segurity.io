---
title: 'Aura-Botnet'
date: 2019-10-04T15:58:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-1eybXSinYH4/XXz_OvszFGI/AAAAAAAAQU8/mPPGm2TPXa0MiXAYAiEUlpjCOpTYjDAoACNcBGAsYHQ/s640/botnet.jpg)](https://1.bp.blogspot.com/-1eybXSinYH4/XXz_OvszFGI/AAAAAAAAQU8/mPPGm2TPXa0MiXAYAiEUlpjCOpTYjDAoACNcBGAsYHQ/s1600/botnet.jpg)

**Aura-Botnet - A Super Portable Botnet Framework With A Django-based C2 Server**

**Aura Botnet**

  
**C2 Server**  
The botnet's C2 server utilizes the [Django](https://www.kitploit.com/search/label/Django "Django") framework as the backend. It is far from the most efficient web server, but this is offset by the following:  

*   Django is extremely portable and therefore good for testing/educational purposes. The server and database are contained within the [`aura-server`](https://github.com/watersalesman/aura-botnet/blob/master/aura-server "A super portable botnet framework with a Django-based C2 server. The client is written in C++, with alternate clients written in Rust, Bash, and Powershell. (5)") folder.
*   Django includes a very intuitive and powerful admin site that can be used for managing bots and commands
*   The server is only handling simple POST requests and returning text
*   Static files should be handled by a separate web server (local or remote) that excels in serving static files, such as nginx

The admin site located at `[http://your_server:server_port/admin](http://your_server:server_port/admin)` can be accessed after setting up a superuser (see below).  
[](https://www.blogger.com/u/1/null)

[  
](https://www.blogger.com/u/1/null)

  

  
**Database**  
The C2 server is currently configured to use a SQLite3 database, `bots.sqlite3`. The current configuration can be changed in [`aura-server/aura/settings.py`](https://github.com/watersalesman/aura-botnet/blob/master/aura-server/aura/settings.py "A super portable botnet framework with a Django-based C2 server. The client is written in C++, with alternate clients written in Rust, Bash, and Powershell. (6)"). You may wish to use MySQL, or even [PostgreSQL](https://www.kitploit.com/search/label/PostgreSQL "PostgreSQL") instead; this easy to do thanks to Django's portable database API.  
  
**Bot Clients**  
The primary client is written in C++, and can be compiled for either Linux or Windows using CMake. Alternate clients are written in Rust, Bash, and Powershell, but are may lack certain functionality as they are mostly unsupported. I will fix any major bugs that come to my attention, but they will continue to lack certain features for the time being, such as running commands in different shells.  
The client will gather relevant system information and send it to the C2 server to register the new bot. Identification is done by initially creating a file containing random data -- referred to as the _auth file_ throughout the code -- which will then be hashed each time the client runs to identify the client and authenticate with the C2 server. It will then install all the files in the folder specified in the code, and initialize the system service or schedule a task with the same privileges that the client was run with. The default settings have the client and other files masquerading as configuration files.  
  
**Getting Started: C2 Server**  
[Read documentation here](https://github.com/watersalesman/aura-botnet/blob/master/docs/c2-server.md "Read documentation here")  
  
**Geting Started: Bot Clients**  
[Read documentation here](https://github.com/watersalesman/aura-botnet/blob/master/docs/bot-client.md "Read documentation here")  
  
**Other Notes**  
Because this is for [testing](https://www.kitploit.com/search/label/Testing "testing") purposes, the C2 server needs to be hard-coded into client and web delivery files. It is currently set to _localhost_ on all the files. This is because an actual [botnet](https://www.kitploit.com/search/label/Botnet "botnet") would use something like a domain generation algorithm (DGA) to sync a stream of changing domains on the client side with a stream of disposable domains being registered -- or just really bulletproof hosting like the original Mirai botnet.  
The code is also not obfuscated nor is there any effort put toward preventing reverse engineering; this would defeat the purpose of being a botnet for testing and demonstrations.  
The _killswitch_ folder contains [scripts](https://www.kitploit.com/search/label/Scripts "scripts") for easy client removal when testing on your devices.  
  
**This tool is for testing/demonstration purposes only. This is not meant to be implemented in any real world applications except for testing on authorized machines.**  
  
  

**[Download Aura-Botnet](http://eunsetee.com/DQBW "Download Aura-Botnet")**

**Regards**

**Kang Asu**