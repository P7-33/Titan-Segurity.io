---
title: 'Why does Wuhan coronavirus genome end in aaaaa.. (33 a''s)?'
date: 2020-01-26T02:42:00+01:00
draft: false
---

![](https://cdn.sstatic.net/Sites/bioinformatics/img/apple-touch-icon@2.png?v=8fff2b3c0878 "sequencing - Why does the Wuhan coronavirus genome end in aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa (33 a's)? - Bioinformatics Stack Exchange")  

This question is quite general, so I'm going to attempt to tie it back to bioinformatics.

**Background** The tree for the current coronavirus is [here](https://www.ecohealthalliance.org/2020/01/phylogenetic-analysis-shows-novel-wuhan-coronavirus-clusters-with-sars), showing it is closely related to bat-coronavirus and in particular SARS.

**Question** The bioinformatics question for the current coronavirus is why this virus appears to be able to infect humans and transmit to human.

**Genome size** Firstly, you said that 30kb was large ... this is a standard size for a coronavirus genome, albeit it is unusual in that the family Coronaviridae are the largest genomes for a single stranded RNA virus, for example flaviviruses are 10kb. Thus, all coronaviruses are all approximately 30Kb. Some coronaviruses don't infect humans (zero symptoms), some cause very mild symptoms, others are MERS and SARS with 40-60% and 10% morality rates respectively. So, genome size is of little bioinformatics interest in my opinion.

**Polyadenylation** and capping (5' methylation) enable the RNA to be trafficked and transcribed by ribosomes and the mechanism is widely used by viruses. Methylation would also prevent the innate immune response from the shredding the vRNA. [Koonin and Moss (2010)](https://www.pnas.org/content/107/8/3283#ref-1), interpreted a given capping mechanism as being common to the Mononegavirales - a viral Order including measles, mumps, Ebolavirus. Its a big statement, but regardless poly-A and capping are simply mimicking the host mRNA which a lot of viruses use. Poly-A and capping per se are not really interesting.

**Conclusion** The bioinformatics question is the genome size wierd - no, its standard for a coronavirus, is the poly-A weird - no its generic amongst lots of viruses as is capping. Is the length of the poly-A excessive (33 As), it looks odd but a human genecist/bioinformaticist needs to answer that ... so is it (potentially) linked with its epidemiology/clinical symptoms?

I don't think 33 poly-As are linked with anything bioinformatically interesting. This is because it will likely vary dramatically between genomes (not simply epidemic vs. non-epidemic strains). I don't know the mechanism for poly-adenylation, but I think slippage is a likely mutation resulting in large variations between individual genomes, particularly for poly-A - which notorious for slippage.

So ultimately could poly-As be linked with the ability of the new coronavirus to infect/transmit and could we therefore explore that bioinformatically? I personally think slippage mutations would prevent a clonal lineage emerging, i.e. that the size of the poly-As is not stable between genomes, but that would assume a given given mechanism of polyadenylation. Thus as a bioinformatics question I wouldn't pursue it, because I don't think there is sufficient biological rationale. I agree weird stuff should be questioned and that bit of the genome jumps out ... but I doubt it would go anywhere.

**Slippage** The definition of a slippage mutation is [here](https://en.m.wikipedia.org/wiki/Slipped_strand_mispairing), but basically it means this genome has 33 poly-As, however another isolate from the same epidemic could say have 30 poly-As (just an example), another might have 25 poly-As and so on.

Just my 2 cents

  
  
from Hacker News https://ift.tt/36roXdK