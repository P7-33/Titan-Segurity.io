---
title: 'Yukihiro Matsumoto: “Ruby is designed for humans, not machines”'
date: 2020-01-19T11:32:00+01:00
draft: false
---

![](https://evrone.com/sites/default/files/n-fields/cases/71531306_2656002431177544_8447687255136403456_o.jpg "Yukihiro Matsumoto interview for Evrone company (in English)")  

Introduction 
-------------

We’re thrilled that our good friend Yukihiro Matsumoto, creator of the Ruby programming language, has been able to join us at RubyRussia 2019 as a speaker for the second time, having previously spoken three years ago at RubyRussia 2016.

In the time that we’ve been holding the conference — now more than ten years — Ruby has undergone a great deal of evolution, and Evrone has grown and developed alongside it.

Grigory Petrov, Developer Relations at Evrone, sat down with Mr Matsumoto to hear from him first-hand about being a star, the philosophy behind Ruby’s design and evolution, and a little about Japanese life and culture.

### The Interview

**Grigory:** This is your second visit to Russia, the first being in 2016, and since then, the number of people attending RubyRussia has doubled. Thank you so much for your talk, I really enjoyed it, and I now know the answers to a few of the questions I was going to ask you!

I saw that people weren’t just asking you questions, but also asking for pictures with you too, and even asking for autographs — you’re a star! We developers certainly like the language, and what you’re doing for the community, but are people like this all over the world, or is this something specific to Russia?

**Yukihiro:** People ask to take photos everywhere: in every country and at every conference, people want to take pictures with me. But I think this is the first time anybody has asked me for an autograph!

**Grigory:** As the creator of a programming language, you presumably get lots of questions, suggestions, ideas, and so on. What’s the one thing you’re asked most often?

**Yukihiro:** The most popular question is: "I’m from the language X community; can’t you introduce a feature from the language X to Ruby?", or something like that. And my usual answer to these requests is… "no, I wouldn’t do that", because we have different language design and different language development policies.

We can’t just take some feature from language X and dump it into Ruby, although in some cases, we do of course borrow ideas from other languages such Python, JavaScript and Elixir. This question gets asked again and again, but getting a positive response to it is very rare.

**Grigory:** It’s great that you’re able to say no; I find that technologies that are “designed by the community” don’t often necessarily end up with the best results. There are so many different languages and technologies, so we can really look at the best practices and implement only the things that are a good fit.

We’ve recently seen a wave of adding gradual typing to dynamically-typed languages such as JavaScript, Python and PHP. What are your thoughts on type annotations and gradual typing? Why are they so popular? And what are your general ideas and plans for type checking in Ruby 3 and beyond?

**Yukihiro:** For example, Rust and Go are statically-typed languages. If the software built using them is growing pretty fast, you can end up maintaining huge codebases, potentially millions of lines of code, with hundreds of team members working on each, and in those cases, type checking is a very convenient way of detecting mismatches.

In contrast, with dynamically-typed languages, we have to write tests in order to avoid type mismatches in our code. As software grows, the volume of tests (and burden of writing them) grows with it, and that’s really helped to drive the recent popularity of static and gradual typing.

At the same time, however, static type declaration is redundant, and with a language like Ruby, we want the benefit of static type checking without the redundancy of manual type declarations.

As a Ruby community and as the Ruby language, we try to satisfy both needs at the simultaneously: we’re going to have the type information file separate from the Ruby program — the Ruby program itself doesn’t contain any static type information. Instead, a separate type information file, we call it "Ruby signature file", contains the type information about the library, Gems and your programs.

We’re going to provide a tool, called the "type profiler", which can collect the type information about your software. After collecting the type information for the library and your software, the type profiler has all the information it needs about all of the classes and methods, so it can then detect type contradictions — type conflicts. You can even refine the type information in your signature file by hand to afford better type checking.

In future Ruby, you’ll be able to check the types statically, to some extent — but to a very limited degree. You’ll have the traditional Ruby behaviour, which does type checking at runtime. With a "level one type checker" it's possible to find between 40-80% of type errors by using the type information available in the source code. A "level two type checker" can generate additional type information based on analysis of the code itself. With these tools, future versions of Ruby can provide static type checks without needing explicit type annotations in your code.

**Grigory:** During the talk at the conference, you’ve mentioned this, and it’s quite the idea. I’m a C/C++ developer, and so static typing is natural for me, and I always viewed types as a way of declaring my intentions, so as to help the language and tools find possible errors in the future.

Your idea is to create a system, where you write code itself, but it’s possible from that code to infer enough information to be able to spot errors without resorting explicit types, and I like the sound of that a great deal.

It’s great that you conduct experiments, test ideas. What future do you see for Ruby? What way do you steer the language? 

**Yukihiro:** Actually, I don’t steer the language or the community. I just provide technology and the community decides which way to go. At least, we have enough technology for as many domains as possible to make Ruby flexible and productive. For example, Ruby is mostly used to build web apps right now, but I’d like to see Ruby used in research, or AI and machine learning. We’re trying to make the technology usable in new domains.

**Grigory:** We developers like to label and categorise things. Like, this is a sports car versus this is a family car. We label programming languages too: JavaScript is a "web language", C is a "system low-level language", C# is "for Windows UI native applications". How do you tend to categorise Ruby?

**Yukihiro:** I would categorise Ruby as a productive programming language. Productivity is one of the biggest, primary goals of Ruby. I designed Ruby for humans, not for machines. Sometimes core contributors complain about the design of the language because it is difficult to implement it efficiently. Ruby’s design isn’t focused on performance first, but on productivity first. That means the implementers have a bigger challenge, but we’re excited about that challenge: we aim to make Ruby as productive for developers as possible, and, at the same time, as performant as possible.

**Grigory:** With Python, we don't have multiline anonymous callables due to implementation issues. It’s good to hear that for Ruby, you and core developers are trying hard to make developers’ life easier, despite the technological challenges of the implementation.

If we talk about challenges… Imagine that you have an opportunity to travel back in time and give only one piece of advice to your younger self, at around the time you’ve started Ruby language development. What advice would you give yourself? 

**Yukihiro:** Don’t take too much from other scripting languages. Your programming language will be the best general-purpose programming language. Features introduced just to make Ruby more comparable with scripting languages will be kind of an appendix in the future — mostly useless, until they go wrong — so it’s best not to focus too much on them.

**Grigory:** In the past, there was a huge difference between "scripting" and "compiled" programming languages. Nowadays, the world has changed: between virtual machines, bytecode, and JIT compilers, the line between them is quite blurred.

During this evolution, you’ve implemented lots of changes and conducted lots of experiments with Ruby. Some were successful, some were not. What do you see as your greatest Ruby design success? What do you like the most? 

**Yukihiro:** If I had to pick one thing, I would say blocks. A Ruby block is a quite unique, quite useful abstraction of a high-order function. It’s much simpler than in other languages. It’s restricted, but it’s convenient.

**Grigory:** It’s a coincidence, but blocks are the things I like the most about Ruby. In my own talks and interviews, I say Ruby is about DSL, syntax sugar and blocks. Blocks are great.

**Yukihiro:** In the languages like Swift, if the last argument is a function you can put braces around it for something like a Ruby block. There’s a proposal for a similar feature to be added to JavaScript. I’m very proud of that.

**Grigory:** Yes, JavaScript can emulate blocks by passing a fat-arrow-function as the last argument, because (since ES6) it has that fat-arrow syntax for multi-line functions. Blocks are great. Meanwhile, are there things in Ruby’s design or evolution that you dislike? What would you call the biggest design failure that should be fixed, or is already fixed?

**Yukihiro:** I have some. Global variables: they were useful for a "scripting language", but now they are more like an appendix. I also regret adding threads to the language, we should have had a better concurrency abstraction. My other design mistake is some objects that are needlessly mutable. For example, there is a possibility to change a time zone for the existing time object, instead of creating a new one. I regret that.

**Grigory:** Yes, mutability is a tricky thing and can easily lead to errors in our source code.

Moving on from the technicalities of Ruby, how do you organize your work on the language? How does your working day look like?

**Yukihiro:** I’m a full-time Ruby developer. I spend half of my time thinking about the design of the future Ruby 3. The rest of the time I am working on another Ruby implementation, MRuby, along with some other projects.

For Ruby, the canonical Ruby implementation is done by the core contributors, and so I only need to make decisions such as "this method should behave like this", "this language feature should be like that", "the syntax like this", "the semantics are these”, and so on. I just make decisions and the other developers implement them. So, I’m half designer and half programmer. I spend about a third of my time on MRuby.

**Grigory:** I’ve checked your GitHub profile and saw lots of commits including during your flight to Russia day. Recently there were a lot of talks about developers "burning out". Do you have any free time? Any hobbies? What do you do for your well-being, in order to not burn out?

**Yukihiro:** Luckily, I spend all the time on open-source software. I have no pressure from the clients. I have no bosses. I manage myself. That’s the reason I’m so relaxed at work. I have no specific deadlines besides the release date. This freedom makes me feel relaxed. That’s the one secret. The other one is that I try to spend time not related to computers and programming at all. For example, I spend time walking with my dog, petting my cat. I do some service for my local church. I spend time with my family. That time spent on my social life helps a lot.

**Grigory:** Many Ruby developers from Russia like Japan as a country and enjoy Japanese culture. They watch anime, read Manga, and some of them visit Japan. As a native of Japan and a software developer, what places and experiences can you recommend to fellow developers who visit Japan?

**Yukihiro:** Japan is a very diverse country. You can visit metropolitan areas like Tokyo, where it’s kind of futuristic. We have a lot of pop culture, like Manga and anime there. At the same time, we have mountains, forests and historical places, like old shrines and temples. We have beautiful cherry blossoms and the leaves. It depends on your taste and preferences, you can enjoy many things: food, nature, technology. I recommend that you enjoy the diversity of the country!

**Grigory:** Is it something in Japanese culture and history that influences Ruby? 

**Yukihiro:** I am not sure. In Japanese, we have sentence chaining, which is similar to method chaining in Ruby, so perhaps this was influenced by the Japanese language. Japan is a wealthy country, some of us didn’t have to work so hard to sustain our lives. That allows me to work on the open-source software, which does not make money at all. We don’t sell open-source software. We can sustain our life through day jobs or from our sponsors, which can help us, including contributors, work on Ruby and to make better technology. That’s what I can think of.

**Grigory:** And the last, tricky question. People often want to know what it’s like to see the world through the eyes of another person — to know what they think, and what they feel. Are there any aspects to being the language author that aren’t really obvious from outside?

**Yukihiro:** The one thing is… Despite what others feel, creating the language is not really a difficult task. Computer science major students take classes for language implementation, and almost everybody that graduates can write their own programming language. Technically, it’s not that difficult.

At the same time, people don’t understand the nature of designing a language. Language is kind of a scaffolding of the mind, a way of structuring your thinking. It’s same to human languages, like Russian, Japanese and English.

Programming languages such as Ruby, Python, JavaScript, and so on, help to develop the mind, to allow you to turn ideas into something tangible and useful. That’s the primary purpose of a programming language.

I think a programming language should have a philosophy of helping our thinking, and so Ruby’s focus is on productivity and the joy of programming. Other programming languages, for example, focus instead on simplicity, performance, or something like that. Each programming language has a different philosophy and design. If you feel comfortable with Ruby’s philosophy, that means Ruby is your language.

**Grigory:** Thank you! That was Grigory Petrov and Yukihiro Matsumoto at RubyRussia 2019! Arigato!

**Yukihiro:** Arigato!

Video interview with Yukihiro Matsumoto:

VIDEO

From the interview with Yukihiro we’ve learned about the philosophy of Ruby, the future plans of the core team for the development of the language. We are glad to be good friends with Yukihiro who inspires us to use Ruby in a wide range of software development projects. If you have cool ideas and love Ruby as much as we do — let's create a new product together!

  
  
from Hacker News https://ift.tt/30yhGaS