---
title: 'Locks, Mutexes, and Semaphores: Types of Synchronization Objects'
date: 2020-01-05T01:38:00+01:00
draft: false
---

### Tuesday, 21 October 2014

I recently got an email asking about locks and different types of synchronization objects, so I'm posting this entry in case it is of use to others.

### Locks

A _lock_ is an abstract concept. The basic premise is that a lock protects access to some kind of shared resource. If you _own_ a lock then you can access the protected shared resource. If you do not _own_ the lock then you cannot access the shared resource.

To own a lock, you first need some kind of _lockable_ object. You then acquire the lock from that object. The precise terminology may vary. For example, if you have a lockable object XYZ you may:

*   _acquire_ the lock on XYZ,
*   _take_ the lock on XYZ,
*   _lock_ XYZ,
*   _take ownership_ of XYZ,
*   or some similar term specific to the type of XYZ

The concept of a lock also implies some kind of _exclusion_: sometimes you might be unable to take ownership of a lock, and the operation to do so will either _fail_, or _block_. In the former case, the operation will return some error code or exception to indicate that the attempt to take ownership failed. In the latter case, the operation will not return until it has taken ownership, which typically requires that another thread in the system does something to permit that to happen.

The most common form of _exclusion_ is a simple numerical count: the lockable object has a maximum number of owners. If that number has been reached, then any further attempt to acquire a lock on it will be unable to succeed. This therefore requires that we have some mechanism of relinquishing ownership when we are done. This is commonly called _unlocking_, but again the terminology may vary. For example, you may:

*   _release_ the lock on XYZ,
*   _drop_ the lock on XYZ,
*   _unlock_ XYZ,
*   _relinquish ownership_ of XYZ,
*   or some similar term specific to the type of XYZ

When you relinquish ownership in the appropriate fashion then a blocked operation that is trying to acquire the lock may not proceed, if the required conditions have been met.

For example if a lockable object only allows 3 owners then a 4th attempt to acquire the lock will block. When one of the first 3 owners releases the lock then that 4th attempt to acquire the lock will succeed.

#### Ownership

What it means to "own" a lock depends on the precise type of the lockable object. For some lockable objects there is a very tight definition of ownership: this specific thread owns the lock, through the use of that specific object, within this particular scope.

In other cases, the definition is more fluid, and the ownership of the lock is more conceptual. In these cases, ownership can be relinquished by a different thread or object than the thread or object that acquired the lock.

### Mutexes

_Mutex_ is short for _MUT_ual _EX_clusion. Unless the word is qualified with additional terms such as _shared mutex_, _recursive mutex_ or _read/write mutex_ then it refers to a type of _lockable_ object that can be owned by exactly one thread at a time. Only the thread that acquired the lock can release the lock on a mutex. When the mutex is locked, any attempt to acquire the lock will fail or block, even if that attempt is done by the same thread.

#### Recursive Mutexes

A _recursive mutex_ is similar to a plain mutex, but one thread may own multiple locks on it at the same time. If a lock on a recursive mutex has been acquired by thread A, then thread A can acquire further locks on the recursive mutex without releasing the locks already held. However, thread B cannot acquire any locks on the recursive mutex until **all** the locks held by thread A have been released.

In most cases, a recursive mutex is undesirable, since the it makes it harder to reason correctly about the code. With a plain mutex, if you ensure that the invariants on the protected resource are valid before you release ownership then you know that when you acquire ownership those invariants will be valid.

With a recursive mutex this is not the case, since being able to acquire the lock does not mean that the lock was not already held, by the current thread, and therefore does not imply that the invariants are valid.

#### Reader/Writer Mutexes

Sometimes called _shared mutexes_, _multiple-reader/single-writer mutexes_ or just _read/write mutexes_, these offer two distinct types of ownership:

*   _shared_ ownership, also called _read_ ownership, or a _read lock_, and
*   _exclusive_ ownership, also called _write_ ownership, or a _write lock_.

_Exclusive_ ownership works just like ownership of a plain mutex: only one thread may hold an exclusive lock on the mutex, only that thread can release the lock. No other thread may hold any type of lock on the mutex whilst that thread holds its lock.

