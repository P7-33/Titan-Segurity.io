---
title: 'Use Noexcept for Exception Handling in C++ Programs'
date: 2020-01-01T11:55:00+01:00
draft: false
---

### Introduction

The `noexcept` specifier was introduced in C++ standard 11. Its explanation is also very straightforward. It specifies whether a function could throw exceptions.

  

I actually did not quite understand why we would like to prevent a program from throwing exceptions. In this blog, I am going to describe how `noexcept` could be used to protect C++ programs from undesired behaviors.

### Example

It turns out that some functions, especially some black box functions from libraries, would cause memory leak when an exception is thrown. The `getArraySum` function, which is an weird orchestrated function, in the following code is a such example.

  

To prevent the undesired memory leak from happening, instead of using the `getArraySumWarraper` function, we would like to use the `getArraySumWarraperNoexcept` function with the `noexcept` specifier. When `getArraySumWarraper` is called, the program would never crash, but potentially have risk of memory leak. When we call `getArraySumWarraperNoexcept`, the program crashes whenever there is an exception thrown from `getArraySum`.

```
#include #include  int getArraySum(size_t n) { int sum = 0; int* array = new int[n]; for (int i = 0; i < n; i ++) { array[i] = i; } // Weird exception criteria // Throwing this exception would cause memory leak if (n > 10) { throw std::runtime_error{"Weird exception!"}; } for (int i = 0; i < n; i ++) { sum += array[i]; } delete array; return sum; } int getArraySumWarraper(size_t n) { return getArraySum(n); } int getArraySumWarraperNoexcept(size_t n) noexcept { return getArraySum(n); } int main(int argc, char **argv) { const int iterations = 3; size_t size; int sum; int (*fcnPtr)(size_t); if (argc == 2 && strcmp(argv[1], "--noexcept") == 0) { std::cout << "Use noexcept specifier." << std::endl; fcnPtr = getArraySumWarraperNoexcept; } else { std::cout << "Do not use noexcept specifier." << std::endl; fcnPtr = getArraySumWarraper; } std::cout << "--------------------------------------" << std::endl; for (int i = 0; i < iterations; i ++) { std::cout << "Iteration #" << i << std::endl; std::cout << "Please input array size: " << std::endl; std::cin >> size; try { sum = (*fcnPtr)(size); } catch(const std::exception& e) { std::cerr << e.what() << std::endl; } } } 
```

To compile the program, run the following command in the terminal.

```
$ g++ noexcept.cpp -o noexcept 
```

