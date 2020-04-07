---
title: 'Polyglot Word Embeddings Discover Language Clusters'
date: 2020-02-04T04:01:00+01:00
draft: false
---

Polyglot word embeddings obtained by training a skipgram model on a multi-lingual corpus discover extremely high-quality language clusters.

These can be trivially retrieved using an algorithm like $k-$Means giving us a fully unsupervised language identification system.

Experiments show that these clusters are on-par with results produced by popular [open source](https://fasttext.cc/blog/2017/10/02/blog-post.html) and [commercial models](https://cloud.google.com/translate/docs/basic/detecting-language).

We have successfully used this technique in many situations involving several low-resource languages that are poorly supported by popular open source models.

This blog post covers methods, intuition, and links to an implementation based on 100-dimensional [FastText embeddings](https://fasttext.cc/).

### **Background**

The skipgram model takes a word as input and predicts its context.

The pipeline maps a one-hot representation of a word in the vocabulary $\\mathcal{V}$ to a dense, real-valued vector called a _word embedding_.

The training scheme for this model involves words and the contexts they appear in (the positives), and negative examples obtained using _negative sampling_.

We’ll henceforth concern ourselves with 100-dimensional [FastText](https://fasttext.cc/) word embeddings and refer to them as `FastText-100`. These results are consistent with the 300-dimensional variant as well.

A _document embedding_ is a single real-valued vector for a full document (sentence, paragraph, social media post etc.).

There are several popular ways of obtaining these but we’ll just use the FastText default:

*   obtain the word-vectors for all words in the document,
*   normalize them, and
*   average them to obtain a single 100-dimensional vector for the whole document.

### **Polyglot Embeddings**

I am going to use a pre-processed Europarl corpus sourced from [here](http://opus.nlpl.eu/Europarl.php).

After a preprocessing step:

*   The text is lowercased and punctuation stripped.
*   Each line corresponds to a distinct _document_, and
*   The full corpus is shuffled.

The corpus contains **21** languages. The documents are shuffled and (polyglot) `FastText-100` embeddings are trained on this 21-language corpus.

You can download it (and models and everything) [here](http://shriphani.com/europarl.zip)

We can visualize the document embedding space using a TSNE plot:

![](http://blog.shriphani.com/img/europarl_plot.png)  

We observe 21 clear, well defined clusters.

Manual inspection shows that there is exactly **one cluster per language** in the corpus.

A simple clustering algorithm like $k-$Means is able to retrieve these clusters and on inspection we notice that the corpus is split into 21 parts - each containing documents written in exactly one language.

### **A Language Identification System**

There are two undiscussed steps - picking a value of $k$, and assigning a language to one of these language clusters.

The latter is easy to solve - human annotators assign the dominant language in each cluster as that cluster’s language. A subsequent cluster membership test can be used for a test document.

What remains to be discussed is picking a good $k$ value for the $k$-Means algorithm.

In our experience, popular methods like the [silhouette heuristic](https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_silhouette_analysis.html), or the [elbow method](https://en.wikipedia.org/wiki/Elbow_method_(clustering)) are quite capable of producing a reasonable value for $k$.

For the Europarl corpus above, here is a silhouette plot for $k=21$:

![](http://blog.shriphani.com/img/europarl_silhouettes21.png)

And here is the elbow plot:

![](http://blog.shriphani.com/img/europarl_elbow.png)

In both cases, we see 21 as the optimal number of clusters for this corpus.

### **How Good Are These Clusters?**

We run human evaluations on several corpora and report performance against popular open and commercial models. These corpora contain several low-resource languages and thus popular language identification systems are unable to identify them at times:

*   $\\mathcal{D}\_{IndPak}$ - Indian and Pakistani News Channels - Contains English, Romanized and Devanagiri Hindi.
*   $\\mathcal{D}\_{ABP}$ - Bengali News Network - English, Romanized Hindi, Romanized and native script Bengali.
*   $\\mathcal{D}\_{OTV}$ - Oriya News Network - English, Romanized Hindi, Romanized and native script Oriya.

In all these cases, our model is able to perform **exceptionally well**. In cases where it makes sense, performance is on par with popular and commercial models. For full details see our [paper](https://arxiv.org/pdf/1909.12940.pdf).

I’m attached the embedding space from $\\mathcal{D}\_{IndPak}$ here:

![](http://blog.shriphani.com/img/d_ind_pak.png)

Notice how clean the full embedding space is.

### Intuition

Why is this happening?

The skipgram training scheme predicts a context for an input word.

A Hindi word’s context is likely to consist of other Hindi words; and example contexts retrieved in the negative sampling phase are likely to be written in languages distinct from the language of the input word.

It just so happens that the skipgram training scheme is perfectly designed to separate out a multilingual corpus into its monolingual components.

And the embeddings reflect this - as we can see from the TSNE plots above.

Note that inside the embedding subspace corresponding to a language, we observe similar properties typically observed when these word embeddings are trained on monolingual corpora.

i.e. standard stuff like analogies, semantic similarities etc. work very well.

### In The Wild

We have used this technique in a variety of text analyses centered in South and South-East Asia.

In particular, South Asian social media users used Romanized variants of their native languages that are mostly unsupported by popular language identification systems.

This unsupervised method is highly capable in such situations eliminating significant annotation requirements.

In [this paper](https://arxiv.org/abs/1910.03206) analyzing the Rohingya crisis, from among dozens of languages (many low-resource), this technique was utilized to extract out English social media posts.

In [an analysis of the India-Pakistan crisis of 2019](https://arxiv.org/pdf/1909.12940.pdf), this technique was used to separate out Romanized Hindi and English for further analysis.

In soon to be published work analyzing the 2019 Indian election, nearly a dozen Indian regional languages were extracted and analyzed with zero annotation burden.

In almost all these cases existing solutions performed poorly or involved prohibitive costs.

For linguistically diverse regions, we foresee that polyglot embeddings are going to be an important NLP pipeline component.

Unsupervised or low-supervision methods have been increasingly deployed in multlingual settings.

For instance, embeddings learned by machine translation models [seem to be organized along linguistic lines](https://arxiv.org/abs/1909.02197).

A clever training setup was used for unsupervised machine translation in [this paper](https://arxiv.org/abs/1804.07755).

Polyglot embeddings (contextual or otherwise) have been used for performance gains in [several](https://arxiv.org/abs/1902.09697) [tasks](https://arxiv.org/pdf/1805.11598.pdf).

### Links

### Cite

```
@inproceedings{kashmir, title={Hope Speech Detection: A Computational Analysis of the Voice of Peace}, author={Palakodety, Shriphani and KhudaBukhsh, Ashiqur R. and Carbonell, Jaime G}, booktitle={Proceedings of ECAI 2020}, pages={To appear}, year={2020} }
```  
  
from Hacker News https://ift.tt/3bdQ9Rd

The document embedding space and 21 clusters discovered by $k$-Means.