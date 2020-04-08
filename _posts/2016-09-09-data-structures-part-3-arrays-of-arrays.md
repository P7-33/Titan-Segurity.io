---
title: 'Data Structures Part 3: Arrays of Arrays'
date: 2019-10-01T03:46:00+01:00
draft: false
---

Welcome to part 3 in this series covering all the data structures you _really_ need (kind of).

*   In [part 1](https://ourmachinery.com/post/data-structures-part-1-bulk-data/), we saw that the best way to store most data is just to use a big old array and that with some tricks we can allocate this array so that the objects in it have fixed indices and permanent pointers.
    
*   In [part 2](https://ourmachinery.com/post/data-structures-part-2-indices/), we saw how to fix the most glaring problem with these arrays — that it is kind of expensive to find things in them — by adding search indices that let us quickly find any subset of objects that we are interested in.
    

In this part, we will tackle a final problem. When we created our bulk data arrays, we assumed that all objects were fixed size so that we could fit their data into a single struct and store the bulk data as just an array of such structs:

```
struct object_t { ... }; uint32_t num_objects; struct object_t *objects; 
```

But what if we need some fields in the object that are _dynamically_ sized?

```
struct object_t { const char *name; uint32_t num_children; object_t **children; }; 
```

How can we store the object names and children in a good way?

Capped Size
-----------

The simplest way of handling dynamically sized objects is to just get rid of the problem. If we set a maximum size for our strings and arrays, we’re back to having a fixed size struct, with the string and array data stored in the struct itself:

```
enum {MAX_NAME_LENGTH = 63}; enum {MAX_CHILDREN = 8}; struct object_t { const char name[MAX_NAME_LENGTH + 1]; uint32_t num_children; object_t *children[MAX_CHILDREN]; }; 
```

Now we can just make an `object_t[]` as before and have all the data in there.

Capping sizes is always a bit scary, because what if we set the cap too low and hit the limit? Personally, I feel a little bit dirty every time I do this. I think it’s PTSD from run-ins with some really ridiculous size limits, such as `MAX_PATH = 260` in Windows.

But there are a lot of situations where having a maximum size is fine. There is a big difference between locking a maximum size down in a file format or an OS API, where it might live for 50 years, causing headaches to generations of programmers, versus just having it in your runtime, where you can change it whenever you want without worrying about compatibility with old software. You can start with a fixed size and change to something more advanced when you need to. Code doesn’t have to be “future-proof” if it is easy for future you to change it.

Also, if you are writing code for just one particular game and not a generic engine, you don’t need to support anything beyond what your game needs. If you only support four players, your player arrays can all be `players[4]`. And anything that’s just for internal use, you can limit to whatever you find reasonable. For example, object debug names can probably be `s[64]` without any problems. Longer names are too hard to read anyway.

Also, keep in mind, that even if you don’t specify an explicit maximum size, there is probably a practical limit anyway. If you have too many things you will eventually overflow an `uint32_t`, run out of memory or drive the FPS down to the point where your app is unusable.

Judicious use of maximum sizes can simplify the code a lot. Of course, it doesn’t always work:

*   Some things can get arbitrarily large.
    
*   Some things have a limit, but the limit is so high that you will waste a lot of memory by using a fixed-size array.
    
*   Some things have a small limit, but enforcing the limit is more trouble than its worth.
    

As an example of the last case, consider your application’s window system. You could probably limit the number of windows to 128 because no sane user will want to deal with more than 128 open windows. (Note that this _does not_ apply to tabs — many users are perfectly happy having a couple of thousand Chrome tabs open.) Using a fixed size of 128 won’t waste much memory either since you only need one global window array.

_But…_ if you decide to set a limit of 128 windows, you have to decide what to do if the user tries to open more than that. You probably don’t want to _crash_. Do you beep? Show an error message? What if the window you can’t open is the window that was supposed to show the error message? Now you have this extra code path in your code, that you have to write, maintain and test. An extra place where things can go wrong. It might be easier to just support an “unlimited” number of windows and let the users dig their own graves.

Heap allocation
---------------

If we can’t use a fixed-size array, the next simplest thing is to just use an off-the-shelf STL object, such as `std::string` or `std::vector`.

```
struct object_t { std::string name; std::vector children; }; 
```

What happens when we use one of these types? STL will allocate data for the `string` and the `vector` on the system heap. Each `string` and `vector` gets its own individual little memory allocation, so we have a situation that looks something like this:

![](https://ourmachinery.com/images/ds3-stl-memory.jpg)

#### STL memory layout.

If we have an `std::vector` with 10 000 items in it, we will use _one_ memory allocation for the `object_t *` array, but an _additional_ 20 000 allocations for the names and children of those objects.

This seems a bit wasteful, but computers are really fast, so this approach can work well in many cases. We have a fair number of arrays like this in _The Machinery_ – not for strings (more about that later), but certainly for vectors. The only difference is that instead of using an `std::vector` we use a [stretchy buffer](https://ourmachinery.com/post/minimalist-container-library-in-c-part-1/). Why? Well, for one, we program in C rather than C++ so we can’t use STL. But even if we used C++ we might still prefer this approach, because C++ classes can be tricky to use with the bulk data allocation approaches I described in [part 1](https://ourmachinery.com/post/data-structures-part-1-bulk-data/).

First, remember how we stored the objects in an “array with holes” by making the stored data type a union of the original data we wanted to store and a free list pointer for keeping track of the free items:

```
typedef union { object_t; freelist_item_t; } item_t; 
```

This doesn’t work with `std::vector`, because objects with non-trivial copy constructors can’t be stored in unions. To make this work with STL objects we either have to use extra memory to store the freelist pointers with the object itself, or use something like `std::variant` (shudder).

Second, remember our nice trick of just reserving a large chunk of VM memory to hold our bulk data array. This works well with our C data structures, because they are zero-initialized and the memory we get from the VM is always cleared to zero (since otherwise, the VM would leak information between processes). So, with C data structures, we can just use the memory directly, whereas with C++ we would have to placement-new our strings and vectors into the memory.

In other words, in this use case, using the STL data types adds a lot of extra bookkeeping for limited benefits.

As I said above, heap allocation can certainly be “good enough” in a lot of circumstances, but if you want to store a really large number of objects, it has some drawbacks that I’ve already talked about earlier in this series:

*   Making thousands of small allocations is time-consuming and can waste a substantial amount of memory on fragmentation, allocation headers, etc.
    
*   Since the arrays are allocated individually on the heap, they might be far apart in memory, resulting in cache misses when we process the objects.
    
*   With lots and lots of small allocations, it is hard to get a good picture of how much memory the system is using and what the access patterns are.
    

So let’s look at alternatives!

Private heap
------------

One way of avoiding to make lots of _small_ allocations from system memory is to make one _big_ allocation and then chop it up ourselves into smaller pieces. Since we’re allocating a big chunk, we can request it directly from the VM and bypass the system heap allocator completely:

![](https://ourmachinery.com/images/ds3-private-heap.jpg)

#### Private heap.

Essentially, what we’re doing here is implementing our own memory allocator. Getting chunks of memory from the VM and chopping them up into chunks to fulfill `malloc` and `new` requests is just what a memory allocator does.

Why would we ever want to do this, since we already have a perfectly good system memory allocator?

Well, to begin with, I think it is a really useful exercise. Writing your own memory allocator makes you think about how memory really works — it’s just bytes all the way down, and any “objects” you see are just your own mental projections. It may seem daunting and scary at first, but it’s not as hard as you might think. Try it!

But OK, personal development aside, why would we want to write our own memory allocator? Certainly, the system allocator has been written by “experts” and there is nothing we mere mortals could ever do to improve on it.

Actually, you’d be surprised. It used to be, not too long ago, a lot of systems shipped with really crappy system allocators. By switching out the standard allocator for something like [dlmalloc](http://gee.cs.oswego.edu/dl/html/malloc.html), you could give your game a nice 5-10 % performance boost. (Provided your game did tons of small memory allocations in the update loop, which of course you should _not_ be doing. That’s what this whole series is about, remember?) I think that’s all fixed these days, though, and everything ships with something that is at least comparable to dlmalloc in terms of performance.

But it’s still possible to do better! How? Well, the standard memory allocator has to deal with a lot of different situations. Different applications have different memory patterns and since the standard allocator can never know exactly what’s going to be thrown at it, it has to do something that works kind-of-okay in a lot of different situations. And it’s really hard to write something that works good for everything, so you can usually come up with some adversarial worst-case input that makes the allocator completely crap out and go O(n²).

In contrast, if you are writing an allocator just for your specific application — or even better, for _one_ _specific system_ in your application — you have a lot more information. Your allocator doesn’t have to work well for any weird data that might be thrown at it, it just has to work well for the allocation patterns of _that_ system. That is a lot simpler, and a lot more well-defined problem to solve. It is also a lot easier to test — you can just feed the allocator the data you expect and see how well it performs. So you can easily check if you manage to do better than the system allocator or not.

Just to convince you further, here are some examples of how you can do better than the system allocator:

*   A lot of command-line programs just perform a single task and then exit. They tend to allocate a bunch of memory as they are performing the task and then free it all when they exit. These programs may actually run significantly faster with an allocator that just _never frees_ the memory. Memory leaks aren’t really an issue with these programs, since once they exit, all the memory is returned to the system anyway. So doing a lot of bookkeeping in order to reclaim memory is not worth it. If memory is never freed we can use a simple [pointer bump allocator](https://en.wikipedia.org/wiki/Region-based_memory_management) to allocate it.
    
*   If you’re not writing a generic allocator, you can change the allocator API. For example, you can make your `free()` function take two arguments — the pointer and the _size_ of the memory block that is being freed. This size should always be known by the owner of the memory block, because if the owner didn’t know the size, how could they use the memory without causing access violations? Forcing the owner to pass the size to `free()` means that the allocator doesn’t have to remember it, which is nice. For example, suppose someone calls `malloc()` to allocate 4K of memory. With a 4K page size, `malloc()` could service this directly from the VM, but where would it store the size of the memory block? Either it has to allocate more memory for a preamble that holds the size, which means that the allocation no longer fits nicely into a system page, or it has to store the size some other way — such as in a hash table. If `free()` passes the size, `malloc()` doesn’t have to worry about storing it. We actually use this approach for all memory allocations in _The Machinery_.
    
*   A generic allocator needs to implement synchronization to make sure multiple threads are not allocating memory simultaneously. If you are writing your own allocator for a specific system, synchronization might already be dealt with by that system, at a higher level, which means you don’t have to repeat the effort in the allocator.
    

So writing your own memory allocator can make things faster. But depending on how simple you are able to make it, there can still be a significant overhead from all those allocations. Also, we haven’t done anything to solve the problem of fragmentation. Allocating and freeing blocks of different sizes will leave holes of different sizes in our memory block, that are hard to reuse.

Can we do better?

Chunked allocator
-----------------

One way of getting rid of fragmentation is to implement [heap compaction](https://en.wikipedia.org/wiki/Mark-compact_algorithm). I.e., instead of holding pointers to objects we hold _handles_ that can be resolved into pointers. This allows us to [defragment](https://en.wikipedia.org/wiki/Defragmentation) the heap by moving the memory blocks and updating the pointers that the handles resolve to. The main problem with this is that it can be really error prone, since you have to make sure to lock and unlock pointers so they don’t get moved while you are using them.

But there is another way. Fragmentation is caused by allocating and freeing memory blocks of _different sizes_. This leaves differently sized holes that we have to try to fill with future allocations. If all allocations were _the same size_ we wouldn’t have this problem at all. In fact, in this case, we would just have the same situation as we had in the first part of this series — the bulk data array. We can just keep all the freed blocks in a free list and when the user wants to allocate more memory, we just give her the first block from the free list. Since all the blocks are the same size, the block will be the right size.

Is there a way to make all allocations the same size when all the objects can have a different number of children? Yes. What if we make each allocation a fixed-size “chunk” or “block” of children — say 16 at a time. If an object needs more than 16 children we can just allocate multiple chunks for that object and link them together with pointers.

Let’s see what it might look like:

```
enum {CHILD_CHUNK_SIZE = 16}; struct child_chunk_t { object_t *children[CHILD_CHUNK_SIZE]; child_chunk_t *prev_chunk; child_chunk_t *next_chunk; }; struct object_t { const char *name; uint32_t num_children; child_chunk_t *child_chunks; }; uint32_t num_child_chunks; struct child_chunk_t *child_chunks; uint32_t num_objects; struct object_t *objects; 
```

With this approach, both `objects` and `child_chunks` are just bulk data arrays, like the ones we encountered in the first part of this series. To find all the children of an object, we follow its `child_chunks` pointer to get to the first chunk of children and then follow the `next_chunk` pointers to get any additional chunks.

How does this solution perform compared to using an `std::vector`? The main drawback is that we can no longer randomly access objects in constant time with `[i]`, so if you need that, this is not a good solution. Note though, that we can still iterate over all objects in _O(n)_ — same as for the `std::vector`.

Allocating and freeing a `child_chunk_t` is very cheap — just a few operations — a lot cheaper than if we were using a generic memory allocator. We can also make use of the tricks we used for the bulk data — such as allocating memory directly from the VM. It is very easy to see how much memory the system is using and what the access patterns are since we only have two allocations that we need to worry about — `objects` and `child_chunks`.

We get less memory coherency than we would with an `std::vector`. Instead of having all items continuous in memory, they are only continuous in chunks of `CHILD_CHUNK_SIZE`. Whenever we follow the `next_chunk` pointer we might get a cache miss. Note though that we have some control of this, by using different values for `CHILD_CHUNK_SIZE`. The higher we set it, the more objects we can process at one time before pointer chasing.

Also note that _most of the time_, chunks from the same child array will tend to end up next to each other since typically the children will be added at the same time, which means they will be allocated next to each other in memory (unless they’re allocated from the free list). So this might be less of an issue than you think.

In terms of memory, this solution has no external fragmentation — all the “holes” created when we free a `child_chunk_t` are perfectly sized for the allocation of another `child_chunk_t`. However, we do have internal fragmentation, since we’re always allocating at least `CHILD_CHUNK_SIZE` items in every chunk, even if we need less than that. The larger `CHILD_CHUNK_SIZE` is, the more memory we lose to internal fragmentation. We also have some overhead from the `prev_chunk` and `next_chunk` pointers. (We could store them as indices to reduce the overhead.)

How does the memory use compare to `std::vector`? It’s a bit tricky to say since there are a lot of factors involved. First, will children be added dynamically, so that we need to use `push_back()` and rely on geometric growth to get amortized constant time for adding elements, or, are all children known in advance so that we can just `resize()` the vector to the right size? If it’s the former, then the vector will be about 50 % empty on average, which for big vectors will be a lot more than the `CHILD_CHUNK_SIZE`. Second, the `vector` will have some amount of external fragmentation as well as overhead from preambles and postambles. But how much this is depends on the implementation details of the allocator and the size of the vector. For example, if the vector is small enough to fit in one of the fixed-size allocation pools of the system allocator, it doesn’t need a preamble and postamble and will not cause external fragmentation.

Personally, the main reason I like this approach over using an std::vector is that it’s _transparent_. It is easy to see exactly how much memory is being used and where memory is being wasted. We can easily follow the access pattern and see how much pointer-chasing we are doing. This transparency makes it easy to discover and fix any performance issues we run into. For example, we can play with the `CHILD_CHUNK_SIZE` or even create two different `child_chunk` arrays with different chunk sizes, to better accommodate both large and small arrays.

In constrast, the system allocator is essentially a black box. Unless you want to do some really deep digging, it’s hard to tell how it works, hard to tell how much memory you are spending on headers and fragmentation. It’s hard to even see if you have a problem, and even harder to fix it, since that means rewriting the system allocator.

I always prefer simple transparent system that can be easily hacked and tweaked over complicated black boxes.

What is a good chunk size for the chunked allocator? If we set it too low then we’re jumping around in memory a lot and also spending a lot of memory overhead on the `prev_chunk` and `next_chunk` pointers. If we set it too high, then we’re losing a lot of memory to internal fragmentation.

I think you shouldn’t go smaller than fitting a `child_chunk_t` in a cache line. If we use 32-bit indices instead of pointers for everything to save space, that means we’re using 4 bytes each for the `prev` and `next` references and 4 bytes for every object index. So if we use `CHILD_CHUNK_SIZE = 14` each `child_chunk_t` will be exactly 64 bytes. I don’t think there are many cases where you would want to go >14 elements either. Usually, small arrays are more common than large ones, so a higher number would mean a lot of internal fragmentation:

```
enum {CHILD_CHUNK_SIZE = 14}; struct child_chunk_t { uint32_t child_indices[CHILD_CHUNK_SIZE]; uint32_t prev_chunk_index; uint32_t next_chunk_index; }; 
```

It is interesting to note what happens if we let `CHILD_CHUNK_SIZE = 1`. In this case, we get:

```
struct child_chunk_t { object_t *child; child_chunk_t *prev_sibling; child_chunk_t *next_sibling; }; 
```

I.e., the child chunks just turn into a linked list of siblings. In fact, in this case, we don’t really need the `child_chunk_t` structure at all, we could just let the sibling pointers point directly into the `object_t *` array and get:

```
struct object_t { const char *name; object_t *first_child; object_t *prev_sibling; object_t *next_sibling; }; 
```

To enumerate all the children of an object stored in this way, we would first follow the `first_child` pointer to get to its first child and then keep following the `next_sibling` pointers to enumerate all the siblings of that child.

This solution is almost exactly the same as the one we used in part 2 of this series to find all the observations with a particular observer.

So this gives us another way of storing arrays of arrays. Instead of explicitly representing the children as an array:

**Parent**

**Children**

Ewing

\[Edith, Phelan, Bouvier\]

Bouvier

\[Jr, Nicholas, Christopher\]

We can represent that data as a relationship, as we would in a relational database:

**Parent**

**Child**

Ewing

Edith

Ewing

Phelan

Ewing

Bouvier

Bouvier

Jr

Bouvier

Nicholas

Bouvier

Christopher

and then use the techniques outlined in the previous post to enumerate all the children of a particular parent.

Which approach is best? Using explicit arrays is faster and uses less memory, but it only allows us to search the data one way, from parent to children. If we want to remove a particular child from the child array of its parent, we have to iterate through all the children to find the child we are looking for, which can be expensive if the arrays get large.

In contrast, the relational representation allows us to search using multiple criteria. For example, as we saw in the last post, we can add a child index and then we can search for a particular child and remove it from its parent as an _O(1)_ operation.

I would use the array representation if I didn’t need these more advanced search options, and the relational representation otherwise.

Arrays of strings
-----------------

So far, I’ve talked a lot about the `children` array, but I haven’t really said anything about the `name` string. Well, a string is just an array of characters, right? So we could just use any of the techniques described above for storing _arrays of things_ to store an _array of characters_, i.e. a _string,_ right?

Wrong! Well, not totally wrong, of course, we _could_ do that, theoretically. But I think that thinking of a string as an “array of characters” is fundamentally misguided. In fact, it’s one of my pet peeves. What matters in data-oriented design is how data is used, and strings are used _very differently_ than other “arrays of things”.

When you think of an `std::vector`, what are the typical operations that you want to do with it?

*   Iterate through all the items and call some method on each one:
    
    ```
    for (const auto &it = v.begin(); it != v.end(); ++it) f(it); 
    ```
*   Add a new item to the vector:
    
    ```
    v.push_back(x); 
    ```
*   Remove an item from the vector:
    
    ```
    std::iter_swap(it, v.end() - 1); v.pop_back(); 
    ```

None of these operations are things you would typically do with a string!

If I have a string `"Niklas"` in my program, I never want to randomly add or remove characters. `"Nklas"` and `"Niklasz"` make no sense. I might iterate over the characters to draw them in the UI, but that’s only at one place in the code. Instead I’m probably more interested in comparing strings for equality (`strcmp()`) or composing substrings into larger strings (`sprintf()`). None of these are typical operations for other “arrays of things”.

The primary differences between strings and other arrays are:

By strings being _immutable_, I simply mean what I said earlier, that we don’t tend to add and remove characters in strings the same way we do with other arrays. Instead, when we change strings, we typically change _the whole thing._

For example, imagine we want to change the string:

```
- last_name = "Frykholm" + last_name = "Gray" 
```

We don’t think of this as removing the letters `F, k, h, o, l, m` and adding `G, a`. Rather, we think of this as a single _rename_ operation — changing the whole last name. And that’s how most strings work (we’ll look at some exceptions later).

So strings aren’t really “arrays of characters”, they are _names_ or _identifiers._ This is why in a lot of cases, you don’t even need to store the string itself, you can just store an `uint64_t` hash of the string and compare _that_ to check if a name matches. The only time you need to store the string is if you need to show it to a human (debug printing, logging, UI) or pass it to another system (`fopen()`).

Unless you’re writing a word processor or something like that, I can only think of two cases where you have mutating strings:

*   When the user is editing a string in a text box.
    
*   When you are building a string up from parts — i.e., concatenating substrings into a path, or an error message.
    

For editing — presumably the user can’t be editing more than one string at a time (in whatever text box has focus), so this is really a special case. You can have a single `char` array in your program to hold this “currently edited string”. At the start of editing, you copy whatever string the user is editing into this array so that the text box can use it. When editing finishes, you create a new immutable string from the content of the array and then _rename_ the original object to this new string.

Building up a string from parts is a good use case for temporary memory. In The Machinery, we have an `sprintf()` implementation that uses a temporary memory allocator, rather than a fixed-size buffer, so it can be used to build arbitrarily large strings. Once you are done constructing the string, you either use it (print the debug message, etc) or if you need to save it for later, convert it into an immutable string.

Reused strings can pop up in things like JSON parsing, where the same object key (e.g. `"properties"`) can show up hundreds or thousands of times. Storing a separate copy of the string each time it appears can be really wasteful.

If we treat strings as immutable, we don’t need separate copies, we can just make all the string pointers point to the same data:

![](https://ourmachinery.com/images/ds3-immutable-strings.png)

#### Immutable strings.

It doesn’t matter how many `"properties"` strings we need. Using this technique, we can create as many strings as we like and still have only one copy in memory. Since the string data will never change (strings are immutable), sharing it is fine.

This technique of letting all the strings with the same data share the same pointer is called [string interning](https://en.wikipedia.org/wiki/String_interning) and it has some interesting consequences. For one, we don’t have to compare strings with `strcmp()` or hashing anymore. Since we know that identical strings will use the same pointer, we can just compare the `const char *` pointers. s1 == s2 if and only if the pointers are equal.

Note that some programming languages, such as [Lua](https://www.lua.org), use interning for all their strings. Others, such as [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)) and [Lisp](https://en.wikipedia.org/wiki/Common_Lisp), have a separate [symbol](https://en.wikipedia.org/wiki/Symbol_(programming)) data type which represents an interned string.

To implement string interning in C, I use a big buffer to hold the string data and a hash table to look up strings in the buffer. The buffer can be reserved from virtual memory or allocated using one of the other techniques described in part 1 of this series. The buffer just stores all the strings consecutively and the hash table holds indices or pointers to these strings:

![](https://ourmachinery.com/images/ds3-string-interning.jpg)

#### String interning.

The hash table is needed when strings enter the string interning system. For example, suppose you read a string from a file. After you’ve read it, it will be in some temporary memory array `char *`. To _intern_ this string you need to check if you have a copy of it in your buffer already. If you do, you can just return a pointer to that string. If not, you should allocate a new string at the end of the buffer and return a pointer to _that_.

Here’s what the code might look like in practice:

```
// Commit VM memory in 4K chunks. enum {CHUNK = 4 * 1024}; struct string_repository { uint32_t buffer_size; char *buffer; hash32_t lookup; }; const char *intern(struct string_repository *sr, const char *s) { const uint64_t h = murmurhash_string(s); const uint32_t idx = hash32_get(&sr->lookup, h, UINT32_MAX); if (idx < UINT32_MAX) return sr->buffer + idx; // Commit VM memory. (Assumes we're using the VM method for storing // the buffer.) Note: This is only needed on Windows which makes a // distinction between reserving and committing virtual memory. const uint32_t n = (uint32_t)strlen(s); const uint32_t size = sr->buffer_size; const uint32_t new_size = size + n + 1; const uint32_t chunks = div_round_up(sr->buffer_size, CHUNK); const uint32_t new_chunks = div_round_up(new_size, CHUNK); if (new_chunks != chunks) vm->commit(sr->buffer + chunks * CHUNK, (new_chunks - chunks) * CHUNK); // Copy string data into buffer and update hash table memcpy(sr->buffer + sr->buffer_size, s, n + 1); hash32_add(&sr->lookup, h, sr->buffer_size); } 
```

Note that if you want to do tricks like comparing strings by pointers, you have to make sure that both the strings are interned. If one of the strings is a string literal or has just been read from a file into a dynamic buffer, it won’t work. It’s only when strings have entered the interning system that strings with the same value have the same pointer.

When programming languages use string interning, they typically have one single string repository where all the strings in the program go. However, when you’re managing your own string repository I find it more useful to have separate per-system or per-object string repositories. For example, when parsing a JSON file, I would assign it it’s own string repository. This way, when you’re done with the parsing, you can just throw away the whole repository and free the memory.

Note that this again means that you need to be careful. If you try to compare strings by pointers and the strings are not from the _same_ string repository, it won’t work.

So far, we haven’t described any mechanism for _removing_ strings from the string repository. If we want to be able to do that, we first need to add reference counts to the string buffer. Since the same buffer data can be shared by multiple strings, we need to count how many times that happens, so that we can know when the data is no longer used and is safe to be deleted or reused.

Second, when strings are deleted, it will leave holes in our big string buffer:

![](https://ourmachinery.com/images/ds3-string-buffer-holes.jpg)

#### String buffer holes.

To reuse this memory for other strings we must keep track of where all the holes are. We also probably want a mechanism for merging small neighboring holes into bigger holes, because otherwise, we’ll end up with smaller and smaller holes, that won’t be useful for anything but the shortest strings.

Note that this is exactly the same problem that a heap memory allocator has to solve, and we can address it using the same techniques. For example, we can link holes together in linked lists based on their sizes to make it possible to find them. We can also add preambles and postambles to all string allocations so that we can find neighboring allocations as targets for merging. Note that these preambles and postambles will add some overhead to every allocation. Also, we must round up the allocations to some minimum size, so that we are sure that the linked list pointers will fit in the “hole” that the allocation leaves when we free it.

Of course, we could also make use of all the other little tricks that memory allocators do. For example, we could have “pools” of allocators for strings of fixed sizes, etc, etc. It starts getting complicated.

Another thing you could do is to represent the strings as handles instead of pointers. I.e. you let the `intern()` function return an `uint32_t` string ID instead of an actual `char *` and then you have another function that looks up from the ID to the actual string data. Now, since nobody is pointing directly to the string, you can move the strings in memory and get rid of holes that way. This is the “compacting heap” approach.

In practice, I do it like this: I allocate the strings in blocks of 4 K. For each block, I keep track of how much “string” data and how much “hole” data it contains. When the block is > 50 % empty, I “defragment” the block by packing the strings tightly. The memory that’s left at the end of the block can then be used for new strings.

![](https://ourmachinery.com/images/ds3-defragment.jpg)

#### String buffer defragmentation.

The third option is to not bother with removing strings and reclaiming memory at all. This the absolutely simplest option and in many cases a perfectly valid one. Remember that our typical use case for this is to store object names and it is unlikely that objects will be renamed so much that the memory leaks become a problem. Another use case was for JSON parsing. Here, by using a designated string repository that we throw away at the end of the parse, there is no memory wasted at all. Any system that produced a large number of unique strings, such as logging, wouldn’t use this system anyway, but instead, just use temporary memory for the strings.

Conclusion
----------

Together, the techniques outlined in this series: bulk data arrays, indices and arrays of arrays, cover almost all the data structure needs we have in _The Machinery_. Is there something that seems to be missing? Tweet me at [@niklasfrykholm](https://twitter.com/niklasfrykholm).

  
  
from Hacker News https://ift.tt/2oEOK1X