---
title: 'I hate Xlib and so should you'
date: 2019-10-16T07:22:00+01:00
draft: false
---

I hate Xlib and so should you
=============================

For over 20 years, Xlib has been at the heart of most graphical applications and user interface frameworks on Unices, including GNU/Linux. It is also knows as libX11, the actual name of the shared library in the file system.

Unfortunately - and given its age, perhaps unsurprisingly - it suffers from some rather troublesome limitations and designs mistakes. This brought a few smart developers to create [XCB, the X C Bindings](http://xcb.freedesktop.org/), a _better_ library around the X11 window system protocol. Nevertheless, 7 years after the inception of XCB, Xlib remains the dominant library to use X11 to this day.

* * *

Error handling
--------------

Error handling is certainly the most obvious annoyance when programming Xlib. Of all the software libraries I know, Xlib is the one with the most confusing (or maybe confused?) and inflexible error handling scheme. First, Xlib assumes that any error is **fatal** by default. Practically, any error will cause the entire process to abort, where most libraries choose to simply return an error value. Unhandled Xlib errors look like this error messages:

> ```
>  X Error of failed request: BadMatch (invalid parameter attributes) Major opcode of failed request: 145 (MIT-SHM) Minor opcode of failed request: 4 (X\_ShmGetImage) Serial number of failed request: 10 Current serial number in output stream: 12 
> ```

... and then the program exits immediately.

To catch errors and handle them other than by an early exit, two functions are provided:

> ```
>  int (\*XSetErrorHandler(int (\*handler)(Display \*, XErrorEvent \*)))(); int (\*XSetIOErrorHandler(int (\*handler)(Display \*)))(); 
> ```

Those prototypes (straight from the Xlib documentation) look a bit confusing. Both functions accept a function pointer as parameter and return a function pointer of the same type, which is the previous error handler. The following equivalent prototypes are easier to read:

> ```
>  typedef int (\*XErrorHandler)(Display \*, XErrorEvent \*); typedef int (\*XIOErrorHandler)(Display \*); XErrorHandler XSetErrorHandler(XErrorHandler handler); XIOErrorHandler XSetIOErrorHandler(XIOErrorHandler handler); 
> ```

`XSetIOErrorHandler` sets the handler for I/O errors, which is to say for when the connection with the X server fails. Most programs want to quit when this happens, which Xlib does. Still, a callback is not exactly the most convenient place to perform last minute operations, such as saving user data, before exiting.

`XSetErrorHandler` is more commonly used; it handles X11 protocol errors. It seems, Xlib developers felt that any protocol error would be a bug and therefore the application should exit with an error message like above. There are however cases where not triggering an X error can be hard or even impossible. For instance, attaching a shared memory segment (`XShmAttach`) [can always fail](https://www.remlab.net/op/mit-shm.shtml), and it always does fail when using X network transparency through SSH. Handling such an error is really tedious. First, because Xlib is asynchronous, the error is reported by the server to Xlib and then passed to the error callback some time after the failed request was made, whenever the first one of the following occurs:

*   `XSync()` is invoked,
*   another X11 request is later made that expects some data in the response, such as `XGetWindowAttributes()`, `XGetGeometry()`, `XGetWindowProperty()`, etc.
*   `XFlush()` is invoked and the X event loop is iterated times enough.

In principles, the `XErrorEvent` can be matched to a specific request through the serial number, but Xlib does not provide sufficient informations to leverage this. Instead, the programmer has to guess from the major and minor opcode what the request was. If using an X extension such as MIT-SHM, the program needs to keep track of the extension opcode manually, as they are dynamically allocated by the X server when it is started (MIT-SHM provides `XShmQueryVersion` for this purpose).

### Multiple displays

But first, a well behaved X11 error handler needs to check which `Display` generated the error, because the Xlib error handler is set per process, not per display. In the good old days, most applications could assume that they had only one display in their process space. The main user interface toolkit, e.g. Qt, GTK, would create the only display connection. But this is not so true anymore:

*   Media frameworks such as LibVLC or gstreamer need to create their own displays for rendering,
*   Rendering libraries like Cairo, EGL, SDL also create their own connection,
*   Even non-graphical libraries like PulseAudio or D-Bus create short-lived display connections to identify the session that they run in, and connect to the right instance of the corresponding daemon.

And then, the error handler need to pass the error down to the previous error handler that might have been registered by another component, as returned by `XSetErrorHandler()` earlier.

If you are smart and fast, you might already have found a **major flaw**. To unregister an error handler, `XSetErrorHandler()` is called a second time with the previous return value as parameter, just like with the POSIX `signal()` function. And just like POSIX signal handlers, this cannot work unless the handlers are unregistered in the exact reverse order that they were registered.

### Multiple threads

The error handling functions are atomic, or at least can be configured to behave so. Even then, the error events are not locked. Therefore, there is always a risk that an error in one thread triggers an undefined situation in the error handler of another thread. If you think this might still work, I humbly advise that you refresh your knowledge on the topic of the POSIX threaded memory model, until you understand why it cannot operate safely.

> As the VLC bug master, I can tell that has been one of the worse crash source on VLC for GNU/Linux. Fortunately, we have now fixed the problem: We got rid of Xlib and used XCB wherever we needed X11 error handling. And if multiple threads are involved, there is more-or-less no safe way to an error handler at all.

### Comparison to XCB

In XCB, error handling is extremely simple. For each X11 protocol request, two functions are provided: one that ignores the result, and one that keeps it. Request functions return an unique cookie (the request serial number), that is passed to a reply function to fetch the result.

If you want to make a single request/response, the code can be as simple as this:

> ```
> xcb\_xv\_query\_adaptors\_reply\_t \*adaptors; adaptors = xcb\_xv\_query\_adaptors\_reply (conn, xcb\_xv\_query\_adaptors (conn, xid), NULL); if (adaptors == NULL) /\* handle error \*/; 
> ```
> 
> or
> 
> ```
>  xcb\_generic\_error\_t \*err; xcb\_void\_cookie\_t ck; ck = xcb\_create\_window\_checked (conn, depth, xid, parent\_xid, 0, 0, width, height, 0, XCB\_WINDOW\_CLASS\_INPUT\_OUTPUT, visual, mask, list); err = xcb\_request\_check (conn, ck); if (err != NULL) { fprintf (stderr, "%s: X11 error %d", str, err->error\_code); free (err); /\* Handle error \*/ } 
> ```

It is however recommended that multiple requests get made consecutively, and then all replies fetched in the same order. This reduces latency, dramatically so if network transparency is in use.

* * *

Thread support
--------------

Xlib provides two groups of functions for multi-thread use:

> ```
>  /\* Thread-safety for global data \*/ Status XInitThreads(void); /\* Thread-safety for an individual display \*/ void XLockDisplay(Display \*display); void XUnlockDisplay(Display \*display); 
> ```

`XInitThreads()` is the most important, and is required for the later two functions to work anyway. `XLockDisplay()` and `XUnlockDisplay()` provide a recursive lock for the unlikely event that a single display is shared across multiple threads, which is generally a bad idea and not terribly useful.

`XInitThreads()` initializes thread callbacks inside Xlib, and protects the global data within Xlib, such as internationalization stuff. Much like most libraries with a similar function, the function can be called multiple times, but it is not re-entrant: the first caller in the lifetime of the process must be the only concurrent caller. Effectively, the beginning of the `main()` function is the only really safe place to call `XInitThreads()`.

However, most real-life programs access Xlib through higher-level libraries, and the libraries do not initialize Xlib threading on their behalf. **Today, most programs with multiple X11 connections and multiple threads are buggy.**

### Consequences

If `XInitThreads()` is not called anywhere in a multi-tasked program, the program will usually work. But weird crashes and other race conditions are bound to happen over time, as Xlib maintains some global data that is shared across all threads and all "displays".

If `XInitThreads()` is called too late, then the process **will crash**, but only some time later in obscure ways. In my experience, the most common case is for the process to hit a segmentation fault within `XCloseDisplay()`, which usually happens at exit.

### Comparison with XCB

XCB is always thread-safe. It always uses POSIX threads internally. In addition, it is usually linked with pthread-stubs to avoid the POSIX threads overhead in single thread programs. This keeps everybody happy.

  
  
from Hacker News https://ift.tt/2OUwwEP