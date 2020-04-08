---
title: 'String Algorithms in Lisp'
date: 2019-12-08T07:10:00+01:00
draft: false
---

It may not be immediately obvious why the whole chapter is dedicated to strings. Aren't they just glorified arrays? There are several answers to these challenges:

*   indeed, strings are not just arrays, or rather, not only arrays: in different contexts, other representations, such as trees or complex combinations of arrays, may be used. And, besides, there are additional properties that are important for strings even when they are represented as arrays
*   there's a lot of string-specific algorithms that deserve their own chapter
*   finally, strings play a significant role in almost every program, so they have specific handling: in the OS, standard library, and even, sometimes, your application framework

In the base case, a string is, indeed, an array. As we already know, this array may either store its length or be a 0-terminated security catastrophe, like in C (see buffer overflow). So, to iterate, strings should store their length. **Netstrings** are a notable take on the idea of the length-aware strings: it's a simple external format that serializes a string as a tuple of length and contents, separated by a colon and ending with a comma: `3:foo,` is the netsrting for the string `foo`.

More generally, a string is a sequence of characters. The characters themselves may be single bytes as well as fixed or variable-length byte sequences. The latter character encoding poses raises a challenging question of what to prefer, correctness or speed? With variable-length Unicode code points, the simplest and fastest string variant, a byte array, breaks, for it will incorrectly report its length (in bytes, not in characters) and fail to retrieve the character by index. Different language ecosystems address this issue differently, and the majority is, unfortunately, broken in one aspect or another. Overall, there may be two possible solution paths. The first one is to use a fixed-length representation and pad shorter characters to full length. Generally, such representation will be 32-bit UTF-32 resulting in up to 75% storage space waste for the most common 1-byte ASCII characters. The alternative approach will be to utilize a more advanced data-structure. The naive variant is a list, which implies an unacceptable slowdown of character access operation to `O(n)`. Yet, a balanced approach may combine minimal additional space requirements with acceptable speed. One of the solutions may be to utilize the classic **bitmap** trick: use a bit array indicating, for each byte, whether it's the start of a character (only a 12% overhead). Calculating the character position may be performed in a small number of steps with the help of an infamous, in close circles, operation — Population count aka Hamming weight. This hardware instruction calculates the number of 1-bits in an integer and is accessible via `logcount` Lisp standard library routine. Behind the scenes, it is also called for bit arrays if you invoke `count 1` on them. At least this is the case for SBCL:

```
CL-USER> (disassemble (lambda (x) (declare (type (simple-array bit) x)) (count 1 x))) ; disassembly for (LAMBDA (X)) ; Size: 267 bytes. Origin: #x100FC9FD1A ... ; DA2: F3480FB8FA POPCNT RDI, RDX 
```

The indexing function implementation may be quite tricky, but the general idea is to try to jump ahead `n` characters and calculate the popcount of the substring from the previous position to the current that will tell us the number of characters we have skipped. For the base case of a 1-byte string, we will get exactly where we wanted in just 1 jump and 1 popcount. However, if there were multibyte characters in the string, the first jump would have skipped less than `n` characters. If the difference is sufficiently small (say, below 10) we can just perform a quick linear scan of the remainder and find the position of the desired character. If it's larger than `n/2` we can jump ahead `n` characters again (this will repeat at most 3 times as the maximum byte-length of a character is 4), and if it's below `n/2` we can jump `n/2` characters. And if we overshoot we can reverse the direction of the next jump or search. You can see where it's heading: if at each step (or, at least, at each 4th step) we are constantly half dividing our numbers this means `O(log n)` complexity. That's the worst performance for this function we can get, and it will very efficiently handle the cases when the character length doesn't vary: be it 1 byte — just 2 operations, or 4 bytes — 8 ops.

Here is the prototype of the `char-index` operation implemented according to the described algorithm (without the implementation of the `mb-linear-char-index` that performs the final linear scan):

```
(defstruct (mb-string (:conc-name mbs-)) bytes bitmap) (defparameter *mb-threshold* 10) (defun mb-char-index (string i) (let ((off 0)) (loop (with ((cnt (count 1 (mbs-bitmap string) :start off :end (+ off i)))) (diff (- i cnt))) (cond ((= cnt i) (return (+ off i))) ((< diff *mb-threshold*) (return (mb-linear-char-index string diff off))) ((< cnt (floor i 2)) (:+ off i) (:- i cnt)) (t (:+ off (floor i 2)) (:- i cnt))))))) 
```

The `length` of such a string may be calculated by perfoming the popcount on the whole bitmap:

```
(defun mb-length (string) (count 1 (mbs-bitmap string))) 
```

It's also worth taking into account that there exists a set of rules assembled under the umbrella of the Unicode collation algorithm that specifies how to order strings containing Unicode code-points.

Strings are often subject to subsequencing, so an efficient implementation may use structure sharing. As we remember, in Lisp, this is accessible via the displaced arrays mechanism (and a convenience RUTILS function `slice` that we have already used in the code above). Yet, structure sharing should be utilized with care as it opens a possibility for action-at-a-distance bugs if the derived string is modified, which results in parallel modification of the original. Though, strings are rarely modified in-place so, even in its basic form (without mandatory immutability), the approach works well. Moreover, some programming language environments make strings immutable by default. In such cases, to perform on-the-fly string modification (or rather, creation) such patterns as the Java `StringBuilder` are used, which creates the string from parts by first accumulating them in a list and then, when necessary, concatenating the list's contents into a single final string. An alternative approach is string formatting (the `format` function in Lisp) that is a higher-level interface, which still needs to utilize some underlying mutation/combination mechanism.

Another important string-related technology is **interning**. It is a space-saving measure to avoid duplicating the same strings over and over again, which operates by putting a string in a table and using its index afterwards. This approach also enables efficient equality comparison. Interning is performed by the compiler implicitly for all constant strings (in the special segment of the program's memory called "string table"/`sstab`), and also may be used explicitly. In Lisp, there's a standard function `intern`, for this. Lisp symbols used interned strings as their names. Another variant of interning is string pooling. The difference is that interning uses a global string table while the pools may be local.

Strings in the Editor
---------------------

Now, let's consider situations, in which representing strings as arrays doesn't work. The primary one is in the editor. I.e. when constant random modification is the norm. There's another not so obvious requirement related to editing: handle potentially arbitrary long strings that still need to be dynamically modified. Have you tried opening a hundred-megabyte text document in your favorite editor? You'd better don't unless you're a Vim user :) Finally, an additional limitation of handling the strings in the editor is posed when we allow concurrent modification. This we'll discuss in the chapter on concurrent algorithms.

