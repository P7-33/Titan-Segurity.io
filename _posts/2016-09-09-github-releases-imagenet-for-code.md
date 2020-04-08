---
title: 'GitHub Releases an ImageNet for Code'
date: 2019-09-27T02:47:00+01:00
draft: false
---

![](https://github.blog/wp-content/uploads/2019/03/engineering-social.png?fit=1201%2C630 "Introducing the CodeSearchNet challenge - The GitHub Blog")  

Searching for code to reuse, call into, or to see how others handle a problem is one of the most common tasks in a software developer’s day. However, search engines for code are often frustrating and never fully understand what we want, unlike regular web search engines. We started using modern machine learning techniques to improve code search but quickly realized that we were unable to measure our progress. Unlike natural language processing with [GLUE](https://gluebenchmark.com/) benchmarks, there is no standard dataset suitable for code search evaluation.

With our partners from [Weights & Biases](https://www.wandb.com/), today we’re announcing the [CodeSearchNet Challenge](https://arxiv.org/abs/1909.09436) evaluation environment and [leaderboard](https://app.wandb.ai/github/codesearchnet/benchmark). We’re also releasing a large dataset to help data scientists build models for this task, as well as several baseline models showing the current state of the art. Our [leaderboard](https://app.wandb.ai/github/codesearchnet/benchmark) uses an annotated dataset of queries to evaluate the quality of code search tools.

[Learn more from our technical report](https://arxiv.org/abs/1909.09436)

The CodeSearchNet Corpus and models[](https://github.blog/2019-09-26-introducing-the-codesearchnet-challenge/#the-codesearchnet-corpus-and-models)
--------------------------------------------------------------------------------------------------------------------------------------------------

We collected a large dataset of functions with associated documentation written in Go, Java, JavaScript, PHP, Python, and Ruby from open source projects on GitHub. We used our [TreeSitter](http://tree-sitter.github.io/tree-sitter/) infrastructure for this effort, and we’re also releasing our [data preprocessing pipeline](https://github.com/github/CodeSearchNet/tree/master/function_parser) for others to use as a starting point in applying machine learning to code. While this data is not directly related to code search, its pairing of code with related natural language description is suitable to train models for this task. Its substantial size also makes it possible to apply high-capacity models based on modern [Transformer](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html) architectures.

Our fully preprocessed CodeSearchNet Corpus is available for [download on Amazon S3](https://github.com/github/CodeSearchNet#downloading-data-from-s3), including:

*   Six million methods overall
*   Two million of which have associated documentation (docstrings, JavaDoc, and more)
*   Metadata that indicates the original location (repository or line number, for example) where the data was found

Building on our earlier efforts in [semantic code search](https://github.blog/2018-09-18-towards-natural-language-semantic-code-search/), we’re also releasing a collection of [baseline models](https://github.com/github/CodeSearchNet) leveraging modern techniques in learning from sequences (including a [BERT](https://arxiv.org/abs/1810.04805)\-like self-attentional model) to help data scientists get started on code search. 

The CodeSearchNet Challenge[](https://github.blog/2019-09-26-introducing-the-codesearchnet-challenge/#the-codesearchnet-challenge)
----------------------------------------------------------------------------------------------------------------------------------

To evaluate code search models, we collected an initial set of code search queries and had programmers annotate the relevance of potential results. We started by collecting common search queries from Bing that had high click-through rates to code and combined these with queries from [StaQC](https://github.com/LittleYUYU/StackOverflow-Question-Code-Dataset), yielding 99 queries for concepts related to code (i.e., we removed everything that was just an API documentation lookup).

We then used a standard [Elasticsearch](https://www.elastic.co/) installation and our baseline models to obtain 10 likely results per query from our CodeSearchNet Corpus. Finally, we asked programmers, data scientists, and machine learning researchers to annotate the proposed results for relevance to the query on a scale from zero (“totally irrelevant”) to three (“exact match”). See our [technical report](https://arxiv.org/abs/1909.09436) for an in-depth explanation of the annotation process and data.

We want to expand our evaluation dataset to include more languages, queries, and annotations in the future. As we continue adding more over the next few months, we aim to include an extended dataset for the next version of CodeSearchNet Challenge in the future.

Other use cases[](https://github.blog/2019-09-26-introducing-the-codesearchnet-challenge/#other-use-cases)
----------------------------------------------------------------------------------------------------------

We anticipate other use cases for this dataset beyond code search and are presenting code search as one possible task that leverages learned representations of natural language and code. We’re excited to see what the community builds next.

Special thanks[](https://github.blog/2019-09-26-introducing-the-codesearchnet-challenge/#special-thanks)
--------------------------------------------------------------------------------------------------------

The CodeSearchNet Challenge would not be possible without the Microsoft Research Team and core contributors from GitHub, including [Marc Brockschmidt](https://www.linkedin.com/in/marc-brockschmidt-995866b0/?originalSubdomain=uk), [Miltos Allamanis](https://miltos.allamanis.com/), [Ho-Hsiang Wu](https://github.com/hohsiangwu), [Hamel Husain,](https://github.com/hamelsmu) and [Tiferet Gazit](https://github.com/tiferet).

We’re also thankful for all of the contributors from the community who helped put this project together:

[@nbardy](https://github.com/nbardy), [@raubitsj](https://github.com/raubitsj), [@staceysv](https://github.com/staceysv), [@cvphelps](https://github.com/cvphelps), [@tejaskannan](https://github.com/tejaskannan), [@s-zanella](https://github.com/s-zanella), [@AntonioND](https://github.com/AntonioND), [@goutham7r](https://github.com/goutham7r), [@campoy](https://github.com/campoy), [@cal58](https://github.com/cal58), [@febuiles](https://github.com/febuiles), [@letmaik](https://github.com/letmaik), [@sebastiandziadzio](https://github.com/sebastiandziadzio), [@panthap2](https://github.com/panthap2), [@CoderPat](https://github.com/CoderPat).

* * *

[Learn more about the CodeSearchNet Challenge](https://github.com/github/codesearchnet#introduction)

  
  
from Hacker News https://ift.tt/2mUHnmf