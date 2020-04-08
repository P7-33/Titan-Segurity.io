---
title: 'KTRW: The Journey to Build a Debuggable iPhone'
date: 2019-10-29T05:40:00+01:00
draft: false
---

Posted by Brandon Azad, Project Zero  
  

In my role here at Project Zero, I do not use some of the tooling used by some external iOS security researchers, in particular development-fused iPhones with hardware debugging capabilities like JTAG enabled. I believe that access to such devices puts those who can obtain them at a significant advantage over researchers who can not or do not wish to use them. Thus, early this year I decided I would try to find a way to build such a capability using regular iPhones you can buy at an Apple store. I identified iBoot and KTRR as primary areas for research, and spent several months looking for vulnerabilities.  
  

On June 16th, I [discovered](https://bugs.chromium.org/p/project-zero/issues/detail?id=1900) that the A11 SoC used in the iPhone 8 and iPhone X has the CoreSight External Debug registers enabled. Combined with the capabilities I reversed from a proprietary debugging register called DBGWRAP, this is sufficient to debug the CPU at any time during its operation, including during execution of the reset vector after a core sleeps and before the MMU and KTRR have been re-enabled. By single-stepping execution of the reset vector and modifying register state at key points, it is possible to skip MMU KTRR lockdown and remap protected kernel memory as writable. I used this capability to build a hardware-level single-step kernel debugger for the iPhone X called [KTRW](https://github.com/googleprojectzero/ktrw) that can be used with LLDB and IDA Pro and works with an off-the-shelf Lightning cable.  

This research was conducted before [@axi0mX](https://twitter.com/axi0mX/status/1177542201670168576) released the [checkm8](https://github.com/axi0mX/ipwndfu) iOS SecureROM exploit and is independent of it.

The bootstrapping problem
-------------------------

Doing security research on iPhones is hard, and in my opinion, much harder than it needs to be. Apple has done an impressive job locking down their devices, and while such security improvements are certainly welcome, it does mean that security researchers have to invest a lot of time and effort to create a viable research platform.  
  

The need to maintain a research platform can create perverse incentives for well-intentioned security researchers. One common outcome is that researchers will hoard vulnerabilities, only reporting some while keeping the rest for bootstrapping. This is of course less than ideal, since some of these vulnerabilities could simultaneously be used as 0-days to attack users.  
  

Alternatively, many security researchers are able to acquire development-fused iPhones with hardware debugging features (SWD, JTAG) enabled, allowing them to debug the main Application Processor (AP) and some peripherals like the Always On Processor (AOP) and the Secure Enclave Processor (SEP). By halting execution in the bootloader, it is possible to patch the kernel to disable security features before the kernel has even had a chance to run. This makes these devices extremely useful for security research.  
  

More recently, virtualization solutions have gained prominence in the iOS security research community. In principle, virtualization offers a way to conduct security testing on iOS without being subject to the hardware restrictions that prevent kernel modification. The caveat is that these products are often accessed over the web, which would mean that any experiments conducted on a virtualized device could in theory be visible to the company providing the service.  
  

None of these options sit well with me. I do not withhold security bugs, I do not use development-fused devices, and I do not feel it is appropriate for me to run sensitive experiments that could disclose potential iOS security vulnerabilities on third party servers. This puts me at a disadvantage relative to adversaries developing and deploying 0-day capabilities who may be using any or all of these strategies.  
  

Thus, back in March, I decided it would be worthwhile to investigate whether it was possible to create my own homebrewed development iPhone using only certified Apple parts.

KTRR and other hardware mitigations
-----------------------------------

At the heart of what makes conducting security research on iOS difficult is a hardware mitigation called KTRR, which likely stands for Kernel Text Readonly Region. Siguza ([@s1guza](https://twitter.com/s1guza)) has an excellent article on [KTRR](https://siguza.github.io/KTRR/) which I highly recommend reading.  

Since Apple does not publish details about their hardware mitigations, it is hard to know the exact boundary of each mitigation. In this post I will try to use the terminology suggested in the public XNU sources, even though this differs from the terms used in some other articles.  
  

In effect, KTRR is a stronger form of [W^X protection](https://en.wikipedia.org/wiki/W%5EX), enforced over all memory accesses from EL1 and implemented in both the [memory management unit](https://en.wikipedia.org/wiki/Memory_management_unit) (MMU) and in the [memory controller](https://en.wikipedia.org/wiki/Memory_controller). (Apple's memory controller appears to be referred to as AMCC in the sources.) The MMUs and the AMCC can each be programmed with a physical address range, respectively referred to as the MMU KTRR region and the AMCC KTRR region. Each MMU ensures that writes to physical addresses within the MMU KTRR region and EL1 instruction fetches from addresses outside the region will generate a synchronous exception. Likewise, the AMCC ensures that writes issued to the memory controller for physical addresses inside the AMCC KTRR region will be discarded. In this way, the kernel locks down its executable code (and read-only data) so that it cannot be modified and new executable code cannot be injected.  

In order to lock down the MMU, Apple has defined three new system registers: KTRR\_LOWER\_EL1, KTRR\_UPPER\_EL1, and KTRR\_LOCK\_EL1. KTRR\_LOWER\_EL1 and KTRR\_UPPER\_EL1 define the lower and upper bounds of the MMU KTRR region. KTRR\_LOCK\_EL1 is a lockdown register: once the value 1 has been written to it, all three registers are locked down and can no longer be modified (although they still lose their values on core reset, that is, after a core wakes from sleep).  
  

Once the MMU has been enabled, it enforces that all memory writes to the MMU KTRR region and all instruction fetches at EL1 from outside the region will generate a synchronous exception. This means that regardless of the permission bits specified in the page tables, and regardless of the configuration of any other system registers (including the [APRR registers](https://siguza.github.io/APRR/)), it is impossible to have memory that is both writable and executable, and it is impossible to change which memory is executable.  

However, implementing KTRR in the MMU alone is not enough to ensure kernel code integrity. For example, DMA attacks and other attacks from peripherals would reach the memory controller without first passing through an MMU on the application processor. Thus, Apple had to bring KTRR to the AMCC as well, with its own readonly region and lockdown registers accessible via [memory-mapped I/O](https://en.wikipedia.org/wiki/Memory-mapped_I/O) (MMIO).

![This is a diagram showing the inteactions between memory, AMCC KTRR and the MMU KTRR regions. On an A11 device, the MMU KTRR region protects all kernel const data except __LAST.__pinst, for example __PRELINK_TEXT, __DATA_CONST, and __TEXT_EXEC are protected. Any writes to the MMU KTRR region and any instruction fetches from outside the MMU KTRR region fault. The AMCC KTRR region is the same as the MMU KTRR region, plus it includes __LAST.__pinst. Any writes to the AMCC KTRR region are discarded at the memory controller. The page tables live in __DATA_CONST, where they are protected by both KTRR regions. Privileged instructions like MSR TTBR1_EL1 reside in __LAST.__pinst and are only protected by the AMCC KTRR region.](https://lh6.googleusercontent.com/W0EEXEiQSa2iZL9IdKVHS7i23Eru_5yG2-12PrrF8-4i6_k1mAY7Pn69xwMZex_U05ZMcgf8k25w1615DeuYJNBcbiRTAk0HbTS0DqjTIKD1xMcUK6G0S6xX3VPp1q6z_Qtc_kMa)

This combination of implementing KTRR in the MMU and the AMCC makes it extremely effective. The MMU and AMCC KTRR regions protect all critical kernel resources, including the page table root and page tables describing the readonly region itself. Instructions which might be used to break KTRR have been moved to a special page, \_\_LAST.\_\_pinst, which is outside the MMU KTRR range (making it non-executable) but inside the AMCC KTRR range (making it non-writable). In particular, there are no executable copies of the instruction MSR TTBR1\_EL1, X0, which sets a new page table root for address translations for the kernel's half of the address space, or of the instruction MSR SCTLR\_EL1, X0, which could be used to turn off the MMU. (This last part is only true on A10 and A11; Apple added a new hardware mitigation on A12 that brings SCTLR\_EL1 back into executable memory.)  
  

In order to bypass KTRR and load new executable code, one would need to find a way to prevent the MMU KTRR lockdown from occurring. However, this attack surface is incredibly slim: after a core wakes from sleep, the system will begin by executing the reset vector, LowResetVectorBase, which programs and locks down the MMU KTRR registers within the first 100 instructions.

The goals for a research iPhone
-------------------------------

So, now that we know what we're up against, what exactly are the features I think would be most useful in a homebrewed research iPhone?  
  

1.  The most important feature, but also the hardest to achieve, is that it should be possible to patch KTRR-protected kernel memory, and in particular to patch \_\_TEXT\_EXEC, the segment that contains the kernel's executable code. If this were possible, it would then become easy to disable other mitigations (like codesigning) that make userspace security research difficult.  
    
2.  It should be possible to perform single-step iOS kernel debugging. This would aid in runtime analysis of the kernel and make it easier to demonstrate incorrect behavior in a PoC for a vulnerability.  
    
3.  It should not be tied to a specific version of iOS: that is, it should be possible to debug new kernel versions as they come out, either by updating the device normally or by chainloading an updated kernel.  
    
4.  It should be usable with existing debugging tools. In particular, I wanted to be able to perform kernel debugging on a live, production-fused iPhone using LLDB and IDA Pro.  
    
5.  It should be relatively easy to port to newer versions of iOS.
    

  

In fact, this research concept is nothing new. Goal 1 was partially demonstrated back in iOS 10.1.1, and goals 2 and 4 were demonstrated in iOS 11.1.2.

iOS 10.1.1: The Yalu KTRR bypass
--------------------------------

Luca Todesco ([@qwertyoruiopz](https://twitter.com/qwertyoruiopz)) demonstrated a [KTRR bypass](http://yalu.qwertyoruiop.com/y7.txt) for iOS 10.1.1 that remapped the kernel's \_\_DATA\_CONST segment, normally protected by KTRR, as writable. His technique relied on two components: one to gain code execution after reset and another to remap KTRR-protected memory.  

First, Luca used the fact that writable data was being used in the reset path (LowResetVectorBase, in [osfmk/arm64/start.s](https://opensource.apple.com/source/xnu/xnu-4903.221.2/osfmk/arm64/start.s.auto.html)) to gain code execution after every reset. This in and of itself was not a KTRR bypass, since KTRR had already been initialized and the MMU turned on at the point at which he gained code execution. But it was useful for persisting the true bypass so that it would be applied every time a core reset.  

Second, an off-by-one error in the MMU KTRR lockdown code in LowResetVectorBase resulted in the \_\_LAST.\_\_pinst page accidentally being included in the MMU KTRR region, meaning that the instruction MSR TTBR1\_EL1, X0 was left executable even after the MMU was turned on. To take advantage of this, Luca used the first capability to execute a ROP payload after each reset. This ROP payload would bypass KTRR by using that executable MSR instruction to set TTBR1\_EL1 to a new page table base that remapped \_\_DATA\_CONST to new, writable physical pages.  
  

The reason \_\_TEXT\_EXEC was left readonly is that the bypass ran after KTRR was already initialized on the MMU: even though the page tables could be changed, the MMU still prevented any physical pages except the original ones protected by the KTRR AMCC region from being executed. Thus, it remained impossible to patch the kernel's executable code.

iOS 11.1.2: Build your own iOS kernel debugger
----------------------------------------------

The other precedent for this work came with iOS 11.1.2, when Ian Beer ([@i41nbeer](https://twitter.com/i41nbeer)) released [async\_wake\_ios\_with\_kdp](https://bugs.chromium.org/p/project-zero/issues/detail?id=1417#c17), a single-step kernel debugger that worked with LLDB. You should absolutely read the slides from his MOSEC 2018 talk ["Build your own iOS kernel debugger"](https://drive.google.com/open?id=1NKS3errk4UQ65spDMYBswJmbJxZYLvAL), which explain in great detail how he accomplished this. I also recommend looking through the source code, which is very well commented.  

If you look at the [ARMv8 Architecture Reference Manual](https://developer.arm.com/docs/ddi0487/latest/arm-architecture-reference-manual-armv8-for-armv8-a-architecture-profile) (all quotes are from version E.a, the latest at the time of writing), Chapter D2 describes an interesting feature called "Aarch64 Self-hosted Debug":

Self-hosted debug supports debugging through the generation and handling of debug exceptions, that are taken using the exception model described in Chapter D1 The AArch64 System Level Programmers' Model.

\[...\]

Within this chapter, debugger means that part of an operating system, or higher level of system software, that handles debug exceptions and programs the Debug System registers.

Essentially, the architecture allows an operating system to program special debug registers in order to act as a debugger, catching exceptions that occur when certain debug-related events are encountered. According to the manual, relevant exception types include:  
  

1.  Breakpoint instruction exceptions: Generated when a BRK instruction is executed.  
    
2.  Breakpoint exceptions: Generated when a hardware breakpoint is hit.  
    
3.  Watchpoint exceptions: Generated when a hardware watchpoint is hit.  
    
4.  Software step exceptions: Generated after a software single-step operation completes.
    

  

If the debug registers are configured properly, then these events will be delivered as synchronous exceptions to the exception vector specified in the register VBAR\_EL1.  
  

Under what circumstances will these debug exceptions actually be generated and delivered?

The PE can only generate a particular debug exception when both:

1.  Debug exceptions are enabled from the current Exception level and Security state.  
      
    See Enabling debug exceptions from the current Exception level on page D2-2405. Breakpoint Instruction exceptions are always enabled from the current Exception level and Security state.
    

2.  A debugger has enabled that particular debug exception.  
      
    All of the debug exceptions except for Breakpoint Instruction exceptions have an enable control contained in the MDSCR\_EL1. See The debug exception enable controls on page D2-2402.
    

Reading through the mentioned sections, we find that the following registers are relevant for enabling self-hosted debug:  
  

1.  PSTATE: Process State. This is not a real register, but a collection of important processor state information. The relevant flags for debugging are the exception mask bits:  
    
    1.  D: Debug exception mask. When set, debug exceptions are suppressed. This field resets to 1 when an exception is taken.
        
    2.  A , I, F: Asynchronous exception mask bits. These bits mask SError, IRQ, and FIQ interrupts, respectively.  
        
2.  MDSCR\_EL1: Monitor Debug System Control Register. This register holds the main debug configuration options.  
    
    1.  MDE: Monitor Debug Enable. Controls whether breakpoint and watchpoint exceptions are enabled.
        
    2.  KDE: Kernel Debug Enable. Enables the kernel running at EL1 to catch its own debug exceptions.  
        
3.  DBGBCR\_EL1: Debug Breakpoint Control Register n, n \= 0 - 15. These 16 registers control the behavior of the hardware breakpoints.  
    
4.  DBGBVR\_EL1: Debug Breakpoint Value Register n, n \= 0 - 15. These registers contain information to match the virtual address at which the corresponding breakpoint should trigger.  
    
5.  DBGWCR\_EL1: Debug Watchpoint Control Register n, n \= 0 - 15. These registers control the behavior of the hardware watchpoints.  
    
6.  DBGWVR\_EL1: Debug Watchpoint Value Register n, n \= 0 - 15. These registers contain information to match the virtual address at which the corresponding watchpoint should trigger.
    

Basically, Ian's debugger worked by finding the appropriate system calls, Mach traps, and gadget sequences to set these registers to the necessary values, thus enabling hardware breakpoints and allowing EL1 (kernel mode) to generate debug exceptions.  
  

The final piece is catching those debug exceptions. Being able to trigger a kernel breakpoint exception is not of much use if we cannot somehow catch that exception, dump registers and memory, and then resume normal execution.  
  

What Ian found is that the exception handling function sleh\_synchronous() (in osfmk/arm64/sleh.c) actually enters a deliberate infinite loop when it catches a breakpoint exception from the kernel:

void

sleh\_synchronous(arm\_context\_t \*context, uint32\_t esr, vm\_offset\_t far)

{

esr\_exception\_class\_t   class = ESR\_EC(esr);

arm\_saved\_state\_t       \*state = &context->ss;

...

switch (class) {

...

case ESR\_EC\_BKPT\_REG\_MATCH\_EL1:

if (FSC\_DEBUG\_FAULT == ISS\_SSDE\_FSC(esr)) {

kprintf("Hardware Breakpoint Debug exception from kernel.  Hanging here (by design).\\n");

for (;;);

  

            \_\_unreachable\_ok\_push

DebuggerCall(EXC\_BREAKPOINT, &context->ss);

break;

            \_\_unreachable\_ok\_pop

        }

panic("Unsupported Class %u event code. state=%p class=%u esr=%u far=%p",

              class, state, class, esr, (void \*)far);

assert(0); /\* Unreachable \*/

break;

...

    }

...

}

At the point at which the thread that generated the breakpoint exception enters that infinite loop, its register state at the time of the exception will have been spilled to memory, making it possible to inspect and modify the register values. And finally, Ian was able to restart execution of the debugged thread by waiting for it to be preempted while spinning in that loop and then modifying the spilled state so that the thread resumes execution at the desired location.  
  

Ian's async\_wake kernel debugger was able to achieve two of the goals mentioned above: the debugger supported single-stepping and it worked with LLDB. This was certainly enough to make a useful research platform. However, Apple mitigated the gadgets Ian used, meaning that I couldn't use his technique on more recent iOS versions. Ideally I wanted something that met all five goals: kernel patching, single-step debugging, support for any iOS version, compatibility with LLDB, and easy maintenance across iOS versions. For that, I turned to iBoot.

Researching iBoot
-----------------

My initial goal was to find a vulnerability in iBoot that would allow me to boot a patched kernelcache. iBoot is Apple's second-stage bootloader on the iPhone: it runs after the SecureROM and is responsible for loading the kernelcache, verifying its signature, and jumping to it. With code execution in iBoot, it is possible to boot a kernelcache that is patched to disable KTRR and enable debugging features.  
  

There are two reasons why iBoot was a particularly attractive research target.  
  

First, an iBoot bug easily checks the updateability box. With an iBoot bug, you could theoretically boot any kernelcache you want, allowing you to "upgrade" or "downgrade" the iOS version arbitrarily. Even after the bug is fixed, iPhones with a vulnerable iBoot version should still be able to boot the latest version of iOS with a patched kernel.  
  

Second, an iBoot bug could make it possible to load a patched kernelcache even when no kernel vulnerabilities are known. Currently, in order to develop an iOS kernel research platform, you need to already have a kernel vulnerability. Unless you withhold bugs, this makes it difficult to analyze the latest kernel version in which all known vulnerabilities have been fixed. However, if iBoot is your entry point, then you do not need any kernel vulnerabilities to conduct research.  
  

Ultimately, I did not end up finding any vulnerabilities in iBoot. That said, I believe such bugs exist, and it could be an interesting area for future research.

All paths lead to debug registers
---------------------------------

Eventually, a number of things drew me away from iBoot and back to KTRR, and in particular to revisit the concept of debug registers:  
  

1.  I had read somewhere (the exact source is lost to history) that the debug registers Ian used in his iOS 11.1.2 kernel debugger (DBGBCR\_EL1, etc.) were also accessible via a memory-mapped interface. If true, this would mean that using these registers for single-step kernel debugging would probably be possible even after Apple mitigated the specific gadgets he used to initialize them.  
    
2.  Looking through the [ARMv8 Architecture Reference Manual](https://static.docs.arm.com/ddi0487/ea/DDI0487E_a_armv8_arm.pdf?_ga=2.217107798.15093376.1567105706-274993115.1567105706)'s table of contents, I noticed that self-hosted debug (Chapter D2) is just one place where debugging is mentioned. In fact there is a whole section (Part H, Chapters H1 - H9) that is devoted to another debugging interface called External Debug.  
    
3.  In LowResetVectorBase, XNU's reset vector, this is the very first instruction:  
      
    // Unlock the core for debugging  
    msr             OSLAR\_EL1, xzr  
    
4.  At [MOSEC 2019](http://en.2019.mosec.org/), Zhenyu Ning and Fengwei Zhang presented an interesting attack on Android platforms called [Nailgun](https://compass.cs.wayne.edu/nailgun/). The Nailgun attack abuses debug registers enabled on certain Android devices to break privilege barriers, for example by [extracting fingerprint images](http://www.cs.wayne.edu/fengwei/paper/nailgun-sp19.pdf) stored in TrustZone protected memory.
    

  

Thus, debug registers were really on my mind when I finally decided to pay attention to what an odd panic message I had occasionally encountered in my experiments was telling me.  
  

If you have ever played around on an iPhone and managed to get a core stuck in an infinite loop with interrupts disabled, you may have received a panic message that goes something like this:

"panicString" : "Attempting to forcibly halt cpu 1\\ncpu 1 failed to halt with error -5: halt not supported for this configuration\\nDebugger synchronization timed out; waited 10000000 nanoseconds\\npanic(cpu 0 caller 0xfffffff00b5c96bc): \\"WDT timeout: CPU 1 failed to respond\\"@\\/BuildRoot\\/...

This message says that the application processor's watchdog timer (WDT) timed out while waiting on CPU (core) 1. This happens when a core fails to check in with the AppleARMWatchDogTimer kext for several seconds.  
  

But what caught my attention was the first part of the panic string: "Attempting to forcibly halt cpu 1". Forcibly halting a CPU while it is running really sounds like some sort of CPU control register might be involved. And with an error string to grep for, I had a starting place.  
  

Searching for this string in the XNU sources, I found that the function DebuggerXCallEnter() (file [osfmk/arm/model\_dep.c](https://opensource.apple.com/source/xnu/xnu-4903.221.2/osfmk/arm/model_dep.c.auto.html)) contained the following interesting snippet:

for (cpu=0; cpu <= max\_cpu; cpu++) {

...

if (proceed\_on\_sync\_failure) {

paniclog\_append\_noflush("Attempting to forcibly halt cpu %d\\n", cpu);

dbgwrap\_status\_t halt\_status = ml\_dbgwrap\_halt\_cpu(cpu, 0);

if (halt\_status < 0)

paniclog\_append\_noflush("cpu %d failed to halt with error %d: %s\\n", cpu, halt\_status, ml\_dbgwrap\_strerror(halt\_status));

...

    }

...

}

A comment above DebuggerXCallEnter() states that this function is responsible for interrupting other cores on the AP "so this core can run in a single-threaded context". This is what we are seeing in this for loop: the function ml\_dbgwrap\_halt\_cpu() seems to be the one that actually does the work to halt a specific core. And looking at the file [osfmk/kern/debug.c](https://opensource.apple.com/source/xnu/xnu-4903.221.2/osfmk/kern/debug.c.auto.html), we can see that DebuggerXCallEnter() is indeed being called as part of the panic path.  

So, how does ml\_dbgwrap\_halt\_cpu() actually halt a running CPU core? The implementation is in the file [osfmk/arm64/dbgwrap.c](https://opensource.apple.com/source/xnu/xnu-4903.221.2/osfmk/arm64/dbgwrap.c.auto.html), which is just filled with interesting information.  

Here is the implementation of ml\_dbgwrap\_halt\_cpu():

dbgwrap\_status\_t

ml\_dbgwrap\_halt\_cpu(int cpu\_index, uint64\_t timeout\_ns)

{

cpu\_data\_t \*cdp = cpu\_datap(cpu\_index);

if ((cdp == NULL) || (cdp->coresight\_base\[CORESIGHT\_UTT\] == 0))

        return DBGWRAP\_ERR\_UNSUPPORTED;

...

volatile dbgwrap\_reg\_t \*dbgWrapReg = (volatile dbgwrap\_reg\_t \*)

            (cdp->coresight\_base\[CORESIGHT\_UTT\] + DBGWRAP\_REG\_OFFSET);

  

if (ml\_dbgwrap\_cpu\_is\_halted(cpu\_index))

return DBGWRAP\_WARN\_ALREADY\_HALTED;

  

/\* Clear all other writable bits besides dbgHalt; none of the

     \* power-down or reset bits must be set. \*/

    \*dbgWrapReg = DBGWRAP\_DBGHALT;

...

else

return DBGWRAP\_SUCCESS;

}

This tells us a lot of tantalizing information! The cpu\_datap() function retrieves a pointer to the current core's cpu\_data struct, so whatever the coresight\_base array is, there is one for each AP core. Then, we see an assignment of some value derived from that array to a volatile variable called dbgWrapReg; the name and the fact that it is declared volatile strongly suggest that dbgWrapReg is a pointer to some sort of MMIO, and reading and writing it will directly read and write a core-specific register. And the comment below suggests that the DBGWRAP register contains bits involved in halting, powering down, and resetting the core.  
  

But the real gem is a bit further down. Keep scrolling past ml\_dbgwrap\_halt\_cpu() and you will find a fascinating function called ml\_dbgwrap\_halt\_cpu\_with\_state():

dbgwrap\_status\_t

ml\_dbgwrap\_halt\_cpu\_with\_state(int cpu\_index, uint64\_t timeout\_ns,

dbgwrap\_thread\_state\_t \*state)

{

cpu\_data\_t \*cdp = cpu\_datap(cpu\_index);

if ((cdp == NULL) || (cdp->coresight\_base\[CORESIGHT\_ED\] == 0))

return DBGWRAP\_ERR\_UNSUPPORTED;

  

/\* Ensure memory-mapped coresight registers can be written \*/

    \*((volatile uint32\_t \*)(cdp->coresight\_base\[CORESIGHT\_ED\]

                + ARM\_DEBUG\_OFFSET\_DBGLAR)) = ARM\_DBG\_LOCK\_ACCESS\_KEY;

  

dbgwrap\_status\_t status = ml\_dbgwrap\_halt\_cpu(cpu\_index, timeout\_ns);

  

/\* A core that is not fully powered (e.g. idling in wfi) can still be

     \* halted; the dbgwrap register and certain coresight registers such

     \* EDPRSR are in the always-on domain. However, EDSCR/EDITR are not in

     \* the always-on domain and will generate a parity abort on read.

     \* EDPRSR can be safely read in all cases, and the OS lock defaults to

     \* being set but we clear it first thing, so use that to detect the

     \* offline state. \*/

if (\*((volatile uint32\_t \*)(cdp->coresight\_base\[CORESIGHT\_ED\]

                    + EDPRSR\_REG\_OFFSET)) & EDPRSR\_OSLK) {

bzero(state, sizeof(\*state));

return DBGWRAP\_WARN\_CPU\_OFFLINE;

    }

  

uint32\_t instr;

  

for (unsigned int i = 0;

            i < (sizeof(state->x) / sizeof(state->x\[0\])); ++i) {

        instr = (0xD51U << 20) | (2 << 19) | (3 << 16)

            | (4 << 8) | i; // msr DBGDTR0, x

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_        state->x\[i\] = ml\_dbgwrap\_read\_dtr(cdp, timeout\_ns, &status);_

_    }_

_    instr = (0xD51U << 20) | (2 << 19) | (3 << 16)_

_        | (4 << 8) | 29; // msr DBGDTR0, fp_

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_    state->fp = ml\_dbgwrap\_read\_dtr(cdp, timeout\_ns, &status);_

_    instr = (0xD51U << 20) | (2 << 19) | (3 << 16)_

_        | (4 << 8) | 30; // msr DBGDTR0, lr_

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_    state->lr = ml\_dbgwrap\_read\_dtr(cdp, timeout\_ns, &status);_

_/\* Stack pointer (x31) can't be used as a register operand for msr;_

_     \* register 31 is treated as xzr rather than sp when used as the_

_     \* transfer operand there.  Instead, load sp into a GPR we've already_

_     \* saved off and then store that register in the DTR.  I've chosen x18_

_     \* as the temporary GPR since it's reserved by the arm64 ABI and unused_

_     \* by xnu, so overwriting it poses the least risk of causing trouble_

_     \* for external debuggers. \*/_

_    instr = (0x91U << 24) | (31 << 5) | 18; // mov x18, sp_

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_    instr = (0xD51U << 20) | (2 << 19) | (3 << 16)_

_        | (4 << 8) | 18; // msr DBGDTR0, x18_

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_    state->sp = ml\_dbgwrap\_read\_dtr(cdp, timeout\_ns, &status);_

_/\* reading PC (e.g. through adr) is undefined in debug state.  Instead_

_     \* use DLR\_EL0, which contains PC at time of entry into debug state.\*/_

_    instr = (0xD53U << 20) | (1 << 19) | (3 << 16) | (4 << 12)_

_        | (5 << 8) | (1 << 5) | 18; // mrs    x18, DLR\_EL0_

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_    instr = (0xD51U << 20) | (2 << 19) | (3 << 16)_

_        | (4 << 8) | 18; // msr DBGDTR0, x18_

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_    state->pc = ml\_dbgwrap\_read\_dtr(cdp, timeout\_ns, &status);_

_/\* reading CPSR is undefined in debug state.  Instead use DSPSR\_EL0,_

_     \* which contains CPSR at time of entry into debug state.\*/_

_    instr = (0xD53U << 20) | (1 << 19) | (3 << 16) | (4 << 12)_

_        | (5 << 8) | 18; // mrs    x18, DSPSR\_EL0_

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_    instr = (0xD51U << 20) | (2 << 19) | (3 << 16)_

_        | (4 << 8) | 18; // msr DBGDTR0, x18_

_ml\_dbgwrap\_stuff\_instr(cdp, instr, timeout\_ns, &status);_

_    state->cpsr = (uint32\_t)ml\_dbgwrap\_read\_dtr(cdp, timeout\_ns, &status);_

_return status;_

_}_

_

What ml\_dbgwrap\_halt\_cpu\_with\_state() appears to do is halt the specified CPU core and then retrieve its register state. That in and of itself is not remarkable. What is remarkable is the way it does this.  
  

In order to retrieve the values of registers on the halted CPU core, this function actually forces the halted CPU to execute instructions that write the general-purpose register values to a special debug register called DBGDTR0. And these instructions are generated programmatically on the fly, not preexisting instructions protected by KTRR.  
  

What this means is that, at least in theory, it might be possible to make a CPU core execute a KTRR-sensitive instruction like MSR TTBR1\_EL1, X0 even if there are no copies of that instruction in KTRR-protected memory.

Digging deeper
--------------

My next step was to figure out what these debug registers were, and if they were actually enabled.  
  

A bit of research revealed that some of the registers mentioned in dbgwrap.c were related to an ARMv8 feature called External Debug and the debug architecture into which it is embedded called CoreSight. Let's start with the latter.

The external debug interface is much simpler to describe, and is documented in Part H of the ARMv8 Architecture Reference Manual. Just like self-hosted debug provides debug exceptions which cause the core to execute debugger code in the exception vector, external debug provides debug events which cause the core to enter debug state.  
  

These are a few of the debug events mentioned in the manual:  
  

1.  Exception catch debug event: An external debugger can program a core to generate an exception catch debug event every time the core enters a particular exception level.  
    
2.  Reset catch debug event: This event can be generated every time the core resets and is about to execute the reset vector.  
    
3.  Breakpoint debug event: This event can be generated when a core hits a hardware breakpoint.  
    
4.  Watchpoint debug event: This event can be generated when a core hits a hardware watchpoint.  
    
5.  Halting step debug event: This event can be generated after a core completes executing an instruction as part of a single-step operation.
    

  

Once a debug event occurs, the core will halt and enter debug state, from where it can be manipulated by an external debugger. From the manual:

In external debug, debug events allow an external debugger to halt the PE. The PE then enters Debug state. When the PE is in Debug state:

*   It stops executing instructions from the location indicated by the program counter, and is instead controlled through the external debug interface.  
    
*   The Instruction Transfer Register, ITR, passes instructions to the PE to execute in Debug state.  
    
*   The Debug Communications Channel, DCC, passes data between the PE and the debugger.
    

  
The PE cannot service any interrupts in Debug state.

The Instruction Transfer Register (ITR) and Debug Communications Channel (DCC) are respectively responsible for making the halted core execute instructions and transferring data from the halted core to ml\_dbgwrap\_halt\_cpu\_with\_state(). In order to read a register from the halted core, the function ml\_dbgwrap\_stuff\_instr() uses the memory-mapped ITR to supply the halted core with an instruction that moves the desired register value into the system register DBGDTR\_EL0. From there, the value of DBGDTR\_EL0 is read by the function ml\_dbgwrap\_read\_dtr() using the memory-mapped DCC registers DBGDTRRX\_EL0 and DBGDTRTX\_EL0.

Finding the registers
---------------------

The XNU code seems to suggest that the external debug registers exist, but how do we find them?  
  

Tracing through the XNU source, we find the function configure\_coresight\_registers() in [osfmk/arm64/cpu.c](https://opensource.apple.com/source/xnu/xnu-4903.221.2/osfmk/arm64/cpu.c.auto.html):

static void

configure\_coresight\_registers(cpu\_data\_t \*cdp)

{

...

/\*

     \* ARMv8 coresight registers are optional. If the device tree did not

     \* provide cpu\_regmap\_paddr, assume that coresight registers are not

     \* supported.

     \*/

if (cdp->cpu\_regmap\_paddr) {

for (i = 0; i < CORESIGHT\_REGIONS; ++i) {

/\* Skip CTI; these registers are debug-only (they are

             \* not present on production hardware), and there is

             \* at least one known Cyclone errata involving CTI

             \* (rdar://12802966).  We have no known clients that

             \* need the kernel to unlock CTI, so it is safer

             \* to avoid doing the access.

             \*/

if (i == CORESIGHT\_CTI)

continue;

/\* Skip debug-only registers on production chips \*/

if (((i == CORESIGHT\_ED) || (i == CORESIGHT\_UTT))

                    && !coresight\_debug\_enabled)

continue;

  

if (!cdp->coresight\_base\[i\]) {

                addr = cdp->cpu\_regmap\_paddr + CORESIGHT\_OFFSET(i);

                cdp->coresight\_base\[i\] = (vm\_offset\_t)

ml\_io\_map(addr, CORESIGHT\_SIZE);

...

            }

...

        }

    }

}

This suggests that the CoreSight registers (external debug, cross-trigger interconnect (CTI), and something called UTT) are mapped at offsets from a fixed base address supplied in the iOS device tree.  
  

The [device tree](https://en.wikipedia.org/wiki/Device_tree) is passed to XNU by iBoot and specifies parameters of the system's hardware, including the physical addresses of any special hardware registers used to interact with devices. In this case, by comparing the device tree with the value of cpu\_regmap\_paddr read at runtime, I learned that the base address of the CoreSight registers for CPU core n can be found in the device tree property cpus/cpu/reg-private. On my iPhone 8, these addresses are 0x20810000 for core n.  

Thus, assuming they are enabled, all one would need to do in order to access the external debug registers is map physical address 0x20810000 (or whatever the reg-private address is in the device tree) and then read and write to the offsets (available in the manual) corresponding to the registers.

Testing the debug registers
---------------------------

So, the registers used by ml\_dbgwrap\_halt\_cpu\_with\_state() are documented in the ARMv8 manual, and we know the base address at which they are mapped, but that does not necessarily mean that these features are implemented and accessible on production hardware. In order to find out, I needed to test whether the debug authentication signals were on and whether the debug registers actually worked.  
  

According to the manual, there should be an implementation-defined authentication interface for the external debug features. When the authentication signals are off, then the corresponding debug features are disabled; when the signals are on, the debug features are available.  
  

To check which debug authentication signals are enabled, I read the value of the external debug register DBGAUTHSTATUS\_EL1 at offset 0xfb8. The architecture provides four signals: SNID (Secure Non-Invasive Debug), SID (Secure Invasive Debug), NSNID (Non-Secure Non-Invasive Debug), and NSID (Non-Secure Invasive Debug). The debugging features we need to bypass KTRR rely on NSNID and NSID being enabled. Surprisingly, reading the DBGAUTHSTATUS\_EL1 register via MMIO produced 0xf, suggesting that both signals were in fact enabled.  
  

So the next step was to test whether ml\_dbgwrap\_halt\_cpu\_with\_state() could actually halt a core and execute instructions on it to read that core's register state. After modifying [voucher\_swap](https://bugs.chromium.org/p/project-zero/issues/detail?id=1731#c10) to map the CoreSight registers manually and then call ml\_dbgwrap\_halt\_cpu\_with\_state(), I saw the following output:

In the output window, the register values read by ml\_dbgwrap\_halt\_cpu\_with\_state() look valid. Thus, it is entirely possible to execute dynamically-generated instructions on a halted CPU core on production A11 iPhones!  
  

But what is even more remarkable from the above screenshot is that it appears that the core was halted while it was executing code from the reset vector with the MMU off! The value of CPSR shows that the core is executing in kernel mode with interrupts disabled, and yet the PC value 0x8042e4120 is not a normal kernel address. In fact, it is the physical address corresponding to the unslid kernel virtual address 0xfffffff0070e4120, which is near the end of LowResetVectorBase (specifically, at the instruction that loads the address of const\_boot\_args into X20 before verifying the reset handler).  
  

The reason this is remarkable is that it opens up another possible technique to bypass KTRR: given that we can halt a core and execute instructions on it before the MMU has been turned on, is it perhaps possible to use these debug registers to modify execution of the reset vector itself to prevent KTRR from ever being enabled on the MMU?

More debugging features needed
------------------------------

Actually, even though we have proved that it is possible to execute instructions on a debugged core while the MMU is off, this alone is not necessarily enough to bypass KTRR. For example, even though we can use DBGWRAP to halt a core, the ARMv8 external debug interface contains no mechanism to get a core out of debug state and resume normal execution (which is called restarting). Thus, I needed to find some other feature that would make these debugging registers useful.  
  

The first thing I looked at was finding a useful instruction to execute on the debugged core. Even though the core will execute instructions written to the ITR, not all instructions are available in debug state. The ARMv8 manual specifies a list of instructions that are available, most of which are related to moving values between registers, accessing system registers, and loading and storing from memory. But even fewer are actually available on the A11: for some reason, load and store instructions fail to execute in debug state.  
  

Even so, most instructions that read and write system registers (MSR and MRS instructions) do work in debug state. Thus, another idea I investigated was whether there exists a system register shared between cores such that writing to it would change global state in some way that facilitates a KTRR bypass. However, without better knowledge of Apple's proprietary system registers, I was unable to find anything that worked.  
  

Finally, I decided to turn back to the DBGWRAP register mentioned in dbgwrap.c. The comment in ml\_dbgwrap\_halt\_cpu() suggests that the register contains many different bits to control the behavior of a core, and yet only 2 bits (DBGHALT to halt a core and DBGACK to check if the core is halted) are defined in the file. Thus, I suspected that there might be other bits of interest and performed experiments to figure out what they might be.  
  

As it turns out, DBGWRAP actually contains at least 3 other, undocumented bits, all of which are extremely useful. Setting bit 29 will cause the core to enter debug state the next time it resets and is about to execute the reset vector. Setting bit 30 will cause the core to restart, exiting debug state and resuming normal execution. And setting bit 26 seems to prevent the core from resetting so long as the phone is plugged in and active (i.e. not sleeping).  
  

With that, we now have everything necessary to bypass KTRR.

Bypassing KTRR
--------------

This is the method I chose to disable KTRR on the MMU (repeated for each core):  
  

1.  Using DBGWRAP, configure the core to enter debug state next time it resets.  
    
2.  Wait for the core to halt. Once it has halted, it is about to execute the first instruction of LowResetVectorBase. The KTRR registers will not yet be initialized.  
    
3.  Using the external debug registers and DBGWRAP, repeatedly single-step execution of the core. On each step, read the PC value on the debugged core to determine the instruction about to be executed.  
    
4.  Once the core is about to execute the KTRR initialization instructions, use the external debug registers to overwrite values in the debugged core's general purpose registers such that it skips KTRR initialization.  
    
5.  Use DBGWRAP to restart the core, exiting out of debug state. KTRR will be disabled on the MMU, meaning that it is now possible to execute memory outside the KTRR readonly region.
    

  

With that, it is possible to set TTBR1\_EL1 to a custom page table base and remap the kernel onto fresh, writable physical pages outside of the AMCC KTRR range.

KTRW
----

In order to make this functionality useful, I packaged the KTRR bypass in an iOS kext loader and kernel debugger named KTRW. KTRW makes it possible to compile a C program into a Mach-O file and then dynamically load and link the binary against the running kernel. The iOS kernel debugger implements a GDB stub accessible over USB.  
  

Of course, KTRW (and in particular the GDB stub kext) is significantly more complicated than just the KTRR bypass itself, and I encountered numerous interesting challenges that needed to be overcome (including writing a USB stack from scratch for undocumented hardware). However, the [KTRW source code](https://github.com/googleprojectzero/ktrw) should be reasonably well commented, so I refer interested readers there.  

This particular KTRR bypass only works on A11 devices; the debugging registers do not appear accessible on A12 devices, and they appear only partially functional on A9 (0x202010000) and A10 (0x202210000, which differs from the device tree). It is difficult to know for sure whether the debugging registers are truly unusable on these other devices without greater insight into the hardware; they might work perfectly under some slight variation of the setup I'm using or if they are first configured using some proprietary mechanism.  
  

Is this a security vulnerability?
---------------------------------

While this was reported to Apple as Project Zero [issue 1900](https://bugs.chromium.org/p/project-zero/issues/detail?id=1900), neither Project Zero nor Apple considers the existence of these debug registers a security vulnerability.  

The reason is that in order to use these registers to bypass KTRR, one would already need to have a kernel arbitrary read/write capability, at which point the device should be considered fully compromised anyway. Once an attacker has kernel read/write, they have access to any data used by any app on the system.  
  

For evidence that kernel read/write is all an attacker needs in practice, I highly recommend reading Ian's phenomenal technical analysis of [five in-the-wild iOS exploit chains](https://googleprojectzero.blogspot.com/2019/08/a-very-deep-dive-into-ios-exploit.html), including his [analysis of the implant itself](https://googleprojectzero.blogspot.com/2019/08/implant-teardown.html). He found that the attackers only used the kernel read/write capability to launch the implant binary; after the implant has launched, it gets access to all the data it exfiltrates using normal userspace APIs.

On research phones and SecureROM exploits
-----------------------------------------

Apple announced at BlackHat 2019 that they are considering providing "research-fused" devices to security researchers. I genuinely hope that they deliver on that promise soon (without requiring NDAs or other restrictions placed on security researchers like myself), as I personally believe that would be a tremendous step forward for open security research.  
  

The presence of the debug registers allow one to bypass KTRR and debug the kernel even in the absence of a SecureROM vulnerability. In practice, however, the publication of the SecureROM exploit solves most of the goals I listed for a research iPhone, and provides the added benefit of not needing a kernel vulnerability to do so. I expect future A11 research platforms to be based around that capability.

Conclusion
----------

One of the things I hoped to convey in this post is that the path to discovering this KTRR bypass was surprisingly straightforward. Considering Ian's prior work looking at self-hosted debug, the extensive ARM documentation on external debug, the public research on the Nailgun attack on Android, and the XNU sources practically spelling out how to execute dynamically generated instructions, I’m confident that I'm not the first one to discover this issue.  
  

My general fear is that the secrecy surrounding knowledge and techniques in the iOS security research community is allowing the privately held state-of-the-art of security research to diverge from the publicly shared state-of-the-art. If this happens, it puts defenders at a systemic disadvantage.  
  

I suspect that KTRR bypasses (and this bypass in particular) are one example of this divergence. Having spoken with several members of the iOS research community, I believe knowledge of these debug registers was widespread in certain circles. For example, Xerub ([@xerub](https://twitter.com/xerub)) presented a slide at MOSEC 2018 that hinted at the surprising capabilities offered by debugging features. And Siguza hinted at a KTRR bypass in his [blog post on APRR](https://siguza.github.io/APRR/).  

Furthermore, I suspect that other KTRR bypass techniques have been privately discovered. This technique is not the only way to bypass KTRR, and there are almost certainly techniques that still work on the A12. And yet, researchers rarely if ever publicly admit that they have these capabilities. All of which makes me wonder: what other techniques and capabilities are known only in private circles?  
  

In making KTRW public, I want to facilitate security researchers like myself interested in understanding how the iPhone works and improving its security, and hopefully narrow the gap between publicly shared and privately held capabilities in the process. Those who acquire development-fused devices have access to troves of information that other researchers (who choose not to use such devices) do not have. Adversaries looking to harm iPhone users already have these capabilities. Hopefully, with more eyes on iOS internals, we can continue to improve its security in the long run.

_

_  
  
from Hacker News https://ift.tt/344Pf4M_