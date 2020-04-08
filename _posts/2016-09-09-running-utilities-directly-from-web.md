---
title: 'Running the utilities directly from the web'
date: 2019-11-05T14:26:00+01:00
draft: false
---

#### Running the utilities directly from the web

[](https://www.blogger.com/u/1/null)Sysinternals Live is a service that enables you to execute Sysinternals utilities directly from the Web without first having to hunt for, download, and extract them. Another advantage of Sysinternals Live is that it guarantees you run the latest versions of the utilities.

[](https://www.blogger.com/u/1/null)To run a utility using Sysinternals Live from Internet Explorer, type **http://live.sysinternals.com/_utilityname_.exe**[](https://www.blogger.com/u/1/null) in the address bar (for example, http://live.sysinternals.com/procmon.exe). Alternatively, you can specify the Sysinternals Live path in UNC as **\\\\live.sysinternals.com\\tools\\_utilityname_.exe**[](https://www.blogger.com/u/1/null). (Note the addition of the “tools” subdirectory, which is not required when you specify a utility’s URL.) For example, you can run the latest version of Process Monitor by running **\\\\live.sysinternals.com\\tools\\procmon.exe**.

* * *

  

[](https://www.blogger.com/u/1/null)The UNC syntax for launching utilities using Sysinternals Live requires that the WebClient service be running. In newer versions of Windows, the service might not be configured to start automatically. Starting the service directly (for example, by running **net start webclient**[](https://www.blogger.com/u/1/null)) requires administrative rights. You can start the service indirectly without administrative rights by running **net use \\\\live.sysinternals.com** from a command prompt or by browsing to _\\\\live.sysinternals.com_ with Windows Explorer.

* * *

[](https://www.blogger.com/u/1/null)You can also map a drive letter to \\\\live.sysinternals.com\\tools or open the directory as a remote share in Windows Explorer, as shown in [Figure 1-6](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/9780133986549/ch01lev2sec2_html#ch01fig06)[](https://www.blogger.com/u/1/null). Similarly, you can view the entire Sysinternals Live directory in a browser at _[http://live.sysinternals.com](http://live.sysinternals.com/)_.

![Image](https://proquest-safaribooksonline-com.eztncc.vccs.edu:2443/getfile?item=Nzk4ZGFncnBjbTUxc3NpczAvL2UzNHQzNmE5OC85MTBmZWhpcy90cGdnYXNyaS9jNmdwMGou)

[](https://www.blogger.com/u/1/null)**FIGURE 1-6**[](https://www.blogger.com/u/1/null) Sysinternals Live displayed in Windows Explorer.