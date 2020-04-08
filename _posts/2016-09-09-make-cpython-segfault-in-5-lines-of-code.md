---
title: 'Make CPython segfault in 5 lines of code'
date: 2019-12-19T03:46:00+01:00
draft: false
---

![](https://github.githubassets.com/images/modules/gists/gist-og-image.png "Make CPython segfault in 5 lines of code. · GitHub")  

[](https://gist.github.com/coolreader18/6dbe0be2ae2192e90e1a809f1624c694#cpython-segfault-in-5-lines-of-code)CPython Segfault in 5 lines of code
================================================================================================================================================

So this is weird, right? Python segfaulting with only 5 lines of code?

Let's look at why this happens. First, we define a subclass of Exception that returns a non-exception from its `__new__` constructor. This could be anything, as long as it's not actually an instance of `BaseException`:

```
import random class E(BaseException): def \_\_new\_\_(cls, \*args, \*\*kwargs): return random.choice(\[1, (), {}, ""\]) def a(): yield # will still always segfault: a().throw(E)
```

Well, almost anything; a few things I've found that don't segfault are lists and generators- I'll come back to this later.

Then, we call the [`generator.throw()`](https://docs.python.org/3/reference/expressions.html#generator.throw) with `E` as its only argument. `gen.throw()` accepts up to 3 arguments, which mirror the [arguments you'd pass to `raise` in Python 2](https://docs.python.org/2.5/ref/raise.html):

```
raise TypeError, "Couldn't do thing", other\_exc.\_\_traceback\_\_
```

We only pass it one argument, which because it's a type object (and a subclass of `BaseException`) it calls to get an exception object to throw to the generator (again, like `raise`). Usually, of course, type objects return an instance of themselves when called, but this one we've defined doesn't. But shouldn't it still just `TypeError`? And does `raise` do the same thing?

```
class E(BaseException): def \_\_new\_\_(cls, \*args, \*\*kwargs): return cls # Python 3 still supports \`raise ExceptionType\`, just not the other arguments raise E
```

```
Traceback (most recent call last): File "segfault.py", line 8, in <module\> raise E TypeError: calling <class '\_\_main\_\_.E'\> should have returned an instance of BaseException, not <class 'type'\>
```

`raise` works fine. Hmmm. Let's try looking up that error message in the CPython codebase.

```
// ceval.c, line 4238 /\* We support the following forms of raise:  raise  raise   raise  \*/ /\* VVVVVVVVVVVVVVVVVVVVVVVVVVV is the argument a subclass of BaseException? \*/ if (PyExceptionClass\_Check(exc)) { type = exc; /\* VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV call the type object \*/ value = \_PyObject\_CallNoArg(exc); if (value == NULL) goto raise\_error; /\* VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV type check for instance of BaseException \*/ if (!PyExceptionInstance\_Check(value)) { \_PyErr\_Format(tstate, PyExc\_TypeError, /\* VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV search result for error message \*/ "calling %R should have returned an instance of " "BaseException, not %R", type, Py\_TYPE(value)); goto raise\_error; } } else if (PyExceptionInstance\_Check(exc)) { /\* most common path, raising an already constructed exception \*/ value = exc; type = PyExceptionInstance\_Class(exc); Py\_INCREF(type); } /\* ... \*/
```

It looks like this type checking is done specifically in the code for executing the `RAISE_VARARGS` bytecode instruction, and not in any deeper machinery in the CPython interpreter. So does `generator.throw()` do this?

```
// genobject.c, line 483 /\* VVVVVVVVVVVVVVVVVVVVVVVVVVV check if it's a subclass of BaseException... \*/ if (PyExceptionClass\_Check(typ)) PyErr\_NormalizeException(&typ, &val, &tb); /\* VVVVVVVVVVVVVVVVVVVVVVVVVVVVVV common path again \*/ else if (PyExceptionInstance\_Check(typ)) { /\* Raising an instance. The value should be a dummy. \*/ /\* ... \*/
```

Nope, it just passes it off to the interpreter function `PyErr_NormalizeException`. Does that validate the result of calling the exception type? Well, the [source](https://github.com/python/cpython/blob/bea33f5e1db6e4a554919a82894f44568576e979/Python/errors.c#L287) is pretty long and not that interesting, but you can read it for yourself and see that it does no checks whatsoever.

So that's why the segfault happens: CPython places a non-exception PyObject as the current exception for the thread, and when it tries to do an operation on it (like editing the traceback), it reaches past the size of the `PyTupleObject` struct that's actually stored there and segfaults.

I'm still not sure why lists and generators don't cause segfaults; it's not because they conform to the sequence protocol as strings and tuples do as well, and tuples and lists are usually very similar in functionality (besides, like, mutability). I'd assume that it's something in the interpreter code that catches that an exception value isn't actually an exception (but only for these types) and throws a proper error, but I'm not sure. If anyone does actually know, I'd love to hear about it.

Note: I came across this while trying to figure out the proper behavior for `generator.throw()` for [`RustPython`](https://github.com/RustPython/RustPython). I suppose the proper behavior in order to be truly CPython compliant is to just dereference a null pointer! 😁

```
PyBaseExceptionRef::try\_from\_object(res).unwrap\_or\_else(|\_| unsafe { \*std::ptr::null() })
```

  
  
from Hacker News https://ift.tt/2S4pejn