We use [Valgrind](https://valgrind.org/) to check whether the program has memory leak or not.

  

If we input three numbers 1, 2, and 3, we don’t have memory leak for the program with or without using the `noexcept` specifier.

```
$ valgrind --leak-check=yes ./noexcept ==7942== Memcheck, a memory error detector ==7942== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al. ==7942== Using Valgrind-3.13.0 and LibVEX; rerun with -h for copyright info ==7942== Command: ./noexcept ==7942== Do not use noexcept specifier. -------------------------------------- Iteration #0 Please input array size: 1 ==7942== Mismatched free() / delete / delete [] ==7942== at 0x4C3123B: operator delete(void*) (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so) ==7942== by 0x109098: getArraySum(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==7942== by 0x1090D4: getArraySumWarraper(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==7942== by 0x10925B: main (in /home/leimao/Workspace/noexcept/noexcept) ==7942== Address 0x5b7e500 is 0 bytes inside a block of size 4 alloc'd ==7942== at 0x4C3089F: operator new[](unsigned long) (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so) ==7942== by 0x108FDE: getArraySum(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==7942== by 0x1090D4: getArraySumWarraper(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==7942== by 0x10925B: main (in /home/leimao/Workspace/noexcept/noexcept) ==7942== Iteration #1 Please input array size: 2 Iteration #2 Please input array size: 3 ==7942== ==7942== HEAP SUMMARY: ==7942== in use at exit: 0 bytes in 0 blocks ==7942== total heap usage: 6 allocs, 6 frees, 74,776 bytes allocated ==7942== ==7942== All heap blocks were freed -- no leaks are possible ==7942== ==7942== For counts of detected and suppressed errors, rerun with: -v ==7942== ERROR SUMMARY: 3 errors from 1 contexts (suppressed: 0 from 0) 
```

```
$ valgrind --leak-check=yes ./noexcept --noexcept ==7865== Memcheck, a memory error detector ==7865== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al. ==7865== Using Valgrind-3.13.0 and LibVEX; rerun with -h for copyright info ==7865== Command: ./noexcept --noexcept ==7865== Use noexcept specifier. -------------------------------------- Iteration #0 Please input array size: 1 ==7865== Mismatched free() / delete / delete [] ==7865== at 0x4C3123B: operator delete(void*) (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so) ==7865== by 0x109098: getArraySum(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==7865== by 0x1090EE: getArraySumWarraperNoexcept(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==7865== by 0x10925B: main (in /home/leimao/Workspace/noexcept/noexcept) ==7865== Address 0x5b7e500 is 0 bytes inside a block of size 4 alloc'd ==7865== at 0x4C3089F: operator new[](unsigned long) (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so) ==7865== by 0x108FDE: getArraySum(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==7865== by 0x1090EE: getArraySumWarraperNoexcept(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==7865== by 0x10925B: main (in /home/leimao/Workspace/noexcept/noexcept) ==7865== Iteration #1 Please input array size: 2 Iteration #2 Please input array size: 3 ==7865== ==7865== HEAP SUMMARY: ==7865== in use at exit: 0 bytes in 0 blocks ==7865== total heap usage: 6 allocs, 6 frees, 74,776 bytes allocated ==7865== ==7865== All heap blocks were freed -- no leaks are possible ==7865== ==7865== For counts of detected and suppressed errors, rerun with: -v ==7865== ERROR SUMMARY: 3 errors from 1 contexts (suppressed: 0 from 0) 
```

If we input three numbers 100, 200, and 300, we are supposed to have memory leaks for the programs. As we can tell from the Valgrind results, without using the `noexcept` specifier, there is memory leak as expected. However, with using the `noexcept` specifier, the program would just crash.

```
$ valgrind --leak-check=yes ./noexcept ==9359== Memcheck, a memory error detector ==9359== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al. ==9359== Using Valgrind-3.13.0 and LibVEX; rerun with -h for copyright info ==9359== Command: ./noexcept ==9359== Do not use noexcept specifier. -------------------------------------- Iteration #0 Please input array size: 100 Weird exception! Iteration #1 Please input array size: 200 Weird exception! Iteration #2 Please input array size: 300 Weird exception! ==9359== ==9359== HEAP SUMMARY: ==9359== in use at exit: 2,400 bytes in 3 blocks ==9359== total heap usage: 12 allocs, 9 frees, 77,707 bytes allocated ==9359== ==9359== 2,400 bytes in 3 blocks are definitely lost in loss record 1 of 1 ==9359== at 0x4C3089F: operator new[](unsigned long) (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so) ==9359== by 0x108FDE: getArraySum(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==9359== by 0x1090D4: getArraySumWarraper(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==9359== by 0x10925B: main (in /home/leimao/Workspace/noexcept/noexcept) ==9359== ==9359== LEAK SUMMARY: ==9359== definitely lost: 2,400 bytes in 3 blocks ==9359== indirectly lost: 0 bytes in 0 blocks ==9359== possibly lost: 0 bytes in 0 blocks ==9359== still reachable: 0 bytes in 0 blocks ==9359== suppressed: 0 bytes in 0 blocks ==9359== ==9359== For counts of detected and suppressed errors, rerun with: -v ==9359== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0) 
```

```
t$ valgrind --leak-check=yes ./noexcept --noexcept ==9466== Memcheck, a memory error detector ==9466== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al. ==9466== Using Valgrind-3.13.0 and LibVEX; rerun with -h for copyright info ==9466== Command: ./noexcept --noexcept ==9466== Use noexcept specifier. -------------------------------------- Iteration #0 Please input array size: 100 terminate called after throwing an instance of 'std::runtime_error' what(): Weird exception! ==9466== ==9466== Process terminating with default action of signal 6 (SIGABRT) ==9466== at 0x541BE97: raise (raise.c:51) ==9466== by 0x541D800: abort (abort.c:79) ==9466== by 0x4EC8956: ??? (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25) ==9466== by 0x4ECEAB5: ??? (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25) ==9466== by 0x4ECDB18: ??? (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25) ==9466== by 0x4ECE487: __gxx_personality_v0 (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25) ==9466== by 0x51D5612: ??? (in /lib/x86_64-linux-gnu/libgcc_s.so.1) ==9466== by 0x51D5B70: _Unwind_RaiseException (in /lib/x86_64-linux-gnu/libgcc_s.so.1) ==9466== by 0x4ECED16: __cxa_throw (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25) ==9466== by 0x109056: getArraySum(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==9466== by 0x1090EE: getArraySumWarraperNoexcept(unsigned long) (in /home/leimao/Workspace/noexcept/noexcept) ==9466== by 0x10925B: main (in /home/leimao/Workspace/noexcept/noexcept) ==9466== ==9466== HEAP SUMMARY: ==9466== in use at exit: 585 bytes in 3 blocks ==9466== total heap usage: 7 allocs, 4 frees, 75,369 bytes allocated ==9466== ==9466== LEAK SUMMARY: ==9466== definitely lost: 0 bytes in 0 blocks ==9466== indirectly lost: 0 bytes in 0 blocks ==9466== possibly lost: 0 bytes in 0 blocks ==9466== still reachable: 585 bytes in 3 blocks ==9466== of which reachable via heuristic: ==9466== stdstring : 41 bytes in 1 blocks ==9466== suppressed: 0 bytes in 0 blocks ==9466== Reachable blocks (those to which a pointer was found) are not shown. ==9466== To see them, rerun with: --leak-check=full --show-leak-kinds=all ==9466== ==9466== For counts of detected and suppressed errors, rerun with: -v ==9466== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0) Aborted (core dumped) 
```

### Conclusions

The `noexcept` specifier protects C++ program from memory leaks and potentially other undesired behaviors brought by throwing exceptions. For key functions we hardly know how to handle its exceptions, it might be a good idea to add the `noexcept` specifier.

* * *

![Lei Mao bio photo](https://leimao.github.io/images//author_images/Lei-Bio-Medium.jpg)

### Lei Mao

Machine Learning, Artificial Intelligence. On the Move.

[Twitter](http://twitter.com/matchaleimao) [Facebook](http://facebook.com/dukeleimao) [LinkedIn](http://linkedin.com/in/lei-mao) [GitHub](http://github.com/leimao) [  G. Scholar](http://scholar.google.com/citations?user=R2VUf7YAAAAJ) [E-Mail](mailto:dukeleimao@gmail.com) [RSS](https://leimao.github.io/feed.xml)

**Use noexcept for Exception Handling in C++ Programs** was published on December 31, 2019 and last modified on December 31, 2019 by [Lei Mao](https://leimao.github.io "About Lei Mao").

  
  
from Hacker News https://ift.tt/2Qx2I0h