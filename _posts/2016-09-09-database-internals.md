---
title: 'Database Internals'
date: 2019-12-15T01:41:00+01:00
draft: false
---

Have you ever wanted to learn more about Databases but did not know where to start? This is a book just for you.

We can treat databases and other infrastructure components as black boxes, but it doesn’t have to be that way. Sometimes we have to take a closer look at what’s going on because of performance issues. Sometimes databases misbehave, and we need to find out what exactly is going on. Some of us want to work in infrastructure and develop databases. This book’s main intention is to introduce you to the cornerstone concepts and help you understand how databases work.

The book consists of two parts: Storage Engines and Distributed Systems since that’s where most of the differences between the vast majority of databases is coming from.

In **Storage Engines**, we start with taxonomy and terminology, then explore In-Place Update storage and discuss several B-Tree variants and their structure. Then we talk about binary data formats and file organization and explore the ways to compose efficient on-disk structures. After that, we go into the detail on what techniques different databases use when implementing B-Trees and talk about related data structures such as Page Buffer, Write-Ahead Log, how to implement compression and perform defragmentation and compaction. Finally, we discuss Log-Structured storage and explore a few different storage engine approaches, such as [Bw-Trees](https://dl.acm.org/citation.cfm?id=2510649.2511251), [FD-](https://dl.acm.org/citation.cfm?id=1920990)[Trees](https://dl.acm.org/citation.cfm?id=1920990), [CoW](https://dl.acm.org/citation.cfm?id=1326544) [B-Tress](https://dl.acm.org/citation.cfm?id=1326544), [Bitcask](https://dl.acm.org/citation.cfm?id=2633459), [WiscKey](https://dl.acm.org/citation.cfm?id=3033273), [2/3 Component LSM](https://dl.acm.org/citation.cfm?id=230826), and some other ones.

In **Distributed Systems**, we start with basic concepts such as processes and links and start building more complex communication patterns. We quickly discover that communication is unreliable and discuss which guarantees we have and how to achieve those. We cover the Important concepts such as Failure Detection, Leader Election and Gossip Dissemination. After that, we explore different Consistency Models and talk about ways to achieve them. After covering Atomic Commitment and Broadcast, we move to the pinnacle of Distributed Systems research: Consensus Algorithms.

This book includes references to 100+ papers, 10+ books several open source database implementations and other sources you can refer to for further study.

  
  
from Hacker News https://databass.dev