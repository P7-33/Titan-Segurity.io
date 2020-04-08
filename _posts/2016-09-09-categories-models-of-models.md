---
title: 'Categories: Models of Models'
date: 2019-10-12T03:38:00+01:00
draft: false
---

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/v1503704344/sequencesgrid/h6vrwdypijqgsop7xwa0.jpg "Categories: models of models - LessWrong 2.0")  

Let me clarify what I mean when I say that math consists of nouns and verbs. Think about elementary school mathematics like addition and subtraction. What you learn to do is take a bunch of nouns—1, 2, 3, etc.—and a bunch of verbs—addition, subtraction—and make sentences. “1 + 2 = 3.”

When you make a sentence like that, what you're doing is taking an object, 1, and observing how it changes when it interacts—specifically, adds—with another object, 2. You observe that becomes a 3. Just like how you can observe a person (object) bump their head (interaction) into a wall (other object) and the corresponding change (equals sign): the bluish bump emerging on their forehead.

Well, it turns out that no matter how far you go in math, you’re still taking objects and observing how they change when they interact with other objects. You learn about other kinds of numbers like 2.5 and 3.333 repeating, and other kinds of interactions like multiplication and division.

Eventually things start getting more abstract. You learn about matrices and the kinds of interactions they can have. You learn about sets and functions in a deep way. Complex numbers, topologies, etc.

But you never get away from nouns and verbs.

What are we going to do with all of these nouns and verbs? Well, at some point, when you have a bunch of things that feel similar in an important way, you often want to take a step back, lump all of the individual things together, and talk about them _in general_. Why do we have the concept of fruit? Because we live in a world where apples, oranges, lemons, papayas, etc., exist.

Why do we have the concept of numbers? Because we have a bunch of them, not just 1, 2, and 3, but also 2.5, 3.333 repeating, irrational numbers, and even complex numbers. Why do we have the concept of “operations?” Because we have addition, subtraction, multiplication, and division. Even though all of these give you very different answers for the same input of numbers, (1 + 2 does not equal 1 - 2 does not equal 1 times 2 does not equal 1 divided by 2), they still have something very similar in common, so it’s worth coming up with the concept of “operation” to study them independently of their individual characteristics. Just like how we can talk about “fruit” without having to reference the shape of an apple.

