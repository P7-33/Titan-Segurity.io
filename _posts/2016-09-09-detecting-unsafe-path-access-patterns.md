---
title: 'Detecting unsafe path access patterns with PathAuditor'
date: 2019-12-09T15:46:00+01:00
draft: false
---

Posted by Marta Rożek, Google Summer Intern 2019, and Stephen Röttger, Software Engineer   
  
**#!/bin/sh  
cat /home/user/foo**  
  
What can go wrong if this command runs as root? Does it change anything if foo is a symbolic link to /etc/shadow? How is the output going to be used?  
  
Depending on the answers to the questions above, accessing files this way could be a vulnerability. The vulnerability exists in syscalls that operate on file paths, such as open, rename, chmod, or exec. For a vulnerability to be present, part of the path has to be user controlled and the program that executes the syscall has to be run at a higher privilege level. In a potential exploit, the attacker can substitute the path for a symlink and create, remove, or execute a file. In many cases, it's possible for an attacker to create the symlink before the syscall is executed.  
  
At Google, we have been working on a solution to find these potentially problematic issues at scale: PathAuditor. In this blog post we'll outline the problem and explain how you can avoid it in your code with PathAuditor.  
  
Let’s take a look at a real world example. The [tmpreaper](http://manpages.ubuntu.com/manpages/bionic/man8/tmpreaper.8.html) utility contained the following code to check if a directory is a mount point:  
**if ((dst = malloc(strlen(ent->d\_name) + 3)) == NULL)**  
**       message (LOG\_FATAL, "malloc failed.\\n");  
strcpy(dst, ent->d\_name);  
strcat(dst, "/X");  
rename(ent->d\_name, dst);  
if (errno == EXDEV) {  
\[...\]**  
  
This code will call rename("/tmp/user/controlled", "/tmp/user/controlled/X"). Under the hood, the kernel will resolve the path twice, once for the first argument and once for the second, then perform some checks if the rename is valid and finally try to move the file from one directory to the other.  
  
However, the problem is that the user can race the kernel code and replace the “/tmp/user/controlled” with a symlink just between the two path resolutions.  
  
A successful attack would look roughly like this:  

*   Make “/tmp/user/controlled” a file with controlled content.
*   The kernel resolves that path for the first argument to rename() and sees the file.
*   Replace “/tmp/user/controlled” with a symlink to /etc/cron.
*   The kernel resolves the path again for the second argument and ends up in /etc/cron.
*   If both the tmp and cron directories are on the filesystem, the kernel will move the attacker controlled file to /etc/cron, leading to code execution as root.

Can we find such bugs via automated analysis? Well, yes and no. As shown in the tmpreaper example, exploiting these bugs can require some creativity and it depends on the context if they’re vulnerabilities in the first place. Automated analysis can uncover instances of this access pattern and will gather as much information as it can to help with further investigation. However, it will also naturally produce false positives.  

  

We can’t tell if a call to open(/user/controlled, O\_RDONLY) is a vulnerability without looking at the context. It depends on whether the contents are returned to the user or are used in some security sensitive way. A call to chmod(/user/controlled, mode) depending on the mode can be either a DoS or a privilege escalation. Accessing files in sticky directories (like /tmp) can become vulnerabilities if the attacker found an additional bug to delete arbitrary files.  
  

**How Pathauditor works**  
To find issues like this at scale we wrote [PathAuditor](https://github.com/google/path-auditor), a tool that monitors file accesses and logs potential vulnerabilities. PathAuditor is a shared library that can be loaded into processes using LD\_PRELOAD. It then hooks all filesystem related libc functions and checks if the access is safe. For that, we traverse the path and check if any component could be replaced by an unprivileged user, for example if a directory is user-writable. If we detect such a pattern, we log it to syslog for manual analysis.  
  
Here's how you can use it to find vulnerabilities in your code:  

*   LD\_PRELOAD the library to your binary and then analyse its findings in syslog. You can also add the library to /etc/ld.so.preload, which will preload it in all binaries running on the system.
*   It will then gather the PID and the command line of the calling process, arguments of the vulnerable function, and a stack trace -- this provides a starting point for further investigation. At this point, you can use the stack trace to find the code path that triggered the violation and manually analyse what would happen if you would point the path to an arbitrary file or directory.
*   For example, if the code is opening a file and returning the content to the user then you could use it to read arbitrary files. If you control the path of chmod or chown, you might be able to change the permissions of chosen files and so on.

PathAuditor has proved successful at Google and we're excited to share it with the community. The project is still in the early stages and we are actively working on it. We look forward to hearing about any vulnerabilities you discover with the tool, and hope to see pull requests with further improvements.

  

Try out the PathAuditor tool [here](https://github.com/google/path-auditor).  

  

_Marta Rożek was a Google Summer intern in 2019 and contributed to this blog and the PathAuditor tool_

  

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=x8GvBFiKHlA:gAEVKUX4Tl8:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=x8GvBFiKHlA:gAEVKUX4Tl8:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=x8GvBFiKHlA:gAEVKUX4Tl8:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/x8GvBFiKHlA)  
  
from Google Online Security Blog https://ift.tt/36jOKoN  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)