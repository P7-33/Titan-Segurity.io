---
title: 'Texas Instruments’ Speak and Spell'
date: 2019-11-01T07:42:00+01:00
draft: false
---

![Texas Instruments’ Speak & Spell](https://spectrum.ieee.org/image/MzM5MDg4NQ.jpeg)

Photo: SSPL/Getty Images

**Proto-Digital Signal Processor:** Texas Instruments’ Speak & Spell prompted its user to spell a word by synthesizing the sound of the word. The user would then try to spell the word using the small keyboard. The original model, released in 1978, had a jazzy blue vacuum fluorescent display and ran on four “C” cells.

Before the [Speak & Spell](http://hackeducation.com/2015/01/13/speak-and-spell) was introduced, hardly anybody other than the four engineers who developed it thought it _should_ be introduced. [Texas Instruments](http://www.ti.com/) management saw little value in the project. When the four described it to one of the nation’s top experts in spelling education, he essentially advised them to kill it. When they test-marketed it, parents were dismissive.

But Paul Breedlove, Gene Frantz, Larry Brantingham, and Richard Wiggins were having fun building it, and didn’t want to stop. They somehow forgot to mention to TI management that they had encountered surprising antipathy to the idea, even where one might have expected warm endorsement. Fortunately for them, though, it just so happened the Speak & Spell was the only consumer-targeted project at TI at that particular moment that was within its budget (two of the others were a CB radio and a home computer).

Well, _almos__t_ within budget. In an interview, Frantz recalls that it’s just possible the team may have neglected to properly expense a few things to keep the official cost tally low. But these things happen, don’t they?

The basic idea for an educational spelling toy was Breedlove’s. Breedlove just happened to have been in _several_ right places, all at the right times.

Breedlove and Frantz had participated in the development of Little Professor, a calculator-with-a-twist that TI introduced in 1976. Educators at the time considered the use of calculators in the classroom to be cheating. TI, then and now one of the world’s biggest makers of calculators, tried to get over that objection and crack the education market by creating a calculator that presented equations lacking their solutions; students had three chances to type in the correct answer.

Breedlove also had a daughter who was learning to spell, and it occurred to him that there was a basic similarity between teaching math and teaching spelling. With math, you present an equation and the student has to solve it; with spelling, you enunciate a word and the student has to spell it. A spelling toy would differ in that the words would have to be spoken aloud. That would obviously require technology that converted stored words to audible speech. Such technology did exist then, but it was costly and would have made any product in which it was used far too expensive for the consumer market.

But Breedlove, who had recently done a stint in TI’s speech-research lab, knew that workers in that lab, and probably elsewhere, were on the verge of creating affordable speech-synthesis tech. Even so, there was yet another hurdle, which was that the speech-synthesis capabilities for this spelling toy would require an amount of memory then considered ridiculous.

He didn’t let it deter him. Instead, he started assembling a team by recruiting Frantz to be the system designer. Breedlove knew Wiggins from the speech-processing lab; conveniently, Wiggins was between projects. Wiggins was good friends with Brantingham, an IC architect, and suggested him for the team. Breedlove then went to TI management to get funding.

They were never going to get funding from the regular R&D budget, Frantz explains, because the risk for the proposed product was too high and the potential return was too low. But TI had a second source of funding for “wild hair” ideas. Alas, the spelling device was too risky for even that. The last-resort option was something called the idea program. All you had to do was convince a senior TI technologist to back it. Breedlove found such a person to sign off on his proposal, and the team got US $25,000 to work with (roughly $100,000 in 2019 dollars).

![The Speak & Spell designers: [from left] Gene Frantz, Richard Wiggins, Paul Breedlove, and Larry Brantingham.](https://spectrum.ieee.org/image/MzM5MDkxMQ.jpeg)

Photo: Gene Frantz/Texas Instruments

**Toy Story:** The Speak & Spell was designed by \[from left\] Gene Frantz, Richard Wiggins, Paul Breedlove, and Larry Brantingham.

They started work in early 1977. Their design called for three new chips: a controller, “huge” ROMs, and a [single-chip speech synthesizer](https://spectrum.ieee.org/tech-history/silicon-revolution/25-microchips-that-shook-the-world), which did not then exist. Initially designated [TMC0281](https://spectrum.ieee.org/tech-history/silicon-revolution/chip-hall-of-fame-texas-instruments-tmc0281-speech-synthesizer), the synthesizer chip would be the world’s first.

The Speak & Spell would ultimately incorporate a pair of 128-kilobit ROM chips. The state of the art at the time was 16 kb.

The synthesizer was based on a technique for coding speech called [linear predictive coding](https://www.researchgate.net/publication/3321695_The_history_of_linear_prediction) (LPC). LPC let the device generate the speech signal for an entire word from a relatively small amount of data, much smaller than what would have been required to simply store digitized recordings of the words themselves. The idea to use LPC, which was cutting edge at the time, [came from Wiggins](http://www.vintagecomputing.com/index.php/archives/528/vcg-interview-richard-wiggins-talks-speak-spell), whose specialty was voice-processing algorithms, and who held a doctorate in applied math from Harvard and had previously worked at the Mitre Corp. Wiggins was acquainted with some of the pioneers of LPC, which was then starting to find commercial applications after being developed in the 1960s at Bell Labs in New Jersey, and at Nagoya University and NTT in Japan.

The synthesizer chip ran digital signal processing logic, although it was not itself a DSP. Wiggins and Brantingham specified and designed the chip entirely by themselves and without any approvals from anyone, according to Frantz. TI management had neglected to fit the project into any particular reporting structure, and that suited the four team members just fine. In Frantz’s estimation, the lack of “help” from management gave Wiggins and Brantingham the freedom they needed to figure out a successful design. “They made the appropriate compromises to get that puppy to work,” Frantz says.

The team also had a choice of process technologies. In addition to complementary metal-oxide-semiconductor (CMOS) technology, its predecessors were available. Negative-channel metal-oxide semiconductor (NMOS) was still widely used in those days. Much less common, and much less fast, was positive-channel metal-oxide semiconductor (PMOS).

“NMOS was high-performance at the time,” Frantz explains. “We did it in PMOS, which was…_not_ high-performance. So we not only designed the first speech-synthesis device, we did it in the worst technology you could pick. And the reason for that was if you were doing a consumer product, you couldn’t afford NMOS.” The ROMs were done in PMOS as well.

When the Speak & Spell hit the market in 1978, it was instantly popular with the only constituency that really mattered—kids. And it appeared to be an effective means of helping youngsters learn to spell. Most important, the Speak & Spell was instrumental in overcoming the resistance to using electronic devices in education.

Texas Instruments wouldn’t produce its first digital signal processor chip for another five years, in 1983. But the implementation of DSP logic in the Speak & Spell was such an important breakthrough that the toy was designated an [IEEE Milestone in 2009](https://ethw.org/Milestones:Speak_%26_Spell,_the_First_Use_of_a_Digital_Signal_Processing_IC_for_Speech_Generation,_1978). It also helped launch TI toward a leadership position in DSP that the company continues to hold more than four decades later.

  
  
from Hacker News https://ift.tt/2WvDulF