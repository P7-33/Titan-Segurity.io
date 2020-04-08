---
title: 'Nasty PHP7 remote code execution bug exploited in the wild'
date: 2019-10-26T08:48:00+01:00
draft: false
---

![php.png](https://zdnet2.cbsistatic.com/hub/i/2018/10/14/8cb090a5-da9d-47c8-b769-e1a9692a5c62/f012e605ffc8c4319a9923f1cddcf320/php.png)

A recently patched security flaw in modern versions of the PHP programming language is being exploited in the wild to take over servers, ZDNet has learned from threat intelligence firm Bad Packets.

The vulnerability is a remote code execution (RCE) in PHP 7, the newer branch of PHP, the most common programming language used to build websites.

The issue, tracked as [CVE-2019-11043](https://bugs.php.net/bug.php?id=78599), lets attackers run commands on servers just by accessing a specially-crafted URL.

Exploiting the bug is trivial, and public proof-of-concept exploit code has been [published on GitHub](https://github.com/neex/phuip-fpizdam) earlier this week.

"The PoC script included in the GitHub repository can query a target web server to identify whether or not it is vulnerable by sending specially crafted requests," says Satnam Narang, Senior Security Response Manager at Tenable. "Once a vulnerable target has been identified, attackers can send specially crafted requests by appending '?a=' in the URL to a vulnerable web server."

### Only Nginx servers affected

Fortunately, not all PHP-capable web servers are impacted. Only NGINX servers with [PHP-FPM](https://php-fpm.org/) enabled are vulnerable. PHP-FPM, or FastCGI Process Manager, is an alternative PHP FastCGI implementation with some additional features.

However, while PHP-FPM is not a standard component of Nginx installs, some web hosting providers include it as part of their standard PHP hosting environments.

One such case is web hosting provider Nextcloud, who issued [a security advisory](https://nextcloud.com/blog/urgent-security-issue-in-nginx-php-fpm/) to its clients on Thursday, October 24, urging customers to update PHP to the latest release, versions [7.3.11](https://www.php.net/ChangeLog-7.php#7.3.11) and [7.2.24](https://www.php.net/ChangeLog-7.php#7.2.24), which had been released on the same day and included fixes for CVE-2019-11043. Many other web hosting providers are also suspected of running the vulnerable Nginx+PHP-FPM combo.

But there are also website owners who cannot update PHP or can't switch from PHP-FPM to another CGI processor due to technical constraints.

[This blog post](https://lab.wallarm.com/php-remote-code-execution-0-day-discovered-in-real-world-ctf-exercise/) from Wallarm, the company that found the PHP7 RCE, includes instructions on how webmasters can use the standard mod\_security firewall utility to block %0a (newline) bytes in website URLs, and prevent any incoming attacks.

Wallarm credited its security researcher Andrew Danau for discovering the bug during a Capture The Flag (CTF) competition last month.

Due to the availability of public PoC code and the simplicity of exploiting this bug, website owners are advised to check server settings and update PHP as soon as possible if they run the vulnerable configuration.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2MN0bhE