So, why array as a string backend doesn't work well in the editor? Because of content relocation required by all edit operations. `O(n)` editing is, obviously, not acceptable. What to do? There are several more advanced approaches:

1.  The simplest change will be, once again, to use an array of arrays. For example, for each line. This will not change the general complexity of `O(n)` but, at least, will reduce `n` significantly. The issue is that, still, it will depend on the length of the line so, for not so rare degraded case when there are few or no linebreaks, the performance will seriously deteriorate. And, moreover, having observable performance differences between editing different paragraphs of the text is not user-friendly at all.
2.  A more advanced approach would be to use trees, reducing access time to `O(log n)`. There are many different kinds of trees and, in fact, only a few may work as efficient string representations. Among them a popular data structure, for representing strings, is a **Rope**. It's a binary tree where each leaf holds a substring and its length, and each intermediate node further holds the sum of the lengths of all the leaves in its left subtree. It's a more-or-less classic application of binary trees to a storage problem so we won't spend more time on it here. Suffice to say that it has the expected binary-tree performance of `O(log n)` for all operations, provided that we keep it balanced. It's an ok alternative to a simple array, but, for such a specialized problem, we can do better with a custom solution.
3.  And the custom solution is to return to arrays. There's one clever way to use them that works very well for dynamic strings. It is called a **Gap buffer**. This structure is an array (buffer) with a gap in the middle. I.e., let's imagine that we have a text of `n` characters. The Gap buffer will have a length of `n + k` where `k` is the gap size — some value, derived from practice, that may fluctuate in the process of string modification. You can recognize this gap as the position of the cursor in the text. Insertion operation in the editor is performed exactly at this place, so it's `O(1)`. Just, afterwards, the gap will shrink by 1 character, so we'll have to resize the array, at some point, if there are too many insertions and the gap shrinks below some minimum size (maybe, below 1). The deletion operation will act exactly the opposite by growing the gap at one of the sides. The Gap buffer is an approach that is especially suited for normal editing — a process that has its own pace. It also allows the system to represent multiple cursors by maintaining several gaps. Also, it may be a good idea to represent each paragraph as a gap buffer and use an array of them for the whole text. The gap buffer is a special case of the Zipper pattern that we'll discuss in the chapter on functional data structures.

Substring Search
----------------

One of the most common string operations is substring search. For ordinary sequences we, usually, search for a single element, but strings, on the contrary, more often need subsequence search, which is more complex. A naive approach will start by looking for the first character, then trying to match the next character and the next, until either something ends or there's a mismatch. Unlike with hash-tables, Lisp standard library has good support for string processing, including such operations as `search` (which, actually, operates on any sequence type) and `mismatch` that compares two strings from a chosen side and returns the position at which they start to diverge.

If we were to implement our own string-specific search, the most basic version would, probably, look like this:

```
(defun naive-match (pat str) (dotimes (i (- (1+ (length str)) (length pat))) (when (= (mismatch pat (slice str i)) (length pat)) (return-from naive-match i)))) 
```

If the strings had been random, the probability that we are correctly matching each subsequent character would have dropped to 0 very fast. Even if we consider just the English alphabet, the probability of the first character being the same in 2 random strings is `1/26`, the first and second — `1/676`, and so on. And if we assume that the whole charset may be used, we'll have to substitute 26 with 256 or a greater value. So, in theory, such naive approach has almost `O(n)` complexity, where `n` is the length of the string. Yet, the worst case has `O(n * m)`, where `m` is the length of the pattern. Why? If we try to match a pattern `a..ab` against a string `aa.....ab`, at each position, we'll have to check the whole pattern until the last character mismatches. This may seem like an artificial example and, indeed, it rarely occurs. But, still, real-world strings are not so random and are much closer to the uniform corner case than to the random one. So, researchers have come up with a number of ways to improve subsequence matching performance. Those include the four well-known inventor-glorifying substring search algorithms: Knuth-Morris-Pratt, Boyer-Moore, Rabin-Karp, and Aho-Corasick. Let's discuss each one of them and try to determine their interesting properties.

### KMP

Knuth-Morris-Pratt is the most basic of these algorithms. Prior to performing the search, it examines the pattern to find repeated subsequences in it and creates a table containing, for each character of the pattern, the length of the prefix of the pattern that can be skipped if we have reached this character and failed the search at it. This table is also called the "failure function". The number in the table is calculated as the length of the proper suffix[\[1\]](http://lisp-univ-etc.blogspot.com/2019/11/programming-algorithms-strings.html#f10-1) of the pattern substring ending before the current character that matches the start of the pattern.

I'll repeat here the example provided in Wikipedia that explains the details of the table-building algorithm, as it's somewhat tricky.

Let's build the table for the pattern `abdcabd`. We set the table entry for the first char `a` to -1. To find the entry for `b`, we must discover a proper suffix of `a` which is also a prefix of the pattern. But there are no proper suffixes of `a`, so we set this entry to 0. To find the entry with index 2, we see that the substring `ab` has a proper suffix `b`. However `b` is not a prefix of the pattern. Therefore, we also set this entry to 0.

For the next entry, we first check the proper suffix of length 1, and it fails like in the previous case. Should we also check longer suffixes? No. We can formulate a shortcut rule: at each stage, we need to consider checking suffixes of a given size `(1+ n)` only if a valid suffix of size `n` was found at the previous stage and should not bother to check longer lengths. So we set the table entry for `c` to 0 also.

We pass to the subsequent character `a`. The same logic shows that the longest substring we need to consider has length 1, and as in the previous case it fails since `d` is not a prefix. But instead of setting the table entry to 0, we can do better by noting that `a` is also the first character of the pattern, and also that the corresponding character of the string can't be `a` (as we're calculating for the mismatch case). Thus there is no point in trying to match the pattern for this character again — we should begin 1 character ahead. This means that we may shift the pattern by match length plus one character, so we set the table entry to -1.

Considering now the next character `b`: though by inspection the longest substring would appear to be `a`, we still set the table entry to 0. The reasoning is similar to the previous case. `b` itself extends the prefix match begun with `a`, and we can assume that the corresponding character in the string is not `b`. So backtracking before it is pointless, but that character may still be `a`, hence we set the entry not to -1, but to 0, which means shifting the pattern by 1 character to the left and trying to match again.

Finally, for the last character `d`, the rule of the proper suffix matching the prefix applies, so we set the table entry to 2.

The resulting table is:

```
 a b c d a b d -1 0 0 0 -1 0 2 
```

Here's the implementation of the table-building routine:

```
(defun kmp-table (pat) (let ((rez (make-array (length pat))) (i 0)) ; prefix length (:= (? rez 0) -1) (loop :for j :from 1 :below (length pat) :do (if (char= (char pat i) (char pat j)) (:= (? rez j) (? rez i)) (progn (:= (? rez j) i i (? rez i)) (loop :while (and (>= i 0) (not (char= (char pat i) (char pat j)))) :do (:= i (? rez i))))) (:+ i)) rez)) 
```

It can be proven that it runs in `O(m)`. We won't show it here, so coming up with proper calculations is left as an exercise to the reader.

Now, the question is, how shall we use this table? Let's look at the code:

```
(defun kmp-match (pat str) (let ((s 0) (p 0) (ff (kmp-table pat)) (loop :while (< s (length str)) :do (if (= (char pat p) (char str s)) ;; if the current characters of the pattern and string match (if (= (1+ p) (length pat))) ;; if we reached the end of the pattern - success (return (- s p)) ;; otherwise, match the subsequent characters (:= p (1+ p) s (1+ s))) ;; if the characters don't match (if (= -1 (? ff p)) ;; shift the pattern for the whole length (:= p 0 ;; and skip to the next char in the string s (1+ s)) ;; try matching the current char again, ;; shifting the pattern to align the prefix ;; with the already matched part (:= p (? ff p))))))) 
```

As we see, the index in the string (`s`), is incremented at each iteration except when the entry in the table is positive. In the latter case, we may examine the same character more than once but not more than we have advanced in the pattern. And the advancement in the pattern meant the same advancement in the string (as the match is required for the advancement). In other words, we can backtrack not more than `n` times over the whole algorithm runtime, so the worst-case number of operations in `kmp-search` is `2n`, while the best-case is just `n`. Thus, the total complexity is `O(n + m)`.

And what will happen in our `aa..ab` example? The failure function for it will look like the following: `-1 -1 -1 -1 (- m 2)`. Once we reach the first mismatch, we'll need to backtrack by 1 character, perform the comparison, which will mismatch, advance by 1 character (to `b`), mismatch again, again backtrack by 1 character, and so on until the end of the string. So, this case, will have almost the abovementiond `2n` runtime.

To conclude, the optimization of KMP lies in excluding unnecessary repetition of the same operations by memoizing the results of partial computations — both in table-building and matching parts. The next chapter of the book will be almost exclusively dedicated to studying this approach in algorithm design.

### BM

Boyer-Moore algorithm is conceptually similar to KMP, but it matches from the end of the pattern. It also builds a table, or rather three tables, but using a different set of rules, which also involve the characters in the string we search. More precisely, there are two basic rules instead of one for KMP. Besides, there's another rule, called the Galil rule, that is required to ensure the linear complexity of the algorithm. Overall, BM is pretty complex in the implementation details and also requires more preprocessing than KMP, so its utility outweighs these factors only when the search is repeated multiple times for the same pattern.

Overall, BM may be faster with normal text (and the longer the pattern, the faster), while KMP will work the best with strings that have a short alphabet (like DNA). However, I would choose KMP as the default due to its relative simplicity and much better space utilization.

### RK

Now, let's talk about alternative approaches that rely on techniques other than pattern preprocessing. They are usually used to find matches of multiple patterns in one go as, for the base case, their performance will be worse than that of the previous algorithms.

Rabin-Karp algorithm uses an idea of the **Rolling hash**. It is a hash function that can be calculated incrementally. The RK hash is calculated for each substring of the length of the pattern. If we were to calculate a normal hash function like fnv-1, we'd need to use each character for the calculation — resulting in `O(n * m)` complexity of the whole procedure. The rolling hash is different as it requires, at each step of the algorithm, to perform just 2 operations: as the "sliding window" moves over the string, subtract the part of the hash corresponding to the character that is no longer part of the substring and add the new value for the character that has just become the part of the substring.

Here is the skeleton of the RK algorithm:

```
(defun rk-match (pat str) (let ((len (length pat)) (phash (rk-hash pat))) (loop :for i :from len :to (length str) :for beg := (- i len) :for shash := (rk-hash (slice str 0 len)) :then (rk-rehash len shash (char str beg) (char str i)) :when (and (= phash shash) (string= pat (slice str beg len)) :collect beg))) 
```

A trivial `rk-hash` function would be just:

```
(defun rk-hash (str) (loop :for ch :across str :sum (char-code ch))) 
```

But it is, obviously, not a good hash-function as it doesn't ensure the equal distribution of hashes. Still, in this case, we need a reversible hash-function. Usually, such hashes add position information into the mix. An original hash-function for the RK algorithm is the Rabin fingerprint that uses random irreducible polynomials over Galois fields of order 2. The mathematical background needed to explain it is somewhat beyond the scope of this book. However, there are simpler alternatives such as the following:

```
(defun rk-hash (str) (assert (> (length str) 0)) (let ((rez (char-code (char str 0)))) (loop :for ch :across (slice str 1) :do (:= rez (+ (rem (* rez 256) 101) (char-code ch)))) (rem rez 101)) 
```

Its basic idea is to treat the partial values of the hash as the coefficients of some polynomial.

The implementation of `rk-rehash` for this function will look like this:

```
(defun rk-rehash (hash len ch1 ch2) (rem (+ (* (+ hash 101 (- (rem (* (char-code ch1) (expt 256 (1- len))) 101))) 256) (char-code ch2)) 101)) 
```

Our `rk-match` could be used to find many matches of a single pattern. To adapt it for operating on multiple patterns at once, we'll just need to pre-calculate the hashes for all patterns and lookup the current rk-hash value in this set. Additional optimization of this lookup may be performed with the help of a Bloom filter — a stochastic data structure we'll discuss in more detail later.

Finally, it's worth noting that there are other similar approaches to the rolling hash concept that trade some of the uniqueness properties of the hash function for the ability to produce hashes incrementally or have similar hashes for similar sequences. For instance, the **Perceptual hash** (phash) is used to find near-match images.

### AC

Aho-Corasick is another algorithm that allows matching multiple strings at once. The preprocessing step of the algorithm constructs a **Finite-State Machine** (FSM) that resembles a trie with additional links between the various internal nodes. The FSM is a graph data structure that encodes possible states of the system and actions needed to transfer it from one state to the other.

The AC FSM is constructed in the following manner:

1.  Build a trie of all the words in the set of search patterns (the search dictionary). This trie represents the possible flows of the program when there's a successful character match at the current position. Add a loop edge for the root node.
2.  Add backlinks transforming the trie into a graph. The backlinks are used when a failed match occurs. These backlinks are pointing either to the root of the trie or if there are some prefixes that correspond to the part of the currently matched path — to the end of the longest prefix. The longest prefix is found using BFS of the trie. This approach is, basically, the same idea used in KMP and BM to avoid reexamining the already matched parts. So backlinks to the previous parts of the same word are also possible.