_Shared_ ownership is more lax. _Any number_ of threads may take shared ownership of a mutex at the same time. No thread may take an exclusive lock on the mutex while any thread holds a shared lock.

These mutexes are typically used for protecting shared data that is seldom updated, but cannot be safely updated if any thread is reading it. The reading threads thus take shared ownership while they are reading the data. When the data needs to be modified, the modifying thread first takes exclusive ownership of the mutex, thus ensuring that no other thread is reading it, then releases the exclusive lock after the modification has been done.

#### Spinlocks

A spinlock is a special type of mutex that does not use OS synchronization functions when a lock operation has to wait. Instead, it just keeps trying to update the mutex data structure to take the lock in a loop.

If the lock is not held very often, and/or is only held for very short periods, then this can be more efficient than calling heavyweight thread synchronization functions. However, if the processor has to loop too many times then it is just wasting time doing nothing, and the system would do better if the OS scheduled another thread with active work to do instead of the thread failing to acquire the spinlock.

### Semaphores

A semaphore is a very relaxed type of lockable object. A given semaphore has a predefined maximum count, and a current count. You take ownership of a semaphore with a _wait_ operation, also referred to as _decrementing_ the semaphore, or even just abstractly called _P_. You release ownership with a _signal_ operation, also referred to as _incrementing_ the semaphore, a _post_ operation, or abstractly called _V_. The single-letter operation names are from Dijkstra's original paper on semaphores.

Every time you _wait_ on a semaphore, you decrease the current count. If the count was greater than zero then the decrement just happens, and the wait call returns. If the count was already zero then it cannot be decremented, so the wait call will _block_ until another thread increases the count by signalling the semaphore.

Every time you _signal_ a semaphore, you increase the current count. If the count was zero before you called _signal_, and there was a thread blocked in _wait_ then that thread will be woken. If multiple threads were waiting, only one will be woken. If the count was already at its maximum value then the signal is typically ignored, although some semaphores may report an error.

Whereas mutex ownership is tied very tightly to a thread, and only the thread that acquired the lock on a mutex can release it, semaphore ownership is far more relaxed and ephemeral. _Any thread_ can signal a semaphore, at any time, whether or not that thread has previously waited for the semaphore.

#### An analogy

