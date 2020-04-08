---
title: 'Small C Compilers'
date: 2019-10-10T03:18:00+01:00
draft: false
---

Welcome to bootstrapping!\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=1 "Edit section: Welcome to bootstrapping!")\]
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

This wiki is about bootstrapping. Building up compilers and interpreters and tools from nothing.

> "Recipe for yogurt: Add yogurt to milk." - Anon.

short sci fi story [Coding Machines](https://www.teamten.com/lawrence/writings/coding-machines/) by _Lawrence Kesteloot, January 2009_

Also see [http://bootstrappable.org](http://bootstrappable.org), which has pointers to a mailing list and IRC channel.

> Simple explanation: bootstrapping is about building a compiler using tools smaller than itself, as opposed to building a compiler using an already built version of itself. The problem with the second is: Where did that prebuilt binary come from?

### Current Topics\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=2 "Edit section: Current Topics")\]

Past Research\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=3 "Edit section: Past Research")\]
-------------------------------------------------------------------------------------------------------------------------------------------

[bcompiler](https://github.com/certik/bcompiler) by Grimley Evans

This is a detailed log of the process of bootstrapping a series of languages up starting from just a hex assembler written using a hex editor.

[The Cuneiform Tablets of 2015](http://www.vpri.org/pdf/tr2015004_cuneiform.pdf) by Long Tien Nguyen, Alan Kay

This discusses methods of long term software preservation. Briefly about hardware that will not degrade over time, but the majority of the paper is about how to design a software stack that can be executed in the far future. In order to achieve this they recommend build everything in terms of a machine with a short simple specification.

[jonesforth.S](https://github.com/nornagon/jonesforth/blob/master/jonesforth.S) by Richard W.M. Jones

In depth literate programming describing a complete implementation of forth. Bootstrapped from intel 32 bit assembly with lots of assembler macros into a fully self extensible forth. This is a really illuminating read, teaching a lot of details about forth as well as showing just how minimal a runtime it is possible to make a programming language with.

[stoneknifeforth](https://github.com/kragen/stoneknifeforth) by Kragen

Kragen (again) doing amazing bootstrapping/self hosting work. This forth is implemented in a screenful of code, able to emit ELF files directly. Self extensible. Single char word names.

[amber](https://speakerdeck.com/nineties/creating-a-language-using-only-assembly-language) by nineties

These slides outline the developement of rowl and amber. This is a programming language bootstrapped up from assembly. rowl is implemented directly in assembly then parts of the amber vm and compiler are implemented in rowl, then the rest of amber is implemented by self hosting.

[SCM-Go](https://pkelchte.wordpress.com/2013/12/31/scm-go/) by pkelcjte

This project builds a SICP-style, Scheme interpreter with a REPL in Go. The blog post describes each phase. They're simple-looking. The Github integrates it into a total of 240 lines of code. Being a simple language, the Go implementation could be ported to anything else in our collection or straight hand-assemblied. Then, more complex stuff built on it like nineties or other LISPers do.

[jrp.c](https://github.com/rain-1/src/blob/master/jrp.c) by curtism

A very small x86 JIT stack calculator implemented in C. All of the instructions are coded in a clever way to make them each a double word or a quad word.

[qcc](https://lists.linuxfoundation.org/pipermail/celinux-dev/2009-December/000217.html)

The QCC project: hooking tcc frontend up with qcc's code generator and creating a toybox style set of cc, as, ld tools.

[List of Diverse Hardware](https://www.schneier.com/blog/archives/2013/09/surreptitiously.html#c1762647)

A big concern in dealing with trust in hardware is whether it's subverted or not. Intel, AMD, and many other big names have backdoors in their chips for management purposes. Among other things... ;) One cheat to get trustworthy image is to just use a computer you have no reason to believe is subverted. Acquire it under a boring buyer, it itself is a boring tech, do your bootstrapping thing in it air gapped, and use what it produces. It will likely \*not\* be subverted \*by default\* since the interdictors and TAO folks have limited resources w/ no reason to target the system. Use several that are different for best results. To help with that, I (Nick P.) put together a list of all kinds of CPU's and execution strategies on Schneier's blog. Something I left off the list are old TI-82 calculators, Palm Pilots, etc. Lots of old stuff lying around you can get in person with cash that is probably unsubverted.

[golang talk](https://www.youtube.com/watch?v=QIE5nV5fDwA) golang transpiled from c to go

"It's time for the Go compilers to be written in Go, not in C. I'll talk about the unusual process the Go team has adopted to make that happen: mechanical conversion of the existing C compilers into idiomatic Go code". They wrote the compiler in C then translated the source code from C into Go almost automatically (had to do some manual fixing up). This is an interesting approach. Let's name it the transpile approach to self hosting.

[asmutils](http://asm.sourceforge.net/asmutils.html) a linux distro/userland implemented in assembly

This is a linux distribution implemented entirely in assembly. It doesn't depend on libc or anything.

[COMFY-65](https://pdfs.semanticscholar.org/f2bb/c26d34d2093ca0e6b9a9024573c95a8d7768.pdf) a macro assembler hosted on lisp

Henry G. Baker implements COMFY-65, a macro assembler hosted on lisp.

> With the power of the entire Lisp language available for use within COMFY-65 macros, the amount of intelligence one can embed in these macros is limitless

[B.Y.O assembler in forth](http://www.bradrodriguez.com/papers/tcjassem.txt) by Brad Rodriguez

This is a teaching document that explains how to make an assembler in forth! It shows a very forth-idiomatic style of programming, and how easy it is to make an advanced assembler once you have a working forth.

[mrustc](https://github.com/thepowersgang/mrustc) by thepowersgang

This is a rust compiler written in C++, it translates rust to C. it makes the normal self hosted rustc compiler bootstrappable! It neglects the borrow checker but is still able to compile valid input source correctly.

[bsdc](http://www.bdsoft.com/resources/bdsc.html) by Leor Zolman

A C compiler (for CP/M) implemented in assembly. 25k lines of asm.

[maru](http://piumarta.com/software/maru/) by Ian Piumarta

This is the real deal. Ian Piumarta implemented a fully bootstrappable scheme here starting from C, then self hosting to a compiler that emits binary directly. Very impressive!

[CakeML](https://cakeml.org/) by Myreen et al

CakeML is really really fascinating. They have created a theory of SML programs inside HOL, allowing them to prove properties of SML programs embedded inside HOL. They have created a (serious) compiler from SML down to assembly and proved that it preserves semantics all the way. They are then able to compile the compile simultaneously bootstrapping the proof to create a verified compiler binary for which it is proven that it compiles input programs and preserves their semantics. To my knowledge this is the first such development.

[bootstrap](https://github.com/ras52/bootstrap) by Richard Smith

This is an incredibly well developed bootstrapping project. hex assembler. elf maker. x86 assembler. linker. B compiler. C compiler. Includes implementations of various POSIX style libc functions along the way. It is extremely well written and worth studying!

[asmc](https://gitlab.com/giomasce/asmc) by Giovanni Mascellani

The asmc project is a small bootable kernel that loads up a payload which. payloads exist for assembly compilers and "G language" compilers. The G language is a low level lang below C which was invented to ease bootstrapping. An assembler (which can build the kernel) has been implemented in G.

[blc](https://pimgooss.home.xs4all.nl/) by Pim Goossens

cmeta - Using ideas from META compiler compiler Pim builds the meta language up from raw hex. blc - binary lambda calculus implementation, capable of computing matt mights factorial program. built using the cmeta system. Incredibly terse. Surprising that the techniques of metacompiler compilers can be applied at such a low level. The amount of leverage may be highest in this project.

[pascal-p](https://sourceforge.net/p/pascalp5/wiki/Home/) by Pascal-P Porting Kit

"It compiles and runs a subset of the Revised Pascal language. That subset was designed to be the minimum language required to self compile for a new machine implementation. It was part of a "bootstrapping" kit designed to facilitate porting Pascal to new machines.". The pascal language was implemented with bootstrapping intention in mind. They have a simple "p code" bytecode language that eases the process.

[eulex](https://davazp.net/2012/12/08/eulex-forth-implementation.html) by David Vázquez Púa

This is a forth operating system with emacs like editor and lisp interpreter built in it. It's a 1700 line assembly script for the bootable forth compiler/interpreter and then the whole rest of the system is implemented in forth. I have not tried but apparently it can build itself with the assembler. This is very impressive work.

Past Research / intray\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=4 "Edit section: Past Research / intray")\]
-------------------------------------------------------------------------------------------------------------------------------------------------------------

important: try to summarize lessons learned from each.

*   [Pascal-S](http://www.eah-jena.de/~kleine/history/languages/Wirth-PascalS.pdf) by Wirth (Small, self-contained subset w/ great error reporting)
*   [Compiler Construction](http://www.ethoberon.ethz.ch/WirthPubl/CBEAll.pdf) by Wirth (Oberon-0 language in book is well-suited to bootstrapping)
*   [Edison](http://brinch-hansen.net/papers/1981b.pdf) by Hansen (Language w/ 5 statements & small OS on PDP-11)
*   [Project Oberon](http://www.projectoberon.com/) by Wirth et al (Simple language, compiler, OS, and RISC CPU w/ source laid out like a book.)
*   [ML/I and Sal](https://www.computer.org/web/csdl/index/-/csdl/trans/ts/1976/02/01702350.pdf) by Tannenbaum (Macro system bootstrapping low-level language, Sal, they built an OS with)
*   [COLA whitepaper](http://piumarta.com/papers/colas-whitepaper.pdf) by Ian Piumarta
*   [PreScheme](https://en.wikipedia.org/wiki/PreScheme) using an low level s-exp IL to implement scheme.
*   [Incremental, Scheme Compiler](http://scheme2006.cs.uchicago.edu/11-ghuloum.pdf) by Ghuloum (Build Scheme-to-ASM compiler in "24, small steps;" Githubs available)
*   [Red Language](http://www.red-lang.org/p/about.html) by Rakocevic et al (LISP-like power/DSL's, can do low-level, batteries included, 1MB standalone)
*   [MinCaml](https://esumii.github.io/min-caml/index-e.html) by IPA (Efficient compiler for minimal, functional language in 2000 lines & 14-week segments)
*   [Spry](http://www.sprylang.org) by Krampe (Combines traits of LISP, Rebol, Smalltalk, and Forth; hosted on Nim; 2300loc)
*   [LCC](https://en.wikipedia.org/wiki/LCC_(compiler)) by Hanson and Fraser (A 20Kloc compiler w/ book describing its workings; literate code; non-FOSS, but free non-commercial)
*   [Axiomatic Bootstrapping: A Guide for Compiler Hackers](http://www.cs.princeton.edu/research/techreps/TR-451-94) by Andrew Appel (bootstrapping SML)
*   [Merlin: Just Add Reflection](http://www.merlintec.com/lsi/jabs7.html) (bootstrapping object oriented merlin)
*   [booting BCPL](http://www.gtoal.com/languages/bcpl/amiga/bcpl/booting.txt) (bootstrapping BCPL using intcode)
*   [High-level Assembly](https://en.wikipedia.org/wiki/High_Level_Assembly) by Hyde (Assembly w/ high-level data types, control flow & a stdlib; use/check just what you need)
*   [Linoleum](https://en.wikibooks.org/wiki/Linoleum) by Ghignola (Cross-platform, lean, fast, assembly-like language)
*   [wingolog](https://wingolog.org/archives/2016/01/11/the-half-strap-self-hosting-and-guile) about the guile compiler (all brilliant posts!)
*   [Partcl](http://zserge.com/blog/tcl-interpreter.html) by Zaitsev (Tiny TCL; TCL's parse & interpret easily; also references Picol etc)
*   [\[1\]](http://repo.or.cz/ld.git/blob/HEAD:/nld.c) neatld linker by ali grudi (and also [neatas](http://repo.or.cz/neatas.git) [neatcc](http://repo.or.cz/neatcc.git))
*   [SchemeRepo](https://www.cs.indiana.edu/scheme-repository/code.lang.html) by Univ. of Indiana (Pile of source for Scheme lexers, parsers, comilers, etc.)
*   [https://www.youtube.com/watch?v=Sk9TatW9ino](https://www.youtube.com/watch?v=Sk9TatW9ino) Tutorial: Building the Simplest Possible Linux System - Rob Landley
*   [Om Language](https://sparist.github.io/Om/) by sparist (Prefix, typeless language with three operators; concatenative like Forth)
*   [\[2\]](http://tratt.net/laurie/blog/entries/the_bootstrapped_compiler_and_the_damage_done.html) by Laurence Tratt
*   [SBCL: a Sanely-Bootstrappable Common Lisp](http://www.doc.gold.ac.uk/~mas01cr/papers/s32008/sbcl.pdf) by Christophe Rhodes
*   prescheme to c compiler - [https://github.com/nineties-retro/sps](https://github.com/nineties-retro/sps)
*   [Ur-Scheme](http://canonical.org/~kragen/sw/urscheme/) by Kragen Sitaker
*   [qhasm](https://cr.yp.to/qhasm.html) by Daniel Bernstein (portable form of Assembly language that standardizes machine instruction syntax across CPUs)
*   [debian rebootstrap](https://wiki.debian.org/HelmutGrohne/rebootstrap) a project with the idea that bootstrapping debian should be a repeatable process, not a hacky one off thing
*   [http://t3x.org/t3x/](http://t3x.org/t3x/) - minimal procedural language with self hosted tiny compiler
*   [\[3\]](https://github.com/skarnet/lh-bootstrap) - bootstrapping a linux system from source
*   [bootstrapping trust in compilers](https://web.archive.org/web/20171227153720/https://www.owlfolio.org/research/bootstrapping-trust-in-compilers/) blog post by Owl's portfolio
*   [programming thought experiment](https://web.archive.org/web/20170503045724/https://www.reddit.com/r/programming/comments/9x15g/programming_thought_experiment_stuck_in_a_room/c0ewj2c/) kragen comment on reddit
*   [scheme from scratch](https://code.google.com/archive/p/scheme-from-scratch/)
*   [http://interim-os.com/](http://interim-os.com/)
*   [https://github.com/m4tx/uefi-jitfuck](https://github.com/m4tx/uefi-jitfuck) UEFI JIT brainfuck
*   [https://miyuki.github.io/2017/10/04/gcc-archaeology-1.html](https://miyuki.github.io/2017/10/04/gcc-archaeology-1.html) gcc archaeology
*   [https://github.com/murisi/L2](https://github.com/murisi/L2)
*   [https://tinygo.org/faq/why-a-new-compiler/](https://tinygo.org/faq/why-a-new-compiler/)
*   [https://github.com/siraben/meta-II](https://github.com/siraben/meta-II)

### Karger-Thompson Attack\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=6 "Edit section: Karger-Thompson Attack")\]

Anything related to the karger thompson attack: proof of concept demos, mitigations, theory.

*   [multics](http://hack.org/mc/texts/classic-multics.pdf) the original paper explaining the attack (before thompson!)
*   [SCM Security](https://www.dwheeler.com/essays/scm-security.html) by Wheeler (Secure distribution & compilation of source fundamentals; Karger advised mastering it)
*   [rotten](https://github.com/rntz/rotten) by rntz (thompson attack demo)
*   [rust infection](https://manishearth.github.io/blog/2016/12/02/reflections-on-rusting-trust/) by manishearth (thompson attack demo in the rust compiler)
*   [tcc ACSAC](https://www.dwheeler.com/trusting-trust/tcc.html) by daved wheeler
*   [CompCert](http://compcert.inria.fr/) by Leroy et al (Mathematically-verified, C compiler whose specs and proofs checked with tiny, verified checker)
*   [CakeML](https://cakeml.org/) by Myreen et al (Mathematically-verified, SML compiler whose specs and proofs checked with different, tiny, verified checker)
*   [VLISP](https://en.wikipedia.org/wiki/PreScheme) by Oliva and Wand (Article has links to VLISP which mathematically verified PreScheme and Scheme48)
*   [KCC](https://github.com/kframework/c-semantics) by Rosu et al (Executable, formal semantics for C in rewrite logic; could do that w/ simpler engine)
*   [TALC](https://www.cs.cornell.edu/talc/) by Cornell (Typed, assembly language to verify safety w/out compiler; checker can be simple; C subset + verified compiler to TALC)
*   [CoqASM](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/12/coqasm.pdf) by Microsoft Research (Bootstrap in verifiably-safe assembly in prover checked by tiny, verified checker)

### Ubiquitous Implementations\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=7 "Edit section: Ubiquitous Implementations")\]

These are tools written in ubiquitous languages, therefore they can be used in a wide variety of contexts.

*   [shasm](https://lists.gnu.org/archive/html/bug-bash/2001-02/msg00054.html) by Hohensee (x86 assembler written in BASH)
*   [AWKLisp](https://github.com/darius/awklisp) by Bacon (LISP written in Awk; includes Perl version from Perl Avenger)
*   [Gherkin](https://github.com/alandipert/gherkin/blob/master/README.md) by Dipert (LISP written in Bash)
*   [BASH Infinity](https://github.com/niieani/bash-oo-framework) by Brzoska (BASH framework/routines that might help write compilers in it)
*   [mal](https://github.com/kanaka/mal) "make a lisp" implementing a very basic lisp interpreter in hundreds of languages
*   [\[4\]](https://github.com/mniip/BOOTSTRA/blob/master/STRAP/STRAP.STR) A new bootstrapping project that is built up to a self host language above assembly from a minimal DOS platform.

### Small C Compilers\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=8 "Edit section: Small C Compilers")\]

*   [c4](https://github.com/rswier/c4/blob/master/c4.c) by rswier (incredibly short c compiler)
*   [cc500](https://web.archive.org/web/20160402225843/http://homepage.ntlworld.com/edmund.grimley-evans/cc500/) by edmund grimley-evans (tiny c compiler)
*   [CUCU](http://zserge.com/blog/cucu-part1.html) by Zaitsev (Small, C compiler designed for easy understanding)
*   [SmallerC](https://github.com/alexfru/SmallerC) by Frunze (Small, single-pass, C compiler for several ISA's)
*   [picoc](https://github.com/zsaleeba/picoc) interpreter.
*   [C Interpreter](http://www.drdobbs.com/cpp/building-your-own-c-interpreter/184408184) by Dr Dobbs (Describes building a C interpreter with source)
*   [\[5\]](http://www.physics.rutgers.edu/~vitchev/smallc-i386.html) Small C for I386 (IA-32)
*   [Selfie](http://selfie.cs.uni-salzburg.at), a tiny self-compiling compiler for a subset of C, a tiny self-executing MIPS emulator, and a tiny self-hosting MIPS hypervisor, all in a single 7kLoC file. [HN discussion.](https://news.ycombinator.com/item?id=13778353) [Paper.](http://www.cs.uni-salzburg.at/~ck/content/publications/conferences/Onward17-Selfie.pdf)
*   [Tiny C expression compiler Written in Forth](https://groups.google.com/forum/#!topic/comp.lang.forth/lBYFfVJ1qhc) based on [tinyc.c](http://www.iro.umontreal.ca/~felipe/IFT2030-Automne2002/Complements/tinyc.c) by marc feeley.
*   [\[6\]](https://github.com/rui314/8cc) [\[7\]](https://github.com/rui314/9cc) C compilers by Rui Ueyama [blog](https://www.sigbus.info/how-i-wrote-a-self-hosting-c-compiler-in-40-days.html)
*   [\[8\]](https://github.com/Fedjmike/mini-c/blob/master/cc.c) 10 hour self hosting c compiler

### Grammars, Parsing, and Term Rewriting\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=9 "Edit section: Grammars, Parsing, and Term Rewriting")\]

*   [Grammar Executing Machine](http://www.cs.dartmouth.edu/~mckeeman/cs48/mxcom/gem/html/GrowingCompiler.html) by McKeeman and He (Incrementally extend languages from simple to complex grammars in interpreter(s))
*   [peg](https://github.com/kragen/peg-bootstrap/blob/master/peg.md) by kragen (parsing)
*   [PEG-based simple compiler](http://www.vpri.org/pdf/tr2010003_PEG.pdf) by Ian Piumarta
*   [META II](http://www.bayfronttechnologies.com/metaii.html) by Bayfront Tech (Original meta-compiler w/ live code and detailed tutorial; OMeta was successor)
*   [META II implementation](https://github.com/lugon/META-II) by Lugon (Looks like a small implementation of META II; also bootstrapped in META II)
*   [OMeta# Intro](http://www.moserware.com/2008/06/ometa-who-what-when-where-why.html) by Moser (OMeta intro that nicely illustrates the meta approach/advantages)

### Virtual Machines, Instruction Sets\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=10 "Edit section: Virtual Machines, Instruction Sets")\]

*   [P-code](https://en.wikipedia.org/wiki/P-code_machine) by Wirth (High-level language & libraries target ultra-simple, portable interpreter)
*   [sweet16](http://www.6502.org/source/interpreters/sweet16.htm) by Steve Wozniak
*   [Tiny BASIC](https://en.wikipedia.org/wiki/Tiny_BASIC) by Allison (Small BASIC whose original VM took 120, virtual opcodes to implement using 3KB RAM)
*   [Klip](https://github.com/DatCodingGuy/Klip) by Cutting (Compiler & runtime for simple language for students; done in C#; runtime is very readable)

### CPU's for Bootstrapping: The Simple, The Verified, and The Necessarily Complex\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=11 "Edit section: CPU's for Bootstrapping: The Simple, The Verified, and The Necessarily Complex")\]

*   [NAND2Tetris](http://nand2tetris.org/) by Nisan and Schocken (Guide that teaches hardware step-by-step in fun way with simple CPU emerging)
*   [J1](http://www.excamera.com/sphinx/fpga-j1.html) by by Bowman (16-bit Forth CPU in 200 lines of Verilog that does 100MIPS on FPGA's)
*   [H2](https://github.com/howerj/forth-cpu) by Howe (Modified, VHDL version of J1 with detailed description and Howe's code MIT-licensed)
*   [RISC-0](http://www.projectoberon.com/) by Wirth (Simple, RISC CPU & SOC designed for Oberon language with detailed docs and source online)
*   [JOP](http://jopdesign.com/) by Shoeberl et al (Embedded Java processor that takes up 1830 slices on FPGA)
*   [Scheme Machine](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.57.736&rep=rep1&type=pdf) by Burger (Scheme interpreter implemented as CPU using formal methods)
*   [ZPU](https://github.com/zylin/zpu/tree/master/zpu/docs/presentations) by Zylin AS (Tiny, 32-bit CPU for deep embedded apps in 440 LUT's)
*   [J2](http://j-core.org/) by Landley et al (Clone of cost-efficient, SuperH-2 CPU in open-source)
*   [VAMP](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.217.2251) by Beyer et al (Formally-verified, DLX-style processor in 18,000 slices on Xilinx)
*   [Leon3](http://soc.microsemi.com/products/ip/search/detail.aspx?id=635) by Gaisler (Industry-grade, 32-bit SPARC w/ auto-configuration of core and GPL license)
*   [Rocket](https://github.com/freechipsproject/rocket-chip) by Univ of CA (1.4GHz RISC-V CPU and generator for customization)
*   [OpenPITON](http://parallel.princeton.edu/piton/#) by Princeton (25-core, shared-memory, SPARC CPU open-sourced and very scalable)

### Minimal Operating Systems\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=12 "Edit section: Minimal Operating Systems")\]

### Biology/Other?\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=13 "Edit section: Biology/Other?")\]

Helpful Links\[[edit](https://bootstrapping.miraheze.org/w/index.php?title=Main_Page&action=edit&section=14 "Edit section: Helpful Links")\]
--------------------------------------------------------------------------------------------------------------------------------------------

<img src="https://bootstrapping.miraheze.org/wiki/Special:CentralAutoLogin/start?type=1x1" alt="" title="" />

  
  
from Hacker News https://ift.tt/324mCUT