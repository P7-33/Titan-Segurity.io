---
title: 'Counting Inversions via Rank Queries'
date: 2020-01-04T03:06:00+01:00
draft: false
---

In a [post from about a year ago](https://byorgey.wordpress.com/2018/10/06/counting-inversions-with-monoidal-sparks/), I explained an algorithm for counting the number of _inversions_ of a sequence in ![O(n \lg n)](https://s0.wp.com/latex.php?latex=O%28n+%5Clg+n%29&bg=ffffff&fg=333333&s=0 "O(n \lg n)") time. As a reminder, given a sequence ![a_1, a_2, \dots, a_n](https://s0.wp.com/latex.php?latex=a_1%2C+a_2%2C+%5Cdots%2C+a_n&bg=ffffff&fg=333333&s=0 "a_1, a_2, \dots, a_n"), an _inversion_ is a pair of positions ![i, j](https://s0.wp.com/latex.php?latex=i%2C+j&bg=ffffff&fg=333333&s=0 "i, j") such that ![a_i](https://s0.wp.com/latex.php?latex=a_i&bg=ffffff&fg=333333&s=0 "a_i") and ![a_j](https://s0.wp.com/latex.php?latex=a_j&bg=ffffff&fg=333333&s=0 "a_j") are in the “wrong order”, that is, ![i < j](https://s0.wp.com/latex.php?latex=i+%3C+j&bg=ffffff&fg=333333&s=0 "i < j") but ![a_i > a_j](https://s0.wp.com/latex.php?latex=a_i+%3E+a_j&bg=ffffff&fg=333333&s=0 "a_i > a_j"). There can be up to ![n(n-1)/2](https://s0.wp.com/latex.php?latex=n%28n-1%29%2F2&bg=ffffff&fg=333333&s=0 "n(n-1)/2") inversions in the worst case, so we cannot hope to count them in faster than quadratic time by simply incrementing a counter. In my previous post, I explained one way to count inversions in ![O(n \lg n)](https://s0.wp.com/latex.php?latex=O%28n+%5Clg+n%29&bg=ffffff&fg=333333&s=0 "O(n \lg n)") time, using a variant of merge sort.

I recently learned of an entirely different algorithm for achieving the same result. (In fact, I learned of it when I gave this problem on an exam and a student came up with an unexpected solution!) This solution does not use a divide-and-conquer approach at all, but hinges on a clever data structure.

Suppose we have a bag of values (_i.e._ a collection where duplicates are allowed) on which we can perform the following two operations:

1.  Insert a new value into the bag.
2.  Count how many values in the bag are _strictly greater than_ a given value.

We’ll call the second operation a _rank query_ because it really amounts to finding the _rank_ or _index_ of a given value in the bag—how many values are greater than it (and thus how many are less than or equal to it)?

If we can do these two operations in logarithmic time (_i.e._ logarithmic in the number of values in the bag), then we can count inversions in ![O(n \lg n)](https://s0.wp.com/latex.php?latex=O%28n+%5Clg+n%29&bg=ffffff&fg=333333&s=0 "O(n \lg n)") time. Can you see how before reading on? You might also like to think about how we could actually implement a data structure that supports these operations.

Counting inversions with bags and rank queries
----------------------------------------------

So, let’s see how to use a bag with logarithmic insertion and rank queries to count inversions. Start with an empty bag. For each element in the sequence, see how many things in the bag are strictly greater than it, and add this count to a running total; then insert the element into the bag, and repeat with the next element. That is, for each element we compute the number of inversions of which it is the right end, by counting how many elements that came before it (and are hence in the bag already) are strictly greater than it. It’s easy to see that this will count every inversion exactly once. It’s also easy to see that it will take ![O(n \lg n)](https://s0.wp.com/latex.php?latex=O%28n+%5Clg+n%29&bg=ffffff&fg=333333&s=0 "O(n \lg n)") time: for each of the ![n](https://s0.wp.com/latex.php?latex=n&bg=ffffff&fg=333333&s=0 "n") elements, we do two ![O(\lg n)](https://s0.wp.com/latex.php?latex=O%28%5Clg+n%29&bg=ffffff&fg=333333&s=0 "O(\lg n)") operations (one rank query and one insertion).

In fact, we can do a lot more with this data structure than just count inversions; it sometimes comes in handy for competitive programming problems. More in a future post, perhaps!

So how do we implement this magical data structure? First of all, we can use a balanced binary search tree to store the values in the bag; clearly this will allow us to insert in logarithmic time. However, a plain binary search tree wouldn’t allow us to quickly count the number of values strictly greater than a given query value. The trick is to augment the tree so that each node also caches the size of the subtree rooted at that node, being careful to maintain these counts while inserting and balancing.

Augmented red-black trees in Haskell
------------------------------------

Let’s see some code! In Haskell, probably the easiest type of balanced BST to implement is a red-black tree. (If I were implementing this in an imperative language I might use [splay trees](https://en.wikipedia.org/wiki/Splay_tree) instead, but they are super annoying to implement in Haskell. (At least as far as I know. I will definitely take you out for a social beverage of your choice if you can show me an elegant Haskell implementation of splay trees! [This](https://gist.github.com/m2ym/4232390) is cool but somehow feels too complex.)) However, this isn’t going to be some [fancy, type-indexed, correct-by-construction implementation](https://github.com/sweirich/dth/tree/master/depending-on-types) of red-black trees, although that is certainly fun. I am actually going to implement _left-leaning_ red-black trees, mostly following [Sedgewick](https://www.cs.princeton.edu/~rs/talks/LLRB/RedBlack.pdf); see those slides for more explanation and proof. This is one of the simplest ways I know to implement red-black trees (though it’s not necessarily the most efficient).

First, a red-black tree is either empty, or a node with a color (which we imagine as the color of the incoming edge), a cached size, a value, and two subtrees.

```
> {-# LANGUAGE PatternSynonyms #-} > > data Color = R | B > deriving Show > > otherColor :: Color -> Color > otherColor R = B > otherColor B = R > > data RBTree a > = Empty > | Node Color Int (RBTree a) a (RBTree a) > deriving Show 
```

To make some of the tree manipulation code easier to read, we make some convenient patterns for matching on the structure of a tree when we don’t care about the values or cached sizes: `ANY` matches any tree and its subtrees, while `RED` and `BLACK` only match on nodes of the appropriate color. We also make a function to extract the cached `size` of a subtree.

```
> pattern ANY l r <- Node _ _ l _ r > pattern RED l r <- Node R _ l _ r > pattern BLACK l r <- Node B _ l _ r > > size :: RBTree a -> Int > size Empty = 0 > size (Node _ n _ _ _) = n 
```

The next thing to implement is the workhorse of most balanced binary tree implementations: rotations. The fiddliest bit here is managing the cached sizes appropriately. When rotating, the size of the root node remains unchanged, but the new child node, as compared to the original, has lost one subtree and gained another. Note also that we will only ever rotate around red edges, so we pattern-match on the color as a sanity check, although this is not strictly necessary. The `error` cases below should never happen.

```
> rotateL :: RBTree a -> RBTree a > rotateL (Node c n t1 x (Node R m t2 y t3)) > = Node c n (Node R (m + size t1 - size t3) t1 x t2) y t3 > rotateL _ = error "rotateL on non-rotatable tree!" > > rotateR :: RBTree a -> RBTree a > rotateR (Node c n (Node R m t1 x t2) y t3) > = Node c n t1 x (Node R (m - size t1 + size t3) t2 y t3) > rotateR _ = error "rotateR on non-rotatable tree!" 
```

To `recolor` a node, we just flip its color. We can then `split` a tree with two red subtrees by recoloring all three nodes. (The “split” terminology comes from the isomorphism between red-black trees and 2-3-4 trees; red edges can be thought of as “gluing” nodes together into a larger node, and this recoloring operation corresponds to splitting a 4-node into three 2-nodes.)

```
> recolor :: RBTree a -> RBTree a > recolor Empty = Empty > recolor (Node c n l x r) = Node (otherColor c) n l x r > > split :: RBTree a -> RBTree a > split (Node c n l@(RED _ _) x r@(RED _ _)) > = (Node (otherColor c) n (recolor l) x (recolor r)) > split _ = error "split on non-splittable tree!" 
```

Finally, we implement a function to “fix up” the invariants by doing rotations as necessary: if we have two red subtrees we don’t touch them; if we have only one _right_ red subtree we rotate it to the left (this is where the name “left-leaning” comes from), and if we have a left red child which itself has a left red child, we rotate right. (This function probably seems quite mysterious on its own; see [Sedgewick](https://www.cs.princeton.edu/~rs/talks/LLRB/RedBlack.pdf) for some nice pictures which explain it very well!)

```
> fixup :: RBTree a -> RBTree a > fixup t@(ANY (RED _ _) (RED _ _)) = t > fixup t@(ANY _ (RED _ _)) = rotateL t > fixup t@(ANY (RED (RED _ _) _) _) = rotateR t > fixup t = t 
```

We can finally implement insertion. First, to insert into an empty tree, we create a red node with size 1.

```
> insert :: Ord a => a -> RBTree a -> RBTree a > insert a Empty = Node R 1 Empty a Empty 
```

If we encounter a node with two red children, we perform a split before continuing. This may violate the red-black invariants above us, but we will fix it up later on our way back up the tree.

```
> insert a t@(ANY (RED _ _) (RED _ _)) = insert a (split t) 
```

Otherwise, we compare the element to be inserted with the root, insert on the left or right as appropriate, increment the cached size, and `fixup` the result. Notice that we don’t stop recursing upon encountering a value that is equal to the value to be inserted, because our goal is to implement a _bag_ rather than a _set_. Here I have chosen to put values equal to the root in the left subtree, but it really doesn’t matter.

```
> insert a (Node c n l x r) > | a <= x = fixup (Node c (n+1) (insert a l) x r) > | otherwise = fixup (Node c (n+1) l x (insert a r)) 
```

Implementing rank queries
-------------------------

Now, thanks to the cached sizes, we can count the values greater than a query value.

```
> numGT :: Ord a => RBTree a -> a -> Int 
```

The empty tree contains 0 values strictly greater than anything.

```
> numGT Empty _ = 0 
```

For a non-empty tree, we distinguish two cases:

```
> numGT (Node _ n l x r) q 
```

If the query value `q` is less than the root, then we know that the root along with _everything_ in the right subtree is strictly greater than `q`, so we can just add `1 + size r` without recursing into the right subtree. We also recurse into the left subtree to count any values greater than `q` it contains.

```
> | q < x = numGT l q + 1 + size r 
```

Otherwise, if `q` is greater than or equal to the root, any values strictly greater than `q` must be in the right subtree, so we recurse to count them.

```
> | otherwise = numGT r q 
```

By inspection we can see that `numGT` calls itself at most once, moving one level down the tree with each recursive call, so it makes a logarithmic number of calls, with only a constant amount of work at each call—thanks to the fact that `size` takes only constant time to look up a cached value.

Counting inversions
-------------------

Finally, we can put together the pieces to count inversions. The code is quite simple: recurse through the list with an accumulating red-black tree, doing a rank query on each value, and sum the results.

```
> inversions :: Ord a => [a] -> Int > inversions = go Empty > where > go _ [] = 0 > go t (a:as) = numGT t a + go (insert a t) as 
```

Let’s try it out!

```
λ> inversions [3,5,1,4,2] 6 λ> inversions [2,2,2,2,2,1] 5 λ> :set +s λ> inversions [3000, 2999 .. 1] 4498500 (0.19 secs, 96,898,384 bytes)
```

It seems to work, and is reasonably fast!

Exercises
---------

1.  Further augment each node with a counter representing the number of copies of the given value which are contained in the bag, and maintain the invariant that each distinct value occurs in only a single node.
    
2.  Rewrite `inversions` without a recursive helper function, using a scan, a zip, and a fold.
    
3.  It should be possible to implement bags with rank queries using [fingertrees](http://hackage.haskell.org/package/fingertree-0.1.4.2/docs/Data-FingerTree.html) instead of building our own custom balanced tree type (though it seems kind of overkill).
    
4.  My intuition tells me that it is not possible to count inversions faster than ![n \lg n](https://s0.wp.com/latex.php?latex=n+%5Clg+n&bg=ffffff&fg=333333&s=0 "n \lg n"). Prove it.
    

  
  
from Hacker News https://ift.tt/34yYBFY