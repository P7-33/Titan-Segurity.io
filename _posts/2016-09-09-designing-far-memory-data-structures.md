---
title: 'Designing far memory data structures: think outside the box'
date: 2019-09-26T03:47:00+01:00
draft: false
---

[Designing far memory data structures: think outside the box](https://www.microsoft.com/en-us/research/uploads/prod/2019/05/hotos19-final67.pdf) Aguilera et al., _HotOS’19_

Last time out we looked at some of the [trade-offs between RInKs and LInKs](https://blog.acolyer.org/2019/06/24/fast-key-value-stores/), and the advantages of local in-memory data structures. There’s another emerging option that we didn’t talk about there: the use of _far-memory_, memory attached to the network that can be remotely accessed without mediation by a local processor. For many data center applications this looks to me like it could be a compelling future choice.

> Far memory brings many potential benefits over near memory: higher memory capacity through disaggregation, separate scaling between processing and far memory, better availability due to separate fault domains for far memory, and better shareability among processors.

It’s not all straightforward though. As we’ve seen a number of times before, there’s [a trade-off between fast one-sided access that doesn’t involve the remote CPU, and a more traditional RPC style that does](https://blog.acolyer.org/2016/12/15/fasst-fast-scalable-and-simple-distributed-transactions-with-two-sided-rdma-datagram-rpcs/). In particular, if you end up needing to make _multiple_ one-sided requests to get to the data you really need, it’s often faster to just go the RPC route.

Therefore, if we want to make full use of one-sided far memory, we need to think carefully about the design of our data structures to make that access efficient. This paper is all about the design of efficient data structures for far-memory, which turns out to have consequences reaching all the way down to the hardware.

> We need new data structures designed specifically for far memory that consider its assumptions and performance. In particular, data structures that complete in O(1) far memory accesses most of the time, preferably with a constant of 1. This requirement precludes most existing data structures today from use with far memory. For instance linked lists take O(n) far accesses, while balanced trees and skip lists take O(log n).

A far memory data structure has:

1.  **far data** in far memory, containing the core content of the data structure
2.  **data caches** at clients
3.  **algorithms** for operations

A far access is an order of magnitude slower (O(1µs)) than a local access (O(100ns)). Processor caches can help to hide local accesses too, but not remote accesses. With distributed data structures a remote processor can receive and serve an RPC request and handle many memory interactions within one round trip. With no remote CPU involved, far memory data structures can’t do that.

> Fundamentally, this is the age-old trade-off between shipping computation or data, where an RPC with traditional memory ships computation, while a one-sided access model with far memory ships data.

### Can I get a helping hand here?

Far memory primitives today are limited to loads, stores, and a few atomics. This makes it challenging to design effective far memory data structures.

> To achieve few far accesses per operation, we need to go beyond the current far memory primitives… We need primitives that do more work, but not so much that they need an application processor to execute… We consider only hardware extensions with three characteristics: (1) they are relatively simple and have a narrow interface; (2) they make a significant difference; and (3) they are general-purpose.

There are three classes of extensions the authors would like to add:

*   **indirect addressing**, i.e. dereferencing a pointer to determine another address to load or store. Indirect addressing is useful for far memory as it avoids a round-trip when a data structure needs to follow a pointer. Indirect versions of fetch-and-add and store-and-add are useful too, as are indirect add instructions with indexing.
    
    ![](https://adriancolyer.files.wordpress.com/2019/06/farmemory-indirect.jpeg?w=480)
    
*   **scatter-gather** extensions permit clients to operate on disjoint buffers in one operation. There are four variants depending on whether we read or write, and whether the disjoint buffers are at the client or far-memory.
    
    ![](https://adriancolyer.files.wordpress.com/2019/06/farmemory-sg.jpeg?w=480)
    
*   **notification** extensions provide callbacks triggered when data changes
    
    ![](https://adriancolyer.files.wordpress.com/2019/06/farmemory-notify.jpeg?w=480)
    
    To manage the scalability of notifications the subscribers of the hardware primitives are compute nodes, and a software layer on each compute node demultiplexes incoming notifications. Subscriptions for nearby regions may be coalesced, as may many notifications to the same subscription. Notifications may be delivered in a best-effort fashion.
    

### Far memory data structures

#### Simple structures

_Counters_ can be implemented with load, store, and atomic operations using immediate addressing, _vectors_ can use indirect addressing to index into a vector given a base pointer. Clients can subscribe to ranges of addresses to receive notifications when they are modified (`notify0`) or reach arbitrary values (`notifye`). _Mutexes_ and _barriers_ are implemented similarly to their shared memory analogues (e.g. compare-and-swap against 0 for a mutex, with a `notifye` on value 0 if the compare fails).

#### Maps

_Maps_ are usually implemented with hash tables or trees, but these don’t work well with far memory. Hash tables have collisions and resizing is disruptive when they are large; tree traversals take O(log n) far accesses.

> To address this problem, we propose a new data structure, the _HT-tree_, which is a tree where each leaf node stores base pointers of hash tables. Clients cache the entire tree, but not the hash tables. To find a key, a client traverses the tree in its cache to obtain a hash table base pointer, applies the hash function to calculate the bucket number, and then finally accesses the bucket in far memory, using indirect addressing to follow the pointer in the bucket.

If one hash table grows too large it can be split and added to the tree without affecting the others. Clients can use notifications to learn that a tree node has changed. An HT-tree can store 1 trillion items with a tree of 10M nodes, and 10M hash tables of 100K elements each.

#### Queues

Queues are typically implemented as a large array with head and tail pointers. The fetch-and-add-indirect and store-and-add-indirect instructions allow the client to atomically update head or tail pointers and extract or insert the required item. This means enqueue and dequeue can be done safely without additional concurrency control mechanisms in the normal (fast) case. If the head or tail pointers need to wrap around though, or the queue is empty or near empty we need to take extra care by executing a slower path.

> Clients must determine that they should run the slowpath without incurring additional far accesses in the fast-path. To do this, we allocate a slack region past the array consisting of n + 1 locations, where n is a bound on the number of clients. Clients check if they reach the slack after an operation completes, in the background, so they need not check during the fast-path whether the head or tail requires a wrap around.

A similar logical slack-region checking for hand and tail 2n positions apart can detect whether a queue is empty or full.

#### Refreshable vectors

Client-side caching of vectors can generate a lot of notifications when the vector changes. A _refreshable vector_ can return stale data, but include a refresh operation to guarantee freshness of the next lookup. A dynamic policy shifts from client-initiated version checks when data is changing frequently to a notification-based scheme as the update rate slows.

> Vector entries are grouped, with a version number per group; a client reads the version numbers from far memory, compares against its cached versions, and then uses a gather operation (rgather) to read at once all entries of groups whose versions have changed.

### A worked example

We don’t get a full-blown evaluation of the ideas in this position paper, but we do get a short case study/sketch of a monitoring application tracking a sampled metric, such as CPU utilization, in far memory. The system must raise alarms of varying severity if thresholds are crossed within time windows.

The far memory is used to keep a vector with a histogram of samples. Produces treat samples as an offset into the vector and use indexed indirect addressing to update the count stored there. Consumers use notifications to get changes in the histogram vector at offsets corresponding to alarm ranges. To track multiple time windows we can use a collection of histogram vectors in a circular buffer. A key outcome of this design is that only exception events cause data transfers to the consumer, reducing far memory traffic.

### The last word

I’m a bit troubled by the single sentence at the end of section 4 that is offered without further discussion on its implications: “_Because we want notifications to be scalable, they may be delivered in a best-effort fashion_.” For example, does a client waiting on a mutex potentially stay blocked forever if its notification never arrives? Is it ok for a local cache to potentially go stale beyond some freshness window? This feels like the chink in the armour where a lot of distributed systems problems might come creeping in!

That said, I’m excited to see where far memory architectures might take us in a few years time!

  
  
from Hacker News https://ift.tt/2JcXKSy