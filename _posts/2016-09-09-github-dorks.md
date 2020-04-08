---
title: 'Github-Dorks'
date: 2019-11-16T09:58:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-V3mjPIlUK4U/XbT1z00uWTI/AAAAAAAAQvs/I5pGGvd1eG4t1P3LJhgZ-jetguCBSbZdgCNcBGAsYHQ/s640/github-dorks.png)](https://1.bp.blogspot.com/-V3mjPIlUK4U/XbT1z00uWTI/AAAAAAAAQvs/I5pGGvd1eG4t1P3LJhgZ-jetguCBSbZdgCNcBGAsYHQ/s1600/github-dorks.png)

**Github-Dorks - Collection Of Github Dorks And Helper Tool To Automate The Process Of Checking Dorks**

  

[Github search](https://github.com/search "Github search")is quite powerful and useful feature and can be used to search sensitive data on the repositories. Collection of github dorks that can reveal sensitive personal and/or organizational information such as private keys, credentials, authentication tokens, etc. This list is supposed to be useful for assessing security and performing pen-testing of systems.  
  
**GitHub Dork Search Tool**  
[github-dork.py](https://github.com/techgaun/github-dorks/blob/master/github-dork.py "github-dork.py")is a simple python tool that can search through your repository or your organization/user repositories. Its not a perfect tool at the moment but provides a basic functionality to automate the search on your repositories against the dorks specified in text file.  
  
**Installation**  
This tool uses[github3.py](https://github.com/sigmavirus24/github3.py "github3.py")to talk with GitHub Search API.  
Clone this repository and run:  

```
pip install -r requirements.txt
```

  
**Usage**  
```
GH_USER  - Environment variable to specify github user  
GH_PWD   - Environment variable to specify password  
GH_TOKEN - Environment variable to specify github token  
GH_URL   - Environment variable to specify GitHub Enterprise base URL
```Some example usages are listed below:  

```
python github-dork.py -r techgaun/github-dorks                          # search single repo  
  
python github-dork.py -u techgaun                                       # search all repos of user  
  
python github-dork.py -u dev-nepal                                      # search all repos of an organization  
  
GH_USER=techgaun GH_PWD= python github-dork.py -u dev-nepal     # search as authenticated user  
  
GH_TOKEN= python github-dork.py -u dev-nepal              # search using auth token  
  
GH_URL=[https://github.example.com](https://github.example.com/) python github-dork.py -u dev-nepal    # search a GitHub Enterprise instance
```

  
**Limitations**  

*   Authenticated requests get a higher rate limit. But, since this tool waits for the api rate limit to be reset (which is usually less than a minute), it can be slightly slow.
*   Output formatting is not great. PR welcome
*   Handle rate limit and retry. PR welcome

  
**Contribution**  
Please consider contributing the dorks that can reveal potentially[sensitive information](https://www.kitploit.com/search/label/Sensitive%20Information "sensitive information")in github.  
  
**List of Dorks**  
I am not categorizing at the moment. Instead I am going to just the list of dorks with a description. Many of the dorks can be modified to make the search more specific or generic. You can see more options[here](https://github.com/search#search_cheatsheet_pane "here").  

Dork

Description

filename:.npmrc \_auth

npm[registry](https://www.kitploit.com/search/label/Registry "registry")authentication data

filename:.dockercfg auth

docker registry authentication data

extension:pem private

private keys

extension:ppk private

puttygen private keys

filename:id\_rsa or filename:id\_dsa

private ssh keys

extension:sql mysql dump

mysql dump

extension:sql mysql dump password

mysql dump look for password; you can try varieties

filename:credentials aws\_access\_key\_id

might return false negatives with dummy values

filename:.s3cfg

might return false negatives with dummy values

filename:wp-config.php

wordpress config files

filename:.htpasswd

htpasswd files

filename:.env DB\_USERNAME NOT homestead

laravel .env (CI, various ruby based frameworks too)

filename:.env MAIL\_HOST=smtp.gmail.com

gmail smtp configuration (try different smtp services too)

filename:.git-credentials

git[credentials](https://www.kitploit.com/search/label/Credentials "credentials")store, add NOT username for more valid results

PT\_TOKEN language:bash

pivotaltracker tokens

filename:.bashrc password

search for passwords, etc. in .bashrc (try with .bash\_profile too)

filename:.bashrc mailchimp

variation of above (try more variations)

filename:.bash\_profile aws

aws access and secret keys

[rds.amazonaws.com](http://rds.amazonaws.com/)password

Amazon RDS possible credentials

extension:json api.forecast.io

try variations, find api keys/secrets

extension:json[mongolab.com](http://mongolab.com/)

mongolab credentials in json configs

extension:yaml[mongolab.com](http://mongolab.com/)

mongolab credentials in yaml configs (try with yml)

jsforce extension:js conn.login

possible salesforce credentials in nodejs projects

SF\_USERNAME salesforce

possible salesforce credentials

filename:.tugboat NOT \_tugboat

Digital Ocean tugboat config

HEROKU\_API\_KEY language:shell

Heroku api keys

HEROKU\_API\_KEY language:json

Heroku api keys in json files

filename:.netrc password

netrc that possibly holds sensitive credentials

filename:\_netrc password

netrc that possibly holds sensitive credentials

filename:hub oauth\_token

hub config that stores github tokens

filename:robomongo.json

mongodb credentials file used by robomongo

filename:filezilla.xml Pass

filezilla config file with possible user/pass to ftp

filename:recentservers.xml Pass

filezilla config file with possible user/pass to ftp

filename:config.json auths

docker registry authentication data

filename:idea14.key

IntelliJ Idea 14 key, try variations for other versions

filename:config irc\_pass

possible IRC config

filename:connections.xml

possible db connections configuration, try variations to be specific

filename:express.conf path:.openshift

openshift config, only email and server thou

filename:.pgpass

PostgreSQL file which can contain passwords

filename:proftpdpasswd

Usernames and[passwords](https://www.kitploit.com/search/label/Passwords "passwords")of proftpd created by cpanel

filename:ventrilo\_srv.ini

Ventrilo configuration

\[WFClient\] Password= extension:ica

WinFrame-Client infos needed by users to connect toCitrix Application Servers

filename:server.cfg rcon password

Counter Strike RCON Passwords

JEKYLL\_GITHUB\_TOKEN

Github tokens used for jekyll

filename:.bash\_history

Bash history file

filename:.cshrc

RC file for csh shell

filename:.history

history file (often used by many tools)

filename:.sh\_history

korn shell history

filename:sshd\_config

OpenSSH server config

filename:dhcpd.conf

DHCP service config

filename:prod.exs NOT prod.secret.exs

Phoenix prod configuration file

filename:prod.secret.exs

Phoenix prod secret

filename:configuration.php JConfig password

Joomla configuration file

filename:config.php dbpasswd

PHP application database password (e.g., phpBB forum software)

path:sites databases password

Drupal website database credentials

shodan\_api\_key language:python

Shodan API keys (try other languages too)

filename:shadow path:etc

Contains encrypted passwords and account information of new unix systems

filename:passwd path:etc

Contains user account information including encrypted passwords of traditional unix systems

extension:avastlic "[support.avast.com](http://support.avast.com/)"

Contains license keys for Avast! Antivirus

filename:dbeaver-data-sources.xml

DBeaver config containing MySQL Credentials

filename:.esmtprc password

esmtp configuration

extension:json googleusercontent client\_secret

OAuth credentials for accessing Google APIs

HOMEBREW\_GITHUB\_API\_TOKEN language:shell

Github token usually set by homebrew users

xoxp OR xoxb

Slack bot and private tokens

.[mlab.com](http://mlab.com/)password

MLAB Hosted[MongoDB](https://www.kitploit.com/search/label/MongoDB "MongoDB")Credentials

filename:logins.json

Firefox saved password collection (key3.db usually in same repo)

filename:CCCam.cfg

CCCam Server config file

msg nickserv identify filename:config

Possible IRC login passwords

filename:settings.py SECRET\_KEY

Django secret keys (usually allows for session hijacking, RCE, etc)

filename:secrets.yml password

Usernames/passwords, Rails applications

filename:master.key path:config

Rails master key (used for decrypting`credentials.yml.enc`for Rails 5.2+)

filename:deployment-config.json

Created by sftp-deployment for Atom, contains server details and credentials

filename:.ftpconfig

Created by remote-ssh for Atom, contains SFTP/SSH server details and credentials

filename:.remote-sync.json

Created by remote-sync for Atom, contains FTP and/or SCP/SFTP/SSH server details and credentials

filename:sftp.json path:.vscode

Created by vscode-sftp for VSCode, contains SFTP/SSH server details and credentails

filename:sftp-config.json

Created by SFTP for Sublime Text, contains FTP/FTPS or SFTP/SSH server details and credentials

filename:WebServers.xml

Created by Jetbrains IDEs, contains webserver credentials with encoded passwords ([not encrypted!](https://intellij-support.jetbrains.com/hc/en-us/community/posts/207074025/comments/207034775 "not encrypted!"))

  
  

**[Download Github-Dorks](http://eunsetee.com/mHrI "Download Github-Dorks")**

**  
Regards**

**Kang Asu**