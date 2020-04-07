---
title: 'KnowledgeNet: A Benchmark for Knowledge Base Population'
date: 2020-01-17T02:32:00+01:00
draft: false
---

[EMNLP 2019 paper](https://www.aclweb.org/anthology/D19-1069.pdf), [dataset](https://github.com/diffbot/knowledge-net), [leaderboard](https://github.com/diffbot/knowledge-net) and [code](https://github.com/diffbot/knowledge-net/tree/master/baselines/EMNLP2019)

[Knowledge bases](https://en.wikipedia.org/wiki/Ontology_(information_science)) (also known as knowledge graphs or ontologies) are valuable resources for developing intelligence applications, including search, question answering, and recommendation systems. However, high-quality knowledge bases still mostly rely on structured data curated by humans. Such reliance on human curation is a major obstacle to the creation of comprehensive, always-up-to-date knowledge bases such as the [Diffbot Knowledge Graph](https://blog.diffbot.com/diffbots-approach-to-knowledge-graph/).

The problem of automatically augmenting a knowledge base with facts expressed in natural language is known as Knowledge Base Population (KBP). This problem has been extensively studied in the last couple of decades; however, progress has been slow in part because of the lack of benchmark datasets. 

![](https://i2.wp.com/blog.diffbot.com/wp-content/uploads/Screenshot-2020-01-10-12.22.27.png?resize=600%2C215)

Knowledge Base Population (KBP) is the problem of automatically augmenting a knowledge base with facts expressed in natural language.

**KnowledgeNet** is a benchmark dataset for populating [Wikidata](https://www.wikidata.org/) with facts expressed in natural language on the web. Facts are of the form (subject; property; object), where subject and object are linked to Wikidata. For instance, the dataset contains text expressing the fact ([Gennaro Basile](https://www.wikidata.org/wiki/Q1367602); RESIDENCE; [Moravia](https://www.wikidata.org/wiki/Q43266)), in the passage:

> “Gennaro Basile was an Italian painter, born in Naples but active in the German-speaking countries. He settled at Brunn, in Moravia, and lived about 1756…”

KBP has been mainly evaluated via annual contests promoted by [TAC](https://tac.nist.gov/). TAC evaluations are performed manually and [are hard to reproduce for new systems](https://www.aclweb.org/anthology/D17-1109/). Unlike TAC, KnowledgeNet employs an automated and reproducible way to evaluate KBP systems at any time, rather than once a year. We hope a faster evaluation cycle will accelerate the rate of improvement for KBP.

Please refer to our [EMNLP 2019 Paper](https://www.aclweb.org/anthology/D19-1069.pdf) for details on KnowlegeNet, but here are some takeaways:

*   State-of-the-art models (using [BERT](https://arxiv.org/abs/1810.04805)) are far from achieving human performance (0.504 vs 0.822).
*   The traditional pipeline approach for this problem is severely limited by error propagation.
*   KnowledgeNet enables the development of end-to-end systems, which are a promising solution for addressing error propagation.

### _Related_

  
  
from Hacker News https://ift.tt/372OnzN