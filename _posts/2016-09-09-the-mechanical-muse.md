---
title: 'The Mechanical Muse'
date: 2020-01-12T13:47:00+01:00
draft: false
---

![](https://media.newyorker.com/photos/5c93e2efdec8304049bc43bc/16:9/w_1200,h_630,c_limit/Rockmore-AIpoetry.jpg "The Mechanical Muse | The New Yorker")  

The history of intelligent machines is one of moving goalposts: Sure, a machine can do this, but can it do that? The “that” is often an achievement that strikes us as strongly connected to emotion—that seems especially human. A robot that can clean the crumbs from your living room isn’t nearly as impressive, or scary, as one that can leave you with a lump in your throat.

Poetry is a good place to move the end zone: it’s rooted in the inspirational and the comical—the deeply human—and yet, in many of its forms, it edges toward the computational and algorithmic. Poetry even seems to have been implicit in the bold 1955 manifesto that first announced the field of artificial intelligence, declaring that “an attempt will be made to find how to make machines use language, form abstractions and concepts.” The pioneers of A.I. never mentioned poetry outright, but, if you squint, you might see its spirit in their ambitions to investigate the “rules” connecting human thought with word “manipulation” and in their efforts to explore the relationship between creativity and randomness—not to mention in their grander goal of creating machines that would “improve themselves.”

There are more resonances between programming and poetry than you might think. Computer science is an art form of words and punctuation, thoughtfully placed and goal-oriented, even if not necessarily deployed to evoke surprise or longing. Laid out on a page, every program uses indentations, stanzas, and a distinctive visual hierarchy to convey meaning. In the best cases, a close-reader of code will be rewarded with a sense of awe for the way ideas have been captured in words. Programming has its own sense of minimalist aesthetics, born of the imperative to create software that doesn’t take up much space and doesn’t take long to execute. Coders seek to express their intentions in the fewest number of commands; [William Carlos Williams](https://www.newyorker.com/contributors/william-carlos-williams), with his sparse style and simple, iconic images, would appreciate that. One poet’s “road not taken” is one programmer’s “if-then-else” statement. Generations of coders have taken their first steps by finding different ways to say “Hello, World.” Arguably, you could say the same for poets.

Many programmers have links to poetry—Ada Lovelace, the acknowledged first programmer ever, was Lord Byron’s daughter—but it’s a challenge to fully bridge the gap. Sonnets occupy something of a sweet spot: they’re a rich art form (good for poets) with clear rules (good for machines). Ranjit Bhatnagar, an artist and programmer, appreciates both sides. In 2012, he invented Pentametron, an art project that mines the Twittersphere for tweets in iambic pentameter. First, using a pronouncing dictionary created at Carnegie Mellon, he built a program to count syllables and recognize meter. Then, with a separate piece of code to identify rhymes, he started to assemble sonnets. For the first National Novel Generation Month (NaNoGenMo), in 2013, Bhatnagar submitted “I got a alligator for a pet!,” a collection of five hundred and four sonnets created with Pentametron.

Bhatnagar’s code required that each line be an entire tweet, or essentially one complete thought (or at least what counts as a thought on Twitter). It also did its best to abide by strict rules of meter and rhyme. This is how “Good night! Tomorrow is another day :)” (the titles are machine-written, too), begins:

> I pay attention to the little shit  
> yeah, teacher aren’t trying anymore… :)  
> Not even going to encourage it.  
> I never been in twitter jail before ….
> 
> Two people wanna be in my bio ?  
> I wanted some banana pudding to  
> Don’t be a menace is a classic tho  
> Know what’s amazing? Johnnie Walker Blue
> 
> Another day another dollar tho.  
> Tomorrow is another awesome day  
> She going hard and he’s complaining so  
> I never liked Sabrina anyway.
> 
> Fuck my retainer has a crack in it  
> This Maybelline mascara is the shit!!!

