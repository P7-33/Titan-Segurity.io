---
title: 'Software Security Is a Programming Languages Issue'
date: 2019-12-05T02:50:00+01:00
draft: false
---

This is the the last of three posts on the course I regularly teach, [CS 330, Organization of Programming Languages](http://www.cs.umd.edu/class/spring2018/cmsc330/). The first two posts covered [programming language styles](http://www.pl-enthusiast.net/2018/07/24/teaching-programming-languages/) and [mathematical concepts](http://www.pl-enthusiast.net/2018/08/02/teaching-programming-languages-part-2/). This post covers the last 1/4 of the course, which focuses on software security, and related to that, the programming language [Rust](https://www.rust-lang.org/).

This course topic might strike you as odd: Why teach security in a programming languages course? Doesn’t it belong in, well, a _security_ course? I believe that if we are to solve our security problems, then we must build software with security in mind right from the start. To do that, _all_ programmers need to know something about security, not just a handful of specialists. Security vulnerabilities are both enabled and prevented by various language (mis)features, and programming (anti)patterns. As such, it makes sense to introduce these concepts in a programming (languages) course, especially one that all students must take.

This post is broken into three parts: the need for security-minded programming, how we cover this topic in 330, and our presentation of Rust. The post came to be a bit longer than I’d anticipated; apologies!

[![Software source code](http://www.pl-enthusiast.net/wp-content/uploads/2018/08/code-1839406_960_720-300x200.jpg)](http://www.pl-enthusiast.net/wp-content/uploads/2018/08/code-1839406_960_720.jpg)

Security is a programming (languages) concern

The Status Quo: Too Much Post-hoc Security
------------------------------------------

There is a lot of interest these days in securing computer systems. This interest follows from the highly publicized roll call of serious data breaches, denial of service attacks, and system hijacks. In response, security companies are proliferating, selling computerized forms of spies, firewalls, and guard towers. There is also a [regular call for more “cybersecurity professionals”](https://www.csoonline.com/article/3247708/security/research-suggests-cybersecurity-skills-shortage-is-getting-worse.html) to help man the digital walls.

It might be that these efforts are worth their collective cost, but call me skeptical. I believe that a disproportionate portion of our efforts focuses on adding security to a system _after it has been built_. Is your server vulnerable to attack? If so, no problem: Prop an [intrusion detection system](https://en.wikipedia.org/wiki/Intrusion_detection_system) in front of it to identify and neuter network packets attempting to exploit the vulnerability. There’s no doubt that such an approach is appealing; too bad [it doesn’t actually work](https://en.wikipedia.org/wiki/Intrusion_detection_system#Limitations). As computer security experts have been saying since at least the 60s, if you want a system to actually be secure then it must be designed and built with security in mind. Waiting until the system is deployed is too late.

### Building Security In

There is a mounting body of work that supports building secure systems from the outset. For example, the [Building Security In Maturity Model (BSIMM)](https://www.bsimm.com/) catalogues the processes followed by a growing list of companies to build more secure systems. Companies such as [Synopsys](https://www.synopsys.com/software-integrity.html) and [Veracode](https://www.veracode.com/) offer code analysis products that look for security flaws. Processes such as Microsoft’s [Security Development Lifecycle](https://www.microsoft.com/en-us/sdl) and books such as [Gary McGraw](https://www.garymcgraw.com/)‘s [Software Security: Building Security In](http://www.swsec.com/), and [Sami Saydjari](https://samisaydjari.com/)‘s recently released [Engineering Trustworthy Systems](https://www.engineeringtrustworthysystems.com/) identify a path toward better designed and built systems.

These are good efforts. Nevertheless, we need even _more_ emphasis on the “build security in” mentality so we can rely far less on necessary, but imperfect, post-hoc stuff. For this shift to happen, we need better education.

Security in a Programming Class
-------------------------------

[![Running off of a cliff](http://www.pl-enthusiast.net/wp-content/uploads/2018/08/jumping-off-1966997_960_720-300x198.jpg)](http://www.pl-enthusiast.net/wp-content/uploads/2018/08/jumping-off-1966997_960_720.jpg)

Choosing performance over security

Programming courses typically focus on how to use particular languages to solve problems efficiently. Functionality is obviously paramount, with performance an important secondary concern.

But in today’s climate shouldn’t security be at the same level of importance as performance? If you argue that security is not important for every application, I would say the same is true of performance. Indeed the rise of slow, easy-to-use scripting languages is a testament to that. But sometimes performance is very important, or becomes so later, and the same is true of security. Indeed, many security bugs arise because code originally written for a benign setting ends up in a security-sensitive one. As such, I believe _educators should regularly talk about how to make code more secure_ just as we regularly talk about how to make it more efficient.

To do this requires a change in mindset. A reasonable approach, when focusing on correctness and efficiency, is to aim for code that works under expected conditions. But expected use is not good enough for security: Code must be secure under _all_ operating conditions.

Normal users are not going to input weirdly formatted files to to PDF viewers. But adversaries will. As such, students need to understand how a bug in a program can be turned into a security vulnerability, and how to stop it from happening. Our two lectures in CS 330 on security shift between illustrating a kind of security vulnerability, identifying the conditions that make that vulnerability possible, and developing a defense that eliminates those conditions. For the latter we focus on language properties (e.g., type safety) and programming patterns (e.g., validating input).

### Security Bugs

In our [first lecture](http://www.cs.umd.edu/class/spring2018/cmsc330/lectures/software-security.pdf), we start by introducing the high-level idea of a [buffer overflow](https://en.wikipedia.org/wiki/Buffer_overflow) vulnerability, in which an input is larger than the buffer designed to hold it. We hint at how to exploit it by [smashing the stack](http://insecure.org/stf/smashstack.html). A key feature of this attack is that while the program intends for an input to be treated as data, the attacker is able to trick the program to treat it as _code_ which does something harmful. We also look at [command injection](https://www.owasp.org/index.php/Command_Injection), and see how it similarly manifests when an attacker tricks the program to treat data as code.

[![SQL injection analogy to Scrabble](http://www.pl-enthusiast.net/wp-content/uploads/2018/08/34852913554_4c401f98ca_b-300x220.jpg)](http://www.pl-enthusiast.net/wp-content/uploads/2018/08/34852913554_4c401f98ca_b.jpg)

SQL injection: malicious code from benign parts

Our [second lecture](http://www.cs.umd.edu/class/spring2018/cmsc330/lectures/web-security.pdf) covers vulnerabilities and attacks specific to web applications, including [SQL injection](https://www.owasp.org/index.php/SQL_Injection), [Cross-site Request Forgery (CSRF)](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)), and [Cross-site scripting (XSS)](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)). Once again, these vulnerabilities all have the attribute that untrusted data provided by an attacker can be cleverly crafted to trick a vulnerable application to treat that data as code. This code can be used to hijack the program, steal secrets, or corrupt important information.

### Coding Defenses

It turns out the defense against many of these vulnerabilities is the same, at a high level: _validate any untrusted input before using it_, to make sure it’s benign. We should make sure an input is not larger than the buffer allocated to hold it, so the buffer is not overrun. In any language other than C or C++, this check happens automatically (and is generally needed to ensure [type safety](http://www.pl-enthusiast.net/2014/08/05/type-safety/)).

For the other four attacks, the vulnerable application uses the attacker input when piecing together another program. For example, an application might expect user inputs to correspond to a username and password, splicing these inputs into a template SQL program with which it queries a database. But the inputs could contain SQL commands that cause the query to do something different than intended. The same is true when constructing shell commands (command injection), or Javascript and HTML programs (cross-site scripting). The defense is also the same, at a high level: user inputs need to either have potentially dangerous content removed or made inert by construction (e.g., through the use of [prepared statements](https://en.wikipedia.org/wiki/Prepared_statement)).

None of this stuff is new, of course. Most security courses talk about these topics. What is unusual is that we are talking about them in a “normal” programming languages course.

Our [security project](https://github.com/anwarmamat/cmsc330spring18-public/tree/master/p6) reflects the defensive-minded orientation of the material. While security courses tend to focus on vulnerability exploitation, CS 330 focuses on _fixing_ the bugs that make an application vulnerable. We do this by giving the students a web application, written in Ruby, with several vulnerabilities in it. Students must fix the vulnerabilities without breaking the core functionality. We test the fixes automatically by having our auto-grading system test functionality and exploitability. Several hidden tests exploit the initially present vulnerabilities. The students must modify the application so these cases pass (meaning the vulnerability has been removed and/or can no longer be exploited) without causing any of the functionality-based test cases to fail.

Low-level Control, Safely
-------------------------

The most dangerous kind of vulnerability allows an attacker to gain [arbitrary code execution](https://en.wikipedia.org/wiki/Arbitrary_code_execution) (ACE): Through exploitation, the attacker is able to execute code of their choice on the target system. Memory management errors in type-unsafe languages (C and C++) comprise a large class of ACE vulnerabilities. Use-after-free errors, double-frees, and buffer overflows are all examples. The latter is still the [single largest category of vulnerability](https://nvd.nist.gov/general/visualizations/vulnerability-visualizations/cwe-over-time#vuln-type-total-by-year-title) today, according to [MITRE’s Common Weakness Enumeration (CWE)](https://cwe.mitre.org/) database.

Programs written in type-safe languages, such as Java or Ruby, [1](http://www.pl-enthusiast.net/2018/08/13/security-programming-languages-issue/#note-1502-1 "Ruby is dynamically typed, but arguably type-safe.") are immune to these sorts of memory errors. Writing applications in these languages would thus eliminate a large category of vulnerabilities straightaway. [2](http://www.pl-enthusiast.net/2018/08/13/security-programming-languages-issue/#note-1502-2 "This is not strictly true as parts of these languages’ implementations are written in C/C++, and programs in type-safe languages can call out to C/C++ via a foreign function interface. Even so, eliminating C/C++ as a normal source programming language would dramatically reduce the attack surface.") The problem is that type-safe languages’ use of abstract data representations and [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)) (GC), which make programming easier, remove low-level control and add overhead that is sometimes hard to bear. C and C++ are essentially the only game in town [3](http://www.pl-enthusiast.net/2018/08/13/security-programming-languages-issue/#note-1502-3 "And even if it is not needed, C/C++ is still used quite a bit anyway. Old habits, and legacy code, die hard.") for operating systems, device drivers, and embedded devices (e.g., [IoT](https://en.wikipedia.org/wiki/Internet_of_things)), which cannot tolerate the overhead and/or lack of control. And we see that these systems are regularly and increasingly under attack. What are we to do?

### Rust: Type safety without GC

In 2010, the [Mozilla](https://www.mozilla.org/) corporation (which brings you Firefox) officially began an ambitious project to develop a safe language suitable for writing high-performance programs. The result is [Rust](https://www.rust-lang.org/). [4](http://www.pl-enthusiast.net/2018/08/13/security-programming-languages-issue/#note-1502-4 "Rust development began in 2006, but was not officially supported by Mozilla until later.") In Rust, type-safety ensures (with various caveats) that a program is free of memory errors and free of data races. In Rust, type safety is possible _without_ garbage collection, which is not true of any other mainstream language.

[![Rust language logo](http://www.pl-enthusiast.net/wp-content/uploads/2018/08/rust-logo-300x300.png)](http://www.pl-enthusiast.net/wp-content/uploads/2018/08/rust-logo.png)

Rust, the programming language

In CS 330, we [introduce Rust](http://www.cs.umd.edu/class/spring2018/cmsc330/lectures/00-rust-introduct.pdf) and its [basic constructs](http://www.cs.umd.edu/class/spring2018/cmsc330/lectures/02-rust-basics.pdf), showing how Rust is arguably closer to a functional programming language than it is to C/C++. (Rust’s use of curly braces and semi-colons might make it seem familiar to C/C++ programmers, but there’s a whole lot more that’s different than is the same!)

We spend much of our time talking about Rust’s use of [_ownership_ and _lifetimes_](http://www.cs.umd.edu/class/spring2018/cmsc330/lectures/03-ownership.pdf). Ownership (aka [linear typing](https://en.wikipedia.org/wiki/Substructural_type_system#Linear_type_systems)) is used to carefully track pointer aliasing, so that memory modified via one alias cannot mistakenly corrupt an invariant assumed by another. Lifetimes track the scope in which pointed-to memory is live, so that it is freed automatically, but no sooner than is safe. These features support managing memory without GC. They also support sophisticated programming patterns via [smart pointers](http://www.cs.umd.edu/class/spring2018/cmsc330/lectures//08-smart-pointers.pdf) and [traits](http://www.cs.umd.edu/class/spring2018/cmsc330/lectures/05-traits.pdf) (a construct I was unfamiliar with, but now really like). We provide a [simple programming project](https://github.com/anwarmamat/cmsc330spring18-public/tree/master/p5) to familiarize students with the basic and advanced features of Rust.

### Assessment

I enjoyed learning Rust in preparation for teaching it. I had been wanting to learn it since my [interview with Aaron Turon](http://www.pl-enthusiast.net/2015/06/09/interview-with-mozillas-aaron-turon/) some years back. The [Rust documentation](https://doc.rust-lang.org/book/) is first-rate, so that really helped.

I also enjoyed seeing connections to my own prior research on the [Cyclone programming language](https://cyclone.thelanguage.org/). (I recently reflected on Cyclone, and briefly connected it to Rust, in a [talk at the ISSISP’18 summer school](https://cs.anu.edu.au/cybersec/issisp2018/assets/slides/cyclone-overview.pdf).) Rust’s ownership relates to Cyclone’s unique/affine pointers, and Rust’s lifetimes relate to Cyclone’s regions. Rust’s smart pointers match patterns we also implemented in Cyclone, e.g., for reference counted pointers. Rust has taken these ideas much further, e.g., a really cool integration with traits handles tricky aspects of polymorphism. The Rust compiler’s error messages are also really impressive!

A big challenge in Cyclone was finding a way to program with unique pointers without tearing your hair out. My impression is that Rust programmers face the same challenge (as long as you don’t resort to frequent use of [**unsafe** blocks](https://doc.rust-lang.org/book/second-edition/ch19-01-unsafe-rust.html)). Nevertheless, [Rust is a much-loved programming language](https://insights.stackoverflow.com/survey/2018/#technology), so the language designers are clearly doing something right! Oftentimes facility is a matter of comfort, and comfort is a matter of education and experience. As such, I think Rust fits into the philosophy of CS 330, which aims to introduce new language concepts that are interesting in and of themselves, and may yet have expanded future relevance.

Conclusions
-----------

We must [build software with security in mind from the start](http://www.pl-enthusiast.net/2015/09/30/penetrate-and-patch-to-building-security-in/). Educating all future programmers about security is an important step toward increasing the security mindset. In CS 330 we illustrate common vulnerability classes and how they can be defended against by the language (e.g., by using those languages, like Rust, that are type safe) and programming patterns (e.g., by validating untrusted input). By doing so, we are hopefully making our students more fully cognizant of the task that awaits them in their future software development jobs. We might also interest them to learn more about security in a subsequent security class.

In writing this post, I realize we could do more to illustrate how type abstraction can help with security. For example, abstract types can be used to increase assurance that input data is properly validated, as explained by [Google’s Christoph Kern in his 2017 SecDev Keynote](https://secdev.ieee.org/2017/keynote/). This fact is also a consequence of _semantic_ type safety, as argued well by [Derek Dreyer in his POPL’18 Keynote](https://popl18.sigplan.org/event/popl-2018-papers-keynote-milner-lecture). Good stuff to do for Spring’19 !

  
  
from Hacker News https://ift.tt/2MENOSn