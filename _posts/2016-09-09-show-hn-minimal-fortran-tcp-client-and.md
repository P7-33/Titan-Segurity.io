---
title: 'Show HN: A minimal Fortran TCP client and server'
date: 2019-10-31T01:12:00+01:00
draft: false
---

![](https://avatars3.githubusercontent.com/u/33155798?s=400&v=4 "GitHub - modern-fortran/tcp-client-server: A minimal Fortran TCP client and server")  

[](https://github.com/modern-fortran/tcp-client-server#tcp-client-server)tcp-client-server
==========================================================================================

A minimal TCP client and server in Fortran, used to teach interoperability with C. Companion code for Chapter 11 of [Modern Fortran: Building Efficient Parallel Applications](https://www.manning.com/books/modern-fortran?a_aid=modernfortran&a_bid=2dc4d442).

It uses [libdill](http://libdill.org) as a sockets library.

[](https://github.com/modern-fortran/tcp-client-server#getting-started)Getting started
--------------------------------------------------------------------------------------

Download and build the code:

```
git clone https://github.com/modern-fortran/tcp-client-server cd tcp-client-server make 
```

[](https://github.com/modern-fortran/tcp-client-server#running-the-server)Running the server
--------------------------------------------------------------------------------------------

In one terminal window, run the server:

```
./server Listening on socket: IP address: 127.0.0.1 Port: 5555 
```

[](https://github.com/modern-fortran/tcp-client-server#running-the-client)Running the client
--------------------------------------------------------------------------------------------

In another terminal window, run the client:

```
./client 5 Hello 
```

On client connection, the server will report:

```
 New connection from 127.0.0.1 
```

  
  
from Hacker News https://github.com/modern-fortran/tcp-client-server