In Bhatnagar’s most recent collection of computer-assisted sonnets, “[Encomials](https://www.amazon.com/dp/1933996668/?tag=thneyo0f-20),” he relaxes these constraints. For a machine to produce work that sounded human-generated, Bhatnagar realized, he had to strike a delicate balance between accuracy and authenticity. “If it made too many mistakes, then it wouldn’t look human, so my hope was that it would be just enough mistakes,” he said.

On a whim, Bhatnagar looked in the debug logs of Pentametron, a repository of tweets that had been discarded because they were close to iambic pentameter but not perfect. Text in this trash heap had been stripped of punctuation and capitalization after being disposed. Bhatnagar built a new program to comb through this corpus and write sonnets with enjambed lines—that is, phrases that flow over naturally from one line to the next:

> I wanna be a little kid again.  
> I’m feeling kinda empty on the low.  
> You should unwind a little now and then.  
> Team Stacie looking like a sleepy hoe.
> 
> Back to the Sunshine State. The devil is  
> a lie. I hate myself a lot sometimes,  
> I mean, possessive, holy shit, this is  
> the second time. I’m always catching dimes.
> 
> I’m not the only one, I’m pinning this  
> again. I love a windy sunny day.  
> Not coming out until tonight. I miss  
> the happy me. I gotta find a way.
> 
> I always fall into the bullshit. Why?  
> Socks on in bed—the devil is a lie.

Bhatnagar’s algorithms use a clever mix of data mining and pattern matching to build sonnets from the dross of the Twittersphere. This is more poetry as collage than true composition. I’m hardly a poet, but, like many, I had early schoolroom experiences learning to write poetry. My wonderfully creative second-grade teacher, Mrs. Clack, had us spend all kinds of time doing special projects; it was the year I learned what a limerick was. I couldn’t get enough of [Edward Lear](https://www.newyorker.com/magazine/2018/04/23/the-sense-beneath-edward-lears-nonsense) in long form (“The Owl and the Pussy-Cat”) or short (“There was a Young Lady whose chin . . . ”), and, encouraged by Mrs. Clack, I tried my hand at making some little limericks of my own.

I loved the wordplay and also the formulaic nature of the composition; perhaps this was an early stirring of the mathematician and computer scientist I would become. A limerick is, in some sense, described by an algorithm: A Mad Lib–ish start (“There was a(n) \[old man / young lady\] \[from / with / who\] . . . ”), followed by five lines of prescribed meter in an aabba rhyme scheme. I ran this little poetry program in my head again and again, turning out dozens of nonsense limericks, complete with the requisite little-kid scatology. Years later, when Mrs. Snyder’s British-literature class introduced me to the sonnet, I once again took naturally to a poetic recipe, working the cadence of iambic pentameter into my head and creating satisfying doggerel in the ababcdcdefefgg template. I’ll spare you an example.

So, if kids can learn to write poems from scratch, what about machines? I was able to start composing after reading just a handful of examples. My brain—like the brains of most children—didn’t need much material to begin the process of mimicry. With machine learning, the latest A.I. technology, computers might finally be able to follow suit. But even the most sophisticated machine-learning techniques out there—the deep neural networks that are today’s most cutting-edge technology—need lots and lots of data in order to train, or become more accurate at a given task. The neural-network architecture, modelled and named after our own brain circuitry, has been a boon to tasks such as language translation (e.g. Google Translate) and image recognition (think picture tagging), largely owing to the ready availability of data: the Internet is full of words and photos for these neurons to train on _in silico_. But, in the absence of enough data, machines can’t begin learning in the first place. This is why the seemingly simple task of teaching a machine to compose a sonnet is such a complex programming feat; deep-learning machines need more inputs than the average school kid.

Kevin Knight, a computer scientist at the University of Southern California, was among the first researchers who studied how deep neural nets could be used to attack the challenges of translation. Knight’s general expertise is in natural language processing, the area of computer science that is all about generating and understanding human language. Without neural nets, even the best programs couldn’t write complete sentences. They could only string together bits of language. As Knight says, they “couldn’t keep a theme going. Couldn’t even keep the grammar going.”

In 2015, Marjan Ghazvininejad, one of Knight’s graduate students, began working on Hafez, a program used to generate sonnets and other poetic forms named after the fourteenth-century Persian lyricist. There were two parts to her project: first, codifying the rules for composition—the template that every sonnet would fit—then deciding what to put in the template. The first stage was easy: programmers are good at coming up with rules, and programs are good at following them. Plus, as Knight explained, Ghazvininejad’s team came up with some clever innovations, such as telling the computer to pick the last word of each line first, then plucking rhyming pairs that seemed topically similar.

But where would the words come from in the first place? Even though the world of lyrical poetry is data poor—there are only so many sonnets available on the Internet—Ghazvininejad and her collaborators realized that the nearby world of song lyrics is data rich. Her team decided to train their program on ninety-five thousand songs pulled from the Music Lyrics Database. For each poem, Hafez responded to a given topic—say, Presidential elections—then collected rhyming words from within the database and strung them together using its ever-improving neural networks.

Ghazvininejad had spent years studying language processing, but even she was impressed by the results. Hafez spat out one sonnet that included the phrase “Honky Tonkin Resolution.” According to Knight, the phrase appeared only once or twice in Google search results: Hafez was quite literally creating original work—and maybe was a child of the sixties.

Training also helped create coherence and style—that most elusive of human touches. One poem, generated from the prompt “wave,” has a sinister, futuristic feel:

> People picking up electric chronic.  
> The balance like a giant tidal wave,  
> Never ever feeling supersonic,  
> Or reaching any very shallow grave.
> 
> An open space between awaiting speed,  
> And looking at divine velocity.  
> A faceless nation under constant need,  
> Without another curiosity.
> 
> Or maybe going through the wave equation.  
> An ancient engine offers no momentum,  
> About the power from an old vibration,  
> And nothing but a little bit of venom.
> 
> Surrounded by a sin Omega T,  
> On the other side of you and me.

The diction here feels credibly consistent; “velocity,” “momentum,” and “vibration” all belong to a similar mathy register. “Divine,” “omega,” and “power” create another tonal through line. Moreover, there is a sense of thematic coherence, glimmers of narrative. And yet, although I’m no critic—just a reader—I can still tell there’s something off about it. I read it and find myself getting jammed rather than enjambed. I feel the presence of the machine, stuck in the literary uncanny valley.

It’s fair to ask: Does that matter?

As it turns out, Hafez was dreamed up and executed as a submission to the 2016 Turing Tests in the Creative Arts at Dartmouth, which I helped organize. A machine passes the Turing Test if it can prove itself to be indistinguishable from a human. Hafez’s challenge was to fool judges into thinking its sonnets had been written by real live poets. In the end, it did win the competition, but it didn’t pass the Turing Test. Hafez was better than the other machines but still distinguishable from a person. When the machine-written sonnets were interspersed among human-written works, there wasn’t a single A.I. poet that fooled a majority of the competition’s judges.

The Turing Test has long been a standard for assessing artificial intelligence, but, in the context of making art—rather than simulating consciousness—it may not be the most valuable, or the most interesting, metric. One of my colleagues, Mary Flanagan, a poet, artist, and professor of digital humanities, thinks the notion that machine-generated poems should be expected to pass the Turing Test is boring. “Humans are already good at producing human-sounding sonnets, so why get a computer to do that? Do something new!”

Flanagan’s reaction raises another question: Given the power of new techniques in artificial intelligence, why not think more broadly about the kinds of art one can make using it? We could think of “machine-generated” as a kind of literary G.M.O. tag—or we could think of it as an entirely new, and worthy, category of art. As we interact more and more with machines, both knowingly and unknowingly, our own expectations around both work and art will change, and labels will start to dissolve. The uncanny valley both widens and narrows as humans and writing gadgets evolve together. In fact, almost all the work we read—including poetry—is touched by machines. Some writers—just a few now, but surely more in the future—are using computers as creative collaborators. (If you’ve ever taken [Gmail’s suggestions](https://www.newyorker.com/tech/annals-of-technology/gmail-smart-replies-and-the-ever-growing-pressure-to-e-mail-like-a-machine) when crafting an e-mail, you, too, have been such a collaborator.) John Seabrook has [examined](https://www.newyorker.com/magazine/2019/10/14/can-a-machine-learn-to-write-for-the-new-yorker) what this artificial intelligence could mean for the future of everyday, utilitarian acts of writing. Last February, the OpenAI project, a multi-billion-dollar venture founded to promote “friendly” A.I., announced that its deep-learning program could complete sentences and even paragraphs. After paragraphs come essays, short stories, novels. Why not sonnets, too? If we stop assessing robots by their imitative powers—how close they get to mastering humanness—we might begin to appreciate their creative powers in a new light. We might even be moved by them.

In “[You Are Not a Gadget](https://www.amazon.com/dp/0307389979/?tag=thneyo0f-20),” Jaron Lanier, a virtual-reality pioneer and frequent philosophizer about the digital future, exhorts readers to resist the easy acceptance of technology as it is. Perhaps machine sonnet-making is part of that resistance, a literary cyberpunk movement, a Dada-esque move. As we explore the ways in which new high-tech tools seem familiar or jarring, we continue to discover aspects of what it means to be human, as writers and readers, creators and consumers. Can a machine write poetry? What is poetry? The goalposts move again.

  
  
from Hacker News https://ift.tt/2s1Qu7H