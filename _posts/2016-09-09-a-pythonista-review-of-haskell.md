---
title: 'A Pythonista''s Review of Haskell'
date: 2020-01-31T07:04:00+01:00
draft: false
---

![](https://www.gravatar.com/avatar/56f019c1fcd83bb2c035aa59a0d73583?s=256 "A Pythonista's Review of Haskell > Ying Wang")  

(I'd like to give a big shoutout to [John Chandler Burnham](https://github.com/johnchandlerburnham), who published [a very clear and comprehensive set of notes](https://github.com/johnchandlerburnham/hpfp) that helped me immensely.)

* * *

Background
----------

I've used Python in production for about three years now. Even as it's a wonderful Swiss Army knife, Python also feels limiting in some ways. The same classes of bugs (e.g. type casting / translation errors, state management errors) kept cropping up, and Sisyphean bugs frustrate me. Python is also quite slow when you compare the operations you want to execute vs. the theoretical maximum performance of those operations on the underlying hardware. I kept wondering about what was possible if I had used a different tool.

What would happen if a data pipeline was lazy instead of eager, not because I'm using a lazy library API, but because the language is non-strict by default? What if you could use types in order to register properties of data instead of state?

Lastly, I wanted to break free of the practitioner's pragmatic culture and see what academia had to offer in the start of the art. I remember one conversation I had years ago with a professor in college who had previously worked in industry, and he said that [A\*](https://en.wikipedia.org/wiki/A*_search_algorithm) was invented twenty years before it was widely used in industry (e.g. video game development). I think having an understanding of what's possible and what the future might bring could prove useful in understanding how to get there as a practitioner.

I thought learning Haskell provided the highest likelihood of satisfying these requirements. So over the past three months, I've been reading through [“Haskell Programming, From First Principles” by Chris Allen and Julie Moronuki](https://haskellbook.com/), the 4th release candidate of the 1.0 edition (1.0-rc4). I'm pleased to say that I made it to the end of this 1,857 page (by the e-reader PDF version) montrosity. Here's some of the things that I, as a software engineer who has used Python in production and Haskell doing book exercises only, liked and didn't like about Haskell.

What I like about Haskell
-------------------------

### The type system

Haskell's type system makes Python's type system look downright primitive. The closest analogy I can think of is if you had direct access to dunder methods, like Python's `__eq__` vs. Haskell's `Data.Eq` typeclass constraint, when defining classes or methods. Then you had the ability to create `typing` type signatures on different, overlapping sets of these dunder methods somehow, and baked it all into your native toolchain as a set of compile-time guarantees. This still doesn't encapsulate the full power of the Haskell type system, like higher-kinded types and actual sum/product types. It's insanely mind-blowing. Constrained polymorphism is probably worth learning Haskell for alone.

I was reading through some of [Hillel Wayne's blog posts](https://hillelwayne.com), and [one of them](https://hillelwayne.com/post/why-dont-people-use-formal-methods/) discussed the [Curry-Howard correspondence](https://en.wikipedia.org/wiki/Curry%E2%80%93Howard_correspondence), which somehow proves a 1:1 association between aspects of a mathematical proof and aspects of a type system. You can convert a proof into a type, if your type system supports it. I think Haskell's type system respects this. I don't think Python's type system does.

### An emphasis on structure

One key aspect of Haskell the authors came back to repeatedly (and I mean _repeatedly_) is Haskell's emphasis on _structure_. If I had to explain functors, applicatives, and monads to somebody else, it wouldn't be in terms of I/O, or error handling, or burritos. It'd be _structure_.

Structure, in this case, refers to a higher-kinded or partially-applied type, like a list. You apply another type to a higher-kinded type to create a concrete type (e.g. `Integer` to `[]` to create `[Integer]` or a list of integers.) A functor instance _lifts_ a function over some structure to affect only the values within. An applicative (a monoidal functor) leverages a structure and function together while lifting the function over structure. A monad (an applicative functor) creates new structure whilst in the process of lifting a function over existing structure.

Let's take this example that might explain functors and structure to a tiny degree. Say you want to add one to a list of integers in Python. You can do this:

```
xs = [1, 2, 3, 4, 5] # xs = [2, 3, 4, 5, 6] xs_ = map(lambda x : x + 1, xs) 
```

In Haskell, this may look like:

```
xs = [1, 2, 3, 4, 5] -- xs' = [2, 3, 4, 5, 6] xs' = map (+1) xs 
```

Sure. But Haskell _also_ has `fmap`, which stands for “functor map”. On lists this is straightforward:

```
-- xs'' = [2, 3, 4, 5, 6] xs'' = fmap (+1) xs 
```

But you can also define it on other types, such as concrete `Maybe` values:

```
-- ys = (Just 2) ys = fmap (+1) (Just 1) 
```

In both cases, you're lifting the method `(+1)` over `[]` and `Just` respectively to affect the value(s) within.

You can also more explicitly lift `fmap` inside nested structure, such as a list of concrete `Maybe` values using function composition:

```
-- zs = [Just 2, Just 3, Just 4] zs = (fmap . fmap) (+1) [Just 1, Just 2, Just 3] -- zs' = [Just 2, Nothing, Just 4] zs' = (fmap . fmap) (+1) [Just 1, Nothing, Just 3] 
```

I don't think you can do anything like this with Python or any other practitioner's language that I'm familiar with. This barely begins to touch the power of Haskell structure. I definitely recommend thinking in terms of structure when learning Haskell.

As an aside, I published [a monad tutorial last year](https://bytes.yingw787.com/posts/2019/12/06/monads) before reading through the monads section, and uh, yeah. Not a good idea to speak authoritatively on a subject you know nothing about (if only because it may lead others astray). You can read [the feedback I got on that from lobste.rs here](https://lobste.rs/s/fwyvqr/monads_aren_t_as_hard_as_you_think).

### Streams and stream-oriented programming foundations

Haskell has native streams in the form of unbounded structures (such as lists), where you can apply `take` to take a number of elements for evaluation:

```
-- [1..] is a never-ending stream of increasingly large integers. -- -- `$` is an associativity forcing function, to evaluate everything to its right -- before evaluating anything to its left. -- -- `take 5` takes the first 5 values. -- -- The compiler takes the full expression, and returns: -- xs = [1, 2, 3, 4, 5] xs = take 5 $ [1..] 
```

No need for separate generator syntax. This is due to Haskell's non-strict evaluation, compiler optimizations, and the clear delination between structure and values. This could be useful for languages implementing streaming frameworks, such as [**`streaming`**](https://hackage.haskell.org/package/streaming). Streaming is important for, among other things, implementing real-time analytics, which is slowly becoming a basic requirement for various BI platforms.

Even the base error type, `bottom` or `_|_`, is defined as an evaluation that never completes successfully, either because a computation failed, or because _there's an infinite loop_. See [the Haskell wiki definition of `bottom`](https://wiki.haskell.org/Bottom). I don't think Python's [`BaseException`](https://docs.python.org/3/library/exceptions.html#BaseException) has a built-in notion of infinite loops evaluating to an error condition. This appears super powerful to me, because the big error type introduced by going over network connections are network timeouts, which appear to most programs as infinitely long computations.

### Property-based testing

Haskell has [**`Test.QuickCheck`**](https://hackage.haskell.org/package/QuickCheck), a property-based testing framework that generates values to check a declared property. Python has [**`hypothesis`**](https://hypothesis.readthedocs.io/en/latest/), but having used it a tiny bit for an open-source contribution, I don't think it's the same without the Haskell type system. The type system empowers effective property-based testing to a high degree. For example, in `Test.QuickCheck`, you can literally create a wholly abstract type, and then _cast it to different concrete types for different QuickCheck runs_. So you can check that your declared monoid is properly associative for _a set of different concrete types_, which QuickCheck will validate by running at least _100 different concrete values per concrete type signature_, while only needing to mutate the type signature. In production, libraries like [**`checkers` or `Test.QuickCheck.Checkers`**](https://hackage.haskell.org/package/checkers) abstract away testing properties of common typeclass instances like functors, applicatives, and monads to give you soft assurances they work as intended. From my current understanding, I would categorize property-based testing as something between Monte Carlo simulation and constraint solving.

I can't overstate how powerful `Test.QuickCheck` is. I can run _hundreds_ of unit tests _per dozen lines of code_, without having to set and mutate my own oracle values. By constrast, a couple thousand unit tests in a project with 10^5 LOC in Python would be considered well-tested. The vast majority of testing I did as part of the book exercises would be through `Test.QuickCheck`. [**`Hspec`**](https://hackage.haskell.org/package/hspec), the Haskell unit testing framework, hardly gets mentioned.

### GHCi

An interpreter for a compiled language? Yup. `stack ghci` was a good friend during this time period. You can pretty much do anything that compiled Haskell can do. Load GHC language extensions? Check. Set runtime conditions like `:set -Wall` to see all raised warnings? Check. Print type signatures, kind-ness signatures, and other information around methods? Check.

There's some weird edges around GHCi, mostly around the difference in runtime behavior between GHC and GHCi. Ordering matters in GHCi and not in an equivalent source file compiled using GHC. GHCi natively prints results to terminal and therefore deriving `Show` is necessary for type definitions referenced in GHCi. GHCi defaults types to `()` if they're not specified vs. GHC's compile-time error, which for me led to some interesting `QuickCheck` behavior. However, none of this really impacted my workflows very much, or took away from how impressive GHCi was.

### Hoogle

[Hoogle](https://hoogle.haskell.org/) is Haskell's API search engine where, among other things, you can search a method for by passing in _the type signature of a method you think you want_. There's [Hackage](https://hackage.haskell.org/), whose search maps more closely to that of [PyPI](https://pypi.org/), but I don't think Python has anything like Hoogle. I don't think Hoogle exists just as a flex on lesser-typed languages. I've had to search for some things there and I'd say it's been useful even to a beginner like me. I can see how using such a tool would become easier as you become more and more familiar with the Haskell standard library and the major package ecosystem.

What I dislike about Haskell
----------------------------

### Cognitive load

My appreciation of programming as an art and as a discipline increased by my learning Haskell, at the cost of my brain constantly melting out my ears and my eyeballs not comprehending what I was reading. The cognitive load was _insane_. Three months in and I still have little idea on how to write production-grade Haskell code.

This may just be that this specific book is a high-level overview of Haskell and not a practitioner's guide. Chris, one of the authors, mentioned [some differences in direction with Julie](https://bitemyapp.com/blog/wrapping-up-haskellbook/) with respect to the book's purpose. Julie's new book, [“The Joy of Haskell”](https://joyofhaskell.com/), sells itself as “extremely approachable” and “a practical problem-motivated approach”, which may be more catered towards her interests. In my experience, the longer a book is, the more times I need to review it in order to absorb all the content.

Then again, I remember how my old Python code was absolute hot garbage, and I only really got good at Python about a year into my first job and asked questions every 20 minutes for a month and read 10-15 books on the subject. If I started using Haskell at a Haskell-friendly workplace, I'm sure it'd be much the same story: first overwhelmed, then awed, then routine.

IMHO, the solution to high cognitive load, given a high enough reward, is just persistent, methodical execution towards learning. If I had to choose one feeling, I generally prefer being overwhelmed to being helpless. I find it easier to sprout enough dendrites to understand this stuff one day and add it to my toolbox rather than stomach the regret of the path not taken.

### Indentation

Haskell, like Python, practices [indentation-as-code](https://en.wikipedia.org/wiki/Off-side_rule), where indentation affects program structure and execution. I found myself unused to Haskell notation where the program seems to backtrack in on itself, such as applying `do`, `let`, and `where` notation. Here's an example with all three in Haskell, taken from the book:

```
gameWords :: IO WordList gameWords = do (WordList aw) <- allWords return $ WordList (filter gameLength aw) where gameLength w = let l = length (w :: String) in l >= minWordLength && l < maxWordLength 
```

IIRC the last few lines wouldn't compile until I indented at least that much (like, past the start of variable `gameLength`, instead of just 2 spaces in like the rest of the program). If I indented more, it would work the same. In Python, I would get a clean `IndentationError` for everything except the proper indentation, and if I indented more and remained valid, it would imply different code behavior (like a scoping change).

Ultimately, I don't think this is a big issue. Haskell has code auto-formatters like [**`haskell-formatter`**](https://hackage.haskell.org/package/haskell-formatter), much like Python's [**`black`**](https://black.readthedocs.io/en/stable/). Use it and move on. Bikeshed about something else, you know?

### Concurrency / Parallelism

Since Haskell is a lambda calculus, and everything is functional, I thought I could get parallelism trivially. Trivially, as in I expected GHCi could be run with multiple processes / threads using a config flag or file, and you could configure GHC to create a compiled binary targeting a (max?) specific number of processes / threads.

Nope. As far as I can tell, you still have to mutate your source code, and use a library, such as [**`Control.Parallel`**](https://hackage.haskell.org/package/parallel-3.2.2.0) (external dep) or [**`Control.Concurrent`**](https://hackage.haskell.org/package/base-4.12.0.0/docs/Control-Concurrent.html) (base stdlib). Simon Marlow's [“Parallel and Concurrent Programming in Haskell”](https://www.oreilly.com/library/view/parallel-and-concurrent/9781449335939/) is probably a must-read to understand this topic (and things like [**`Control.Concurrent.MVar`**](https://hackage.haskell.org/package/base-4.12.0.0/docs/Control-Concurrent-MVar.html)).

I get concerns about resource contention, and the fact that side effects may exist and compile may imply non-trivial parallelization, but it does reduce the value proposition of Haskell when comparing to something that's more “traditional”, where you have to change the source anyways to get those benefits. When I apply property-based testing to check monadic associativity and applicative composition on naive custom-defined `List` types using [**`checkers`**](https://hackage.haskell.org/package/checkers-0.4.4/docs/Test-QuickCheck-Checkers.html), the fact that it stalls one CPU core while not using the other 11 CPU cores (I have an Intel Xeon) kind of kills me inside.

I could be wrong. There might be an option in GHC or GHCi I don't know about that enables this to occur. If that's not the case though, I think if Haskell made parallelization more upfront and trivial, it would be a material selling point for practitioners.

### Strictness / Non-strictness

Haskell is fundamentally a non-strict language. However, _you still need strict-ness in order to do useful stuff_. So the way Haskell ended up appearing to me in this regards was a mish-mash of strict and non-strict portions of the codebase. You have to take a look at GHC Core, the underlying strict (transpilation?) of GHC Haskell to understand how the code actually behaves, and GHC Core is not the most readable language. For example, for `Foldable` types, a left-associative fold `foldl` is strict over spine evaluation, while right-associative folds `foldr` is non-strict over spine evaluation.

There's some conventions people follow. For example, when implementing `Foldable` types, making the spine lazy and values strict is a point constantly hammered home. So does properly raising asynchronous exceptions. However, to me this falls far short of the guarantees I thought I could get, and I honestly prefer having an explicit distinction between lazy/eager APIs after seeing the alternative.

### Package Management

`stack uninstall $PACKAGE` does not exist, and I wish the reasoning was more clear (like code samples to indicate _why_ it is unnecessary). Here's the [GitHub issue related to implementing `stack uninstall`](https://github.com/commercialhaskell/stack/issues/361), which was, as far as I can tell, closed without action. As a newbie, I do wish that there was guidance on the “proper” way to uninstall packages if `stack uninstall` is not available.

I also wish that there was a better way to version and lock environments. I would have loved to have package lockfiles available for source code work as part of the book, as parts of GHC have changed since the book was written.

### Compatibility

On the issue of compatibility.

Haskell has the ability to declare a type alias around an existing type, called `newtype`, that guarantees only the type name and not the underlying data representation changes. Ostensibly, this serves as a way to typecheck data and act as an extra constraint. What `newtype` really reminds me of though is a comment on Hacker News talking about how Lisp's type system enabled the creation of Lisp macros and tightly coupled a developer's team to its codebase. If you could define a DSL on top of Haskell and shoot yourself in the foot, `newtype` would likely the culprit. I'm not sure how library compatibility would work. Does `newtype` exist as part of native top-level APIs for Haskel libraries? How much churn do production Haskell type signatures suffer from? This is an unknown quantity to me.

In addition to concerns about “horizontal” compatibility between third-party libraries in the same environment, I also worry about “vertical” (backwards / forwards) compatibility when upgrading or downgrading environments. Haskell respects the mathematics behind type theory, and when there are new discoveries, Haskell doesn't mind making breaking changes. For example, [this Stack Overflow answer](https://stackoverflow.com/a/52238024/1497211) helped me understand why I needed to implement `Semigroup` every time I needed to implement `Monoid`, which wasn't the case in the book examples. When [`Applicative` and `Traversable` was discovered](http://www.staff.city.ac.uk/~ross/papers/Applicative.html), they were added to GHC 7.10. I believe I had to implement `Applicative` when I needed to implement `Monad` for various type definitions. Yeah. _Math changes_.

I'm interested in seeing any published upgrade paths, or how existing Haskell projects pull core dependencies from upstream. Maybe it's just a different workflow than what I'm used to, but in any case it would be helpful to understand for any production Haskell projects.

### Small Nits

Haskell has no null definition of type `Char`, at least according to [this Stack Overflow answer](https://stackoverflow.com/a/58924575). Python doesn't distinguish between `Char` and `String` types with single and double quotes, so empty char is empty string is an empty list. It seems weird to me that for all the typing wealth Haskell provides, this base case doesn't exist, though I personally don't know what it is.

* * *

`Int` and `Integer` are two different types, according to [this Stack Overflow post](https://stackoverflow.com/a/12273762/1497211). Apparently it's easier to just change the type signature rather than execute a type conversion. I'm sure they have their reasons, but I personally don't understand this.

* * *

I don't like how Haskell applies wildcard imports by default. Here's Haskell:

```
-- Wildcard import import Package -- Namespaced import import qualified Package as Package 
```

vs Python:

```
# Namespaced import import package # Wildcard import from package import * 
```

* * *

Haskell can raise errors partway through evaluating an error message. This (feature?) seems alien to me:

```
Prelude> map (+1) [1, 2, undefined] -- '[2, 3,' is still visible, and has been executed. [2,3,*** Exception: Prelude.undefined CallStack (from HasCallStack): error, called at libraries/base/GHC/Err.hs:79:14 in base:GHC.Err undefined, called at <interactive>:27:17 in interactive:Ghci14 Prelude> 
```

### Community Organization

One day, I was looking up how to use `FlexibleInstances`, which is a GHC language extension. The book referenced this URL:

```
https://ghc.haskell.org/trac/haskell-prime/wiki/FlexibleInstances 
```

As of `2020-01-14T16:38:59.758039-05:00`, this link returned `nginx: 404 Not Found`. When I searched for `FlexibleInstances` using DuckDuckGo, I got this completely new link:

```
https://prime.haskell.org/wiki/FlexibleInstances 
```

From [Christopher Allen's blog post finalizing “The Haskell Book”](https://bitemyapp.com/blog/wrapping-up-haskellbook/), it looks like the book was last updated around end of 2018. So in less than two years, the link had rotted.

I think Python's spoiled me. I can go to python.org's website, and pull up a set of offline docs for _every GA version of Python going back to Python 1.4, published October 25th, 1996_. Don't take my word for it. Here's the [Python 1.4 documentation](https://docs.python.org/release/1.4/ref/). I have no idea who even uses Python 1.4. But I'm pretty sure that for whoever needs Python 1.4 (maybe some poor legacy embedded systems engineer), this specific link _will not rot_.

To be clear, I didn't choose to learn Haskell because it's friendly to developers. One of my reasons for learning Haskell, is to see what a language is like when it doesn't compromise. However, things like link rot, or a general affinity towards terseness, or a lack of unstructured documentation (IMHO type signatures aren't a substitute for documentation) or migrating the bug tracker to a GitLab deploy for reasons (where you now have to create an account and sign in to read issues) stand out in my mind as impediments that might make learning Haskell and growing the Haskell community unnecessarily difficult.

Perhaps I'm being dramatic, but I oftentimes forget that I'm extraordinarily privileged to live in a first-world country, with the financial capacity to attend conferences at will, gain access to core devs and library maintainers over email, and spend time to learn things for fun. Not everybody has that ability, and this stark contrast between community management styles brings this privilege to my mind's forefront. I think the Haskell community could take many cues on this subject from the Python community, and I think that would lend a massive step towards in sharing Haskell's beauty with more people around the world.

Projects I'd like to do in Haskell
----------------------------------

I'm probably tabling my journey towards learning additional Haskell until I ship some other stuff, but I already have some ideas for projects I would like to implement in Haskell:

*   **A tool to model ETL workflows for integration testing**: I've found ETL workflows to be tremendously difficult to model, because verifying correctness almost entirely revolves around parsing side effects. Haskell is great at abstracting away side effects, and it's great at generative testing. Both of these attributes could apply to a new integration testing framework for something like Apache Airflow.
    
*   **An RFC-4180 compliant CSV parser**: There's plenty of CSV parsers out there. There aren't too many that openly state to be RFC-4180 compliant, given the need to satisfy business requirements. Of those that are, I haven't seen any that publish test reports that can automatically verify RFC-4180 compliance. Of course, the goal of a CSV parser is to get the CSV file into a highly structured format as quickly as possible in order to avoid parsing errors further down the pipeline, but even getting that first step done is a materially non-trivial task. I'd love to have a CSV parser that could be verified using some kind of IETF grammar generation tool, or modeled using formal reasoning. [**`liquidhaskell`**](http://hackage.haskell.org/package/liquidhaskell) and [**`cassava`**](https://hackage.haskell.org/package/cassava) would be great prior art for me to study.
    
*   **A POSIX-compatible, lazy data engineering pipelining tool**: The big data engineering tool I've used in the past is Apache Spark, but there are parts of Spark I wish were different. I believe the Spark RDD binary format underneath is framework-specific. Using it involves a REPL, instead of `stdin`/`stdout`. Finally, while the pipeline is lazy, the pipeline constructor is monolithic.
    
    I'd love to have a POSIX-compatible, composable data engineering framework with something like standard Parquet files (highly structured, a small, independent type system striped alongside data, columnar formatted, binary) acting as a persistent backing. I think POSIX and Haskell paired together would be such a great combination, and it's where Haskell's strengths like bare-metal performance and non-strictness can really shine. Imagine something like this:
    
    ```
    pipelineBuilder source.parquet --conf baseConf.json \  | transformA --conf conf1.json \  | transformB -conf conf2.json \  > out.parquet 
    ```
    

Conclusion
----------

One interesting section of Haskell code the author pointed out was this method, as part of [**`yesod-core`**](https://github.com/softmechanics/yesod-core) pinned at commit `db5e987797768e19cb6c0e6b7f8df1f836634c3b`:

```
addSubWidget :: (YesodSubRoute sub master) => sub -> GWidget sub master a -> GWidget sub' master a addSubWidget sub w = do master <- liftHandler getYesod let sr = fromSubRoute sub master i <- GWidget $ lift $ lift $ lift $ lift $ lift $ lift $ lift get w' <- liftHandler $ toMasterHandlerMaybe sr (const sub) Nothing $ flip runStateT i $ runWriterT $ runWriterT $ runWriterT $ runWriterT $ runWriterT $ runWriterT $ runWriterT $ unGWidget w let ((((((((a, body), title), scripts), stylesheets), style), jscript), h), i') = w' GWidget $ do tell body lift $ tell title lift $ lift $ tell scripts lift $ lift $ lift $ tell stylesheets lift $ lift $ lift $ lift $ tell style lift $ lift $ lift $ lift $ lift $ tell jscript lift $ lift $ lift $ lift $ lift $ lift $ tell h lift $ lift $ lift $ lift $ lift $ lift $ lift $ put i' return a 
```

The author points out that this is an abuse of monad transformers, and I'm sure you can tell this isn't the cleanest Haskell code out there. My goal here isn't to diss the maintainers or authors of this code. I'm pretty sure [**`@snoyberg`**](https://github.com/snoyberg/) is one of the most pre-eminent Haskell programmers in the world and he probably had good reason to write this method the way it is. What I do want to point out is _Haskell isn't a magical elixir_. It's still a programming language. For me, I put Haskell and those who used it on a pedestal and I thought that if I just learned Haskell, all my technical problems would go away. Learning Haskell and understanding it intimately helped me take it down from its pedestal, and I realized that the fundamental truths of software engineering still hold. How you use a tool is just as important as which tool you use. There are always tradeoffs you weigh when making decisions, especially in the face of development limitations like manpower and money. Make things work, then right, then fast, in order to ship.

Getting to a bare beginner's level in Haskell was an informative experience for me, and I hope I can continue learning and applying Haskell in my life. I think I grew immensely, both personally and professionally, from this experience, and I'm tremendously grateful to the Haskell community for the journey thus far. To more adventures! 🍷

* * *

(If you're interested, here are [my notes for “The Haskell Book”](http://github.com/yingw787/thehaskellbook).)

[Hacker News](https://news.ycombinator.com/item?id=22195072)

[Lobste.rs](https://lobste.rs/s/ovebeq/pythonista_s_review_haskell)

  
  
from Hacker News https://ift.tt/2RHeO8X