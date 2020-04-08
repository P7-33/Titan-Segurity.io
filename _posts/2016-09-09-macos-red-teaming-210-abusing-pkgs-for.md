---
title: 'MacOS Red Teaming 210: Abusing Pkgs for Privilege Escalation'
date: 2019-10-11T17:16:00+01:00
draft: false
---

Hey all, this is going to be a shorter post as this is a well explored technique so I'm going to try to point to a lot of existing research. This technique also generally relies on vulnerable third party apps, so it can take a bit of hunting to find a good example. I have a simple example at the end but I wanted to cover the technique because it's useful when auditing third party apps in a software review. A lot of what I'm going to discuss here abuses a security auth trampoline, such that when a user goes to enter thier credentials for a privileged installer a malicious actor can take advantage of that elevated execution for privilege escalation. Specifically we are going to look at abusing .pkg files, the default file format for the Installer application on macOS. Patrick Wardle talked about it at DefCon 25 in excruciating depth, talking about the exact API calls many installer applications make. I link to his talk at the end, but at a high level we can examine .pkg files and see if they have any [TOCTOU installer vulnerabilities](https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use) that an attacker can leverage at run time to escalate privileges. [Jaron Bradley covered the same techniques at OBTS2](https://objectivebythesea.com/v2/talks/OBTS_v2_Bradley.pdf) this year, focusing more on the package structure. This post is much more inline with his technique, so I urge you to checkout his example. But today I am going to pull largely from a presentation I saw by [Andy Grant (a VP w/ NCC Group) this year at BSidesLV](https://media.defcon.org/DEF%20CON%2027/DEF%20CON%2027%20presentations/DEFCON-27-Andy-Grant-Unpacking-pkgs.pdf).  
  
The key to successfully understanding what's inside of a .pkg file is first understanding the package file structure. There are commands to deflate the package below, or you could use _pkgutil --expand_ command. Next you may want to check the Distribution XML to understand if there are any special execution conditions. Following that, checking the PackageInfo will let you know which scripts or resources will be executed along with the payload location. Finally, analyzing the exact content of the payloads or scripts within is often the most valuable step. Many times the scripts will copy and execute files from locations with insecure permissions, creating a race condition and an opportunity for privilege escalation. Andy Grant gave us all of these structures, commands, and several different examples in his awesome presentation, so I'm going to provide them as a cheat sheet below:  
  

[![](https://1.bp.blogspot.com/-XoI4I5WNBR8/XZ6t2Jxv7CI/AAAAAAAAKnk/WC6xm3UnF2UvBV7UF_0vDeK_Wy3iUbdqgCLcBGAsYHQ/s640/pkg_structure.png)](https://1.bp.blogspot.com/-XoI4I5WNBR8/XZ6t2Jxv7CI/AAAAAAAAKnk/WC6xm3UnF2UvBV7UF_0vDeK_Wy3iUbdqgCLcBGAsYHQ/s1600/pkg_structure.png)

  
**Expand the package:**  
_xar -xf "/path/to/package.pkg" -C "/path/to/extract/to/"_  
  
**Expand the payload or script:**  
_cpio -i < Payload_  
  

[![](https://1.bp.blogspot.com/-F2Oy2M1ajMg/XZ6v1T15sBI/AAAAAAAAKnw/aoKFg6-0h9M2-JBJuAV9GaD-qsZTCsSGwCLcBGAsYHQ/s640/pkg_order_of_operations.png)](https://1.bp.blogspot.com/-F2Oy2M1ajMg/XZ6v1T15sBI/AAAAAAAAKnw/aoKFg6-0h9M2-JBJuAV9GaD-qsZTCsSGwCLcBGAsYHQ/s1600/pkg_order_of_operations.png)

  
Again, a large part of the analysis involves analyzing the scripts or payloads embedded in the pkg. Often the preinstall or postinstall scripts will either write or execute files from temporary locations or locations with writable file permissions. Another good trick to stop the installer from overwriting a file you've placed is by making the file immutable like so:  
_chflags uchg "/path/to/file"_  
  
We can use that trick to exploit the example below. Below we have a postinstall script from a pkg that installs some additional 3rd party tools at the end. Unfortunately, by writing and installing tools from /tmp/ the script is vulnerable to this style of TOCTOU privilege escalation. We can use the above trick to make /tmp/nmap.dmg an immutable file that we've placed in /tmp/, then the curl in the postinstall script will fail but the rest of the script will still run, after the user has already authenticated as an Administrator, thus installing our dmg as root.  
  

[![](https://1.bp.blogspot.com/-D3n3GQt1t1E/XaCl6d7WZeI/AAAAAAAAKoE/cYUx5ZmXTooBnb_AEtPoHfsmSVxxllE7QCLcBGAsYHQ/s640/vuln_postinstall.png)](https://1.bp.blogspot.com/-D3n3GQt1t1E/XaCl6d7WZeI/AAAAAAAAKoE/cYUx5ZmXTooBnb_AEtPoHfsmSVxxllE7QCLcBGAsYHQ/s1600/vuln_postinstall.png)

  
If the recordings were out I would link Andy Grant's talk, but I couldn't find a good copy on YouTube. In the mean time, checkout this wild presentation by Patrick Wardle where he looks at very similar privilege escalations dynamically, from a debugging perspective. He also breaks SIP at one point, which is pretty interesting to watch: