---
title: 'Debugging hidden memory leaks in Ruby'
date: 2019-10-19T08:47:00+01:00
draft: false
---

In 2015 I wrote about some of the tooling Ruby provides for [diagnosing managed memory leaks](https://samsaffron.com/archive/2015/03/31/debugging-memory-leaks-in-ruby). The article mostly focused on the easy managed leaks.

This article covers tools and tricks you can use to attack leaks that you can not easily introspect in Ruby. In particular I will discuss mwrap, heaptrack, iseq\_collector and chap.

### An unmanaged memory leak

This little program leaks memory by calling malloc directly. It starts off consuming 16MB and finishes off consuming 118MB of RSS. The code allocates 100k blocks of 1024 bytes and de-allocates 50 thousand of them.

```
 require 'fiddle' require 'objspace' def usage rss = `ps -p #{Process.pid} -o rss -h`.strip.to_i * 1024 puts "RSS: #{rss / 1024} ObjectSpace size #{ObjectSpace.memsize_of_all / 1024}" end def leak_memory pointers = [] 100_000.times do i = Fiddle.malloc(1024) pointers << i end 50_000.times do Fiddle.free(pointers.pop) end end usage # RSS: 16044 ObjectSpace size 2817 leak_memory usage # RSS: 118296 ObjectSpace size 3374 
```

Even though our RSS is 118MB, our Ruby object space is only aware of 3MB, introspection wise we have very little visibility of this very large memory leak.

A real world example of such a leak is [documented by Oleg Dashevskii](http://www.be9.io/2015/09/21/memory-leak/), it is an excellent article worth reading.

### Enter Mwrap

[Mwrap](https://80x24.org/mwrap/README.html) is a memory profiler for Ruby that keeps track of all allocations by intercepting malloc and family calls. It does so by intercepting the real calls that allocate and free memory using [LD\_PRELOAD](https://blog.jessfraz.com/post/ld_preload/). It uses [liburcu](https://liburcu.org/) for bookkeeping and is able to keep track of allocation and de-allocation counts per call-site for both C code and Ruby. It is reasonably lightweight and will approximately double the RSS for the program being profiled and approximately halve the speed.

It differs from many other libraries in that it is very lightweight and Ruby aware. It track locations in Ruby files and is not limited to C level backtrackes valgrind+masif and similar profilers show. This makes isolating actual sources of an issue much simpler.

Usage involves running an application via the mwrap wrapper, it inject the LD\_PRELOAD environment and execs the Ruby binary.

Let’s append mwrap to our above script:

```
require 'mwrap' def report_leaks results = [] Mwrap.each do |location, total, allocations, frees, age_total, max_lifespan| results << [location, ((total / allocations.to_f) * (allocations - frees)), allocations, frees] end results.sort! do |(_, growth_a), (_, growth_b)| growth_b <=> growth_a end results[0..20].each do |location, growth, allocations, frees| next if growth == 0 puts "#{location} growth: #{growth.to_i} allocs/frees (#{allocations}/#{frees})" end end GC.start Mwrap.clear leak_memory GC.start # Don't track allocations for this block Mwrap.quiet do report_leaks end 
```

Next we will launch our script with the mwrap wrapper

```
% gem install mwrap % mwrap ruby leak.rb leak.rb:12 growth: 51200000 allocs/frees (100000/50000) leak.rb:51 growth: 4008 allocs/frees (1/0) 
```

Mwrap correctly detected the leak in the above script (50,000 \* 1024). Not only it detected it, it isolated the actual line in the script ( `i = Fiddle.malloc(1024)` ) which caused the leak. It correctly accounted for the `Fiddle.free` calls.

It is important to note we are dealing with estimates here, mwrap keeps track of **total** memory allocated at the call-site and then keeps track of de-allocations. However, if you have a single call-site that is allocating memory blocks of different sizes the results can be skewed, we have access to the estimate: `((total / allocations) * (allocations - frees))`

Additionally, to make tracking down leaks easier mwrap keeps track of `age_total` which is the sum of the lifespans of every object that was freed, and `max_lifespan` which is the lifespan of the oldest object in the call-site. If `age_total / frees` is high, it means the memory growth survives many garbage collections.

Mwrap has a few helpers that can help you reduce noise. `Mwrap.clear` will clear all the internal storage. `Mwrap.quiet {}` will suppress Mwrap tracking for a block of code.

Another neat feature Mwrap has is that it keeps track of total allocated bytes and total freed bytes. If we remove the clear from our script and run:

```
usage puts "Tracked size: #{(Mwrap.total_bytes_allocated - Mwrap.total_bytes_freed) / 1024}" # RSS: 130804 ObjectSpace size 3032 # Tracked size: 91691 
```

This is very interesting cause even though our RSS is 130MB, Mwrap is only seeing 91MB, this demonstrates we have bloated our process. Running without mwrap shows that the process would normally be 118MB so in this simple case accounting is a mere 12MB, the pattern of allocation / deallocation caused fragmentation. Knowing about fragmentation can be quite powerful, in some cases with untuned glibc malloc processes can fragment so much that a very large amount memory consumed in RSS is actually free.

### Could Mwrap isolate the old redcarpet leak?

In [Oleg’s article](http://www.be9.io/2015/09/21/memory-leak/) he discussed a very thorough way he isolated a very subtle leak in redcarpet. There is lots of detail there. It is critical that you **have instrumentation**. If you are not graphing process RSS you have very little chance at attacking any memory leak.

Let’s step into a time machine and demonstrate how much easier it can be to use Mwrap for such leaks.

```
def red_carpet_leak 100_000.times do markdown = Redcarpet::Markdown.new(Redcarpet::Render::HTML, extensions = {}) markdown.render("hi") end end GC.start Mwrap.clear red_carpet_leak GC.start # Don't track allocations for this block Mwrap.quiet do report_leaks end 
```

Redcarpet version 3.3.2

```
redcarpet.rb:51 growth: 22724224 allocs/frees (500048/400028) redcarpet.rb:62 growth: 4008 allocs/frees (1/0) redcarpet.rb:52 growth: 634 allocs/frees (600007/600000) 
```

Redcarpet version 3.5.0

```
redcarpet.rb:51 growth: 4433 allocs/frees (600045/600022) redcarpet.rb:52 growth: 453 allocs/frees (600005/600000) 
```

Provided you can afford for a process to run at half speed simply re-launching it in production with Mwrap and logging Mwrap output once in a while to a file can identify a broad spectrum of memory leaks.

### A mysterious memory leak

Recently we upgraded Rails to version 6 at Discourse. Overall the experience was extremely positive, performance remained more or less the same, Rails 6 includes some very nice features we get to use (like [Zeitwerk](https://medium.com/@fxn/zeitwerk-a-new-code-loader-for-ruby-ae7895977e73)).

Rails amended the way templates are rendered which required a few backwards compatible changes.

Fast forward a few days after our upgrade and we noticed RSS for our Sidekiq job runner was climbing.

Mwrap kept on reporting a sharp incline in memory due to memory being allocated at:

[github.com](https://github.com/rails/rails/blob/94fe2430da93daf52f63dbc248dcbdc8e8de2c31/actionview/lib/action_view/template.rb#L341)

331.  `source.encode!`
332.  `# Now, validate that the source we got back from the template`
333.  `# handler is valid in the default_internal. This is for handlers`
334.  `# that handle encoding but screw up`
335.  `unless source.valid_encoding?`
336.  `raise WrongEncodingError.new(source, Encoding.default_internal)`
337.  `end`
338.  `begin`
339.  `mod.module_eval(source, identifier, 0)`
340.  `rescue SyntaxError`
341.  `# Account for when code in the template is not syntactically valid; e.g. if we're using`
342.  ``# ERB and the user writes <%= foo( %>, attempting to call a helper `foo` and interpolate``
343.  `# the result into the template, but missing an end parenthesis.`
344.  `raise SyntaxErrorInTemplate.new(self, original_source)`
345.  `end`
346.  `end`
347.  `def handle_render_error(view, e)`
348.  `if e.is_a?(Template::Error)`

`We initially found this very confusing and kept thinking to ourselves, why is Mwrap complaining? Could it be broken?`

`During the period where memory was climbing the Ruby heaps were not growing in size in a significant manner.`

``2 million slots in the heap are a meager 78MB (40 bytes per slot), strings and arrays can take up more space, but this simply did not explain the enormous memory usage we were seeing. This was confirmed when I ran `rbtrace -p SIDEKIQ_PID -e ObjectSpace.memsize_of_all`.``

Where did all the memory go?

### Heaptrack

[Heaptrack](https://github.com/KDE/heaptrack) is a memory heap profiler for Linux.

Milian Wolff does a great job explaining what it is and how it came to be [on his blog](https://milianw.de/blog/heaptrack-a-heap-memory-profiler-for-linux.html). He also has several talks about it ([1](https://www.youtube.com/watch?v=myDWLPBiHn0), [2](https://www.youtube.com/watch?v=YB0QoWI-g8E), [3](https://www.youtube.com/watch?v=-8cOWt7lvUQ))

In essence it is an incredibly efficient native heap profiler that gathers backtraces from a profiled applications using [libunwind](https://www.nongnu.org/libunwind/).

It is significantly faster than [Valgrind/Massif](http://valgrind.org/docs/manual/ms-manual.html) and has a feature that makes is much more suitable for **temporary** production profiling.

It can attach to an already running process!

As with most heap profilers, when every single malloc family function is called it needs to do some accounting. This accounting certainly slows down the process a bit.

The design, in my mind, is the best possible design for this type of program. It intercepts using an LD\_PRELOAD trick or a [GDB trick](https://milianw.de/blog/heaptrack-attaching-to-running-process) to load up the profiler. It ships the data out of the profiled process as quickly as possibly using a [FIFO special file](https://linux.die.net/man/3/mkfifo). The wrapper [`heaptrack`](https://github.com/KDE/heaptrack/blob/983cc35dd000a8219e0d5713ab0a0d298af59c97/src/track/heaptrack.sh.cmake) is a simple shell script, something that makes troubleshooting simple. A second process runs to read from the FIFO and compress the tracking data on the fly. Since heaptrack operates in “chunks” you can start looking at the profiled information seconds after you start profiling, mid way through a profiling session. Simply copy the profile file to another location and run the heaptrack gui.

This [ticket at GitLab](https://gitlab.com/gitlab-org/gitlab-foss/issues/49702) alerted me to the possibility of running heaptrack. Since they were able to run it, I knew it was a possibility for me.

We run our application in a container, I needed to relaunch our container with `--cap-add=SYS_PTRACE` which allows GDB to use [ptrace](https://en.wikipedia.org/wiki/Ptrace) which we needed so heaptrack can inject itself. Additionally, I needed a [small hack](https://github.com/KDE/heaptrack/pull/22) on the shell file to allow `root` to profile a non `root` process (we run our Discourse application under a restricted account in the container).

Once this was done it was as simple as running `heaptrack -p PID` and waiting for results to stream in.

The UX of heaptrack is fantastic and extremely rich, it was very easy to follow what was happening with my memory leak.

At a top level I could see two jumps, one was due to `cppjieba` and the other was originating from Ruby `objspace_xmalloc0`

I knew about [cppjieba](https://github.com/fantasticfears/cppjieba_rb), segmenting Chinese is expensive, large dictionaries are needed, it was not leaking.

But why was ruby allocating memory and further more, not telling me about it?

The largest increase was coming from `iseq_set_sequence` in `compile.c`. So it follows that we were leaking instruction sequences.

This made the leak Mwrap detected make sense. `mod.module_eval(source, identifier, 0)` was causing a leak cause it was creating instruction sequences that were never being removed.

In retrospect if I carefully analyzed a heap dump from Ruby I should have seen all these IMEMOs, cause they are included in heap dumps, just invisible from in-process introspection.

From here on debugging was pretty simple, I tracked down all calls to the module eval and dumped out what it was evaluating. I discovered we kept on appending methods over and over to a big class.

Simplified, this is the bug we were seeing:

```
require 'securerandom' module BigModule; end def leak_methods 10_000.times do method = "def _#{SecureRandom.hex}; #{"sleep;" * 100}; end" BigModule.module_eval(method) end end usage # RSS: 16164 ObjectSpace size 2869 leak_methods usage # RSS: 123096 ObjectSpace size 5583 
```

Ruby has a class to contain instruction sequences called: `RubyVM::InstructionSequence`. However, Ruby is lazy about creating these wrapping objects, cause it is inefficient to have them around unless needed.

Interestingly [Koichi Sasada](http://www.atdot.net/~ko1/) created the [iseq\_collector](https://github.com/ko1/iseq_collector) gem. If we add this snippet we can now find our hidden memory:

```
require 'iseq_collector' puts "#{ObjectSpace.memsize_of_all_iseq / 1024}" # 98747 
```

`ObjectSpace.memsize_of_all_iseq` will materialize every instruction sequence, which can introduce slight process memory growth and slightly more GC work.

If we, for example, count the number of ISEQs before and after running the collector we will notice that after running `ObjectSpace.memsize_of_all_iseq` our `RubyVM::InstructionSequence` class count grows from 0 to 11128 in the example above:

```
def count_iseqs ObjectSpace.each_object(RubyVM::InstructionSequence).count end 
```

These wrappers will stay around for the life of a method and need to be visited when a full GC runs.

For those curious, our fix to our issue was reusing the class responsible for rendering email templates. ([fix 1](https://review.discourse.org/t/perf-reuse-renderer-when-rendering-email-templates/6010), [fix 2](https://review.discourse.org/t/fix-during-concurrent-emails-generation-renderer-should-not-be-reused/6097))

### chap

During my debugging I came across a very interesting tool.

Tim Boddy, extracted an internal tool used at VMWare for analysis of memory leaks and open sourced it a few years ago. The only video I can find about it [is here](https://www.youtube.com/watch?v=EZ2n3kGtVDk). Unlike most tools out there this tool has zero impact on a running process. It can simply run against core dump files, as long as the allocator being used is glibc (no support for jemalloc/tcmalloc etc)

The initial leak I had can be very easily detected using chap. Not many distros include a binary for chap, but you can easily [build it from source](https://github.com/vmware/chap). It is very actively maintained.

```
# 444098 is the `Process.pid` of the leaking process I had sudo gcore -p 444098 chap core.444098 chap> summarize leaked Unsigned allocations have 49974 instances taking 0x312f1b0(51,573,168) bytes. Unsigned allocations of size 0x408 have 49974 instances taking 0x312f1b0(51,573,168) bytes. 49974 allocations use 0x312f1b0 (51,573,168) bytes. chap> list leaked ... Used allocation at 562ca267cdb0 of size 408 Used allocation at 562ca267d1c0 of size 408 Used allocation at 562ca267d5d0 of size 408 ... chap> summarize anchored .... Signature 7fbe5caa0500 has 1 instances taking 0xc8(200) bytes. 23916 allocations use 0x2ad7500 (44,922,112) bytes. 
```

Chap can use signatures to find where various memory is allocated and can complement GDB. When it comes to debugging Ruby it can do a great job helping you finding out what the actual memory is in use for a process. `summarize used` gives the actual memory, sometimes glibc malloc can fragment so much that the `used` number is enormously different to the actual RSS. See: [Feature #14759: \[PATCH\] set M\_ARENA\_MAX for glibc malloc - Ruby master - Ruby Issue Tracking System](https://bugs.ruby-lang.org/issues/14759) for more discussion. Chap can correctly account for all memory usage and provide deep analysis around memory allocation behaviors.

Additionally chap can be integrated into build pipelines to automatically detect leaks and flag builds that are leaking.

### Future work

This round of debugging did prompt me to raise a few issues with our supporting tool-sets:

### Summary

Our existing tooling for debugging very complex memory leaks in 2019 is vastly superior to what we had 4 years ago! Mwrap, heaptrack and chap provide us with very powerful tools for attacking memory related issues both in development and production.

If you are hunting a simple memory leak in Ruby, I recommend [my earlier article](https://samsaffron.com/archive/2015/03/31/debugging-memory-leaks-in-ruby) from 2015, most of it still holds.

I hope that next time you are stuck debugging a complex native memory leak you have an easier time!

If you have any interesting battle stories or tools I have forgotten to mention you would like to share, please post a comment!

  
  
from Hacker News https://ift.tt/33Amc9h