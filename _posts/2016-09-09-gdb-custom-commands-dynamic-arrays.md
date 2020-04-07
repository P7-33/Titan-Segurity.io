---
title: 'GDB Custom Commands: Dynamic Arrays'
date: 2020-01-31T01:34:00+01:00
draft: false
---

Introduction
------------

As a C shop, we don't have easy access to fancy data structures. Most of the time this isn't a problem - when you work with small data sets, most tasks don't require anything crazy. As we say in the business: arrays are love, arrays are life.

So, we have an array module, which is mostly a set of macros using some extra data hidden behind a typed array pointer (more on that approach [here](https://github.com/nothings/stb/blob/master/stretchy_buffer.h)). For the purposes of this post, all you need to know is that we have a function `array_size()` to, uh, get the size of the array, and we can access array elements using the typical `array[index]` approach. Anyways, since we use arrays so much, it would be pretty fetch if our favorite debugger GDB could understand our arrays. Let's try the 'print' command, which can be abbreviated as 'p', on an array of integers.

```
(gdb) print values $1 = (int *) 0x607020
```

Ahh, nothing soothes the soul like a hex value. While the memory address of the array is occasionally useful, what I usually want here is the actual values stored in the array. GDB wouldn't be a very useful debugger if it didn't support that.

```
(gdb) print *values $1 = 4
```

As would be expected for those familiar with C, this will only print the first value in the array. We could also print each value individually using `values[i]`, but that's tedious if we want to see all the values.

```
(gdb) p array_size(values) $1 = 6 (gdb) p *values@6 $2 = {4, 8, 15, 16, 23, 42}
```

Much better. This is the typical way to print multiple sequential values in GDB. Given how often I need to examine data like this, it would be nice to have a simple command - something like 'pa' for 'printarray'. Forcing me to type those 20 extra characters each time should be an OSHA violation.

![Now this is an Avengers level threat](https://testfit.io/images/avengers_threat.jpg)

Boilerplate
-----------

Luckily, GDB supports extensions written in Python. The 'Hello world' version of a custom command looks like this:

```
class PrintArray(gdb.Command): def __init__(self): gdb.Command.__init__(self, "pa", gdb.COMMAND_DATA, gdb.COMPLETE_SYMBOL, True) def invoke(self, arg, from_tty): print("Hello, world") PrintArray()
```

The only noteworthy items so far are the 'pa' name we gave our command and the `print()` call. We'll save this file as print\_array.py.

Now we have to tell GDB to run our script using the `source` command. We could run this every time we launch GDB, but there is a .gdbinit file that is run automatically on launch. GDB looks for this file in 2 places: the user's home directory and the current working directory. Whichever location you choose, add the following line:

```
source print_array.py
```

You can also execute this command while GDB is running, which comes in handy when testing changes to our script. Anyways, we should be up and running.

```
(gdb) pa Hello, world
```

Pack it in, job's finished.

The Meaty Bits
--------------

Printing Hello world is so last paragraph. I'd prefer some real logic.

```
 def invoke(self, arg, from_tty): args = gdb.string_to_argv(arg) if len(args) < 1: print("Need array to print") return
```

I said, some real logic.

```
 pointer = args[0] size = int(gdb.parse_and_eval("array_size(%s)" % pointer)) gdb.execute("p %d" % size) if size == 0: print("Empty") else: gdb.execute("p *%s@%d" % (pointer, size))
```

Perfection. `parse_and_eval()` will let us send an expression back to gdb for evaluation, but, unlike `execute()`, it returns the result instead of executing like a normal GDB command. Since it returns a `gdb.Value` type, which for our purposes is less useful than a plain old integer, we cast the result.

```
(gdb) pa values $1 = 6 $2 = {4, 8, 15, 16, 23, 42}
```

Now that's more like it.

The Super Meaty Bits
--------------------

So, this is nice and all, but most of the time we're not just printing arrays of integers.

```
struct value { int so_much_data[4096]; int interesting_value; int seriously_stop_this_is_way_too_much_data[4095]; };
```

Printing arrays of structs will work, but the output can be pretty verbose. For large structs or long arrays, we may not even get anything.

```
(gdb) pa values $1 = 6 Error occurred in Python command: value requires 196608 bytes, which is more than max-value-size
```

We can tell gdb to raise the limit, but that won't solve the verbosity problem. Most of the time when this happens, I only want to know the value of 1 or 2 struct members for every item in the array. We should be able to focus on a particular field and exclude all others.

```
 if size == 0: print("Empty") elif len(args) == 1: gdb.execute("p *%s@%d" % (pointer, size)) else: member = args[1] statement = "p { " for i in range(0, size): if i > 0: statement += ", " statement += ("(%s)[%d].%s" % (pointer, i, member)) statement += " }" gdb.execute(statement)
```

Now, if we optionally provide a specific struct member to our custom command, GDB will only print that value for each element. Combining it into one statement instead of calling `execute()` on each element tells GDB to still print it as an array.

```
(gdb) pa values interesting_value $2 = 6 $3 = {4, 8, 15, 16, 23, 42}
```

To examine multiple members, I just call the command multiple times. Personally, I like the ergonomics of that better than passing multiple struct members to a single command.

Result
------

The final script, suitably tailored for your copy-and-pasting pleasure:

```
class PrintArray(gdb.Command): def __init__(self): gdb.Command.__init__(self, "pa", gdb.COMMAND_DATA, gdb.COMPLETE_SYMBOL, True) def invoke(self, arg, from_tty): args = gdb.string_to_argv(arg) if len(args) < 1: print("Need array to print") return pointer = args[0] size = int(gdb.parse_and_eval("array_size(%s)" % pointer)) gdb.execute("p %d" % size) if size == 0: print("Empty") elif len(args) == 1: gdb.execute("p *%s@%d" % (pointer, size)) else: member = args[1] statement = "p { " for i in range(0, size): if i > 0: statement += ", " statement += ("(%s)[%d].%s" % (pointer, i, member)) statement += " }" gdb.execute(statement) PrintArray()
```

Printing arrays, while useful, isn't incredibly exciting. However, it's a good introduction into a whole new world of extending GDB. So that's it for now. If we spend much more time in python today, we risk catching a serious case of memory bloat.

For further information, GDB's online [Python extension documentation](https://sourceware.org/gdb/onlinedocs/gdb/Python.html#Python) is well-written.

No semi-colons were harmed during the production of this post.

[<< Back](https://testfit.io/devblog)  

Sound interesting? We're [hiring](https://blog.testfit.io/engineerprogrammer)!

  
  
from Hacker News https://ift.tt/37GntOs