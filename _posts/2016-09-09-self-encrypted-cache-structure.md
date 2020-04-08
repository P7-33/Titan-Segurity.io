---
title: 'Self-Encrypted Cache Structure'
date: 2019-11-06T03:02:00+01:00
draft: false
---

![](https://www.nayuki.io/res/page-icon/64/self-encrypted-cache-structure.png) Self-encrypted cache structure
=============================================================================================================

Classic cache
-------------

### Background

[Caches](https://en.wikipedia.org/wiki/Cache_(computing) "Wikipedia: Cache (computing)") are a general concept where data retrieval can be sped up by reading from a closer and/or faster source. For example, sectors from a hard disk drive (with latency ~10 ms and speed ~100 MB/s) can be cached in RAM (latency ~10 ns, speed ~10 GB/s). For example, files from the Internet (latency like 1 s, speed like 1 MB/s) can be cached on the local computer’s HDD/SSD/RAM.

The standard way to implement a cache is to use an [associative data structure](https://en.wikipedia.org/wiki/Associative_array "Wikipedia: Associative array") / dictionary / mapping, storing each desired search key in association with its value. The key could be a URL/URI, file system path, disk block numeric address, randomly generated UUID, file hash, etc. The actual cache structure could be a simple array, B-tree, hash table, etc. The cache’s actual data could be stored ephemerally in RAM, or persistently on magnetic disk / flash memory.

### Privacy hazard

Normally, a cache is completely transparent. You can examine the structure, list all the stored keys and values, and see everything in plain sight. Of course, it is usually possible to selectively delete cached entries or purge the entire cache, as long as the system is under your control.

The problem is that transparent caches are a privacy hazard. For example, web browser software usually caches web pages and images, in order to speed up the browsing experience after the first visit. As a user browses around the web, pieces of his history will be stored in the cache. These pieces include mundane things, things he doesn’t want to share with others, or things he never even saw or knew about (e.g. from a script that prefetches images). Web caches are stored on disk, and it is too easy to forget the existence of the cache when its storage media ultimately gets disposed or transferred. Someone could obtain the media by looting dumpsters/abandonware or by an intentional secondhand sale/donation. The new owner could see the entire contents of the caches, which is probably not what the original owner expected or wanted.

Self-encrypted cache
--------------------

### Proposal

It turns out we can do better: We can design a data structure that stores and retrieves values by lookup keys exactly like a classic cache, but yields no useful information when listing the contents without knowing the original lookup keys.

The broad way to accomplish these goals is to still use an associative data structure, but now we encrypt each value using its corresponding key, and also obscure each key in some manner.

A semi-concrete implementation looks like this (Python pseudocode):

```
class SelfEncryptedCache: def \_\_init\_\_(self): self.dictionary = {} def set(self, key, value): temp = encrypt\_aes\_cbc(message=value, key=key) self.dictionary\[hash\_sha256(key)\] = temp def get(self, key): temp = self.dictionary\[hash\_sha256(key)\] return decrypt\_aes\_cbc(message=temp, key=key)
```

(We assume that `key` and `value` are byte arrays, `key` fits the cipher algorithm’s acceptable key lengths, and `value` fits the cipher algorithm’s acceptable message lengths.)

What does the above logic accomplish?

*   Clearly, `put()` and `get()` behave correctly, meeting the basic requirements of a cache.
    
*   The cache’s stored keys are random-looking hashes. You can’t tell if the cache contains keys like “kitten”, “Europe”, or “porn”. It’s easy to convert a key to a hash, but hard to do the reverse.
    
*   The only way to figure out an original key that got stored in the cache is to guess: Starting from a large set of candidates, compute the hash of each one and test whether that hash is among the stored keys.
    
*   The cache’s stored values are random garbage unless the key is supplied. This is how a modern, unbroken symmetric block cipher is supposed to work.
    
*   The confidentiality of each value hinges on whether the original key can be guessed.
    

### Attacks and defenses

If the cache is expected to have simple keys like English words or URLs of popular web sites, then searching these small spaces by brute force shouldn’t be much of a deterrent. In this case, we can borrow from the best practices of storing user passwords safely, and choose a hash function that requires more computation or memory, which can slow down brute force attacks by orders of magnitude. Typical hard hash functions include [scrypt](https://en.wikipedia.org/wiki/Scrypt "Wikipedia: scrypt"), [bcrypt](https://en.wikipedia.org/wiki/Bcrypt "Wikipedia: bcrypt"), [PBKDF2](https://en.wikipedia.org/wiki/PBKDF2 "Wikipedia: PBKDF2").

But even a hard hash function isn’t enough. Suppose everyone uses the same web browser, and the same URL will generate the same hash key for everyone. An attacker can precompute a large database of key+hash pairs that she is interested in. When she obtains a victim’s cache, she can check all the hashed keys against her database in much less time thanks to the precomputing. This is like the concept of [rainbow tables](https://en.wikipedia.org/wiki/Rainbow_table "Wikipedia: Rainbow table") in password cracking. So we borrow from password storage best practices again, and make every user generate a unique salt to incorporate into their key hashing process. Now an attacker cannot benefit from precomputation; she would need to run a fresh and expensive brute-force search for every victim she handles.

After hardening the key against brute-force guessing attacks, we can’t directly use the original key as the encryption key for the value. This is because it would be faster to guess the key by decrypting the value and looking for known patterns (e.g. file headers) instead of trying to un-hash the key. So we need to hash the key first, then encrypt the value with the hashed key. Our new algorithm looks like this:

```
class SelfEncryptedCache: def \_\_init\_\_(self): self.salt = random\_bytes() self.dictionary = {} def set(self, key, value): newkey = hash\_scrypt(self.salt + key) temp = encrypt\_aes\_cbc(message=value, key=newkey) self.dictionary\[newkey\] = temp def get(self, key): newkey = hash\_scrypt(self.salt + key) temp = self.dictionary\[newkey\] return decrypt\_aes\_cbc(message=temp, key=newkey)
```

Using a hard hash function can be detrimental to the legitimate user though. Suppose it takes a millisecond to compute the hash of a key. This means the computer can only serve up to a thousand requests per second. This could be unacceptable if say, a web browser is capable of rendering a thousand images per second but would be limited by the cache speed. So there is a trade-off between defending from attackers versus denying the primary user.

To my knowledge, the weaknesses of this “self-encrypted cache” scheme are easily guessable keys and the hash function trade-off. Although the scheme is not absolutely foolproof, it is not worse than a classic unencrypted cache, and I believe it provides a substantial privacy benefit in practice.

If we wanted to, we could add another layer of personal encryption that is independent of any cached data (key-value pairs). For example, the keys and values could be encrypted with a personal key, or the raw byte representation of the cache structure could be encrypted. We could also fuse the personal encryption functionality into the “self-encrypted cache” scheme to reduce the number of encryption operations performed, although this needs to be designed with care to avoid unintended security holes.

Just because the cache’s keys and data are encrypted doesn’t mean that an attacker can learn nothing. He can still examine aspects such as the sizes of keys and values (e.g., a document is 10 KB but a photo is 1000 KB), how long a key is stored (if he can continually monitor the cache over time), how frequently the cache is updated, etc. All the usual cryptographic caveats apply in this application. And the usual countermeasures apply – padding the data, inserting bogus key-value pairs that the legitimate user would never see or use, mimicking different time patterns, etc.

Miscellaneous
-------------

I call this structure a _self-encrypted cache_ because the encryption keys are supplied by the data being stored, not by some external choice that is independent from the data. Although it is legal to encrypt the entire cache’s data under some key, it doesn’t produce the desirable properties because anyone who obtains the encryption key can read the entire cache’s contents.

I believe that using self-encrypted caches can promote more caching with less concern about privacy. The results of expensive operations, like extracting thumbnails from videos, could be cached more liberally or aggressively if we knew that the cache would not disclose sensitive data whenever the original base data is gone.

For a classic cache, a user or program could remove key-value entries from the cache based on examining the key and/or value (e.g. pruning any key that starts with “http://example.com/”). But for an encrypted cache, a deleter can only look at the key and value sizes (unless they knew the original key to allow decryption). If we want to purge data after some expiration time, we could add an unencrypted timestamp field to each key-value pair.

It is entirely conceivable that peer-to-peer darknet software, which are designed to be private and censorship-resistant, and which automatically download and cache content from other users, would already implement some form of self-encrypted cache to protect its users.

  
  
from Hacker News https://ift.tt/33h4Nmh