A semaphore is like a public lending library with no late fees. They might have 5 copies of [C++ Concurrency in Action](http://cplusplusconcurrencyinaction.com) available to borrow. The first five people that come to the library looking for a copy will get one, but the sixth person will either have to wait, or go away and come back later.

The library doesn't care who returns the books, since there are no late fees, but when they do get a copy returned, then it will be given to one of the people waiting for it. If no-one is waiting, the book will go on the shelf until someone does want a copy.

#### Binary semaphores and Mutexes

A binary semaphore is a semaphore with a maximum count of 1. You can use a binary semaphore as a mutex by requiring that a thread only signals the semaphore (to unlock the mutex) if it was the thread that last successfully waited on it (when it locked the mutex). However, this is only a convention; the semaphore itself doesn't care, and won't complain if the "wrong" thread signals the semaphore.

### Critical Sections

In synchronization terms, a _critical section_ is that block of code during which a lock is owned. It starts at the point that the lock is acquired, and ends at the point that the lock is released.

#### Windows `CRITICAL_SECTION`s

Windows programmers may well be familiar with `CRITICAL_SECTION` objects. A `CRITICAL_SECTION` is a specific type of _mutex_, not a use of the general term _critical section_.

### Mutexes in C++

The C++14 standard has five mutex types:

The variants with "timed" in the name are the same as those without, except that the lock operations can have time-outs specified, to limit the maximum wait time. If no time-out is specified (or possible) then the lock operations will block until the lock can be acquired — potentially forever if the thread that holds the lock never releases it.

`std::mutex` and `std::timed_mutex` are just plain single-owner mutexes.

`std::recursive_mutex` and `std::recursive_timed_mutex` are recursive mutexes, so multiple locks may be held by a single thread.

`std::shared_timed_mutex` is a read/write mutex.

#### C++ lock objects

To go with the various mutex types, the C++ Standard defines a triplet of class templates for objects that hold a lock. These are:

For basic operations, they all acquire the lock in the constructor, and release it in the destructor, though they can be used in more complex ways if desired.

`std::lock_guard<>` is the simplest type, and just holds a lock across a critical section in a single block:

```
std::mutex m; void f(){ std::lock_guard guard(m); // do stuff }
```

`std::unique_lock<>` is similar, except it can be returned from a function without releasing the lock, and can have the lock released before the destructor:

```
std::mutex m; std::unique_lock f(){ std::unique_lock guard(m); // do stuff return std::move(guard); } void g(){ std::unique_lock guard(f()); // do more stuff guard.unlock(); }
```

See my previous [blog post](http://www.justsoftwaresolutions.co.uk/threading/multithreading-in-c++0x-part-5-flexible-locking.html) for more about `std::unique_lock<>` and `std::lock_guard<>`.

`std::shared_lock<>` is almost identical to `std::unique_lock<>` except that it acquires a shared lock on the mutex. If you are using a `std::shared_timed_mutex` then you can use `std::lock_guard` or `std::unique_lock` for the exclusive lock, and `std::shared_lock` for the shared lock.

```
std::shared_timed_mutex m; void reader(){ std::shared_lock guard(m); // do read-only stuff } void writer(){ std::lock_guard guard(m); // update shared data }
```

### Semaphores in C++

The C++ standard does not define a semaphore type. You can write your own with an atomic counter, a mutex and a condition variable if you need, but most uses of semaphores are better replaced with mutexes and/or condition variables anyway.

Unfortunately, for those cases where semaphores really are what you want, using a mutex and a condition variable adds overhead, and there is nothing in the C++ standard to help. Olivier Giroux and Carter Edwards' proposal for a `std::synchronic` class template ([N4195](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4195.pdf)) might allow for an efficient implementation of a semaphore, but this is still just a proposal.

Posted by Anthony Williams  
_\[/ [threading](https://www.justsoftwaresolutions.co.uk/threading/) /\] [permanent link](https://www.justsoftwaresolutions.co.uk/threading/locks-mutexes-semaphores.html)_  
Tags: [locks](http://technorati.com/tag/locks), [mutexes](http://technorati.com/tag/mutexes), [semaphores](http://technorati.com/tag/semaphores), [multithreading](http://technorati.com/tag/multithreading), [synchronization](http://technorati.com/tag/synchronization)  
[Stumble It! ![stumbleupon logo](https://www.justsoftwaresolutions.co.uk/images/stumbleupon.png)](http://www.stumbleupon.com/submit?url=https%3A%2F%2Fwww.justsoftwaresolutions.co.uk%2Fthreading%2Flocks-mutexes-semaphores.html&title=Locks%2C%20Mutexes%2C%20and%20Semaphores%3A%20Types%20of%20Synchronization%20Objects) | [Submit to Reddit ![reddit logo](https://www.justsoftwaresolutions.co.uk/images/reddit.png)](http://reddit.com/submit?url=https%3A%2F%2Fwww.justsoftwaresolutions.co.uk%2Fthreading%2Flocks-mutexes-semaphores.html&title=Locks%2C%20Mutexes%2C%20and%20Semaphores%3A%20Types%20of%20Synchronization%20Objects) | [Submit to DZone ![dzone logo](https://www.justsoftwaresolutions.co.uk/images/dzone.png)](http://www.dzone.com/links/add.html?url=https%3A%2F%2Fwww.justsoftwaresolutions.co.uk%2Fthreading%2Flocks-mutexes-semaphores.html&title=Locks%2C%20Mutexes%2C%20and%20Semaphores%3A%20Types%20of%20Synchronization%20Objects) 

[Comment on this post](https://www.justsoftwaresolutions.co.uk/threading/locks-mutexes-semaphores.html#makecomment)

If you liked this post, why not [subscribe to the RSS feed ![RSS feed](https://www.justsoftwaresolutions.co.uk/images/feed-icon-14x14.png)](https://www.justsoftwaresolutions.co.uk/index.rss) or [Follow me on Twitter](http://twitter.com/a_williams)? You can also subscribe to this blog by email using the [form on the left](https://www.justsoftwaresolutions.co.uk/threading/locks-mutexes-semaphores.html#subscribe).

  
  
from Hacker News https://ift.tt/1wGNwwS