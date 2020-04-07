---
title: 'Great Microprocessors of the Past'
date: 2020-01-11T04:47:00+01:00
draft: false
---

  
  
from Hacker News https://ift.tt/2glzZu1

### Section Seven: _Weird and Innovative Chips_

### Part I: Intel 432, Extraordinary complexity (1980) . .

The Intel iAPX 432 was a complex, object oriented 32-bit processor that included high level operating system support in hardware, such as process scheduling and interprocess messaging. Originally named the 8800 (a progression from previous 8008 and 8080), it was intended to be the main Intel 32-bit microprocessor (the [8086](http://www.cpushack.com/CPU/cpu3.html#8086) was envisioned as a short term "plan B" product until the 432 was available when it was delayed, so little effort was spent on the design (some say two engineers took only three weeks, but that was probably only the initial architecture). Others say the [80286](http://www.cpushack.com/CPU/cpu3.html#80286) was envisioned as a step between the [8086](http://www.cpushack.com/CPU/cpu3.html#8086) and the 432, rushed through design when the 432 was late and resulting its own design problems, but was actually designed later). The 432 actually included four chips. The GDP (processor) and IP (I/O controller) were introduced in 1980, and the BIU (Bus Interface Unit) and MCU (Memory Control Unit) were introduced in 1983 (but not widely). The GDP complexity was split into 2 chips (decode/sequencer and execution units, like the [Western Digital MCP-1600](http://www.cpushack.com/CPU/cpu2.html#MCP1600)), so it wasn't really a microprocessor.

The GDP was exclusively object oriented - normal linear memory access wasn't allowed, and there was hardware support for data hiding, methods, inheritance, late binding, and access protection, and it was promoted as being ideal for the Ada programming language. To enforce this, permission and type checks for every memory access (via a 2 stage [segmentation](http://www.cpushack.com/CPU/cpuAppendC.html#segment)) slowed execution (despite cached segment tables). It supported up to 2^24 segments, each limited to 64K in size (within a 2^32 address space), but the object oriented nature of the design meant that was not a real limitation. The stack oriented design meant the GDP had no user data registers. Instructions were bit encoded (and bit-aligned in memory), ranging from 6 bits to 321 bits long (the [T-9000](http://www.cpushack.com/CPU/cpu7.html#T9000) has variable length byte encoded/aligned instructions) and could be very complex.

The BIU defined the bus, designed for multiprocessor support allowing up to 63 modules (BIU or MCU) on a bus and up to 8 independent buses (allowing memory interleaving to speed access). The MCU did automatic parity checking and ECC error correcting. The total system was designed to be fault tolerant to a large degree, and each of these parts contributes to that reliability.

Despite these advanced features, the 432 didn't catch on. The main reason was that it was slow, sometimes up to five or ten times slower than a [68000](http://www.cpushack.com/CPU/cpu3.html#68000) or Intel's own [80286](http://www.cpushack.com/CPU/cpu3.html#80286). Part of this was the lack of local (user) data registers, or a data cache. Part of this was the fault-tolerant BIU, which defined an (asynchronous protocol) clocked bus that resulted in 25% to 40% of the access time being used by wait states. The instructions weren't aligned on bytes or words, and took longer to decode. In addition, the protections imposed on the objects slowed data access. Finally, the implementation of the GDP on two chips instead of one produced a slower product. However, the fact that this complex design was produced and bug free is impressive.

Its high level architecture was similar to the [Transputer](http://www.cpushack.com/CPU/cpu7.html#Transputer) systems, but it was implemented in a way that was much slower than other processors, while the [T-414](http://www.cpushack.com/CPU/cpu7.html#T414) wasn't just innovative, but much faster than other processors of the time.

* * *

The [Intel i960](http://www.cpushack.com/CPU/cpu5.html#960) is sometimes considered a successor of the 432 (also called "RISC applied to the 432"), and does have similar hardware support for context switching. This path came about indirectly through the [960 MC](http://www.cpushack.com/CPU/cpu5.html#960) designed for the BiiN machine, which was still very complex (it included many i432 object-oriented ideas, including a tagged memory system). The M-series design predated the released i960 (which removed tag bits and complex instruction microcode), but was released later.

* * *

### Part II: Rekursiv, an object oriented processor .

The Rekursiv processor is actually a 4 chip processor motherboard, not a microprocessor, but is neat. It was created by a Scottish Hi-Fi manufacturing company called Linn, to control their manufacturing system. The owner (Ivor) was a believer in automation, and had automated the company as much as possible with [Vaxes](http://www.cpushack.com/CPU/cpuAppendA.html#VAX), but wasn't satisfied, so hired software experts to design a new system, which they called LINGO. It was completely object oriented, like Smalltalk (and unlike C++, which allows object concepts, but handles them in a conventional way), but too slow on the VAXes, so Linn commissioned a processor designed for the language.

This is not the only processor designed specifically for a language that is slow on other CPUs. Several specialized LISP processors, such as the Scheme-79 lisp processor, were created, but this chip is unique in its object oriented features at a time when the concept wasn't well-known (actually, I hadn't the foggiest idea of what object-oriented programming was when I first learned about it - obvious from reading unrevised versions of this description). It also manages to support objects without the slowness of the [Intel 432](http://www.cpushack.com/CPU/cpu7.html#432).

The Rekursiv processor features a writable instruction set, and is highly parallel. The four chips were Numerik, Logik, Objekt, and Klock.

The CPU itself consisted of Numerik and Logik. Numerik was the ALU, based on [AMD 2900-series](http://www.cpushack.com/CPU/cpu1.html#2903) bitslice CPU components (sixteen 32-bit registers, ALU, barrel shifter, 32x32-bit multiplier). The CPU was similar to the [Patriot Scientific PSC1000](http://www.cpushack.com/CPU/cpu7.html#PSC1000), with sixteen registers, an evaluation stack, and a return address stack. A 64k area (16k X 128 bit words) held [microcode](http://www.cpushack.com/CPU/cpuAppendC.html#microcode), allowing an instruction set to be constructed on the fly, and could change for different objects. There were two program counters, one for application instructions, one for the microcode routines which implement them. Microcode used sixty-field 160-bit words.

Logik was the instruction sequencer.

Objekt was the object manager/MMU, which swapped objects to and from disk as needed (completely invisible to the CPU, allowing microcoded instructions to access objects without generating exceptions and forcing them to roll back and restart - microcode could be recursive, hence the processor's name). Objects were identified by 40-bit tags, with the actual reference, types, and sizes stored in three 64K hash table (collisions were resolved by a fourth table holding the ID of the object actually stored in the tables at a given time). Objects could be relocated transparently, facilitating garbage collection.

Klock was the clock and support circuitry.

It executed LINGO fast enough, and is a perfect match between language and CPU, but it could also use more conventional languages, such as Smalltalk or C. Unfortunately, Linn did not have the resources to pursue this very promising (the prototype was "surprisingly easy" to implement) architecture. However, the writable instruction set concept (specifically, isolating CPU implementation from the program code) was resurrected and automated in the [Intel 80x86](http://www.cpushack.com/CPU/cpu6.html#transmeta%3ETransmeta%20Crusoe%3C/a%3E%20architecture,%20using%0Asophisticated%20compiling%20and%20translating%20technology%20to%20implement%20the%0A%3Ca%20href=) instruction set on a custom [VLIW](http://www.cpushack.com/CPU/cpuAppendC.html#VLIW) processor.

* * *

Rekursiv:

[http://www.brouhaha.com/~eric/retrocomputing/rekursiv/](http://www.brouhaha.com/~eric/retrocomputing/rekursiv/)

* * *

### Part III: MISC M17: Casting Forth in Silicon\[1\] (pre 1988?) . .

[Forth](http://www.cpushack.com/CPU/cpuAppendB.html#Forth) is used widely for programming embedded systems because of its simplicity and efficiency. It explicitly manipulates data on a stack, and so defines a simple virtual machine architechture which makes programs independent of the CPU - only the interpreter needs to be ported. Because of this, extra CPU features are wasted when running Forth programs, and since cost reduction is important to embedded systems, it's logical to want a simpler, cheaper CPU which runs only Forth programs.

The Minimum Instruction Set Computer (MISC) Inc. M17 CPU wasn't the first Forth microprocessor (the Novix NC4000/4016 (1985?) designed by Forth inventor Chuck Moore came before), but the M17 is a good example of low cost Forth CPUs. It featured two 16 bit stack pointers (Data and Return (subroutine) stacks), plus three 16-bit top of stack data registers (X, Y, Z, plus an extra LastX which could hold values popped from X). An I/O register buffered data during I/O while the ALU operated concurrently. Finally, there was an Index register which normally held the top element of the Return stack, but could also be used as a loop counter, and a 6 instruction buffer (for short loops, like the [Motorola 68010](http://www.cpushack.com/CPU/cpu3.html#68010)).

Address space was 64K, but external memory could be either a single bank or up to five banks, signaled by status pins, depending on the context - data stack, return stack, program code, A or B buffers. Some other Forth processors include on chip stack memory, and while most (including the M17) were 16 bit, some 32 bit Forth processors have also been developed.

The simplicity of design allows the M17 (and most other Forth CPUs, such as the more recent 7,000 transistor MuP21 (also designed by Chuck Moore), which includes a composite video generator on chip) to execute instructions in only two cycles (load, execute), or one cycle each from the instruction cache, making them faster than more complex CPUs (though instructions do less, the higher clock speed usually compensates). Stack advocates often cite this as the strongest advantage for stack based designs, though critics contend that the state nature of stacks compared to registers make conventional speedup tricks such as pipelining and superscalar execution far more complex than using a register array. As it is, register-based load-store processors dominate when it comes to speed.

Other prominent Forth-based microprocessors include the Harris RTX-2000, a descendant of the NC4016 (the "-2000" like the name of the [Motorola 68000](http://www.cpushack.com/CPU/cpu3.html#68000) comes from the fact that it only uses about 2000 gates in its design) which has the ability to group certain instructions like the [T-9000 Transputer](http://www.cpushack.com/CPU/cpu7.html#T9000) and [microJava](http://www.cpushack.com/CPU/cpu7.html#microJava) processors. Chuck Moore went on to design the 20-bit MuP21, and is involved in the highly integrated F21 (expected late 1998/early 1999) CPUs. A 32 bit CPU, the FRISC-3 (Forth Reduced Instruction Set Computer) was produced by Silicon Composers and renamed the SC-32, and includes an automatic stack-to-memory cache, eliminating the main weakness of Forth chips, the fixed stack sizes.

* * *

\[1\] Sun Microelectronics' first slogan for its Java Processors was "Casting Java in Silicon".  

* * *

Stack Computers: the new wave (online book):

[http://www.cs.cmu.edu/~koopman/stack\_computers/index.html](http://www.cs.cmu.edu/~koopman/stack_computers/index.html)

Stack Computers & Forth (links):

[http://www-2.cs.cmu.edu/~koopman/stack.html](http://www-2.cs.cmu.edu/~koopman/stack.html)

Forth Chips (more links):

[http://www.ultratechnology.com/chips.htm](http://www.ultratechnology.com/chips.htm)

* * *

### Part IV: AT&T CRISP/Hobbit, CISC amongst the RISC (1987) . . . .

The AT&T Hobbit ATT92010 (around 1992) was a commercial version of the CRISP processor, inspired by the Bell Labs C Machine project, aimed at a design optimised for the C language (designed in part by David Ditzel, who later worked on the 64-bit [SPARC](http://www.cpushack.com/CPU/cpu4.html#SPARC), and later the [AMD 29000](http://www.cpushack.com/CPU/cpu6.html#transmeta%3ETransmeta%3C/a%3E).%20Since%20C%20is%20a%20stack%0Abased%20language,%20the%20processor%20is%20optimised%20for%20memory%20to%20memory%20stack%0Abased%20execution,%20and%20has%20no%20user%20visible%20registers%20(stack%20pointer%20is%0Amodified%20by%20special%20instructions,%20an%20accumulator%20is%20in%20the%20stack),%20with%0Athe%20goal%20of%20simplifying%20the%20compiler%20as%20much%20as%20possible.%3CP%3E%0A%20%20%20%20Instead%20of%20registers,%20a%20thirty-two%20entry%2032%20bit%20two%20ported%20stack%0Acache%20is%20provided.%20This%20is%20similar%20to%20the%20stack%20cache%20of%20the%0A%3CA%20href=) (in Hobbit it's much smaller (64 32-bit words) but is easily expandable), and Hobbit has no global registers. Addresses can be memory direct or indirect (for pointers) relative to the stack pointer without extra instructions or operand bits. The cache is not optimised for multiprocessors.

Hobbit has an instruction prefetch buffer (3K in 92010, 6K in the 92020), like the [8086](http://www.cpushack.com/CPU/cpu3.html#8086), but decodes the variable length (1, 3 or 5 halfword (16 bit)) instructions into a thirty-two entry instruction cache. Branches are not delayed, and a prediction bit directs [speculative branch execution](http://www.cpushack.com/CPU/cpuAppendC.html#speculative). The decode unit folds branches into the decoded instructions (which include next and alternate next PC), so a predicted branch does not take any clock cycles. The three stage execution unit takes instructions from the decode cache. Results can be forwarded when available to any prior stage as needed.

Though CISC in philosophy, the Hobbit is greatly simplified compared to traditional memory-data designs, and features some very elegant design features. AT&T prefers to call it a RISC processor, and performance is comparable to similar load-store designs such as the [ARM](http://www.cpushack.com/CPU/cpu4.html#ARM). Its most prominent use was in the EO Personal Communicator, a competitor to Apple's Newton which used the [ARM](http://www.cpushack.com/CPU/cpu4.html#ARM) processor, as well as a prototype development machine for BeOS. The product and name were discontinued.

As an aside, the complexity in making a stack-based CPU fast led fellow AT&T researchers working on the Inferno operating system to decide on a register based virtual machine, rather than stack-based like Sun Java and Microsoft .NET IL.

* * *

Wide hardware and applications support for AT&T Hobbit chips:

[http://www.att.com/press/1192/921116.mea.html](http://www.att.com/press/1192/921116.mea.html)

Hobbit

[http://mes.loyola.edu/faculty/phs\_eg769/hobbit.htm](http://mes.loyola.edu/faculty/phs_eg769/hobbit.htm)

The design of the Inferno virtual machine

[http://www.cs.bell-labs.com/cm/cs/who/rob/hotchips.html](http://www.cs.bell-labs.com/cm/cs/who/rob/hotchips.html)

* * *

### Part V: T-9000, parallel computing (1994) . . . . . .

The INMOS T-9000 was the latest version of the Transputer architecture, a processor designed to be hooked up to other processors for parallel processing. The previous versions were the 16 bit T-212 and 32 bit T-414 and T-800 (which included a 64 bit FPU) processors (1983 and 1985). The instruction set is minimised, like a RISC design, but is based on a stack/accumulator design (similar in idea to the [PDP-8](http://www.cpushack.com/CPU/cpu2.html#PDP8)), and designed around the OCCAM language. The most important feature is that each chip contains 4 serial links to connect the chips in a network.

While the transputers were originally faster than their contemporaries, recent load-store designs have surpassed them. The T-9000 was an attempt to regain the lead. It starts with the architecture of the T-800 which contains only three 32 bit integer and three 64 bit floating point registers which are used as an evaluation stack - they are not general purpose. Instead, like the [TMS 9900](http://www.cpushack.com/CPU/cpu3.html#9900), it uses memory, addressed relative to the workspace register (the 9900 workspace contained only sixteen registers, the Transputer workspace can be any length, though access slows down with every 4 bits used for offset from the workspace register - sixteen bytes can be accessed with just one instruction, 256 needs two, and so on). This allows very fast context switching, less than a microsecond, speeding and simplifying process scheduling enough that it is automated in hardware (supporting two priority levels and event handling (link messages and interrupts)). The [Intel 432](http://www.cpushack.com/CPU/cpu7.html#432) also attempted some hardware process scheduling, but was unsuccessful.

Unlike the [TMS 9900](http://www.cpushack.com/CPU/cpu3.html#9900), the T-9000 is far faster than memory, so the CPU has several levels of high speed caches and memory types. The main cache is 16K, and is designed for 3 reads and 1 write simultaneously. The workspace cache is based on 32 word rotating buffers, allows 2 reads and 1 write simultaneously.

Instructions are in bytes, consisting of 4 bit op code and 4 bit data (usually a 16 byte offset into the workspace), but prefix instructions can load extra data for an instruction which follows, 4 bits at a time. Less frequent instructions can be encoded with 2 (such as process start, message I/O) or more bytes (CRC calculations, floating point operations, 2D block copies and scheduler queue management). The stack architecture makes instructions very compact, but executing one instruction byte per clock can be slow for multibyte instructions, so the T-9000 has a grouper which gathers instruction bytes (up to eight) into a single CISC-type instruction then sent into the 5 stage pipeline (fetching four per cycle, grouping up to 8 if slow earlier instructions allow it to catch up). For example, two concurrent memory loads (simple or indexed), a stack/ALU operation and a store (a\[i\] = b\[2\] + c\[3\]) can be grouped.

The T-9000 contains 4 main internal units, the CPU, the VCP (handling the individual links of the previous chips, which needed software for communication), the PMI, which manages memory, and the Scheduler.

This processor is ideal for a model of parallel processing known as systolic arrays (a pipeline is a simple example). Even larger networks can be created with the C104 crossbar switch, which can connect 32 transputers or other C104 switches into a network hundreds of thousands of processors large. The C104 acts like a instant switch, not a network node, so the message is passed through, not stored. Communication can be at close to the speed of direct memory access.

Like the many CPUs, the Transputers can adapt to a 64, 32, 16, or 8 bit bus. They can also feed off a 5 MHz clock, generating their own internal clock (up to 50MHz for the T-9000) from this signal, and contain internal RAM, making them good for high performance embedded applications.

Unfortunately excessive delays in the T-9000 design (partly because of the stack based design) left it uncompetitive with other CPUs (roughly 36 MIPS at 50 MHz). The T-4xx and T-8xx architecture still exist in the SGS-Thomson ST20 microcore family. SGS-Thomson and Hotachi teamed up for a successor based on the [Hitachi SH-4](http://www.cpushack.com/CPU/cpu4.html#SH4), named ST50 by SGS-Thomson and SH-5 by Hitachi.

* * *

As a note, the T-800 FPU is probably the first large scale commercial device to be proven correct through formal design methods. To simplify interrupt handling, the multi-cycle square root instruction was implemented in single cycle "step" instructions, executed three (single precision) or seven (double precision) times to perform a complete square root - a strategy also used in the first [SPARC](http://www.cpushack.com/CPU/cpu4.html#SPARC) systems for integer multiply.  

* * *

SGS-Thomson Products Contents:

[http://www.st.com/stonline/books/index.htm](http://www.st.com/stonline/books/index.htm)

The Transputer archive (links):

[http://www.afm.sbu.ac.uk/transputer/](http://www.afm.sbu.ac.uk/transputer/)

IPCA:Parallel:Vendors:Inmos (links):

[http://wotug.ukc.ac.uk/parallel/vendors/inmos/](http://wotug.ukc.ac.uk/parallel/vendors/inmos/)

Advanced Risc Machines, SGS-Thomson and Siemens:

[http://www.omimo.be/members/book\_molina.html](http://www.omimo.be/members/book_molina.html)

* * *

### Part VI: Patriot Scientific ShBoom: from Forth to Java (April 1996) . .

An innovative stack-oriented processor, the 32 bit ShBoom PSC1000 was originally meant for high speed embedded [Forth](http://www.cpushack.com/CPU/cpuAppendB.html#Forth) applications (like the [M17](http://www.cpushack.com/CPU/cpu7.html#M17) and others), but Patriot Scientific has decided to position it as a Java processor as well - though it doesn't directly execute Java bytcodes, ShBoom instructions are also byte length, and Java bytecodes can be translated very closely to the native ShBoom instruction set. In addition, unlike pure stack-based machines, the ShBoom has several general registers.

At 100MHz, the microprocessing unit (MPU) executes about one instruction per cycle, without normal instruction/data caches. Byte instructions are loaded in groups of four (32 bits), and executed sequentially. The problem of loading constants is handled in a unique way. The [68000](http://www.cpushack.com/CPU/cpu3.html#68000) and [PDP-11](http://www.cpushack.com/CPU/cpu3.html#PDP11) could load a constant stored in program memory following the current instruction, and the [Hitachi SH](http://www.cpushack.com/CPU/cpu4.html#SH) uses a similar PC-relative mode to load constants. Processors like the [Mips R3000](http://www.cpushack.com/CPU/cpu4.html#MIPS) load half a constant at a time using two instructions. [Transputers](http://www.cpushack.com/CPU/cpu7.html#Transputer) always contain 4 bits of data and 4 bits of op code in each byte instruction.

The ShBoom loads single bytes of data from the rightmost bytes of the current instruction group, and words from program memory following the current group. For example, a load byte instruction could be in position one, two or three from the left, the data would always be in the fourth (rightmost) byte. Four consecutive load word instructions would be grouped together, and the constants taken fromthe four 32 bit words following the group. This ensures data alignment without extra circuitry (but may get in the way in the future, such as for 64 bit versions).

There are sixteen 32 bit global registers (g0 to g15), a sixteen register local stack (r0 to r14 can be used as a [stack frame](http://www.cpushack.com/CPU/cpuAppendC.html#stack) (R15 is not user visible), or as a Forth return stack), and an eighteen element operand stack (s0 to s17, accessed only by data stack operations) - the stacks automatically spill and refill to and from memory, s0 and r0 can also be used as index registers, g0 is used for multiply and divide instructions. There's also an extra index register x, a loop counter ct, and a mode register (like a CC or PSW register).

The CPU also contains an I/O coprocessor on chip for simultanious I/O (much more advanced than the I/O buffer register of the [M17](http://www.cpushack.com/CPU/cpu7.html#M17), but the same idea), which communicates with the MPU via the global data registers. It's a simple, independent unit which executes small data transfer programs until I/O is complete. There are also a programmable memory interface, 8 channel DMA controller, and interrupt controller.

The system was later renamed to the more markety IGNITE. It is a very innovative and elegant attempt at combining stack and register oriented architectures, with emphasis on the stack operation simplicity. It would give Java a good home.

* * *

Patriot Scientific Corporation:

[http://www.ptsc.com/](http://www.ptsc.com/)

* * *

### Part VII: Sun picoJava - not another language-specific processor! (October 1997) . .

Sun first introduced [Java](http://www.cpushack.com/CPU/cpuAppendB.html#Java) as a combination of language, integrated classes, and a run time system called the [Java Virtual Machine (JVM)](http://www.cpushack.com/CPU/cpuAppendB.html#JVM). To support Java, Sun Microelectronics designed picoJava and microJava hardware to execute Java bytecode programs faster than a [virtual machine](http://www.cpushack.com/CPU/cpuAppendC.html#virtualmachine) or recompiled code.

The picoJava I (early 1997) is a stack oriented CPU core like the JVM, with a 64 entry stack cache (similar to the [Patriot Scientific ShBoom PSC1000](http://www.cpushack.com/CPU/cpu7.html#ShBoom)), but there are interesting differences between it and [Forth](http://www.cpushack.com/CPU/cpuAppendB.html#Forth)\-style stack CPUs. Java only uses a single stack (like many languages such as C, which the [AT&T Hobbit](http://www.cpushack.com/CPU/cpu7.html#Hobbit) and [AMD 29K](http://www.cpushack.com/CPU/cpu4.html#29K) were designed to support) and the picoJava CPU enhances performance with a 'dribbler' unit which constantly updates a complete copy of the stack cache in memory, without affecting other CPU operations (similar to a write-back cache), so stack frames can be added without waiting for a stack frame to be stored. Some Java instructions are complex, so the CPU has [microcoded](http://www.cpushack.com/CPU/cpuAppendC.html#microcode) instructions, and a 4 stage pipeline (fetch, decode, execute/cache, stack writeback). Finally, picoJava groups (or 'folds') load and stack operations together, executing both at once (treating the top of stack as an [accumulator](http://www.cpushack.com/CPU/cpuAppendC.html#accumulator)) (this is a much simpler version of instruction grouping tried in the [Transputer T-9000](http://www.cpushack.com/CPU/cpu7.html#T9000)), This usually eliminates 60% of stack operation inefficiency. Seldom used instructions aren't implemented, but are emulated using trap handlers.

The picoJava II (October 1997) core is used in the first actual CPU from Sun, the microJava701. It extends the pipeline to 6 stages, and can fold up to four instructions into one operation. It also adds a FPU and separate 16Kb I/D caches. Following waning interest, Sun released the picoJava core design (as well as certain older [SPARC](http://www.cpushack.com/CPU/cpu4.html#SPARC) designs) to the public (with certain reserved rights) as a type of "open source" CPU, manufactured by Fujitsu, among others. Although Sun's CPU did not include peripherals such as I/O or timers, licensed versions do.

While Sun delivered the picoJava CPU first, an engineering group at Rockwell Collins also created a Java CPU called GEM1 in 1997, but it was spun off in July 1999 into a company called Ajile to produce the aJ-100. The aJ-100 implements thread control instructions unlike the picoJava, which emulates them in software or using an OS. It is also is multithreaded, supporting two JVMs operating independently. A lower cost aJ-80 uses an 8-bit data bus rather than 32-bits of the aJ-100.

Advancel initially made designs based on the picoJava I and II, but later designed their own TinyJ CPU which translates simple Java bytecodes to a conventional load/store execution unit (like the [ARM](http://www.cpushack.com/CPU/cpu4.html#ARM) CPU). Complex bytecodes are trapped and emulated. The ALU is a load-store style unit with sixteen 32-bit registers, a 64-bit "top of stack" accumulator used in bytecode interpretation, and a four stage pipeline with variable length (one to four byte) instructions. Non-Java programs are executed directly, and Java programs are interpreted using the decoder for the bytecode, while a conventional JVM executes directly as a non-Java program (various JVMs can be used).

* * *

Sun Microsystems:

[http://www.sun.com/](http://www.sun.com/)

picoJava Core:

[http://www.sun.com/microelectronics/picoJava/](http://www.sun.com/microelectronics/picoJava/)

Fujitsu Java Solutions:

[http://www.fujitsu.com/services/microelectronics/product/micom/java/webpage\_pdt-mic-java.html](http://www.fujitsu.com/services/microelectronics/product/micom/java/webpage_pdt-mic-java.html)

aJile aJ-100:

[http://www.ajile.com/aj100.htm](http://www.ajile.com/aj100.htm)

Advancel Logic Corp. - Product Datasheets:

[http://209.61.201.106/advancel/datasheets.htm](http://209.61.201.106/advancel/datasheets.htm)

* * *

### Part VIII: Imsys Cjip - embedded WISC (Writable Instruction Set Computer) (Mid 2000) .

Swedish company Imsys AB started making components for embedded imaging systems, and decided to expand into more general microcontroller systems with the Cjip (pronounced... somehow).

Binary compatibility has been a problem since the beginning of programmable computers, in that it ties software (abstract, theoretical) to particular hardware (fixed, physically limited). There have been attempts to reduce this through hardware using rewritable microcode ([Western Digital MCP-1600](http://www.cpushack.com/CPU/cpu2.html#MCP1600)), as well as software ([Patriot Scientific ShBoom PSC1000](http://www.cpushack.com/CPU/cpu6.html#transmeta%3ETransmeta%20Crusoe%3C/a%3E%0Awhich%20interprets,%20translates,%20and%20optimises%2080x86%20code%20as%20its%20executed,%0Aand%20the%0A%3CA%20href=) which recompiles Java bytecodes to its native instruction set when loaded). Since the Cjip is a very low resource CPU, the software overhead would be unacceptable, so Imsys followed the hardware approach using rewritable microcode. Imsys had some experience with [UCSD Pascal](http://www.cpushack.com/CPU/cpuAppendB.html#pMachine), an early VM system.

Unlike the [DEC Alpha](http://www.cpushack.com/CPU/cpu5.html#alpha) PALCode or [Rekursiv](http://www.cpushack.com/CPU/cpu7.html#Rekursiv) CPU, Cjip uses actual 72-bit wide microcode, which is far more efficient but harder to program, while unlike the MCP-1600, Cjip microcode can be modified at runtime. In addition, instructions can be emulated with regular program subroutines. Four initial instruction sets available include a legacy [Z-80](http://www.cpushack.com/CPU/cpu1.html#Z80)\-style, and three stack-based virtual machines: C/C++ and 32-bit [Forth](http://www.cpushack.com/CPU/cpuAppendB.html#Forth), [Java](http://www.cpushack.com/CPU/cpuAppendB.html#JVM), and 16-bit [Forth](http://www.cpushack.com/CPU/cpuAppendB.html#Forth).

The microcode sees four banks of 256 bytes, split into: evaluation stack, internal locals stack (microcode subroutines), general data (emulated registers), microcode internal variables. The evaluation and data stack spill into external RAM. The general data stack is in external memory only.

Language-specific processors have generally failed, because economies from widespread use of general-purpose processors allows new technology to be incorporated more quickly. The difference with Cjip is that its language support is not limited to just one language - or any language at all. It will be interesting to see if the advantages of generalized language support are enough to win acceptance over competing processors.

* * *

Imsys AB:

[http://www.imsys.se/](http://www.imsys.se/)

* * *

[Previous Page](http://www.cpushack.com/CPU/cpu6.html)  
[Table of Contents](http://www.cpushack.com/CPU/cpu.html#tableofcontents)  
[Next Page](http://www.cpushack.com/CPU/cpuAppendA.html)