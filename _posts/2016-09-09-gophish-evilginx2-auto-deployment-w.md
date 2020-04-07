---
title: 'GoPhish & Evilginx2 Auto-Deployment w/ Phish Composer'
date: 2020-01-25T03:34:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-iGz3DPmYJjM/Xiq6psKfqRI/AAAAAAAALN0/Bi6L9bC6RFYnG1uFT6wo2K5cFjiwrJOOACLcBGAsYHQ/s320/phish_composer.jpg)](https://1.bp.blogspot.com/-iGz3DPmYJjM/Xiq6psKfqRI/AAAAAAAALN0/Bi6L9bC6RFYnG1uFT6wo2K5cFjiwrJOOACLcBGAsYHQ/s1600/phish_composer.jpg)

This is a quick post on automating the deployment of some [phishing technology we previously covered on this blog](http://lockboxx.blogspot.com/2018/12/gophish-evilginx2-for-phishing.html). This solution uses docker-compose to deploy three docker images. The three major components of our phishing framework are gophish, evilginx2, and a postfix proxy. Before you start, this solution relies on [docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and [docker-compose](https://docs.docker.com/compose/install/), so you will need to have those. The project is called [phish\_composer](https://github.com/ahhh/phish_composer), which has the docker-compose file and many configuration files you will want to deploy this setup automatically. Some more quick prerequisite notes before you try to deploy this: If your using Linux that uses systemd, you may have to disable [systemd-resolved](https://www.freedesktop.org/software/systemd/man/systemd-resolved.service.html) first. This is so that [evilginx2 can start its DNS server](https://github.com/kgretzky/evilginx2/issues/125) on 53. You will also need a mail sender account, like mailgun or sendgrid. These details will go into your postfix configuration, in the [docker-compose.yml](https://github.com/ahhh/phish_composer/blob/master/docker-compose.yml#L46) file. Likewise you will need to register the phishing domains for your mailing address and landing pages.  
  
This solution will only deploy your basic docker containers, you still need to configure many of the services to talk to one another in the applications. If you want to test the solution without completely configuring things, [remove the comment that adds the developer flag](https://github.com/ahhh/phish_composer/blob/master/docker-compose.yml#L30). Granted this solution can be fully automated and configured by yaml files without interacting with the deployment.  The following are your key configuration files, where much of the specific configuration can be done:  
  
[docker-compose.yml](https://github.com/ahhh/phish_composer/blob/master/docker-compose.yml#L48) - This is the most important file. The only configuration this file requires is adding your mail sender account details and your phishing domain if you wish to route through postfix and your mail provider.   
  
[gophish.db](https://github.com/ahhh/phish_composer/tree/master/gophish) - This will be the persistent gophish database which will store your users, targets, and results. It uses the default credentials but can store your changes across various docker deployments by mounting the same database, giving you a bit of persistence in your stats across deployments and operations.  
[  
](https://www.blogger.com/u/1/goog_1562128923)[config.yaml](https://github.com/ahhh/phish_composer/blob/master/evilginx2/config.yaml) - This will be the general evilginx2 configuration file, which will include things like your IP, domain, and any phishlets you want enabled. This can be used to deploy evilginx2 in a totally automated fashion.  
  
[custom\_phishlet.yaml](https://github.com/ahhh/phish_composer/tree/master/evilginx2/phishlets) - This is for any custom configured phishlets you have set up that you want use with evilginx2. By default the stock phishlets are added to evilginx2 but often you will want to customize your landing page for your specific domains.  
[  
](https://github.com/ahhh/phish_composer/blob/master/postfix/header_checks)[header\_checks](https://github.com/ahhh/phish_composer/blob/master/postfix/header_checks) - This is a regex file that postfix will check and strip headers from before sending email. You can put custom checks in here, but the defaults should work well.  
  
Finally, spinning this all up is as simple as:  
```
sudo docker-compose up -d  
sudo docker ps
```Enjoy! Let me know what you think, and as always pull requests and improvements are welcome!