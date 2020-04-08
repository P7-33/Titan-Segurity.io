---
title: 'This CPU Has Only One Instruction'
date: 2019-12-07T10:32:00+01:00
draft: false
---

Most of us will be familiar at some level with the operation of a basic CPU, usually through exposure to microprocessors of the type that find their way into our projects. We can look at its internal block diagram and get how it works, see the registers and ALU, follow the principles of a von Neumann architecture, and understand that it has an instruction set with different instructions for each of its functions. We all know that this only describes one type of CPU though, and thus it’s always interesting to see alternatives. \[Ike Jr\] then has a project that should provide a lot of interest, it’s [a CPU that only has a single instruction](http://ikejr.com/2019/11/23/periwinkle-one-instruction-set-computer/). It can only move data from one place to another, which seems to preclude any possibility of computation. How on earth can it work?

The machine has a set of registers as well as memory, and it achieves computation by having specific registers where we might expect to see instructions. For example the AND register is a two-position stack, that when it is full computes the AND of its two pieces of data and places the result in a general purpose register. The write-up goes into significant detail on the CPU’s operation, and while it’s unlikely the world will move en masse to this architecture it’s still a very interesting read. For now this is a machine that exists in software simulation rather than in silicon, and he’s working to release it so enthusiasts for unusual CPUs can have a go.

The idea of having registers that compute reminds us of a [transport triggered architecture](https://hackaday.com/2017/04/21/an-8-bit-transport-triggered-architecture-cpu-in-ttl/) machine, being not the same as a one instruction CPU with [a more conventional computing instruction](https://hackaday.com/2012/09/05/mess-of-wires-is-actually-a-one-instruction-computer/).

Abstract PCB header image: Harland Quarrington/MOD \[[OGL v1.0](https://commons.wikimedia.org/wiki/File:Computer_Circuit_Board_MOD_45153619.jpg)\].

  
  
from Hackaday https://ift.tt/2LwEHVz  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)