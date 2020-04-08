---
title: 'Efficient lock-free durable sets'
date: 2019-12-05T05:40:00+01:00
draft: false
---

[Efficient lock-free durable sets](https://arxiv.org/abs/1909.02852) Zuriel et al., _OOPSLA’19_

Given non-volatile memory (NVRAM), the naive hope for persistence is that it would be a no-op: what happens in memory, stays in memory. Unfortunately, a very similar set of issues to those concerned with flushing volatile memory to persistent disk exist here too, just at another level. _Memory_ might be durable, but…

> …it is expected that caches and registers will remain volatile. Therefore the state of data structures underlying standard algorithms might not be complete in the NVRAM view, and after a crash this view might not be consistent because of missed writes that were in the caches but did not reach the memory. Moreover, for better performance, the processor may change the order in which writes reach the NVRAM, making it difficult for the NVRAM to even reflect a consistent prefix of the computation.

Plus ça change, plus c’est la même chose.

So, we’re going to need to take care that everything we say is committed is truly durable, and that we can recover to a consistent state following a crash. The traditional way to accomplish this is with a write-ahead log. You’ll no doubt be familiar with the phrase _lock-free_ data structures, but in this paper we’ll be examining _log-free_ data structures (that are lock-free in addition).

When persisting to disk, flushing is expensive and we want to minimise the number of times we need to do it. When persisting to memory, the analogous operation is called `psync`, it’s comparatively expensive, and we want to minimise the number of times we need to do it.

> State-of-the-art constructions of durable lock-free sets, denoted Log-Free Data Structures, were recently presented by [David et al., 2018](https://www.usenix.org/conference/atc18/presentation/david). They proposed two clever techniques to optimize durable structures and built four implementations of sets. Their techniques were aimed at reducing the number of required explicit write backs (`psync` operations) to the non-volatile memory. In this paper, we present a new idea with two algorithms for durable lock-free sets, which reduce the number of flushes substantially.

The members of the sets we’ll be looking at are actually key-value pairs, but membership is based only on keys. So they’re not actually sets at all in my book, they’re maps (or functions, if you’re mathematically inclined)! To stick with the terminology of the paper I’ll call them sets anyway.

Think of the underlying implementation of such a set as having a data plane (the nodes storing the actual key-value pairs) and a control plane (the structure, e.g. a linked-list, that connects those nodes together and supports the set operations). (That’s my analogy, so blame me if it doesn’t work for you!). The central idea in this paper is to store the nodes in the data plane durably, but keep the control plane structure ephemeral. That means of course that we have to have a way to _recover_ the control plane structure after a crash, and we’ll be trading off slightly longer recovery times while we recreate it, for faster operation in the normal case. At a high level, you can think of this as “data is durable, pointers are not.”

![](https://adriancolyer.files.wordpress.com/2019/12/log-free-sketch.jpeg?w=520)

> Not persisting pointers significantly reduces the number of flushes (and associated fences), thereby drastically improving the performance of the obtained durable data structure.

The paper presents _two_ implementations of this idea: _link-free sets_ is a fairly straightforward implementation of the basic idea; whereas _SOFT_ (Sets with an Optimal Flushing Technique) further reduces the number of fences to the theoretical minimum — at the expense of algorithmic complexity.

### Link-free sets

The link-free algorithm adds two validity bits to each node. One bit is used to mark a node as invalid while it is in the process of being inserted into the list, and the other bit is used as a logical deletion marker. A node is considered in the set if it is both valid and not deleted. A `contains` operation always makes sure that a node pending insert is made durable (valid) before returning. Thus the returned value always matches the NVRAM view of the state.

The insertion operation proceeds as follows:

1.  A new node is initialised, with its validity set to false
2.  The key and value are written into the new node
3.  The node is inserted into the linked list structure, and the validity bit is flipped
4.  A `pysnc` operation makes the node durable

![LogFree-Listing-1.jpeg](https://adriancolyer.files.wordpress.com/2019/12/logfree-listing-1.jpeg?w=656)

Details of all the other operations can be found in §3 of the paper.

When recovering after a crash, the validity scheme is used to determine whether or not a node was linked to the list before the crash occurred.

> The procedure starts by initializing an empty list with a head and a tail. Afterwards, it scans the durable areas of the threads for nodes. All nodes that are valid and unmarked are inserted, one by one, to an initially empty link-free list. All other nodes (invalid nodes and valid and marked nodes) are sent to the memory manager for reclamation. The linking of the valid nodes is done without any psync operations since all the data in the nodes is already stored in the NVRAM.

### SOFT

SOFT reduces the number of `psync` operations required to the theoretical lower bound, by dividing each update operation into two stages: _intention_ and _completion_.

Set entries are represented by both a volatile node and a persistent node (PNode). PNodes are stored in the durable area and use three validity bits in a similar, but extended, scheme to that used in the log-free algorithm. Volatile nodes maintain the linked structure of the set, with pointers to the PNodes. They track node state as one of four values:

*   Inserted
*   Deleted
*   Intention to insert (being inserted, but the PNode is not yet guaranteed to be in NVRAM)
*   Inserted with intention to delete (being removed, but the removed condition is not yet guaranteed to be in NVRAM)

> The goal of the states is to make threads help each other complete operations and reduce the number of `pysnc` operations to the minimum.

After a crash all the volatile nodes are lost, and hence so is all the intention information. During recovery, membership is decided solely based on the bits in the PNodes. A PNode is considered valid and part of the set if `validStart` and `validEnd` have the same value, and `deleted` has a different value.

### Memory management

Both the link-free algorithm and SOFT need a way to reclaim memory. There are lock-free algorithms for this, but none quite fit the bill. Instead the authors use the _Epoch Based Reclamation_ scheme (EBR). EBR is not lock-free, but offers good performance and provides progress for memory management when threads are not stuck.

> Both link-free and SOFT use durable areas as part of their memory allocation scheme. These are address spaces in the heap memory used solely for node allocation…

Knowing that these durable areas are used only for the persistent nodes, any leaks following a crash can be identified during recovery using the validity scheme and the memory for removed or invalid nodes freed and reused.

### Performance evaluation

The evaluation compares the lock-free and SOFT sets to the [log-free state-of-the-art](https://www.usenix.org/conference/atc18/presentation/david), measuring throughput as the number of threads increases (and hence also contention), as the number of keys increases, and also across different workload types (read/write mix). The relative improvements of lock-free and SOFT over log-free are up 3.3x.

![LogFree-Fig-3.jpeg](https://adriancolyer.files.wordpress.com/2019/12/logfree-fig-3.jpeg?w=656)

For long lists where traversals are long and psync operations infrequent, the link-free version comes out on top, but otherwise SOFT is generally the best performing method.

  
  
from Hacker News https://ift.tt/37Yh2a4