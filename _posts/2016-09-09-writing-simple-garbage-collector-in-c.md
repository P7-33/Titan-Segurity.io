---
title: 'Writing a Simple Garbage Collector in C'
date: 2019-12-15T06:11:00+01:00
draft: false
---

To begin, we need to write a memory allocator, or as we will be calling it, a malloc function. The simplest malloc implementations maintain a linked-list of free blocks of memory that can be partitioned and given out as needed. When a user requests a chunk of memory, a block of the right size is removed from the free list and returned. If no blocks of the right size exist, either a block of a larger size is partitioned into smaller blocks or more memory is requested from the kernel. Freeing a chunk of memory simply adds it back to the free list.

Each chunk of memory in the free list begins with a header describing the block. Our header will contain two fields, one indicating the size of the chunk and the second pointing to the next free block of memory:

```
typedef struct header { unsigned int size; struct header \*next; } header\_t; 
```

Using headers that are embedded in the memory we allocate is really the only sensible way of doing this, but it has the added benefit of automatically word-aligning the chunks, which is important.

Because we will need to keep track of the blocks of memory currently in use as well as the blocks that are not, we will have a used list in addition to a free list. Items will be added to the used list when they are removed from the free list, and vice-versa.

We are almost ready to complete the first step and write our malloc implementation. Before we do that, we first need to understand how to request memory from the kernel.

Dynamically allocated memory resides in the so-called heap, a section memory between the stack and the BSS (uninitialized data segment - all your global variables that have the default value of zero). The heap starts at a low address bordering the BSS and ends at the program break, which resides somewhere between the BSS and the stack. Attempting to access any memory between the stack and the break will cause an access violation (unless you access within the amount the stack can be extended by, but that's a whole separate conversation). In order to obtain more memory from the kernel, we simply extend the break, thus allowing us to access more memory. To do this, we call the Unix sbrk system call, which extends the break by its argument and returns the address of the previous break on success, thus giving the program more memory. On failure, sbrk returns -1 casted to a void pointer, which is a terrible convention that no one likes.

We can use this knowledge to create two functions: `morecore` and `add_to_free_list`. In the case theta we are out of blocks in the free list, we will call `morecore` to request more memory. Since requesting the kernel for more memory is expensive, we will do it in page-size chunks. Knowing what a page is is not important right now, but a terse explanation is that it is the smallest unit of virtual memory that can be mapped to any particular location in physical memory. We will use the function `add_to_free_list` to do exactly what it sounds like.

```
static header\_t base; /\* Zero sized block to get us started. \*/ static header\_t \*freep = &base; /\* Points to first free block of memory. \*/ static header\_t \*usedp; /\* Points to first used block of memory. \*/ /\*  \* Scan the free list and look for a place to put the block. Basically, we're  \* looking for any block the to be freed block might have been partitioned from.  \*/ static void add\_to\_free\_list(header\_t \*bp) { header\_t \*p; for (p = freep; !(bp > p && bp < p->next); p = p->next) if (p >= p->next && (bp > p || bp < p->next)) break; if (bp + bp->size == p->next) { bp->size += p->next->size; bp->next = p->next->next; } else bp->next = p->next; if (p + p->size == bp) { p->size += bp->size; p->next = bp->next; } else p->next = bp; freep = p; } #define MIN\_ALLOC\_SIZE 4096 /\* We allocate blocks in page sized chunks. \*/ /\*  \* Request more memory from the kernel.  \*/ static header\_t \* morecore(size\_t num\_units) { void \*vp; header\_t \*up; if (num\_units > MIN\_ALLOC\_SIZE) num\_units = MIN\_ALLOC\_SIZE / sizeof(header\_t); if ((vp = sbrk(num\_units \* sizeof(header\_t))) == (void \*) -1) return NULL; up = (header\_t \*) vp; up->size = num\_units; add\_to\_free\_list (up); return freep; } 
```

Now that we have our two helper functions, writing our malloc function is pretty straight forward. We simply scan the free list and use the first block that is at least as big as the chunk we're trying to find. Because we use the first block we find instead of trying to find a "better" block, this algorithm is known as first fit.

A quick note to clarify: the size field in the header struct is measured in header-sized blocks, and not bytes.

```
/\*  \* Find a chunk from the free list and put it in the used list.  \*/ void \* GC\_malloc(size\_t alloc\_size) { size\_t num\_units; header\_t \*p, \*prevp; num\_units = (alloc\_size + sizeof(header\_t) - 1) / sizeof(header\_t) + 1; prevp = freep; for (p = prevp->next;; prevp = p, p = p->next) { if (p->size >= num\_units) { /\* Big enough. \*/ if (p->size == num\_units) /\* Exact size. \*/ prevp->next = p->next; else { p->size -= num\_units; p += p->size; p->size = num\_units; } freep = prevp; /\* Add to p to the used list. \*/ if (usedp == NULL) usedp = p->next = p; else { p->next = usedp->next; usedp->next = p; } return (void \*) (p + 1); } if (p == freep) { /\* Not enough memory. \*/ p = morecore(num\_units); if (p == NULL) /\* Request for more memory failed. \*/ return NULL; } } } 
```

Although this code isn't going to win any awards for low fragmentation, it'll work. And if it works, that means we can finally get to the fun part - the garbage collection!

  
  
from Hacker News https://ift.tt/2PkNtYQ