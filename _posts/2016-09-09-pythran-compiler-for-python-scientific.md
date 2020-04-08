---
title: 'Pythran – a compiler for Python scientific kernels – release'
date: 2019-11-07T08:22:00+01:00
draft: false
---

Pythran 0.9.4 just got [released](https://github.com/serge-sans-paille/pythran/tree/0.9.4post0), and it has an unusual number of unexpected features. Unexpected? Yes, that's the kind of features I never thought Pythran would have, but they ended up being possible, and even better, consistent with the whole picture. So let's take a deeper look!

Before that, if you're just interested in the changes etc, please read [the announce on the mailing list](https://www.freelists.org/post/pythran/Pythran-094-Hollsent).

Support for the isinstance(...) builtin
---------------------------------------

The following code is perfectly valid in Python:

```
def abssqr(x): if isinstance(x, complex): return x.real \*\* 2 + x.imag \*\* 2 else: return abs(x) \*\* 2 
```

However, it is not trivial to turn it into a statically compiled, generic function because of the guard over isinstance(...). This closely resembles a feature of C++17, [if constexpr](https://en.cppreference.com/w/cpp/language/if), something supported by Pythran (even though we're generating C++11 code in the back-end, but that's another story). So it was just a small step forward to handle the isinstance(...) builtin. Icing on the cake: it's actually the same code transformation that we already use to support is None!

Trivia: Pythran automatically detect a call to abs(x) \*\* 2 and replaces it by a call to a Pythran builtin, optimized for the actual type of x, so this example is just... well... an example!

Support the type(...) builtin
-----------------------------

Typing is difficult, so I've always been reluctant to implement type-related operators. Here is the implementation of the type(...) in pythonic:

```
template <class T\> typename type\_functor<T\>::type type(T const &) { return {}; } 
```

Where type\_functor maintains a binding between types and functors capable of building that type, as in:

```
template <class T\> struct type\_functor<types::list<T\>> { using type \= functor::list; }; 
```

That's some ugly internals of pythonic but the interesting part is that all the pieces fit together! _Gast_ do I love static polymorphism and modern C++! Say hello to beautiful polymorphic code like:

```
def poly(x, l): return type(x)(l) + x 
```

clang-cl
--------

Native extension like the ones produced by Pythran are supposed to be compiled using the Microsoft Visual Studio Compiler. That behavior is [hardcoded in distutils](https://github.com/python/cpython/blob/e42b705188271da108de42b55d9344642170aa2b/Lib/distutils/msvc9compiler.py#L384). Unfortunately, this compiler regularly fails to compile Pythran code that compiles fine with GCC and Clang.

The (relatively hacky, but so satisfying) answer I found out is to rely on clang-cl.exe, a binary shipped with the clang toolchain that mimics the cl.exe Command Line Interface. It requires some monkey patching in distutils, but it's worth the price: Pythran now seems to work nice in a MS environment. And according to [AppVeyor](https://ci.appveyor.com/project/serge-sans-paille/pythran/builds/28505845), the generated module run just fine.

Python 3.8 support
------------------

Pythran uses an internal representation that closely resembles the Python AST, but which is independent from it: it can represent both py2, py35, py36, py37 and now py38 code. That's all thank to this innocent package: [gast](https://github.com/serge-sans-paille/gast) and not to forget its happy companion [beniget](https://github.com/serge-sans-paille/beniget/) which provides use-def chains for Python.

Fun fact: gast is a relatively small package but it's by far the most popular one I created, according to [pypistats](https://pypistats.org/packages/gast).

  
  
from Hacker News https://ift.tt/36FKxga