If you lived in a world with only apples, you wouldn’t have the concept of fruit. If you lived in a world where the only kind of thing was a rock, you wouldn’t have the concept of nouns. If you lived in a world where the only kind of math-thing was numbers, category theorists wouldn’t have come up with the concept of objects. (They wouldn't have come up with category theory at all!)

And what is the use of generalization? A bird’s-eye view of something lets you see things from new perspectives, potentially changing your concept of the thing entirely. When you think of numbers as various ways you can count stuff on your fingers, you can inch your way past the natural numbers to negatives, fractions and irrational numbers. But complex numbers will throw you for a total loop—they just don’t seem to be relatable to “amounts of things” in a way that you’re ever likely to see in the world.

In fact, complex numbers made no sense to me until I learned what numbers _[actually are](https://en.wikipedia.org/wiki/Field_(mathematics))_, at which point everything clicked into place. The generalization helped me understand the specific case—complex numbers are just another type of number, like how apples are just another type of fruit.

_Generalization_ _is helpful when life stops throwing convenient examples at you._

For example, say you want to grow new kinds of fruit that have never existed. Having a concept of fruit is _necessary_ to conceiving of that idea. Life's not going to give you examples of fruit that have never existed! You have to explore the conceptual space of all fruit.

(In fact, this experience with complex numbers, years ago, probably inspired these posts. I got the idea that if you just bothered to take a _really long time_ to explain the mathematics, the average person could probably grasp quantum physics. This series is the category-theory version of that original idea.)

Category theory exists for the same reason the concept of fruit does: there are lots of individual things that have certain commonalities that make generalization an appealing idea. Apples and oranges are very different on the surface and very similar deep down. Natural numbers and complex numbers are very different on the surface and very similar deep down.

Category theory goes one step wider. It emerges when people look at entire fields of math like “algebra” and “topology” and notices that, while they’re very different on the surface, they seem to be very similar deep down. Many other fields of mathematics seemed to also share these deep similarities, and so gradually they all became mere examples of the generalization, that generalization being a _category_. (A category being something we'll define by the end of this post.) Just like how apples and oranges become mere examples of the generalization that is “fruit.”

And one of those commonalities is that all of these superficially disparate fields of mathematics study _things_ and _interactions between those things._ I.e., they study objects and morphisms.

That might sound really general. And it is! And yet, just like with the general definition of fields that lets us understand complex numbers, we can learn really interesting things from this super-general perspective. (Specifically, the Yoneda lemma and adjunction.)

But right now you are having to take my word for the idea that many different fields of math can be thought of as studying “nouns and verbs.” So let’s look at things from a different perspective.

Even if you don’t know higher maths, you probably know things like, “pouring milk in my cereal will make my cereal soggy.”

So “milk + cereal = soggy cereal.” Seems awfully..._mathematical_.

Why does math exist, anyway? Well, there’s lots of ways to answer that question, so let’s rephrase it: why do _mathematicians_ exist? Or even better, why do mathematicians get _paid_? It certainly isn’t for the joy of doing math. Instead, “mathematician” is a job that you can actually get paid to do because math is very useful for modeling our reality.

So why does math boil down to objects and morphisms so often? Probably for the same reason English boils down to nouns and verbs: we use language to discuss reality, and reality seems to boil down to nouns and verbs.

Take birds, for example. They _are_ birds, so they’re nouns (objects). And they do stuff like fly, tweet, lay eggs, eat, etc. I.e., verbs (morphisms).

Whatever you may or may not know of maths, you definitely know a thing or two about reality. You’ve been living in it your whole life.

The rest of this post will take common sense ideas about creating models of our reality, break them down into their most abstract components, and end up with some simple rules that any model should follow. We’ll discover that those components and rules are _exactly_ the components and rules that define a category.

\*\*\*

You know a lot of models, even if most of them would never make it into a textbook. You use these models to navigate reality.

For example, a sentence like "Alice pushes Bob" is a model of reality. By themselves, those letters in that order are meaningless. But because you can use them to make predictions (specifically, you're inferring the speaker's state of mind), the sentence is correspondingly a model of (that particular part of) reality.

Sentences themselves exist, so we can model them too. You can think of a sentence structure as a way of modeling a sentence. As for models themselves, a model is a way of abstracting away from some details of whatever you're studying so that other features become more salient. For example, you can model a specific cat, Mr. Peanuts, as just a cat, neglecting specific features like his name, his color, etc., so that other, more general features of cats, like the tendency to meow, eat tuna fish, and utterly despise humans become more salient.

That is to say, what will Mr. Peanuts do in \[specific situation\]? Hard to say unless you know him personally. But if we ask, "What will _a cat_ do in \[specific situation\]?" you might have a decent guess. The cat's not going to start barking, for one.

You have a model of cats inside your head, and this lets you make predictions, at the expense of specificity.

Sentence structure models specific sentences like "Alice pushes Bob" in terms of their abstract components: "Noun verbs noun."

You might be surprised to learn that you can make predictions with sentence structure. For example, one of the rules of grammar is that a prepositional phrase ends with a noun. So let's say I ask you, "Who will the soccer player kick the ball to?" You don't know the answer—I haven't even given you a list of people to choose from.

Let's also say that you don't know what the word "who" means, so you don't even know what I'm asking. In fact, let's say you don't know what _any_ of the words in the sentence means, only their parts of speech. You certainly aren't going to give the specific answer I'm looking for.

But you do know sentence structure! You know that "to" is a preposition, so the phrase it opens up must end with a noun.

So who is the soccer player going to kick the ball to? Answer: a person, place, or thing—a noun.

This is not a brilliant answer. But it _is_ an answer—a correct one, in fact! This super abstract model of sentences let you figure things out even when you didn't know what any of the specific words meant.

So sentences are models, and sentence structure is a model of a model, and models are really useful: they let you predict things.

But sentence structure is a model of just one kind of model—sentences themselves. What if we wanted a model of all kinds of different models—sentences, sentence structure, scientific models, models from sensory data, mathematical models, everything? What if we wanted to model _modeling itself_?

Why, we'd turn to category theory.

So what are the _general qualities_ of _all models_?

First of all, every model has things—_objects_—and actions that the objects to do other objects—_morphisms_. For example, you can model a person by seeing them. That is to say, you hit them with some photons and form a picture of them based on the result. Every model is ultimately found in how one object changes another object—hence the term "_morph_ism."

(Notice how sentences, which themselves boil down to nouns and verbs, can be thought of as models of anything. After all, it's hard to imagine any kind of phenomenon that can't be expressed in a sentence, even if you have to make up some new words to do it. Effectively, the reason we use category theory to form models of models of everything instead just sticking with English is because we can define our category as obeying certain rules or axioms that correspond to how models ought to work, while English can say pretty much anything. The rest of this post discusses these rules.)

So categories—models of models—consist of objects and morphisms. But what are the _rules_ we require our objects and morphisms to obey so that they match up with our ideas of how models of reality ought to work? One is that every object ought to be, in some sense, a _perfect_ model of _itself_.

Think about what models do: they transform how we view objects. If I tell you someone is a murderer, this changes how you view them because you apply a different model. Loosely, you could say that you apply the "murderer" morphism to the person in question. Well, every object ought to have a model that you can apply that doesn't transform the object at all—_not_ because you aren't transforming, but because there's _no effect_, like multiplying by 1. For example, if you apply the "Mr. Peanuts" morphism to Mr. Peanuts, this shouldn't change anything: Mr. Peanuts is already Mr. Peanuts. This morphism is, in a certain clear sense, the _identity_ of Mr. Peanuts.

So perhaps unsurprisingly, in category theory, we say that _every_ object has an _identity morphism_ that "does nothing." For an arbitrary object A, its identity morphism is written 1A. That's because it's like multiplying by 1—you _are_ multiplying, it's just that nothing changes. (But just like multiplying both sides by 1 helps you solve equations, the identity morphism is extremely useful.)

What does it actually mean, mathematically, for the identity morphism to "do nothing?" To answer that, let's look at another requirement we'd expect of a general model of models: _compositionality_.

Say Alice pushes Bob, and Bob bumps into Charles. Let's diagram this as Af→Bg→C. Hopefully the interpretation of this diagram is obvious. We could say that Alice affects Bob, and Bob affects Charles—that is to say, Bob's state is a model of Alice's action on Bob, and Charles's state is a model of Bob's action on Charles. (I know we used p to stand for push last time, but f and g are the typical "generic morphism" symbols in category theory, and it's better to get used to using generic symbols than trying to name them after things all the time. Here, f is Alice pushing Bob, and g is Bob bumping into Charles.)

But we also might have an intuition that Alice affects Charles. Sure, she does so indirectly through Bob, but clearly Charles's state is a model of Alice's actions—actions which are in some sense actions _on Charles_.

That is to say, Alice pushed Charles just as clearly as she pushed Bob.

_Effect flows through_. We're all just models of the original state and laws of the universe, whatever they were. So whenever we have something like Af→Bg→C, we should really expect to also have something like Ah→C. Moreover, this morphism h should be _equal_ to what happened when Alice pushed Bob and then Bob bumped into Charles. After all, that _is_ what Alice did to Charles.

Let's use the symbol ∘ to mean "following." So if we write g∘f , that reads as "g following f." (Yes, that means you read it right to left, in effect. Get used to it, every field has at least one counterintuitive piece of notation.) We would then say that h\=g∘f. More to the point, the idea is that _whenever_ you have something that looks like Af→Bg→C, _regardless_ of what these objects and morphisms are meant to stand in for, then you _necessarily_ have Ah→C such that h\=g∘f.

[This is what composition looks like as a diagram. (The backwards E means "there exists," and the dotted line, redundantly, means the same thing.)](https://imgur.com/VqPjHsY)

An example of ∘ that you are hopefully familiar with is function composition. (We'll cover it in another post anyway.) Say you have 2x2. You should know how to evaluate this: first, square the x, then multiply it by 2.

Let's see how this is exactly like what we did before. You can see it like this: say that f stands for the action of squaring the x (it's a transformation—a morphism). And the other morphism g stands for multiplying it by 2.

f\=x2

g\=2x

If you're given the problem of determining what you have if you do g following f, you can write that like g∘f. Plugging in the actual equations, you are told to "multiply x by 2 following squaring x." [Which is exactly what you did](https://imgur.com/LuUbGab).

If you were told to determine f∘g instead, you should be able to see that this tells you to "square x following multiplying x by 2." I.e., (2x)2.

The symbol ∘ in fact tells you that you are composing one morphism with another (exactly how composition works is defined by the category), and the requirement that Af→Bg→C implies Ah→C such that h\=g∘f is called compositionality. _Every_ category has a rule of composition.

Composition is the real action of any category. If you know the rule of composition, you know how the category works internally. (Think about the concept of the laws of physics, the view of the world as a chain of events such that we can predict our current state from the Big Bang. Understanding that rule of composition is the theory of everything, the holy grail of physics.)

Now that we know what composition is, we can use it to rigorously define how the identity morphism "does nothing." Suppose you have an object A and the identity morphism 1A. Say you also have a morphism f:A→B. Since B is an object, it has an identity morphism as well, 1B.

The identity morphism 1A is a morphism "on A"—what does that mean? It means that 1A goes from A to A. It goes nowhere, in effect—just what we'd expect of an identity morphism.

So we have a morphism 1A:A→A. We also have a morphism f:A→B, as stated. Well, look at this! According to the rule of composition, we must have a morphism h:A→B such that h\=f∘1A.

But we already had a morphism going from A to B, f itself. The identity morphism does nothing, so it shouldn't have any effect on what we already had. This is _precisely_ defined by the following condition:

f∘1A\=f.

That is to say, doing f after doing 1A is the same as just doing f. Composing by 1 is just like multiplying by 1.

And notice we also have 1B:B→B. And since we still have f:A→B, we again have a rule of composition saying that we have a morphism going from A to B that is equal to 1B∘f.

What is this morphism? Again, 1B does nothing, meaning that 1B∘f\=f.

Basically, if you give a nut to a bird, and the nut _is_ the nut, that's the same as just giving a nut to a bird. Similarly, if you give a nut to a bird, and the bird _is_ the bird, that's just the same as giving a nut to a bird. Brilliant, I know, but sometimes math is about piling up trivialities until something profound emerges.

There's one last rule we'd expect any model to obey. Let's take again the sequence of events where Alice pushes Bob, and Bob stumbles into Charles. _Temporally_, Alice pushed Bob before Bob ran into Charles. But logically, we should be able to study the events out of order: we should be able to study Bob's motion into Charles, and then look backwards in time to study Alice pushing Bob. (Just like how we can study Alice pushing Bob before we look backwards in time to see how the Big Bang pushed Alice into pushing Bob.)

This ability to study the events out of order as long as ultimately put things together in the right order is called _associativity_. You might be familiar with this in terms of the associativity of multiplication, for example. Because (2×3)×4\=2×(3×4),we say that multiplication is associative.

Let's add David into the equation, so that we have a path like Af→Bg→Ci→D. We have a new composition Ai∘g∘f−−−→D. Associativity would tell us that

(i∘g)∘f\=i∘(g∘f).

Indeed, in any category, the rule of composition must be associative. This should be interpreted as saying that we study at any individual interaction out of order, as long as we don't forget what the order actually was! (Why "study?" Because we're modeling models, and models are for studying reality.)

You could think of associativity this way: Say you're planning a trip from North America to Europe to Asia. Associativity says that you can think about the trip from Europe to Asia before you think about the trip from North America to Europe so long as you remember to leave from North America when it's time to take the trip!

And...we're done. We have the rules we'd expect any model to obey. And, not coincidentally, we now have the rules we'd expect any _model of models_ to obey—the rules that define a category.

**Definition**: a _category_ C is a mathematical structure consisting of

i) a bunch of objects written A,B,C, etc.

ii) a bunch of morphisms written f,g,h, etc., which obey some rules.

