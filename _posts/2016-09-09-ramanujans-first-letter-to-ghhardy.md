---
title: 'Ramanujan’s First Letter to G.H.Hardy'
date: 2020-01-13T04:47:00+01:00
draft: false
---

![](https://miro.medium.com/max/1000/1*LNVVywVtXt_bOY_NXi400g.png "Ramanujan’s First Letter to G.H. Hardy - Cantor’s Paradise - Medium")  

**Left**: One of few surviving photographs of Ramanujan. **Right**: The text of Ramanujan’s cover letter.

Ramanujan’s First Letter to G.H. Hardy
======================================

On or about the 31st of January 1913, mathematician [G.H. Hardy](https://en.wikipedia.org/wiki/G._H._Hardy) of Trinity College at Cambridge University received a parcel of papers from Madras, India which included a cover letter from an aspiring young Indian mathematician by the name of [Srinivasa Ramanujan](https://en.wikipedia.org/wiki/Srinivasa_Ramanujan) (1887–1920). The cover letter discussed three topics:

1.  An introduction of Ramanujan and his precarious situation;
2.  A claim about the domain of the gamma function; and
3.  A claim about the distribution of prime numbers;

This essay provides an overview of the mathematical content of Ramanujan’s first letter, as well as Hardy’s reaction and response.

The Cover Letter
================

Ramanujan’s letter may be divided into four paragraphs, covering essentially three topics: 1. An introduction of who he is; 2. A discussion of the gamma function for negative and fractional values; and 3. A discussion of the distribution of prime numbers.

The First Paragraph
-------------------

> Dear Sir,
> 
> I beg to introduce myself to you as a clerk in the Accounts Department of the Port Trust Office at Madras on a salary of only £20 per annum. I am now about 23 years of age. I have had no University education but I have undergone the ordinary school course. After leaving school I have been employing the spare time at my disposal to work at Mathematics. I have not trodden through the conventional regular course which is followed in a University course, but I am striking out a new path for myself. I have made a special investigation of divergent series in general and the results I get are termed by the local mathematicians as "startling".

As Kanigel (1991) writes, such an introduction was perhaps intended to incite both pity and wonder in Hardy, then 36 years old and generally recognized as the leading English pure mathematician of his time (Berndt & Rankin, 1995).

The Second Paragraph
--------------------

By the second paragraph however, Ramanujan was already getting to the point of his inquiry by suggesting that he could give meaning to negative values of the so-called [gamma function](https://medium.com/cantors-paradise/the-riemann-hypothesis-explained-fa01c1f75d3f):

> Just as in elementary mathematics you give a meaning to aⁿ when n is negative and fractional to conform to the law which holds when n is a positive integer, similarly the whole of my investigations proceed on giving a meaning to Eulerian Second Integral for all values of n. My friends who have gone through the regular course of University education tell me that

> is true only when n is positive. They say that this integral relation is not true when n is negative. Supposing this is true only for positive values of n and also supposing the definition

> to be universally true, I have given meanings to these integrals and under the conditions I state the integral is true for all values of n negative and fractional. My whole investigations are based upon this and I have been developing this to a remarkable extent so much so that the local mathematicians are not able to understand me in my higher flights.

Ramanujan is referring to the [analytic continuation](https://en.wikipedia.org/wiki/Analytic_continuation) of the gamma function, despite seemingly having no knowledge of the well-known technique’s existence. Yet still, his definition of Γ(n) is precisely what one obtains if he had known of it (Berndt & Rankin, 1995).

The gamma function Γ(n) Ramanujan referred to has been an important object of study since the problem of extending the factorial function to non-integer arguments was studied by Daniel Bernoulli and Christian Goldbach in the 1720s. It is an extension of the factorial function _n_! (1 x 2 x 3 x 4 x 5 x …. _n_), shifted down by 1:

Its plot is very curious:

The Gamma Function Γ(z) plotted in the range -6 ≤ z ≤ 6

Here shown as the function of a variable z. Even 50 years before Ramanujan’s time the gamma function was known to be defined for all complex values of _z_ larger than zero. Complex numbers, as you probably know, are a class of numbers with an _imaginary part,_ written as Re(_z_) + Im(_z_), where Re(_z_) is the real part (ordinary real number) and Im(_z_) is the imaginary part, denoted by the letter _i_. A complex number is typically written in the form _z = σ + it_ where sigma _σ_ is the real part and _i_t is the imaginary part. Complex numbers are useful because they allow mathematicians and engineers to evaluate and work on problems where ordinary real numbers will not allow it. Visualized, complex numbers extend the traditional one-dimensional “number line” into a two-dimensional “number plane”, called the _complex plane,_ in which the real part of a complex number is plotted on the x-axis and the imaginary part is plotted on the y-axis (Veisdal, 2016). In order to be able to use the gamma function Γ(z), it is typically rewritten to the form:

The functional relationship of the gamma function Γ(z)

Using this identity, one can obtain values for z below zero. It does not however give values for negative integers, as they are not defined (technically they are singularities, or simple poles). This is where analytic continuation comes in, and where Ramanujan’s first investigation had taken him.

The Third Paragraph
-------------------

> Very recently I came across a tract published by you styled Orders of Infinity in page 36 of which I find a statement that no definite expression has been as yet found for the number of prime numbers less than any given number. I have found an expression which very nearly approximates to the real result, the error being negligible. I would request you to go through the enclosed papers.

Ramanujan in this third paragraph goes on to address the seemingly completely separate issue of [the distribution of prime numbers](https://medium.com/cantors-paradise/the-riemann-hypothesis-explained-fa01c1f75d3f) (although, the two topics are actually related, [as shown](https://medium.com/cantors-paradise/the-riemann-hypothesis-explained-fa01c1f75d3f) by Bernhard Riemann in his 1859 paper _Ueber die Anzhal der Primzahlen unter einer gegebenen Grösse,_ “On prime numbers less than a given magnitude”).

Ramanujan’s claim about finding an expression for the number of prime numbers less than a given number had also been tackled before, perhaps most prominently by four mathematicians: [Gauss](https://en.wikipedia.org/wiki/Carl_Friedrich_Gauss), [Legendre](https://en.wikipedia.org/wiki/Adrien-Marie_Legendre), [Dirichlet](https://en.wikipedia.org/wiki/Peter_Gustav_Lejeune_Dirichlet) and [Riemann](https://en.wikipedia.org/wiki/Bernhard_Riemann). A prime counting function π(n) gives the number of primes less than or equal to a given real number. Given that there is no known formula for finding primes, the prime counting formula is known to us only as a plot, or _step function_ increasing by 1 whenever _x_ is prime. The plot below shows the function up to x = 200 (Veisdal, 2016):

The prime counting function π(x) up to x = 200

Gauss considered the question of how many primes there below a given number when at the age of 15 or 16 in 1792–93. Legendre slightly later, in 1797–98 conjectured (based on prime number tables by [Felkel](https://en.wikipedia.org/wiki/Anton_Felkel) and [Vega](https://en.wikipedia.org/wiki/Jurij_Vega)) that a [prime counting function](https://en.wikipedia.org/wiki/Prime-counting_function) π(n) is approximated by the function

where A and B are unspecified constants. He later approximated them to be A = 1, B = -1.08366. Both Gauss and Legendre’s prime-counting functions imply what is known as the [prime number theorem](https://en.wikipedia.org/wiki/Prime_number_theorem), namely that:

Which in English states “As x goes to infinity, the prime counting function π(x) will approximate the function x/ln(x)”_._ In other words, if you count high enough, and plot the number of primes up to a very large number _x,_ then plot _x_ divided by the natural logarithm of _x_, the ratio between the two will approach 1. The two functions are plotted below for x = 1000:

The prime counting function π(x) and the estimate from the prime number theorem plotted up to x = 1000

Dirichlet later formulated his own approximation, which is better than that provided by Legandre and Gauss, known now as the [logarithmic integral function Li(x)](https://medium.com/cantors-paradise/the-riemann-hypothesis-explained-fa01c1f75d3f):

Plotting this function alongside the prime counting function and the formula from the prime number theorem, we see that Li(x) is actually a better approximation than x/ln(x):

The logarithmic integral function Li(x), the prime counting function π(x) and x/ln(x) plotted together

As pointed out by Berndt & Rankin (1995), Ramanujan’s claimed approximation for the prime counting function π(x) were much less precise than he believed, but still remarkable given his limited access to existing theory.

The Fourth Paragraph
--------------------

> Being poor, if you are convinced that there is anything of value I would like to have my theorems published. I have not given the actual investigations nor the expressions that I get but I have indicated the lines on which I proceed. Being inexperienced I would very highly value any advice you give me. Requesting to be excused for the trouble I give you.
> 
> I remain, Dear Sir, Yours truly, S. Ramanujan

In the pages that followed Ramanujan’s one-page cover letter, the Indian mathematician would go on to provide at least 11 more pages (at least two of which are now lost) containing technical results in topics ranging from work on infinite series and the gamma function, the [distribution of prime numbers](https://en.wikipedia.org/wiki/Prime_number_theorem), [hypergeometric series](https://en.wikipedia.org/wiki/Hypergeometric_function), [continued fractions](https://en.wikipedia.org/wiki/Continued_fraction), [elliptic functions](https://en.wikipedia.org/wiki/Elliptic_function), [Bromwich’s infinite series](https://en.wikipedia.org/wiki/1_%2B_2_%2B_3_%2B_4_%2B_%E2%8B%AF), divergent functions, a discussion of the [Bernoulli numbers](https://en.wikipedia.org/wiki/Bernoulli_number) and more.

Hardy’s reaction
================

> Certainly the most remarkable \[letter\] I have ever received, its author a mathematician of the highest quality, a man of altogether exceptional originality and power.

Ramanujan’s letter would be the first of numerous written communications between himself and G.H. Hardy, which would culminate in the invitation by Hardy for Ramanujan to come to Trinity College, Cambridge to work with him, which Ramanujan did in 1914.

Left: G.H. Hardy. Right: The first page of Hardy’s response letter.

Upon receiving the Ramanujan’s first letter however, Hardy was initially skeptical. As Kanigel (1991) writes:

```
_"For Hardy, Ramanujan's pages of theorems were like an alien forest whose trees were familiar enough to call trees, yet so strange they seemed to have come from another planet; it was the strangeness of Ramanujan's theorems that struck him first, not their brilliance. The Indian, he supposed, was just another crank."_\- Excerpt, The Man Who Knew Infinity by Robert Kanigel (1991)
```

However, after having _“put the manuscript aside and lost himself in the day’s London Times”, “set to work on mathematics, kept at it until about one, then ambled over to Hall for lunch”_ and next been _“off to the university courts on Grange Road for a game of “real” tennis”_ (Kanigel, 1991),

> “The Indian Manuscript scraped and tugged at his composure with, as Snow (1966) wrote, its “wild theorems. Theorems such as he had never seen before, nor imagined”.

After going back to read Ramanujan’s manuscripts again and seeing his [theorem on continued fractions](https://en.wikipedia.org/wiki/Rogers%E2%80%93Ramanujan_continued_fraction) on the last page, Hardy is to have said that they “_defeated me completely; I had never seen anything in the least like them before”._ He asked his colleague and collaborator [J. E. Littlewood](https://en.wikipedia.org/wiki/John_Edensor_Littlewood) (1885–1977) to take a look at the papers. Littlewood’s reaction was amazement at the Indian’s genius, leading Hardy to conclude that the letter was _“certainly the most remarkable I have received”_ and that Ramanujan was _“a mathematician of the highest quality, a man of altogether exceptional originality and power”_ (Hardy, 1920).

[Bertrand Russell](https://en.wikipedia.org/wiki/Bertrand_Russell) (1872–1970) later wrote that by the next day he _“found Hardy and Littlewood in a state of wild excitement because they believed they had found a second Newton, a Hindu clerk in Madras making 20 pounds a year”_.

  
  
from Hacker News https://ift.tt/2ThewXi