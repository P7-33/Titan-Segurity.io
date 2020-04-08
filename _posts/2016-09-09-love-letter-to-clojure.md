---
title: 'Love Letter to Clojure'
date: 2019-10-12T03:53:00+01:00
draft: false
---

In this blog post, I will explain how learning the Clojure programming language three years ago changed my life. It led to a series of revelations about all the invisible structures that are required to enable developers to be productive. These concepts show up all over in [_The Unicorn Project_](https://itrevolution.com/the-unicorn-project/), but most prominently in The First Ideal of Locality and Simplicity, and how it can lead to the Second Ideal of Focus, Flow, and Joy.

Without doubt, learning Clojure was one of the most difficult things I’ve learned professionally, but it has also been one of the most rewarding. It brought the joy of programming back into my life. For the first time in my career, as I’m nearing fifty years old, I’m now finally able to write programs that do what I want it to do, and am able to build upon them for years, without it collapsing like a house of cards, as has been my normal experience.

The famous French philosopher Claude Lévi-Strauss would say of certain tools, “Is it good to think with?” For reasons that I will try to explain in this post, Clojure embraces a set of design principles and sensibilities were new to me: functional programming, immutability, an astonishingly strong sense of conservative minimalism (e.g., hardly any changes in ten years!), and much more…

Clojure introduced to me a far better set of tools to think with and to also build with. It’s also led to a set of aha moments that explain why my code for decades would eventually fall apart, becoming more and more difficult to change, as if collapsing under its own weight. Learning Clojure taught me how to prevent myself from constantly self-sabotaging my code in this way.

For nearly three years, I’ve been gushing to whoever would listen about how great Clojure is. I was dazzled by Bryan Cantrell’s amazing [“I’m falling in love with Rust” blog article in September 2018](https://twitter.com/bcantrill/status/1042180114199375872) — after reading it, I committed myself to eventually write my love letter to Clojure (but only after I first wrote a love letter to my wife, [@notoriousMVK](https://twitter.com/notoriousmvk?lang=en), of course!).

Organizing, writing and finishing this post has been surprisingly difficult. I’ve wanted to write this article for years, having written portions of it over the last twelve months, trying to figure out how to share my experience and epiphanies without being insipid, pretentious, or boring. But after three days of constant writing and second-guessing myself, and now exceeding 8,500 words, in the interest of _finally_ getting something posted, I’m committed to post this today.

The stuff that doesn’t make it in will go into “My Love Letter to Clojure #2”. 🙂

I will discuss the following:

*   What The Second Ideal of Focus, Flow and Joy Means To Me
*   Relearning Coding: How Coding Mostly Left My Daily Life in 2008, But Came Back in 2016
*   Why I Love LISPs Now
*   Functional Programming and Immutability (and John Carmack)
*   A Mistake I’ve Been Making Since Grad School, and How I Fixed It: Composability
*   The Epiphany I Had Reading “An Introduction to React in 2019 (For People Who Know Just Enough jQuery To Get By)”
*   What Rich Hickey Says About Simplicity: Where The First Ideal Of Locality and Simplicity Comes From
*   Solving Business Problems, Not Solving Puzzles — Why I Detest Doing Infrastructure Work These Days…
*   Lastly, the REPL… The Ultimate in Fast and Fun Feedback Loops!
*   The Creations Amazing Clojure Community, Parting Thoughts, and What I’d Like To Write About In The Future  
    

What hopefully comes across is my gratitude to Clojure, its inventor Rich Hickey, and the entire Clojure community.

What The Second Ideal of Focus, Flow and Joy Means To Me
--------------------------------------------------------

*   The First Ideal—Locality and Simplicity
*   The Second Ideal—Focus, Flow, and Joy
*   The Third Ideal—Improvement of Daily Work
*   The Fourth Ideal—Psychological Safety
*   The Fifth Ideal—Customer Focus  
    

In _The Unicorn Project_, The Second Ideal of Focus, Flow, and Joy is intended to describe the optimal mental state of creative flow that we all seek, so beautifully described by the famous psychologist Dr. Mihaly Csikszentmihalyi (pronounced CHEEK-sek MEE-hai). He gave one of the most [amazing TED talks ever (2004)](https://www.ted.com/talks/mihaly_csikszentmihalyi_on_flow?language=en), and wrote the book [“Flow: The Psychology of Optimal Experience (2008).”](https://www.amazon.com/Flow-Psychology-Experience-Perennial-Classics/dp/0061339202)[1](https://itrevolution.com/love-letter-to-clojure-part-1/#fn1)

For many of us in technology, we often associate those amazing moments of productivity and creative flow with coding. It’s the feeling that you get when you are getting so much productive work done, you lose track of time, and maybe even our sense of self, feeling the triumph of achieving amazing feats, brilliantly solving the problem you set out to solve — for me, it often felt like conquering the Level 30 quest when you’re only a Level 5 Paladin. (Insert your D&D character of choice here.)

For most of the twenty years of my professional career, I have self-identified primarily as an Ops person. This is despite getting my masters degree in computer science in 1995 — the courses I loved the most were high-speed compilers (main lesson: don’t read files more than once), and high-speed networking (main lesson: avoid making memory copies entirely, if you can).

But as much as I loved computer science, I always gravitated towards Ops, because I observed that that’s where the excitement was, and that’s where the saves were made — it if weren’t for the heroic work of Ops, all the mistakes and failures of Dev and Infosec would affect our customers.

But something changed three years ago. I now self-identify as a developer! Without a doubt, it’s because I learned the Clojure programming language. I mentioned that above that it was one of the most difficult things I’ve learned professionally — before I wrote my first line of working code, I must have spent forty hours of reading books and blog posts, as well as watching videos, before I was able to write my first real non-trivial program.

A big reason is that it’s a LISP programming language, which I’ve never used before. Another reason is that Clojure is a functional programming language, that embraces and encourages immutability, which means that you’re not allowed to mutate variables, which is another thing I’ve never been exposed to before.

I’m incredibly grateful for the help I got from [Mike Nygard](https://twitter.com/mtnygard) (author of the amazing book [“Release It!,”](https://www.amazon.com/Release-Production-Ready-Software-Pragmatic-Programmers/dp/0978739213) and incidentally, the person who first showed me Clojure and the Datomic database in 2012, which baffled me so much, I mostly forgot about it until five years later) and so many other people in the Clojure community. (More on the incredible community around Clojure later.)

Now, solving problems with Clojure has become one of my favorite things to do.

Coding in Clojure is fun, in a way that I’ve never experienced before. For years, in my ideal month, I’m spending 50% of my time writing, and 50% of my time hanging out with the best in the game. These days, that’s still the case, but I want to be spending 20% of my time coding to solve problems I want to solve, as well.

Because that’s how much fun I’m having.

Over the last three years, I’ve built many programs to solve my own problems, such as quickly exporting and transforming data from one tool to another, building word clouds, analyzing git repo histories… But there are some tools that I’ve built that I use nearly every day, such as a program to manage cards on my Trello boards, grab screenshots from Google Photos, track information from various book e-commerce sites. It’s blown me away how I can solve problems with a level of ease and joy I’ve never experienced before.

My first Clojure project I tackled revealed something stunning to me. I’m fortunate to have participated in helping write and rewrite an application called [TweetScriber](https://tweetscriber.com/) three times. It’s a program that a bunch of us wrote in 2012 to allow us to take notes and tweet at the same time on an iPad — it turns out that this is a very useful thing to do when you’re writing a book, as it forces you to take notes, write things succinctly enough so that you can tweet it out (which forces a certain pithy and terse style), and get feedback by observing what tweets get people’s attention. (The tweets that got the most retweets inevitably found their way into a presentation or a book.)

*   In 2012, Flynn and Raechel Little wrote the first version as an iPad app in Objctive-C — it was about 3,000 lines of code. (They did such an awesome job!! It worked splendidly until iOS 7 or so, when something broke terribly and it wouldn’t even start up anymore.)
*   In 2015, I rewrote it as a JavaScript/React application, and it was about 1,500 lines of code.
*   In 2017, I rewrote it again as a ClojureScript application, and it was only 500 lines of code! Holy cow!!!  
    

First off, I was actually amazed that I could even rewrite this application in ClojureScript as a novice, and how surprisingly straightforward it was. (Clojure runs on the JVM or on the CLR for all you .NET people, while ClojureScript gets transpiled into JavaScript so it can run on the browser, inside node.js, etc. In all cases, they can leverage the massive library and tooling ecosystem that these universes provide.) But what was so remarkable to me was how superior my ClojureScript implementation was, in so many dimensions.

It was shorter. It forced a separation of concerns between mutable state, control flow logic, UI elements, etc. that I’ve long read about, but finally was able to put into practice. (I used the [re-frame](https://github.com/Day8/re-frame) framework, which co-evolved at the same time as the JavaScript Redux framework.)

What what has been the most astonishingly to me is that I’ve been able to keep adding functionality to TweetScriber, year after year. Right before the last DevOps Enterprise Summit, I added a way to add photos to tweets without leaving the app; I experimented with saving the tweet ids in a database, instead of just text. It was easy to experiment with adding these features, without blowing everything else up.

It’s now nearly 5,000 lines of code, and I’m still able to understand it, and add things I want to it without it falling over like a house of cards.

The ability to do this is new to me. There’s something very different about the way I code now, and I attribute it to Clojure and what it’s taught me. I will make the maybe astonishing claim that 90% of the errors I used to make have simply disappeared — as in, an entire category of errors I used to make have been eliminated.

(I intend to open source the TweetScriber application, along with there other apps I’ve written. Just as soon as I figure out how to take all the secrets out of my GitHub repo. If anyone wants to help, let me know. I’ll take any help I can get. :).

You can run TweetScriber, albeit with non-existent documentation [here](https://tweetscriber-app.herokuapp.com). You can read all the notes I’ve posted [here](http://scribes.tweetscriber.com/). (OMG, I’m thrilled that someone else is using the program!) You can read all saved scribed that people have posted over the years [here](http://scribes.tweetscriber.com/) (that portion was written by awesome [Jeff Weiss](https://github.com/jeffweiss) and [William Hertling](https://itrevolution.com/love-letter-to-clojure-part-1/twitter.com/hertling)).

In short, Clojure brought the joy of programming back into my life!

Relearning Coding: How Coding Mostly Left My Daily Life in 2008, But Came Back in 2016
--------------------------------------------------------------------------------------

If I can learn Clojure, anyone can.

Before I got into my specific aha moments, I thought it would be worthwhile to describe to what extent coding stopped being part of my daily life. I’m going to make the case that me learning Clojure is sort of like Encino Man learning to drive — you know, the movie about the caveman who was frozen in ice and wakes up in the completely changed, modern world.

I think this is relevant to many people in technology — I’ve observed that many people in the technology field started their careers coding, but then as their career progressed, they start coding less—sometimes it’s to go into people management, project management, information security, or product management, or into the business functions.

But I believe now more than ever that coding is a proficiency that will be needed in every profession, regardless of what specific domain you specialize in, or what role you have within an organization. As the brilliant Mark Schwartz (former CIO of US Citizenship and Immigration Services, and author of many amazing books, including [“Seat at the Table: IT Leadership in the Age of Agility”](https://www.amazon.com/dp/B075TD7JJ3/)) stated in an address to the government system integrator community, “we need technical people, because last I heard, this is still a technical field.”

(I mean, OMG, right? The response to any remark that “I’m not technical” seems more and more jarring to me. Maybe I’ll write more on that at at later date.)

Here are some concrete statistics on what happened to me, mostly to motivate my claim that I had become “non-technical” for almost a decade. Here’s a chart that shows my my programming background, showing year by year how many lines of code I wrote (it’s a wild guess).

I created this graph after Dr. Mik Kersten mentioned to me that he’s written over one million lines of Java in his career, and Rod Johnson (inventor of Spring) said that he’s written millions of lines of Java. Until then, I had never thought about how many lines of code I’ve written in my career…

What I discovered was pretty surprising…

*   Perl: thousands of LoC
*   C/C++: hundreds of thousands of LoC
*   Ruby: tens of thousands of LoC
*   Java: hundreds of LoC  
    

What really caught my attention was that I had only written “hundreds of lines of Java.” In contrast, most of my generation had likely written 10K, 100K, or even millions of lines of Java! In contrast, I had gotten stuck in the C and C++ cul-de-sac, and due to a fluke of timing, I managed to miss the entire Java revolution, which was undeniably the center of gravity for both industry and academic research — multiple generations of Ph.D.s were created around almost every aspect of Java and the JVM.

Maybe amusingly, at the time, I was happy to sit on the Java sidelines, because… stupid reasons…. When I got my undergraduate degree in computer science (1990-1993), the predominant pedagogic language was C. By the time I went to graduate school (1993-1995), C++ was just coming out, and it seemed laughable at the time. One of my professors, the famous Dr. Todd Proebsting, joked: “How do you know if a program was written in C++? It takes 10 seconds for the program to exit()!” (The long delay before the program actually quit was from all the class destructors being called.)

Around 1995, Java was just starting to be talked about — and we mostly laughed at that, too, because of the absurdly long startup times of the JVM. At that time, Perl and Tcl were dismissed as mere “scripting languages,” not suitable for real programmers.

By the time the Java revolution was in full swing in the early 2000s, coding had virtually vanished from my daily life, and it wasn’t until the late 2000s that I got back into doing substantial hobby coding projects. (I had great fun trying to compete in the Netflix recommendation challenge with William Hertling, which we did in Ruby.)

In contrast, Java revolutionized programming, and a whole ecosystem flourished around it, such as Maven (Maven is to Java as npm is to JavaScript, ruby gems is to Ruby, pip is to Python, etc.), the JVM, Eclipse, etc…

I somehow not only missed out on the Java revolution, but I never got exposed to LISP programming (or even Emacs). Which made my entry into Clojure much more difficult.

And yet, I’m love the JVM, which Clojure runs on. And I love LISP, which Clojure is a dialect of.

Again, my point is, if I can do it, anyone can!

Why I love LISPs Now
--------------------

Let’s talk about Clojure being a LISP first. As noted in the chart above, LISP is a very ancient language. And very distinctive. Even before I went to college, I knew that people made fun of LISP, joking that it stood for “lots of stupid parentheses.”

But I’m never going back. Like almost everything about Clojure, as a LISP, its syntax is astonishingly simple. Everything is inside parentheses, the verb is always at the front, and arguments are next.

Yes, almost everyone who hasn’t used a LISP initially finds it alien — my first reaction was, “holy cow, this doesn’t even look like code.” But it’s actually a far more uniform and simpler syntax.

I’m never going back.

Contrast LISP to the complicated order of precedence operations you find in almost every other programming language, as well as the huge grammars and syntax. That takes a lot of brain space.

I was talking to a JavaScript programming lead at a bar (yes, this is what I love talking about in bars), and he asked what a Clojure program would look like that would parse an integer in a JSON file, and increment that integer. Here’s what it looks like — I think it’s quite beautiful:

```
; input is JSON string: "{foo: 2}" (defn xform [s] (-> (js/JSON.parse s) js->clj (update "foo" + 2) clj->js js/JSON.stringify)) 
```

Here’s a slightly more annotated version that describes more fully what is going on:

```
(defn xform-annotated [s] ; I love the -> function called threading ; it basically chains the functions together -- composition ; of functions, passing results of previous function as first argument (-> ; calls out to node.js ; note that first is name of function, and "s" is argument (js/JSON.parse s) ; convert it from native JS object to Clojure map (js->clj) ; update key "foo" by applying function (fn (+ 1)) ; note that no mutation happens -- it returns a new map (update "foo" + 2) ; convert back to native JSON object (clj->js) ; call out to node function to convert back into string (js/JSON.stringify))) 
```

A wonderful (and free primer) on LISP syntax is here: [https://www.braveclojure.com/do-things/](https://www.braveclojure.com/do-things/) — this is just one portion of Daniel Higgenbottom’s fantastic book [“Clojure for the Brave and True: Learn the Ultimate Language and Become a Better Programmer”](https://www.amazon.com/Clojure-Brave-True-Ultimate-Programmer/dp/1593275919). (More book recommendations later.)

To end this section, like I said, I’m never going back to a non-LISP. Life is too short to learn fussy language grammars. But I’ve become fussy in other ways, too. (More on that later.)

Functional Programming and Immutability (and John Carmack)
----------------------------------------------------------

Another thing that initially flummoxed me about Clojure was the notion of immutability. After all, how are you supposed to write a program when you’re no longer allowed to change the value of variable?

Over the years, I’ve read many articles about functional program extolling the value of pure functions and immutability — these are two of the characteristics often associated with functional programming languages, such as Haskell, OCaml, Erlang, Elm, Elixir, Scala, PureScript, and of course, Clojure.

Some of the promised benefits include programs that are easier to reason about, the ability to trivially parallelize them, and so forth. One of the first books I read to learn Clojure wa [“Clojure Programming: Practical LISP For The Java World”](https://www.amazon.com/Clojure-Programming-Practical-Lisp-World/dp/1449394701) — a book I highly recommend, because it is targeted at programmers who are used to Python, Ruby and Java.

I was still struggling to get my head around core principles and its idioms. And then I read a code sample, with the following warning: “In Ruby, even strings, often faithfully immutable in other languages, are mutable. This can be the source of all sorts of trouble.”

When I read the following code sample, I literally bolted upright in bed, panicked by what I just read:

```
# Ruby code s1 = "hello" s2 = "world" s3 = s1 + s2 # s1 is still "hello" s4 = s1 << s2 # s1 is now "hello world" # !!!! Mutation of s1 is side-effect! >> s = "hello" => "hello" >> s << "*" => "hello*" # s value was mutated!!!! >> s == "hello" => false 😱😱😱 
```

When I say that I “bolted upright in bed,” I mean it quite literally. I was actually panicked from the terror that I felt, wondering how many times I might have accidentally written code that changed a variable I didn’t mean to change. In fact, you can see this tweet I wrote the next morning in that state of existential horror. That was when I realized that mutation was more dangerous than I had thought.

> I love Ruby. Last night, while reading, I learned I didn’t understand something very fundamental about Ruby strings: shame on me! [pic.twitter.com/Mk26jH1z35](https://t.co/Mk26jH1z35)
> 
> — Gene Kim (@RealGeneKim) [October 18, 2016](https://twitter.com/RealGeneKim/status/788408398245040129?ref_src=twsrc%5Etfw)

(Incidentally, people have reported similar feelings of sheer terror after reading Brian Goetz’s book [“Java Concurrency In Practice,”](https://www.amazon.com/Java-Concurrency-Practice-Brian-Goetz/dp/0321349601) realizing all the things that can go wrong in concurrent programming in code they had written, often leading one to embrace languages like Clojure. More on Brian Goetz later.)

Over the next year, it genuinely dawned on me how disallowing variable mutation made programs simpler and easier to reason about, even for single-threaded programs. It made me realize that “passing variables by reference,” something that I thought was such a time-saver, was actually one of the things that caused me tremendous problems, because it caused variables to be changed by distant parts of the code.

Here’s a brief video I did that described my aha moment of how potentially dangerous passing variables by reference is to the unsuspecting.

VIDEO

Horrors! After programming in Clojure, it seemed so dangerous (and vulgar!) that you could call a function, and it could change the object you passed it! How can you reason about a program that allowed uncontrolled mutation like this?

(By the way, that talk from Scott Havens is amazing: Until very recently, he was Director of Software Engineering, Jet.com/Walmart Labs, where he was responsible for rebuilding the entire inventory management systems that support Walmart, the world’s largest company. He will be sharing how he used functional programming principles to massively simplify the vast architecture that supported the inventory management systems, making it simpler, more reliable, easier to maintain, and cheaper to run. This is functional programming not in the small, but in one of the largest and most complex business processes in the world — and this is what the last 20% of _The Unicorn Project_ is inspired by.)

Just as Clojure showed me how a simpler LISP syntax frees your brain to think more about the problem you want to solve, the world without mutation made me realize just how difficult it is to keep track of how mutations are happening in your programs.

But don’t take it from me — take it from [John Carmack](https://itrevolution.com/love-letter-to-clojure-part-1/twitter.com/ID_AA_Carmack), who influenced so many of us, as one of the founders of id Software (DOOM, Quake, etc.), now CTO of Oculus VR. He wrote an [amazing article in 2013 in Gamasutra magazine](http://www.gamasutra.com/view/news/169296/Indepth%5C_Functional%5C_programming%5C_in%5C_C.php) about the power of using functional programming concepts in C++.

> My pragmatic summary: A large fraction of the flaws in software development are due to programmers not fully understanding all the possible states their code may execute in. In a multithreaded environment, the lack of understanding and the resulting problems are greatly amplified, almost to the point of panic if you are paying attention. Programming in a functional style makes the state presented to your code explicit, which makes it much easier to reason about, and, in a completely pure system, makes thread race conditions impossible.
> 
> No matter what language you work in, programming in a functional style provides benefits. You should do it whenever it is convenient, and you should think hard about the decision when it isn’t convenient. You can learn about lambdas, monads, currying, composing lazily evaluated functions on infinite sets, and all the other aspects of explicitly functionally oriented languages later if you choose.  
>   
> C++ doesn’t encourage functional programming, but it doesn’t prevent you from doing it…  
>   
> Pure functions are trivial to test; the tests look like something right out of a textbook, where you build some inputs and look at the output. Whenever I come across a finicky looking bit of code now, I split it out into a separate pure function and write tests for it. Frighteningly, I often find something wrong in these cases, which means I’m probably not casting a wide enough net.

I remember reading this article in 2013, but it wasn’t until I re-read that article in 2016 that I realized how universal this problem is — it’s not just for games written in C++ that need to run at 60 frames per second, it’s for any programmer.

In his 2013 QuakeCon keynote, he describes his experiments rewriting _Castle Wolfenstein 3D_ using functional programming techniques in Haskell, to explore to what extent one could use a programming language that disallowed mutation, which was absolutely fascinating.

VIDEO

(There’s another article somewhere about Carmack’s explorations in LISPs, which is equally fascinating…)

A Mistake I’ve Been Making Since Grad School: Composability
-----------------------------------------------------------

After gaining more proficiency in Clojure, many other things become apparent. One thing that I learned is the benefits of pushing side-effects (I.e., any impure functions, such as anything that involves input or output) to the edges of the program, and making sure that everything else in between is a pure function.

To recap, pure functions are those that the output is strictly a function of the inputs. One of the benefits of pure functions is that the function can be tested completely in isolation, as John Carmack noted above.

When I started making a point of doing this, the benefits started becoming quite apparent. In fact, I started to get the suspicion that _not practicing this_ was one of the main reasons the code I wrote would become increasingly untestable and difficult to change — which led to the feeling that my code was collapsing under its own weight.

This is a problem that I’ve been having for a _very long time_ … In fact, I still have a very vivid memory of when I this problem killed a project I was working on. It was during my high speed compilers class in graduate school, where we built a Modula-2 compiler in C++ that generated SPARC assembly code, which was then compiled into a Solaris executable.

You first wrote a lexical analyzer to tokenize the input (using _lex_ ), then the compiler that would turn the tokens into an abstract syntax tree (using _yacc_), turn it into some intermediate format, and then emit assembly code. And then use _as_ to compile.

It started off great, especially since I had written lexers and parsers before. But at each later stage, I remember the feeling of tucking the previous compilation phase into the next phase, thinking, “okay, here goes nothing… I’m putting my code somewhere where I can no longer directly access it, and it feels like throwing it into a deep, dark well, and I sure hope it works.”

In other words, I had written the phases in a way where each phase was no longer independently runnable, let alone testable. I was good enough where it was not really a problem until the very last phase, where we were having to compile the generated assembler code, and execute it.

I remember that my compiler working for all the test cases, until we had to implement recursion. Then it started blowing up when after a certain number of recursive calls — after several all-nighters, I finally figured out that I was incorrectly computing the memory locations of variables on the stack.. After a certain number of recursive function calls, the generated program would just segfault and die.

Even thought I figured out conceptually what was going wrong, I ran out of time, and couldn’t fix the mess I had created before submitting my fatally flawed compiler. I probably got one of the lowest grades in the class.

What I had learned was that burying my code so that it could only be executed inside other functions violated the principle of composition — the ability to run and test it, independent of other modules. (My thanks to [Dr. Stephen Magill](https://twitter.com/stephnmagill) for taking the time to explain this to me, who also helped me write my first Haskell program!)

```
 ; ; good way: steps are composed together, which each compiler phase ; indepdendently executable and testable ; (-> (tokenize-source-files!) (generate-abstract-syntax-tree) (generate-intermediate-representation) (generate-assembly-instructions) (write-assembly-output-files!)) ; ; bad way ; all the intermediate steps buried inside other functions, no longer reachable or inspectable ; tokenize-source-files-and-generate-ir-and-generate-assembly(); 
```

In Clojure, I fell in love with the convention of marking impure functions with a `!`, to make it obvious when side-effects could happen. This includes any function that reads from disk or a database, let alone writes to one — after all, even these inputs make the output impure. These effectful functions should be pushed to the beginning or the end of your program, which makes everything in the middle independently runnable and testable.

It’s embarrassing that it’s taken thirty years after I started coding professionally, to finally discover this mistake, which has plagued almost every large program that I’ve worked on.

And of course, many people learned this twenty years ago, either by intuition, experience, or by reading great books such as [“Refactoring: Improving the Design of Existing Code”](https://www.amazon.com/gp/product/0134757599) by Martin Fowler… But knuckle-headed me only learned after being forced to confront this in Clojure, which seems to bring these problems to the front and center.

(What’s also interesting to me is that by pushing side-effects to the edges, almost everything can be rewritten as pure functions and unit tests. Previously, most of my tests often tested my code and the I/O, API calls, etc… In the ideal, you just want to test the code you wrote. You don’t need to test whether the file system works in every test, or whether Trello API works, etc…. By doing this, use of brittle mocks and stubs almost disappears.)

The Epiphany I Had Reading “React for jQuery Programmers To Get By”
-------------------------------------------------------------------

Something else happened during my first rewrite of TweetScriber that primed me for another Clojure. Knowing almost nothing about writing a JavaScript app, I was initially doing some research and stumbled upon this amazing article, [“An Introduction to React in 2019 (For People Who Know Just Enough jQuery To Get By)”](https://medium.freecodecamp.org/react-introduction-for-people-who-know-just-enough-jquery-to-get-by-2019-version-28a4b4316d1a) which was originally written by Shu Uesugi ([@chibicode](https://twitter.com/chibicode)) in 2015, and revised by Julien Benchetrit ([@julienbenc](https://twitter.com/julienbenc)).

I had virtually no experience with working in the browser DOM, had never used jQuery (but had heard about how revolutionary it was years back), and I’ve certainly more modern frameworks like React.

It was an incredible article to read, because it walked through a couple of exercises that taught me some profound lessons in how program state leads to incredible complexity — more things that have caused my programs to eventually collapse in on itself. And the exercises represented about half the program I wanted to write!

The article seemed perfect, because at first glance, the exercises seemed to cover 50% of the TweetScriber functionality I needed! But reading through the exercises, it seemed to discuss something very, very important….

*   Step 1. Write a Tweetbox, which lets you type into an textarea window, with a Tweet button.  
      
    Cool. I barely knew enough HTML to write this, so copying this code would be awesome. Easy enough.  
    
*   Step 2. Change the Tweetbox so that if the contents exceed 140 characters (the original article was written in 2015), then disable the Tweet button.  
      
    Great. We now have some state associated with the program, but it isn’t too bad, because it’s just keeping track of the number of characters in the textarea, and adjusting whether the button is disabled or not.  
    
*   Step 7. Change the Tweetbox so that it displays characters remaining, and display message that indicates too many characters.  
    Okay, this is getting a little more complicated, because now message and message components need to know about the state of the application. I’m starting to see how potentially untenable having all these components knowing about each other is…  
    
*   Step 9. Add an Add Photo button, which displays “photo added” if a photo has already been added, and also subtract 23 characters from the number of characters remaining (link to photos consume characters).  
    Okay, the point of the exercises is becoming very evident, because now state management is becoming a real issue, and using the jQuery style of callbacks is becoming a real mess — even keeping track of which components need to know of each other, and what their responsibilities are to each other is impossible to remember.  
    

In other words, in the jQuery implementation, the flow of information from one component to another becomes entangled. The diagram below shows it magnificently.

![Source: Shu Uesugi and Julien Benchetrit](https://itrevolution.com/love-letter-to-clojure-part-1/)

<img src="https://itrevolution.com/wp-content/uploads/2019/10/DraggedImage-3-10.png" alt="Source: Shu Uesugi and Julien Benchetrit" class="wp-image-6919" />

Source: Shu Uesugi and Julien Benchetrit

In contrast, consider the the same functionality implemented with something like React, in a more functional style, where state is mutated in one place, and all the UI elements are rendered from the state. State is changed in a very uniform way, and the UI is rendered as pure functions, never mutating state.

The diagram below show how much simpler the data flow is…

![Source: Shu Uesugi and Julien Benchetrit](https://itrevolution.com/love-letter-to-clojure-part-1/)

<img src="https://itrevolution.com/wp-content/uploads/2019/10/DraggedImage-4-8.png" alt="Source: Shu Uesugi and Julien Benchetrit" class="wp-image-6922" />

Source: Shu Uesugi and Julien Benchetrit

I found this to be a shockingly convincing argument about how code should be written. And I was pretty happy with my first version that I wrote in TypeScript and React.

(In my ClojureScript rewrite using re-frame, it addressed one of the problems I found in using React, which was state is scattered across all the components. Re-frame and Redux take a different approach, which is to put all mutable state into one place, which I’ve found works magnificently. This has been so successful for me that I will never write a client web app in any other type of framework.)

I think this aha moment prepared me for the discovery of Rich Hickey and Clojure…

What Rich Hickey Says About Simplicity: Where The First Ideal Of Locality and Simplicity Comes From
---------------------------------------------------------------------------------------------------

Rich Hickey is the inventor of Clojure, and his talks and Clojure have so much affected how I think about software — in fact, this entire blog post attempts to frame some of these aha moments.

There was one particular Rich Hickey talk that hit me like a ton of bricks, which was his famous “Simple Made Easy” talk that he gave at Strange Loop 2011 — if the jQuery/React epiphany was an aha moment, this talk was a chorus of aha moments. [2](https://itrevolution.com/love-letter-to-clojure-part-1/#fn2)

The talk is on the InfoQ site [here](https://www.infoq.com/presentations/Simple-Made-Easy/) (which shows the slides associated with the soundtrack), and you can find a wonderful transcript of the talk [here](https://github.com/matthiasn/talk-transcripts/blob/master/Hickey_Rich/SimpleMadeEasy.md). You can also find a version of the talk he did for the Ruby and Ruby on Rails community on YouTube [here.](https://www.youtube.com/watch?v=rI8tNMsozo0)

This talk is so impactful to me that I’m almost tempted to say, “Go ahead and take an hour to listen to the talk. I’ll wait here.”

Among many other things, he talks about how limited the human brain is in its ability to reason about things, to keep track of things, to grapple with complexity (like the jQuery example above) He stated that the difference in cognitive capability between your average programmer and your average programmer is not the vaunted 10x difference. He said (emphasis mine):

> Then we have this other part though, which is the mental capability part. And that’s the part that’s always hard to talk about, the mental capability part because, the fact is, we can learn more things. We actually can’t get much smarter. We’re not going to move; we’re not going to move our brain closer to the complexity. We have to make things near by simplifying them.
> 
> But the truth here is not that they’re these super, bright people who can do these amazing things and everybody else is stuck because the juggling analogy is pretty close. **Right? The average juggler can do three balls. The most amazing juggler in the world can do, like, 9 balls or 12 or something like that. They can’t do 20 or 100. We’re all very limited. Compared to the complexity we can create, we’re all statistically at the same point in our ability to understand it, which is not very good. So we’re going to have to bring things towards us.**

He talks about the need for simplicity in the software we write, and the stuff that we write our software in. The conditions for simplicity include having components that are completely decoupled from each other, with no knowledge each other. Just like in the jQuery example, things quickly become a complete mess when all the different controls have to know about each other — it’s difficult to get it to work correctly, to reason about what happens when state changes, and it’s difficult to write additional functionality to it.

Hickey goes through the some of the core concepts in programming languages, and describes the extremes of which represent the ideal of simplicity and which ones represent complexity that eventually leads to the inability to understand and safely change our code, as well as misery and catastrophe.

![Source: Rich Hickey, Simple Made Easy (2011)](https://itrevolution.com/love-letter-to-clojure-part-1/)

<img src="https://itrevolution.com/wp-content/uploads/2019/10/DraggedImage-6-4.png" alt="Source: Rich Hickey, Simple Made Easy (2011)" class="wp-image-6921" />

Source: Rich Hickey, Simple Made Easy (2011)

![Source: Rich Hickey, Simple Made Easy (2011)](https://itrevolution.com/love-letter-to-clojure-part-1/)

<img src="https://itrevolution.com/wp-content/uploads/2019/10/DraggedImage-7-4.png" alt="Source: Rich Hickey, Simple Made Easy (2011)" class="wp-image-6916" />

Source: Rich Hickey, Simple Made Easy (2011)

As I mentioned in the beginning of this article, _The Unicorn Project_ is about the invisible structures that enable developers to be productive. So much of this comes from the concepts that Rich Hickey has espoused over the years, and which have become infused into Clojure and the Clojure community:

> Erik answer, “‘Complect’ is an archaic word, resurrected by Sensei Rich Hickey. It is a verb that means to turn something simple into something complex.
> 
> “In tightly coupled and complected systems, it’s nearly impossible to change anything, because you can’t just change one area of the code, you must change one hundred, or even a thousand, areas of the code. And even the smallest changes can cause wildly unpredictable effects in distant parts of the system, maybe in something you’ve never even heard of.
> 
> “Sensei Hickey would say, ‘think of four strands of yarn that hang independently—that’s a simple system. Now take those same four strands of yarn and braid them together. Now you’ve complected them.’ Both configurations of yarn could fulfill the same engineering goal, but one is dramatically easier to change than the other. In the simple system, you can change one string independently without having to touch the others. Which is very good.”
> 
> Erik laughs, “However, in the complected system, when you want to make a change to one strand of yarn, you are forced to change the other three strands, too. In fact, for many things you may want to do, you simply cannot, because everything is so knotted together!
> 
> “And when that happens,” he continues, “you’ve trapped yourself in a system of work where you can no longer solve real business problems easily anymore—instead, you’re forced to merely solve puzzles all day, trying to figure out how to make your small change, obstructed by your complected system every step of the way. You must schedule meetings with other teams, try to convince them to change something for you, escalate it to their managers, maybe all the way up the chain.
> 
> “Everything you do becomes increasingly distant from the real business problem you’re trying to solve,” he says. “And that, Dwayne, is what everyone discovered when they switched out the routers in those manufacturing plants. Before, you had three independent strands, with team able to work independently but at the cost of having to maintain three networking switches.
> 
> “When you put them all on one switch, you complected their value streams, all now having dependencies on each other that didn’t exist before! They must constantly communicate, coordinate, schedule, marshal, sequence, and deconflict their work. They now have an extremely high cost of coordination, which lengthened lead times, decreased quality, and in your story, led to a week-long catastrophe that significantly impaired the business, going all the way up to Steve!” Erik says with glee.

You can find many collections of “Rich Hickey’s Greatest Hits” on the Internet. Here are some:

(In _The Unicorn Project_, the joke about “how many people do you need to take out to lunch in order to get a feature done” was taken from his talk that he did at 2015 Java One conference: [https://www.youtube.com/watch?v=VSdnJDO-xdg](https://www.youtube.com/watch?v=VSdnJDO-xdg). In fact, in some ways, coupling as one of the key themes of the book came from watching this talk, where he compared modern REST interfaces with the bad old days of CORBA and Sun RPC, where changing anything needed everybody to cooperate.)

What I find so interesting is that functional programming also eliminates iteration and looping, which is so prone to off-by-one errors. In _The Unicorn Project_, when Maxine pairs with some middle schoolers in Python, she spots their “off by one” error when they’re iterating through an array. This was inspired by Cornelia Davis, describing when she worked with her college-aged son on a genomic sequencing program in Python, showing the contrast in imperative vs. functional programming style: [https://youtu.be/R1RDhUf1Go4?t=492](https://youtu.be/R1RDhUf1Go4?t=492)

By the way, here’s a whole brilliant talk about showing how to convert an imperative program into a more functional style in JavaScript: “Solving Problems The Clojure Way,” by Rafal Dittwald.

VIDEO

Solving Business Problems, Not Solving Puzzles — Why I Detest Infrastructure These Days…
----------------------------------------------------------------------------------------

So, I feel like I need to explain another consequence of now recognizing and wanting to avoid complexity. I mentioned that I now self-identify as a developer… what I didn’t tell you was that I now self-identify as one of those _very fussy, parochial developers_ that Ops people hate.

In my ideal, I just want to work on solving the problem I set out to solve, working within my pure functional application bubble. And I don’t want to deal with anything outside of that bubble.

Here’s all the things I used to love doing, but now I detest doing…

*   Dealing with anything outside of my application
*   Connecting to anything to anything (including databases)
*   SQL databases and figuring out why my queries are so slow
*   Updating dependencies (because, so hard…)
*   Secrets management (ditto)
*   Bash
*   YAML
*   Patching (so inconvenient…)
*   Building kubernetes deployment files (mostly by Googling)
*   Trying to understand why my cloud costs are so high  
    

This is not to say that these things aren’t important. On the contrary, they’re absolutely critical. Which is why I think the brightest days of Infrastructure and Operations and Infosec are still ahead of us, not behind us. I believe the job of infrastructure and security people is to create the platforms that developers can use to take care of all these non-functional requirements, without having to Google and Stack Overflow all day.

Lastly, the REPL… The Ultimate In Fast Feedback Loops!
------------------------------------------------------

Okay, it’s about time to wrap up this first article is pushing 8K words, and there’s so many other things I want to write about, because I’m so excited by them, but it’s time to post something… otherwise, I’ll never post anything.

But there’s one thing that I need to write about, which is something that seems pretty unique to Clojure, or LISPs, which is the amazingly interactive nature of development. One reason I think I’ll be using Clojure for years (or decades) to come is because of the REPL.

REPL stands for Read-Eval-Print-Loop, which many languages have. But I don’t know of any other modern language that can be integrated into an editor, where you can modify the running program, inspect variables, run functions… from inside the program!

In the spirit of Focus, Flow, and Joy, I think the REPL experience is absolutely amazing and sublime. It feels like you’re building your program from the inside, writing and testing expressions, saving I/O to variables and transforming the output using pure functions. I’ve done this with Clojure programs running on the JVM, or ClojureScript programs running in a browser… I’ve done it to analyze and visualize large data sets, save to and query databases…

Going back to programming where you have to save and reload your program, and then maybe even navigate to get back to a certain program state, just seems intolerable now.

This is definitely one of those things that you have to see a master at work to fully appreciate. Here’s Bruce Hauman talking in 2015 about the now famous figwheel, a ClojureScript build tool that enables live code reloading (and so much more). Watch as he shows something he wrote on the plane ride out to the conference, as he changes the solar system simulator, and the JavaScript app gets hot-reloaded in real time.

VIDEO

(Yes, you can do this in JavaScript, but trust me, due to how dicey state mutation is, it’s very flakey. On the other hand, the way Clojure enforces mutation to be done in a very specific way makes it almost perfect for this style of coding.)

Here’s a 2019 video of Sean Corfield (famous for his work on the mostly widely used Clojure JDBC libraries) showing how he uses the REPL to debug a problem reported in the `core.memoize` function. He walks through the steps required to reproduce the problem, form by form, and the output of each form as it’s evaluated is displayed in the editor. In the failing case, we watch as he inspects the internal state of the function, hypothesizes what is going wrong, confirms it, and fixes it. (We then watch as he creates an additional test to the Clojure test suite and runs in across 10 years of Clojure versions.)

I think Sean makes debugging almost look fun, and it shows just how powerful working within a REPL can be.

VIDEO

(I use the [Cursive plug-in for IntelliJ](https://cursive-ide.com/) by Colin Fleming and team, which I find to be absolutely terrific. I use Visual Studio Code for almost all non-Clojure files, so I have high hopes for the Calva plug-in… But I love the Cursive features so much, I can’t imagine switching anytime in the near future.)

Here’s a great video of Mark Seeman implementing the “fizzbuzz” program in three languages: C#, Haskell, and then Clojure. Note that he’s using a REPL to do the Clojure implementation, and it sure seems like he’s having more fun doing it than in the other languages! (He’s using a mostly abandoned editor called LightTable, which was groundbreaking when it was released.)

VIDEO

The Creations Amazing Clojure Community, Parting Thoughts, and What I’d Like To Write About In The Future
---------------------------------------------------------------------------------------------------------

I’ve found the Clojure community to be incredibly amazing and supportive. There’s a [Clojurian Slack Channel](http://clojurians.net/) that is incredible. The [Clojure/conj](https://clojure.org/events/2019/clojureconj) and other conferences tend to attract very experienced developers who share similar sensibilities. All these conferences tend to invite some of the most accomplished researchers and contributors in the programming domain.

An example: One of most amazing talks I’ve seen was from the 2016 Clojure/conj where Brian Goetz, architect for the Java language, talked about his stewardship of the Java ecosystem. What’s unmistakable & so admirable is his sense of responsibility to not break code that nine million developers have written.

VIDEO

Here’s a talk from Tiago Luchini on writing declarative domain models — after you watch this, you’ll never want to deal with a SQL or noSQL database again… and which is why I switched to using the Datomic database, from the same organization that brings us Clojure.

VIDEO

Some great learning aids for Clojure:

I recommend the following books to get up the speed on Clojure:

(I’ve bought almost every book on Clojure that I could find — I like everyone one of them.)

The work within the Clojure community is so interesting, I subscribe to the Planet Clojure RSS feed, which aggregates articles about Clojure and functional programming from many sources: [http://planet.clojure.in/](http://planet.clojure.in/)

I have a lot of enthusiasm to write in the future about the following, because it illuminates the First Ideas of Simplicity and Locality, and the Second Ideal of Focus, Flow, and Joy.

*   The Clojure programs I wrote to analyze writing patterns throughout development of _The Unicorn Project_.
*   My top twenty videos from the Clojure community that blew my mind.
*   My adventures in trying to learn static functional programming languages, like Haskell, and learning category theory — that’s been unexpectedly rewarding. This is the world of monoids, functors, applicative functors, and the monad.
*   Doing a screencast of analyzing the Stack Overflow 2019 Survey data to better understand the demographics of Clojure developers, and why they rank as the highest paid population.

1.  Thank you to Parker Matthew from Pivotal for cementing this connection for me in one of our many amazing conversations. It’s interesting to note the amazing tension and mutually supportive nature between Dr. Csikszentmilhali’s work, and the work of Dr. Anders Ericsson about deliberate practice, described in [“Peak: Secrets from the New Science of Expertise”](Peak:%20Secrets%20from%20the%20New%20Science%20of%20Expertise).  
    The dueling dynamic of “practice as a transcendental experience” vs. “practice as hard work and perseverance” is magnificently described in Dr. Sally Ducksworth book [“Grit: The Power of Passion and Perseverance”](https://www.amazon.com/Grit-Passion-Perseverance-Angela-Duckworth-ebook/dp/B010MH9V3W/) [↩](https://itrevolution.com/love-letter-to-clojure-part-1/#ffn1)
2.  The person who created the Strange Loop conference is Alex Miller, who is also a very prominent figure in the Clojure community. In another strange twist of history, Adrian Cockcroft ([@adrianco](http://twitter.com/adrianco)) told me that this was his favorite conference in 2014. I filed it away at the time.  
    Years later in 2017, I found myself devouring video after video from this conference — it is a magnificent program, a confluence of Papers We Love, static typers and category theorists, hackers working on amazing projects, and even DevOpsy things. I’ve been wanting to attend for the last three years, but had to cancel at the last minute each time.  
    2020 will be the year, I’m sure!!! [↩](https://itrevolution.com/love-letter-to-clojure-part-1/#ffn2)

  
  
from Hacker News https://ift.tt/2onOVPL