Rule 1: Every morphism goes "from" an object in the category C "to" an object in the category C. The "from" object is called the _domain_ and the "to" object is called the _codomain_. (This should sound similar from learning about functions—functions are just a type of morphism; functions have a domain and codomain because all morphisms do.) For example, if you have a morphism f:A→B, then A is the domain of f and B is the codomain of f.

Rule 2: The category C must have a rule of composition such that, if the domain of one morphism in C is the codomain of another morphism in C, then there is a way of composing the two morphisms to get a single morphism extending from the domain of the latter morphism to the codomain of the former morphism such that this new "composite" morphism is equal to the composition of the latter morphism following the former morphism. E.g., if you have morphisms f:A→B and g:B→C, then you necessarily have h:A→C such that h\=g∘f.

Rule 3: Every object in C has an _identity morphism_ going from itself to itself that does nothing. For an arbitrary object A in C, the identity morphism is written 1A:A→A. The identity morphism "does nothing" in the sense that composing it with other morphisms is the same as just doing the other morphism.

Rule 4: Composition is _associative_. Associativity means that if you have a chain of compositions i∘g∘f, then it is always true that (i∘g)∘f\=i∘(g∘f).

Why are there so many rules for morphisms, and none really for objects? We'll explore in a few posts from now the idea that categories are all about the morphisms. Basically, we'll explore the idea that an object is totally defined by what it _does_ and what is _done_ to it—i.e., all the morphisms it is a part of.

Coming up next are examples of categories. This next post should hopefully both clarify the claim that category theory generalizes different fields of mathematics and also help make the concept of a category much more concrete. Afterward, we'll talk about a very important type of category, the category of sets and functions, and then a series of posts on both conceptual matters and enhancing our mathematical understanding of categories.

  
  
from Hacker News https://ift.tt/30U1kIc