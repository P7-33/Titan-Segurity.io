---
title: 'what is docker run -it flag?'
date: 2019-11-03T18:14:00+01:00
draft: false
---

  

===

  

`docker run -it ubuntu:xenial /bin/bash` starts the container in the interactive mode (hence `-it` flag) that allows you to interact with `/bin/bash` of the container. That means now you will have `bash` session _inside_ the container, so you can `ls`, `mkdir`, or do any bash command inside the container.

The key here is the word "interactive". If you omit the flag, the container still executes `/bin/bash` but exits immediately. With the flag, the container executes `/bin/bash` then patiently waits for your input.

[share](https://stackoverflow.com/a/48368598/7565545 "short permalink to this answer")[edit](https://stackoverflow.com/posts/48368598/edit "revise and improve this post")

answered Jan 21 '18 at 15:47

[

![](https://i.stack.imgur.com/tUV0d.jpg?s=32&g=1)

](https://stackoverflow.com/users/1032340/dvnguyen)

[dvnguyen](https://stackoverflow.com/users/1032340/dvnguyen)

1,8311010 silver badges20