---
title: 'Checking for Stack Overflow at
Runtime #Programming #Debugging @McuOnEclipse'
date: 2019-10-21T14:53:00+01:00
draft: false
---

![MCU on Eclipse](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-74.png)

[Erich Styger](https://mcuoneclipse.com/author/mcuoneclipse/ "View all posts by Erich Styger") on [MCU on Eclipse writes](https://mcuoneclipse.com/2019/09/28/stack-canaries-with-gcc-checking-for-stack-overflow-at-runtime/) about using stack canaries with the GCC compiler to check for stack overflow at runtime.

> Stack overflows are probably the number 1 enemy of embedded applications: a call to a a printf() monster likely will use too much stack space, resulting in overwritten memory and crashing applications. But stack memory is limited and expensive on these devices, so you don’t want to spend too much space for it. But for sure not to little too. Or bad things will happen.
> 
> The problem is that application call stack (function calls, pushing parameters and using local variables) is growing into one direction. If the reserved stack space is not large enough, the call stack space can grow into the other memory area and corrupt data.

The article lists different ways to deal with this:

*   **Static Analysis**. Making a good analysis how much stack is needed. Recursion can be a problem.
*   Using **MPU** (Hardware Memory Protection) to detect and protect the overflow
*   Using** hardware ****watchpoints** to detect the overwrite
*   Place **sentinel** **values** at the end of the stack space which are periodically checked

The last option is what can be turned on in FreeRTOS.

#### Security

> There is another problem especially when considering security: arbitrary code execution causing a stack overflow/corruption with the goal to take control over the system. These are called ‘stack overflow exploits’. See [http://phrack.org/issues/49/14.html](http://phrack.org/issues/49/14.html) for a good tutorial on this concept (and if you want to get into the hacking business  ).
> 
> To counter these exploits, compilers including the gcc started to add ‘hardening’ options to detect these exploits. One of it is the GNU gcc StackGuard (see[ ftp://gcc.gnu.org/pub/gcc/summit/2003/Stackguard.pdf](ftp://gcc.gnu.org/pub/gcc/summit/2003/Stackguard.pdf)). In that approach, the compiler is placing a ‘canary’ guard into each instrumented function stack frame.

The gcc compiler provides a set of options to use canaries (see [https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html)).

> **\-fstack-protector**: Emit extra code to check for buffer overflows, such as stack smashing attacks. This is done by adding a guard variable to functions with vulnerable objects. This includes functions that call alloca, and functions with buffers larger than 8 bytes. The guards are initialized when a function is entered and then checked when the function exits. If a guard check fails, an error message is printed and the program exits.
> 
> **\-fstack-protector-all**: Like -fstack-protector except that all functions are protected.

[See the article](https://mcuoneclipse.com/2019/09/28/stack-canaries-with-gcc-checking-for-stack-overflow-at-runtime/) on how things are implemented.

![__stack_chk_guard](https://mcuoneclipse.files.wordpress.com/2019/09/stack_chk_guard.png?w=584&h=224)