Here is the example FSM for the search dictionary `'("the" "this" "that" "it" "his")`:

[![](https://2.bp.blogspot.com/-w84XBosyVpk/XdUY_5st4HI/AAAAAAAACPc/GnyFn0F62hk0LtqDlaZMU4Nbg-j1086EwCPcBGAYYCw/s640/ac.jpg)](https://2.bp.blogspot.com/-w84XBosyVpk/XdUY_5st4HI/AAAAAAAACPc/GnyFn0F62hk0LtqDlaZMU4Nbg-j1086EwCPcBGAYYCw/s1600/ac.jpg)

Basically, it's just a trie with some backlinks to account for already processed prefixes. One more detail missing for this graph to be a complete FSM is an implicit backlink from all nodes without an explicit backlink that don't have backlinks to the root node.

The main loop of the algorithm is rather straightforward, examine each character and then:

*   either follow one of the transitions (direct edge) if the character of the edge matches
*   or follow the backlink if it exists
*   or reset the FSM state — go to root
*   if the transition leads us to a terminal node, record the match(es) and return to root as, well

As we see from the description, the complexity of the main loop is linear in the length of the string: at most, 2 matches are performed, for each character. The FSM construction is also linear in the total length of all the words in the search dictionary.

The algorithm is often used in antivirus software to perform an efficient search for code signatures against a database of known viruses. It also formed the basis of the original Unix command `fgrep`. And, from my point of view, it's the simplest to understand yet pretty powerful and versatile substring search algorithm that may be a default choice if you ever have to implement one yourself.

Regular Expressions
-------------------

Searching is, probably, the most important advanced string operation. Besides, it is not limited to mere substring search — matching of more complex patterns is even in higher demand. These patterns, which are called "regular expressions" or, simply, **regex**es, may include optional characters, repetition, alternatives, backreferences, etc. Regexes play an important role in the history of the Unix command-line, being the principal technology of the infamous `grep` utility, and then the cornerstone of Perl. All modern programming languages support them either in the standard library or, as Lisp, with high-quality third-party addons ([cl-ppcre](http://edicl.github.io/cl-ppcre/)).

One of my favorite programming books, "Beautiful Code", has a chapter on implementing simple regex matching from Brian Kernighan with code written by Rob Pike. It shows how easy it is to perform basic matching of the following patterns:

```
c matches any literal character c . matches any single character ^ matches the beginning of the input string $ matches the end of the input string * matches zero or more occurrences of the previous character 
```

Below the C code from the book is translated into an equivalent Lisp version:

```
(defun match (regex text) "Search for REGEX anywhere in TEXT." (if (starts-with "^" regex) ; STARTS-WITH is from RUTILS (match-here (slice regex 1) text) (dotimes (i (length text)) (when (match-here regex (slice text i)) (return t))))) (defun match-here (regex text) "Search for REGEX at beginning of TEXT." (cond ((= 0 (length regex)) t) ((and (> (length regex) 1) (char= #\* (char regex 1))) (match-star (char regex 1) (slice regex 2) text)) ((string= "$" regex) (= 0 (length text))) ((and (> (length text) 0) (member (char text 0) (list #\. (char text 0))) (match-here (slice regex 1) (slice text 1))))) (defun match-star (c regex text) "Search for C*REGEX at beginning of TEXT." (loop (when (match-here regex text) (return t)) (:= text (slice text 1)) (unless (and (> (length text) 0) (member c (list #\. (char text 0)))) (return))) 
```

This is a greedy linear algorithm. However, modern regexes are much more advanced than this naive version. They include such features as register groups (to record the spans of text that match a particular subpattern), backreferences, non-greedy repetition, and so on and so forth. Implementing those will require changing the simple linear algorithm to a backtracking one. And incorporating all of them would quickly transform the code above into a horrible unmaintainable mess: not even due to the number of cases that have to be supported but due to the need of accounting for the complex interdependencies between them.

And, what's worse, soon there will arise a need to resort to backtracking. Yet, a backtracking approach has a critical performance flaw: potential exponential runtime for certain input patterns. For instance, the Perl regex engine (PCRE) requires over sixty seconds to match a 30-character string `aa..a` against the pattern `a?{15}a{15}` (on standard hardware). While the alternative approach, which we'll discuss next, requires just twenty microseconds — a million times faster. And it handles a 100-character string of a similar kind in under 200 microseconds, while Perl would require over 1015 years.[\[2\]](http://lisp-univ-etc.blogspot.com/2019/11/programming-algorithms-strings.html#f10-2)

This issue is quite severe and has even prompted Google to release their own regex library with strict linear performance guarantees — [RE2](https://github.com/google/re2). The goal of the library is not to be faster than all other engines under all circumstances. Although RE2 guarantees linear-time performance, the linear-time constant varies depending on the overhead entailed by its way of handling of the regular expression. In a sense, RE2 behaves pessimistically whereas backtracking engines behave optimistically, so it can be outperformed in various situations. Also, its goal is not to implement all of the features offered by PCRE and other engines. As a matter of principle, RE2 does not support constructs for which only backtracking solutions are known to exist. Thus, backreferences and look-around assertions are not supported.

The figures above are taken from a [seminal article](https://swtch.com/~rsc/regexp/regexp1.html) by Russ Cox. He goes on to add:

> Historically, regular expressions are one of computer science's shining examples of how using good theory leads to good programs. They were originally developed by theorists as a simple computational model, but Ken Thompson introduced them to programmers in his implementation of the text editor QED for CTSS. Dennis Ritchie followed suit in his own implementation of QED, for GE-TSS. Thompson and Ritchie would go on to create Unix, and they brought regular expressions with them. By the late 1970s, regular expressions were a key feature of the Unix landscape, in tools such as ed, sed, grep, egrep, awk, and lex. Today, regular expressions have also become a shining example of how ignoring good theory leads to bad programs. The regular expression implementations used by today's popular tools are significantly slower than the ones used in many of those thirty-year-old Unix tools.

The linear-time approach to regex matching relies on a similar technic to the one in the Aho-Corasick algorithm — the FSM. Actually, if by regular expressions we mean a set of languages that abide by the rules of the regular grammars in the Chomsky hierarchy of languages, the FSM is their exact theoretical computation model. Here is how an FSM for a simple regex `a*b$` might look like:

[![](https://3.bp.blogspot.com/-hgkgpHFZwVg/XdUY6Wwvg8I/AAAAAAAACPc/gjDY5Qza96YLrRtg-rXeib87AQw13QYZgCPcBGAYYCw/s400/regex.jpg)](https://3.bp.blogspot.com/-hgkgpHFZwVg/XdUY6Wwvg8I/AAAAAAAACPc/gjDY5Qza96YLrRtg-rXeib87AQw13QYZgCPcBGAYYCw/s1600/regex.jpg)

Such FSM is called an **NFA** (Nondeterministic Finite Automaton) as some states have more than one alternative successor. Another type of automata are **DFA**s (Deterministic Finite Automata) that permit transitions to at most one state, for each state. The method to transform the regex into an NFA is called the Thompson's construction. And an NFA can be made into a DFA by the Powerset construction and then be minimized to get an optimal automaton. DFAs are more efficient to execute than NFAs, because DFAs are only ever in one state at a time: they never have a choice of multiple next states. But the construction takes additional time. Anyway, both NFAs and DFAs guarantee linear-time execution.

The Thompson's algorithm builds the NFA up from partial NFAs for each subexpression, with a different construction for each operator. The partial NFAs have no matching states: instead, they have one or more dangling arrows, pointing to nothing. The construction process will finish by connecting these arrows to a matching state.

*   The NFAs for matching a single character `e` is a single node with a slot for an incoming arrow and a pending outgoing arrow labeled with `e`.
*   The NFA for the concatenation `e1e2` connects the outgoing arrow of the `e1` machine to the incoming arrow of the `e2` machine.
*   The NFA for the alternation `e1|e2` adds a new start state with a choice of either the `e1` machine or the `e2` machine.
*   The NFA for `e?` alternates the `e` machine with an empty path.
*   The NFA for `e*` uses the same alternation but loops a matching `e` machine back to the start.
*   The NFA for `e+` also creates a loop, but one that requires passing through `e` at least once.

Counting the states in the above constructions, we can see that this technic creates exactly one state per character or metacharacter in the regular expression. The only exception is the constructs `c{n}` or `c{n,m}` which require to duplicate the single chracter automaton `n` or `m` times respectively, but it is still a constant number. Therefore the number of states in the final NFA is at most equal to the length of the original regular expression plus some constant.

### Implementation of the Thompson's Construction

The core of the algorithm could be implemented very transparently with the help of the Lisp generic functions. However, to enable their application, we'd first need to transform the raw expression into a sexp (tree-based) form. Such representation is supported, for example, in the cl-ppcre library:

```
PPCRE> (parse-string "ab[0-9]+c$") (:SEQUENCE "ab" (:GREEDY-REPETITION 1 NIL (:RANGE #\0 #\9)) #\c :END-ANCHOR) 
```

Parsing is a whole separate topic that will be discussed next. But once we have performed it, we gain a possibility to straightforwardly implement the Thompson's construction by traversing the parse tree and emitting, for each state, the corresponding part of the automaton. The Lisp generic functions are a great tool for implementing such transformation as they allow to define methods that are selected based on either the type or the identity of the arguments. And those methods can be added independently, so the implementation is clear and extensible. We will define 2 generic functions: one to emit the automaton fragment (`th-part`) and another to help in transition selection (`th-match`).

First, let's define the state node of the FSM. We will use a linked graph representation for the automaton. So, a variable for the FSM in the code will point to its start node, and it will, in turn, reference the other nodes. There will also be a special node that will be responsible for recording the matches (`*matched-state*`).

```
(defstruct th-state transitions) (defparameter *initial-state* nil) (defparameter *matched-state* (make-th-state)) (defun th-state (&rest transitions) "A small convenience function to construct TH-STATE structs." (make-th-state :transitions (loop :for (cond state) :on transitions :by 'cddr :collect (pair cond state)))) 
```

And now, we can define the generic function that will emit the nodes:

```
(define-condition check-start-anchor () ()) (defgeneric th-part (next-state kind &rest args) (:documentation "Emit the TH-STATE structure of a certain KIND (which may be a keyword or a raw string) using the other ARGS and pointing to NEXT-STATE struct.") (:method (next-state (kind (eql :sequence)) &rest args) (apply 'th-part (if (rest args) (apply 'th-part :sequence (rest args)) next-state) (first args))) (:method (next-state (kind (eql :greedy-repetition)) &rest args) ;; this method can handle *, +, {n}, and {n,m} regex modifiers ;; in any case, there's a prefix sequence of fixed nonnegative length ;; of identical elements that should unconditionally match ;; followed by a bounded or unbounded sequence that, ;; in case of a failed match, transitions to the next state (apply 'th-part (let ((*initial-state* next-state)) (apply 'th-part next-state :sequence (loop :repeat (or (second args) 1) :collect (mklist (third args))))) :sequence (loop :repeat (first args) :collect (mklist (third args))))) (:method (next-state (kind character) &rest args) (th-state kind next-state ;; Usually, *initial-state* will be nill, i.e. further computations ;; alone this path will be aborted, but for some variants (? or *) ;; they will just continue normally to the next state. ;; The special variable allows to control this as you can see in ;; the method for :greedy-repetition t *initial-state*)) (:method (next-state (kind (eql :end-anchor)) &rest args) (th-state nil *matched-state* t *initial-state*)) (:method (next-state (kind (eql :start-anchor)) &rest args) ;; This part is unique in that all the other parts consume the next character ;; (we're not implementing lookahead here), but this one shouldn't. ;; To implement such behavior without the additional complexity created by passing ;; the string being searched to this function (which we'll still, probably, need to do ;; later on, but were able to avoid so far), we can resort to a cool Lisp technique ;; of signaling a condition that can be handled specially in the top-level code (signal 'check-start-anchor) next-state)) 
```

Here, we have defined some of the methods of `th-part` that specialize for the basic `:sequence` of expressions, `:greedy-repetition` (regex `*` and `+`), a single character and single symbols `:start-anchor`/`:end-anchor` (regexes `^` and `$`). As you can see, some of them dispatch (are chosen based on) the identity of the first argument (using `eql` specializers), while the character-related method specializes on the class of the arg. As we develop this facility, we could add more methods with `defmethod`. Running `th-part` on the whole parse-tree will produce the complete automaton, we don't need to do anything else!

To use the constructed FSM, we run it with the string as input. NFAs are endowed with the ability to guess perfectly when faced with a choice of next state: to run the NFA on a real computer, we must find a way to simulate this guessing. One way to do that is to guess one option, and if that doesn't work, try the other. A more efficient way to simulate perfect guessing is to follow all admissible paths simultaneously. In this approach, the simulation allows the machine to be in multiple states at once. To process each letter, it advances all the states along all the arrows that match the letter. In the worst case, the NFA might be in every state at each step, but this results in at worst a constant amount of work independent of the length of the string, so arbitrarily large input strings can be processed in linear time. The efficiency comes from tracking the set of reachable states but not which paths were used to reach them. In an NFA with `n` nodes, there can only be `n` reachable states at any step.

```
(defun run-nfa (nfa str) (let ((i 0) (start 0) (matches (list)) (states (list nfa))) ;; this is the counterpart for the start-anchor signal (handler-bind ((check-start-anchor ;; there's no sense to proceed matching a ^... regex ;; if the string is not at its start (lambda (c) (when (> i 0) (return-from run-nfa))))) (dovec (char (concatenate 'vector str #(nil))) ; for handling end-anchor (let ((new-states (list))) (dolist (state states) (dolist (tr (? state 'transitions)) (when (th-match tr char) (case (rt tr) (*matched-state* (push start matches)) (nil ) ; ignore it (t (pushnew (rt tr) new-states))) (return)))) (if new-states (:= states new-states) (:= states (list nfa) start nil))) (:+ i) (unless start (:= start i)))) matches)) 
```

The `th-match` function may have methods to match a single char and a character range, as well as a particular predicate. Its implementation is trivial and left as an exercise to the reader.

Overall, interpreting an automaton is a simple and robust approach, yet if we want to squeeze all the possible performance, we can compile it directly to machine code. This is much easier to do with the DFA as it has at most 2 possible transitions from each state, so the automaton can be compiled to a multi-level conditional and even a jump-table.

Grammars
--------

Regexes are called "regular" for a reason: there's a corresponding mathematical formalism "regular languages" that originates from the hierarchy of grammars compiled by Noah Chomsky. This hierarchy has 4 levels, each one allowing strictly more complex languages to be expressed with it. And for each level, there's an equivalent computation model:

*   Type-0: recursivel-enumerable (or universal) grammars — Turing machine
*   Type-1: context-dependent (or context-sensitive) grammars — a linear bounded automaton
*   Type-2: context-free grammars — pushdown automaton
*   Type-3: regular grammars — FSM

We have already discussed the bottom layer of the hierarchy. Regular languages are the most limited (and thus the simplest to implement): for example, you can write a regex `a{15}b{15}`, but you won't be able to express `a{n}b{n}` for an arbitrary `n`, i.e. ensure that `b` is repeated the same number of times as `a`. The top layer corresponds to all programs and so all the programming science and lore, in general, is applicable to it. Now, let's talk about context-free grammars which are another type that is heavily used in practice and even has a dedicated set of algorithms. Such grammars can be used not only for simple matching but also for parsing and generation. **Parsing**, as we have seen above, is the process of transforming a text that is assumed to follow the rules of a certain grammar into the structured form that corresponds to the particular rules that can be applied to this text. And generation is the reverse process: applying the rules, obtain the text. This topic is huge and there's a lot of literature on it including the famous [Dragon Book](https://en.wikipedia.org/wiki/Compilers:_Principles,_Techniques,_and_Tools).

Parsing is used for processing both artificial (including programming) and natural languages. And, although different sets of rules may be used, as well as different approaches for selecting a particular rule, the resulting structure will be a tree. In fact, formally, each grammar consists of 4 items:

*   The set of terminals (leaves of the parse tree) or tokens of the text: these could be words or characters for the natural language; keywords, identifiers, and literals for the programming language; etc.
*   The set of nonterminals — symbols used to name different items in the rules and in the resulting parse tree — the non-leaf nodes of the tree. These symbols are abstract and not encountered in the actual text. The examples of nonterminals could be `VB` (verb) or `NP` (noun phrase) in natural language parsing, and `if-section` or `template-argument` in parsing of C++ code.
*   The root symbol (which should be one of the nonterminals).
*   The set of production rules that have two-sides: a left-hand (lhs) and a right-hand (rhs) one. In the left-hand side, there should be at least one nonterminal, which is substituted with a number of other terminals or nonterminals in the right-hand side. During generation, the rule allows the algorithm to select a particular surface form for an abstract nonterminal (for example, turn a nonterminal `VB` into a word `do`). During parsing, which is a reverse process, it allows the program, when it's looking at a particular substring, to replace it with a nonterminal and expand the tree structure. When the parsing process reaches the root symbol in the by performing such substitution and expansion, it is considered terminated.

Each compiler has to use parsing as a step in transforming the source into executable code. Also, parsing may be applied for any data format (for instance, JSON) to transform it into machine data. In natural language processing, parsing is used to build the various tree representations of the sentence, which encode linguistic rules and structure.

There are many different types of parsers that differ in the additional constraints they impose on the structure of the production rules of the grammar. The generic context-free constraint is that in each production rule the left-hand side may only be a single nonterminal. The most wide-spread of context-free grammars are LL(k) (in particular, LL(1)) and LR (LR(1), SLR, LALR, GLR, etc). For example, LL(1) parsers (one of the easiest to build) parses the input from left to right, performing leftmost derivation of the sentence, and it is allowed to look ahead at most 1 character. Not all combinations of derivation rules allow the algorithm to build a parser that will be able to perform unambiguous rule selection under such constraints. But, as the LL(1) parsing is simple and efficient, some authors of grammars specifically target their language to be LL(1)-parseable. For example, Pascal and other programming languages created by Niklas Wirth fall into this category.

There are also two principal approaches to implementing the parser: a top-down and a bottom-up one. In a top-down approach, the parser tries to build the tree from the root, while, in a bottom-up one, it tries to find the rules that apply to groups of terminal symbols and then combine those until the root symbol is reached. Obviously, we can't enumerate all parsing algorithms here, so we'll study only a single approach, which is one of the most wide-spread, efficient, and flexible ones — **Shift-Reduce Parsing**. It's a bottom-up linear algorithm that can be considered one of the instances of the pushdown automaton approach — a theoretical computational model for context-free grammars.

A shift-reduce parser operates on a queue of tokens of the original sentence. It also has access to a stack. At each step, the algorithm can perform:

*   either a `shift` operation: take the token from the queue and push it onto the stack
*   or a `reduce` operation: take the top items from the stack, select a matching rule from the grammar, and add the corresponding subtree to the partial parse tree, in the process, removing the items from the stack

Thus, for each token, it will perform exactly 2 "movement" operations: push it onto the stack and pop from the stack. Plus, it will perform rule lookup, which requires a constant number of operations (maximum length of the rhs of any rule) if an efficient structure is used for storing the rules. A hash-table indexed by the rhs's or a trie are good choices for that.

Here's a small example from the domain of NLP syntactic parsing. Let's consider a toy grammar:

```
S -> NP VP . NP -> DET ADJ NOUN NP -> PRP$ NOUN ; PRP$ is a posessive pronoun VP -> VERB VP VP -> VERB NP 
```

and the following vocabulary:

```
DET -> a|an|the NOUN -> elephant|pijamas ADJ -> large|small VERB -> is|wearing PRP$ -> my 
```

No, let's parse the sentence (already tokenized): `A large elephant is wearing my pyjamas .` First, we'll need to perform part-of-speech tagging, which, in this example, is a matter of looking up the appropriate nonterminals from the vocabulary grammar. This will result in the following:

```
DET ADJ NOUN VERB VERB PRP$ NOUN . | | | | | | | | A large elephant is wearing my pyjamas . 
```

This POS tags will serve the role of terminals for our parsing grammar. Now, the shift-reduce process itself begins:

```
1. Initial queue: (DET ADJ NOUN VERB VERB PRP$ NOUN .) Initial stack: () Operation: shift 2. Queue: (ADJ NOUN VERB VERB PRP$ NOUN .) Stack: (DET) Operation: shift (as there are no rules with the rhs DET) 3. Queue: (NOUN VERB VERB PRP$ NOUN .) Stack: (ADJ DET) Operation: shift 4. Queue: (VERB VERB PRP$ NOUN .) Stack: (NOUN ADJ DET) Operation: reduce (rule NP -> DET ADJ NOUN) ; we match the rules in reverse to the stack 5. Queue: (VERB VERB PRP$ NOUN .) Stack: (NP) Operation: shift 6. Queue: (VERB PRP$ NOUN .) Stack: (VERB NP) Operation: shift 7. Queue: (PRP$ NOUN .) Stack: (VERB VERB NP) Operation: shift 8. Queue: (NOUN .) Stack: (PRP$ VERB VERB NP) Operation: shift 9. Queue: (.) Stack: (NOUN PRP$ VERB VERB NP) Operation: reduce (rule: NP -> PRP$ NOUN) 10. Queue: (.) Stack: (NP VERB VERB NP) Operation: reduce (rule: VP -> VERB NP) 11. Queue: (.) Stack: (VP VERB NP) Operation: reduce (rule: VP -> VERB VP) 12. Queue: (.) Stack: (VP NP) Operation: shift 11. Queue: () Stack: (. VP NP) Operation: reduce (rule: S -> NP VP .) 12. Reached root symbol - end. The resulting parse tree is: __________S___________ / \ \ / __VP__ \ / / \ \ / / __VP_ \ / / / \ \ ___NP_____ / / _NP_ \ / | \ / / / \ \ DET ADJ NOUN VERB VERB PRP$ NOUN . | | | | | | | | A large elephant is wearing my pyjamas . 
```

The implementation of the basic algorithm is very simple:

```
(defstruct grammar rules max-length) (defmacro grammar (&rest rules) `(make-grammar :rules (pairs->ht (mapcar (lambda (rule) (pair (nthcdr 2 rule) (first rule))) ',rules)) :max-length (let ((max 0)) (dolist (rule ',rules) (when (> #1=(length (nthcdr 2 rule)) max) (:= max #1#))) max))) ; #1= & #1# are reader-macros for anonymous variables (defun parse (grammar queue) (let ((stack (list))) (loop :while queue :do (print stack) ; diagnostic output (if-it (find-rule stack grammar) ;; reduce (dotimes (i (length (cdr it)) (push it stack)) (pop stack)) ;; shift (push (pop queue) stack)) :finally (return (find-rule stack grammar))))) (defun find-rule (stack grammar) (let (prefix) (loop :for item in stack :repeat (? grammar 'max-length) :do (push (car (mklist item)) prefix) (when-it (? grammar 'rules prefix) ;; otherwise parsing will fail with a stack ;; containing a number of partial subtrees (return (cons it (reverse (subseq stack 0 (length prefix))))))))) CL-USER> (parse (print (grammar (S -> NP VP |.|) (NP -> DET ADJ NOUN) (NP -> PRP$ NOUN) (VP -> VERB VP) (VP -> VERB NP))) '(DET ADJ NOUN VERB VERB PRP$ NOUN |.|)) #S(GRAMMAR :RULES #{ '(NP VP |.|) S '(DET ADJ NOUN) NP '(PRP$ NOUN) NP '(VERB VP) VP '(VERB NP) VP } :MAX-LENGTH 3) NIL (DET) (ADJ DET) (NOUN ADJ DET) ((NP DET ADJ NOUN)) (VERB (NP DET ADJ NOUN)) (VERB VERB (NP DET ADJ NOUN)) (PRP$ VERB VERB (NP DET ADJ NOUN)) (NOUN PRP$ VERB VERB (NP DET ADJ NOUN)) ((NP PRP$ NOUN) VERB VERB (NP DET ADJ NOUN)) ((VP VERB (NP PRP$ NOUN)) VERB (NP DET ADJ NOUN)) ((VP VERB (VP VERB (NP PRP$ NOUN))) (NP DET ADJ NOUN)) (S (NP DET ADJ NOUN) (VP VERB (VP VERB (NP PRP$ NOUN))) |.|) 
```

However, the additional level of complexity of the algorithm arises when the grammar becomes ambiguous, i.e. there may be situations when several rules apply. Shift-reduce is a greedy algorithm, so, in its basic form, it will select some rule (for instance, with the shortest rhs or just the first match), and it cannot backtrack. This may result in a parsing failure. If some form of rule weights is added, the greedy selection may produce a suboptimal parse. Anyway, there's no option of backtracking to correct a parsing error. In the NLP domain, the peculiarity of shift-reduce parsing application is that the number of rules is quite significant (it can reach thousands) and, certainly, there's ambiguity. In this setting, shift-reduce parsing is paired with machine learning technics, which perform a "soft" selection of the action to take at each step, as `reduce` is applicable almost always, so a naive greedy technique becomes pointless.

Actually, shift-reduce would better be called something like stack-queue parsing, as different parsers may not limit the implementation to just the shift and reduce operations. For example, an NLP parser that allows the construction of non-projective trees (those, where the arrows may cross, i.e. subsequent words may not always belong to a single or subsequent upper-level categories), adds a `swap` operation. A more advanced NLP parser that produces a graph structure called an AMR (abstract meaning representation) has 9 different operations.

Shift-reduce parsing is implemented in many of the parser generator tools, which generate a parser program from a set of production rules. For instance, the popular Unix tool `yacc` is a LALR parser generator that uses shift-reduce. Another popular tool ANTLR is a parser generator for LL(k) languages that uses a non-shift-reduce direct pushdown automaton-based implementation.

Besides shift-reduce and similar automata-based parsers, there are many other parsing technics used in practice. For example, CYK probabilistic parsing was popular in NLP for some time, but it's an `O(n^3)` algorithm, so it gradually fell from grace and lost to machine-learning enhanced shift-reduce variants. Another approach is packrat parsing (based on PEG — parsing expression grammars) that has a great Lisp parser-generator library [esrap](https://scymtym.github.io/esrap/). Packrat is a more powerful top-down parsing approach with backtracking and unlimited lookahead that nevertheless guarantees linear parse time. Any language defined by an LL(k) or LR(k) grammar can be recognized by a packrat parser, in addition to many languages that conventional linear-time algorithms do not support. This additional power simplifies the handling of common syntactic idioms such as the widespread but troublesome longest-match rule, enables the use of sophisticated disambiguation strategies such as syntactic and semantic predicates, provides better grammar composition properties, and allows lexical analysis to be integrated seamlessly into parsing. The last feature makes packrat very appealing to the programmers as they don't have to define separate tools for lexical analysis (tokenization and token categorization) and parsing. Moreover, the rules for tokens use the same syntax, which is also quite similar to regular expression syntax. For example, here's a portion of the esrap rules for parsing tables in Markdown documents. The Markdown table may look something like this:

```
| Left-Aligned | Center Aligned | Right Aligned | | :------------ |:---------------:| -----:| | col 3 is | some wordy text | $1600 | | col 2 is | centered | $12 | | zebra stripes | are neat | $1 | 
```

You can see that the code is quite self-explanatory: each `defrule` form consists of a rule name (lhs), its rhs, and a transformation of the rhs into a data structure. For instance, in the rule `table-row` the rhs is `(and (& #\|) (+ table-cell) #\| sp newline)`. The row should start with a `|` char followed by 1 or more `table-cell`s (a separate rule), and ended by `|` with some space charctaers and a newline. And the transformation `(:destructure (_ cells &rest __) ...` only cares about the content, i.e. the table cells.

```
(defrule sp (\* space-char) (:text t)) (defrule table-cell (and #\\| sp (\* (and (! (or (and sp #\\|) endline)) inline)) sp (& #\\|)) (:destructure (\_ \_\_ content &rest \_\_\_) (mapcar 'second content))) (defrule table-row (and (& #\\|) (+ table-cell) #\\| sp newline) (:destructure (\_ cells &rest \_\_) (mapcar (lambda (a) (cons :plain a)) cells))) (defrule table-align-cell (and sp (? #\\:) (+ #\\-) (? #\\:) sp #\\|) (:destructure (\_ left \_\_ right &rest \_\_\_) (if right (if left 'center 'right) (when left 'left)))) (defrule table-align-row (and #\\| (+ table-align-cell) sp newline) (:destructure (\_ aligns &rest \_\_) aligns)) (defrule table-head (and table-row table-align-row)) 
```

To conclude the topic of parsing, I wanted to pose a question: can it be used to match the regular expressions? And the answer, of course, is that it can, as we are operating in a more powerful paradigm that includes the regexes as a subdomain. However, the critical showstopper of applying parsing to this problem is the need to define the grammar instead of writing a compact and more or less intuitive regex...

String Search in Action: Plagiarism Detection
---------------------------------------------

Plagiarism detection is a very challenging problem that doesn't have an exact solution. The reason is that there's no exact definition of what can be considered plagiarism and what can't, the boundary is rather blurry. Obviously, if the text or its part is just copy-pasted, everything is clear. But, usually (and especially when they know that plagiarism detection is at play), people will apply their creativity to alter the text in some slight or even significant ways. However, over the years, researchers have come up with numerous algorithms of plagiarism detection, with quality good enough to be used in our educational institutions. The problem is very popular and there are even shared task challenges dedicated to improving plagiarism catchers. It's somewhat an arms race between the plagiarists and the detection systems.

One of the earliest but, still, quite effective ways of implementing plagiarism detection is the Shingle algorithm. It is also based on the idea of using hashes and some basic statistical sampling techniques. The algorithm operates in the following stages:

1.  Text normalization (this may include case normalization, reduction of the words to basic forms, error correction, cleanup of punctuation, stopwords, etc.)
2.  Selection of the shingles and calculation of their hashes.
3.  Sampling the shingles from the text at question.
4.  Comparison of the hashes of the original shingles to the sampled hashes and evaluation.

The single shingle is a continues sequence of words from the normalized text (another name for this object, in NLP, is `ngram`). The original text will give us `(1- n)` shingles, where `n` is the number of words. The hashes of the shingles are normal string hashes (like fnv-1).

The text, which is analyzed for plagiarism, is also split into shingles, but not all of them are used. Just a random sample of `m`. The Sampling theorem can give a good estimate of the number that can be trusted with a high degree of confidence. For efficient comparison, all the original hashes can be stored in a hash-set. If the number of overlapping shingles exceeds some threshold, the text can be considered plagiarised. The other take on the result of the algorithm application may be to return the plagiarism degree, which will be the percentage of the overlapping shingles. The complexity of the algorithm is `O(n + m)`.

In a sense, the Shingle algorithm may be viewed as an instance of massive string search, where the outcome we're interested in is not so much the positions of the patterns in the text (although, those may also be used to indicate the parts of the text that are plagiarism-suspicious) as the fact that they are present in it.

Take-aways
----------

Strings are peculiar objects: initially, it may seem that they are just arrays. But, beyond this simple understanding, due to the main usage patterns, a much more interesting picture can be seen. Advanced string representations and algorithms are examples of special-purpose optimization applied to general-purpose data structures. This is another reason why strings are presented at the end of the part on derived data structures: string algorithms make heavy use of the material we have covered previously, such as trees and graphs.

We have also discussed the FSMs — a powerful data-structure that can be used to reliably implement complex workflows. FSMs may be used not only for string matching but also for implementing protocol handling (for example, in the HTTP server), complex user interactions, and so on. The Erlang programming language even has a standard library behavior `gen_fsm` (replaced by the newer `gen_statem`) that is a framework for easy implementation of FSMs — as many Erlang applications are mass service systems that have state machine-like operation.

P.S. Originally, I expected this chapter to be one of the smallest in the book, but it turned out to be the longest one. Strings are not so simple as they might seem... ;)

* * *

[\[1\]](http://lisp-univ-etc.blogspot.com/2019/11/programming-algorithms-strings.html#r10-1) A proper suffix is a suffix that is at least one character shorter than the string itself. For example, in the string `abc` the proper suffices are `bc` and `c`.

[\[2\]](http://lisp-univ-etc.blogspot.com/2019/11/programming-algorithms-strings.html#r10-2) Perl is only the most conspicuous example of a large number of popular programs that use the same algorithm; the same applies to Python, or PHP, or Ruby, or many other languages.

  
  
from Hacker News https://ift.tt/35npLAz