---
title: 'Kore4 and Python'
date: 2019-11-16T06:34:00+01:00
draft: false
---

Kore4 and Python
----------------

2019-11-14

The upcoming Kore release is going to drastically change how you can run your Python applications. Before, you had to jump through a few hoops, fight a few dragons and pray to some deity in the hopes to get it up and running. You would be struggling with how to create the application, managing a separate Kore configuration file, etc.

With Kore4, you will be able to launch your Kore Python applications directly as an argument to the kore binary. And better yet, you can skip the entire configuration file and setup everything you need directly from inside your Kore Python application.

  

A simple web application
------------------------

Let us take a look at an example of a simple Kore4 Python web application.

```
 import kore class App: def configure(self, args): kore.config.deployment = "dev" kore.server("default", ip="127.0.0.1", port="8888", tls=False) d = kore.domain("*", attach="default") d.route("/", self.index, methods=["get"]) d.route("^/([a-z]+)$", self.group, methods=["get"]) def index(self, req): req.response(200, 'hello world') async def group(self, req, name): await kore.suspend(1000) req.response(200, name.encode()) koreapp = App() 
```

Nice, short and concise. So how do we run this? Easy, with Kore4 you can pass your script or module directly to the kore binary and it will load it:

```
 $ kore app.py [parent]: deployment set to dev [parent]: default serving http on 127.0.0.1:8888 [parent]: privsep: no root path set, using working directory [parent]: privsep: will not change user [parent]: privsep: no keymgr_root set, using 'root` directory [parent]: privsep: will not chroot [parent]: kore is starting up [parent]: python built-in enabled [wrk 1]: worker 1 started (cpu#1, pid#16107) [wrk 2]: worker 2 started (cpu#2, pid#16108) [wrk 3]: worker 3 started (cpu#3, pid#16109) [wrk 4]: worker 4 started (cpu#0, pid#16110) 
```  

Another example
---------------

Kore implements await/async for a lot of things such as [sockets](https://docs.kore.io/3.3.1/api/python.html#asyncsocket), [queues](https://docs.kore.io/3.3.1/api/python.html#asyncqueue), [locks](https://docs.kore.io/3.3.1/api/python.html#asynclock), [http requests](https://docs.kore.io/3.3.1/api/python.html#httpclient), [pgsql queries](https://docs.kore.io/3.3.1/api/python.html#pgsql), etc. Let us take a look at how easy it is to write a simple TCP echo server in Kore.

```
 import kore import socket class EchoServer: def configure(self, args): kore.config.deployment = "dev" kore.config.workers = 1 s = socket.socket(socket.AF_INET, socket.SOCK_STREAM, 0) s.setblocking(False) s.bind(("127.0.0.1", 8888)) s.listen() self.sock = kore.socket_wrap(s) kore.task_create(self.run()) async def run(self): while True: client = await self.sock.accept() kore.task_create(self.handle(client)) async def handle(self, client): while True: data = await client.recv(1024) if not data: break await client.send(data) koreapp = EchoServer() 
```

Now we can run it in the same way as before:

```
 $ kore echo.py 
```  

Python and Seccomp
------------------

If you are running on Linux, Kore will be using seccomp to disallow system calls that it does not require. Via the koreapp.seccomp hook you can extend this list and either allow or disallow additional system calls.

The hook will receive a kore seccomp object that has methods for altering the filter list. Your filters are always loaded before the default Kore seccomp filters, allowing you to override them as you see fit. (The default whitelist is strict and enough to cover the most normal use cases).

For example, if you want to deny your Python code from touching your file system you could do something like this:

```
 import kore class App: ... def seccomp(self, seccomp): seccomp.deny("open") seccomp.deny("openat") seccomp.deny("mkdir") seccomp.deny("mkdirat") ... koreapp = App() 
```

This will make those system calls fail with an EACCESS errno. A lot more ways exist for filtering system calls. You can for example deny certain system calls if they are called with a given mask or flag value (eg: deny open if called with O\_CREAT). These will be documented in the upcoming Kore4 release its documentation.

  

Automatic x509s via ACME
------------------------

The [ACME support coming in Kore4](https://blog.kore.io/posts/automagic-x509s-via-acme) can of course be enabled via the Python API.

```
 import kore class Acme: def configure(self, args): kore.config.deployment = "dev" kore.config.tls_dhparam = "dh2048.pem" kore.server("default", ip="127.0.0.1", port="8888") d = kore.domain("hackers.coma.one", attach="default", acme=True) d.route("/", self.index, methods=["get"]) def index(self, req): req.response(200, b'hi') koreapp = Acme() 
```

Running this will let Kore automatically create/renew the x509s for the configured domains with the configured ACME provider (Let's Encrypt by default), all while privilege separated.

I believe all of this will make it so that Kore4 will massively improve your experience with its Python API. These improvements would not have been possible without the support of my employer, [Tutus Data](https://www.tutus.se). We develop high assurance cryptographic systems for the most demanding customers, and we're [hiring](https://tutus.se/en/jobs).

.joris

  
  
from Hacker News https://ift.tt/376OH0z