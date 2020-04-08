---
title: 'A neural algorithm for similarity search (2017)'
date: 2019-10-28T06:27:00+01:00
draft: false
---

![](https://science.sciencemag.org/sites/default/files/highwire/sci/358/6364.cover-source.gif "A neural algorithm for a fundamental computing problem | Science")  

Fly brain inspires computing algorithm
--------------------------------------

Flies use an algorithmic neuronal strategy to sense and categorize odors. Dasgupta _et al._ applied insights from the fly system to come up with a solution to a computer science problem. On the basis of the algorithm that flies use to tag an odor and categorize similar ones, the authors generated a new solution to the nearest-neighbor search problem that underlies tasks such as searching for similar images on the web.

_Science_, this issue p. [793](https://science.sciencemag.org/lookup/doi/10.1126/science.aam9868)

Abstract
--------

Similarity search—for example, identifying similar images in a database or similar documents on the web—is a fundamental computing problem faced by large-scale information retrieval systems. We discovered that the fruit fly olfactory circuit solves this problem with a variant of a computer science algorithm (called locality-sensitive hashing). The fly circuit assigns similar neural activity patterns to similar odors, so that behaviors learned from one odor can be applied when a similar odor is experienced. The fly algorithm, however, uses three computational strategies that depart from traditional approaches. These strategies can be translated to improve the performance of computational similarity searches. This perspective helps illuminate the logic supporting an important sensory function and provides a conceptually new algorithm for solving a fundamental computational problem.

An essential task of many neural circuits is to generate neural activity patterns in response to input stimuli, so that different inputs can be specifically identified. We studied the circuit used to process odors in the fruit fly olfactory system and uncovered computational strategies for solving a fundamental machine learning problem: approximate similarity (or nearest-neighbors) search.

The fly olfactory circuit generates a “tag” for each odor, which is a set of neurons that fire when that odor is presented ([_1_](https://science.sciencemag.org/content/358/6364/793#ref-1)). This tag is critical for learning behavioral responses to different odors ([_2_](https://science.sciencemag.org/content/358/6364/793#ref-2)). For example, if a reward (e.g., sugar water) or a punishment (e.g., electric shock) is associated with an odor, that odor becomes attractive (a fly will approach the odor) or repulsive (a fly will avoid the odor), respectively. The tags assigned to odors are sparse—only a small fraction of the neurons that receive odor information respond to each odor ([_3_](https://science.sciencemag.org/content/358/6364/793#ref-3)–[_5_](https://science.sciencemag.org/content/358/6364/793#ref-5))—and nonoverlapping: Tags for two randomly selected odors share few, if any, active neurons, so that different odors can be easily distinguished ([_1_](https://science.sciencemag.org/content/358/6364/793#ref-1)).

The tag for an odor is computed by a three-step procedure ([Fig. 1A](https://science.sciencemag.org/content/358/6364/793#F1)). The first step involves feedforward connections from odorant receptor neurons (ORNs) in the fly’s nose to projection neurons (PNs) in structures called glomeruli. There are 50 ORN types, each with a different sensitivity and selectivity for different odors. Thus, each input odor has a location in a 50-dimensional space determined by the 50 ORN firing rates. For each odor, the distribution of ORN firing rates across the 50 ORN types is exponential, with a mean that depends on the concentration of the odor ([_6_](https://science.sciencemag.org/content/358/6364/793#ref-6), [_7_](https://science.sciencemag.org/content/358/6364/793#ref-7)). For the PNs, this concentration dependence is removed ([_7_](https://science.sciencemag.org/content/358/6364/793#ref-7), [_8_](https://science.sciencemag.org/content/358/6364/793#ref-8)); that is, the distribution of firing rates across the 50 PN types is exponential, with close to the same mean for all odors and all odor concentrations ([_1_](https://science.sciencemag.org/content/358/6364/793#ref-1)). Thus, the first step in the circuit essentially “centers the mean”—a standard preprocessing step in many computational pipelines—using a technique called divisive normalization ([_8_](https://science.sciencemag.org/content/358/6364/793#ref-8)). This step is important so that the fly does not mix up odor intensity with odor type.

Fig. 1 Mapping between the fly olfactory circuit and locality-sensitive hashing (LSH).

(**A**) Schematic of the fly olfactory circuit. In step 1, 50 ORNs in the fly’s nose send axons to 50 PNs in the glomeruli; as a result of this projection, each odor is represented by an exponential distribution of firing rates, with the same mean for all odors and all odor concentrations. In step 2, the PNs expand the dimensionality, projecting to 2000 KCs connected by a sparse, binary random projection matrix. In step 3, the KCs receive feedback inhibition from the anterior paired lateral (APL) neuron, which leaves only the top 5% of KCs to remain firing spikes for the odor. This 5% corresponds to the tag (hash) for the odor. (**B**) Illustrative odor responses. Similar pairs of odors (e.g., methanol and ethanol) are assigned more similar tags than are dissimilar odors. Darker shading denotes higher activity. (**C**) Differences between conventional LSH and the fly algorithm. In the example, the computational complexity for LSH and the fly are the same. The input dimensionality _d_ = 5. LSH computes _m_ = 3 random projections, each of which requires 10 operations (five multiplications plus five additions). The fly computes _m_ = 15 random projections, each of which requires two addition operations. Thus, both require 30 total operations. **x**, input feature vector; _r_, Gaussian random variable; _w_, bin width constant for discretization.

The second step, where the main algorithmic insight begins, involves a 40-fold expansion in the number of neurons: Fifty PNs project to 2000 Kenyon cells (KCs), connected by a sparse, binary random connection matrix ([_9_](https://science.sciencemag.org/content/358/6364/793#ref-9)). Each KC receives and sums the firing rates from about six randomly selected PNs ([_9_](https://science.sciencemag.org/content/358/6364/793#ref-9)). The third step involves a winner-take-all (WTA) circuit in which strong inhibitory feedback comes from a single inhibitory neuron, called APL (anterior paired lateral neuron). As a result, all but the highest-firing 5% of KCs are silenced ([_1_](https://science.sciencemag.org/content/358/6364/793#ref-1), [_3_](https://science.sciencemag.org/content/358/6364/793#ref-3), [_4_](https://science.sciencemag.org/content/358/6364/793#ref-4)). The firing rates of these remaining 5% correspond to the tag assigned to the input odor.

From a computer science perspective, we view the fly’s circuit as a hash function, whose input is an odor and whose output is a tag (called a hash) for that odor. Although tags should discriminate odors, it is also to the fly’s advantage to associate very similar odors with similar tags ([Fig. 1B](https://science.sciencemag.org/content/358/6364/793#F1)), so that conditioned responses learned for one odor can be applied when a very similar odor, or a noisy version of the learned odor, is experienced. This led us to conjecture that the fly’s circuit produces tags that are locality-sensitive; that is, the more similar a pair of odors (as defined by the 50 ORN firing rates for that odor), the more similar their assigned tags. Locality-sensitive hash \[LSH ([_10_](https://science.sciencemag.org/content/358/6364/793#ref-10), [_11_](https://science.sciencemag.org/content/358/6364/793#ref-11))\] functions serve as the foundation for solving numerous similarity search problems in computer science. We translated insights from the fly’s circuit to develop a class of LSH algorithms for efficiently finding approximate nearest neighbors of high-dimensional points.

Imagine that you are provided an image of an elephant and seek to find the 100 images—out of the billions of images on the web—that look most similar to your elephant image. This is called the nearest-neighbors search problem, which is of fundamental importance in information retrieval, data compression, and machine learning ([_10_](https://science.sciencemag.org/content/358/6364/793#ref-10)). Each image is typically represented as a _d_\-dimensional vector of feature values. (Each odor that a fly processes is a 50-dimensional feature vector of firing rates.) A distance metric is used to compute the similarity between two images (feature vectors), and the goal is to efficiently find the nearest neighbors of any query image. If the web contained only a few images, then brute force linear search could easily be used to find the exact nearest neighbors. If the web contained many images, but each image was represented by a low-dimensional vector (e.g., 10 or 20 features), then space-partitioning methods ([_12_](https://science.sciencemag.org/content/358/6364/793#ref-12)) would similarly suffice. However, for large databases with high-dimensional data, neither approach scales ([_11_](https://science.sciencemag.org/content/358/6364/793#ref-11)).

In many applications, returning an approximate set of nearest neighbors that are “close enough” to the query is adequate, so long as they can be found quickly. This has motivated an approach for finding approximate nearest neighbors by LSH ([_10_](https://science.sciencemag.org/content/358/6364/793#ref-10)). For the fly, as noted, the locality-sensitive property states that two odors that generate similar ORN responses will be represented by two tags that are themselves similar ([Fig. 1B](https://science.sciencemag.org/content/358/6364/793#F1)). Likewise, for image search, the tag of an elephant image will be more similar to the tag of another elephant image than to the tag of a skyscraper image.

Unlike a traditional (non-LSH) hash function, where the input points are scattered randomly and uniformly over the range, a LSH function provides a distance-preserving embedding of points from _d_\-dimensional space into _m_\-dimensional space (the latter corresponds to the tag). Thus, points that are closer to one another in input space have a higher probability of being assigned the same or a similar tag than points that are far apart. \[A formal definition is given in ([_13_](https://science.sciencemag.org/content/358/6364/793#ref-13)).\]

To design a LSH function, one common trick is to compute random projections of the input data ([_10_](https://science.sciencemag.org/content/358/6364/793#ref-10), [_11_](https://science.sciencemag.org/content/358/6364/793#ref-11))—that is, to multiply the input feature vector by a random matrix. The Johnson-Lindenstrauss lemma ([_14_](https://science.sciencemag.org/content/358/6364/793#ref-14), [_15_](https://science.sciencemag.org/content/358/6364/793#ref-15)) and its many variants ([_16_](https://science.sciencemag.org/content/358/6364/793#ref-16)–[_18_](https://science.sciencemag.org/content/358/6364/793#ref-18)) provide strong theoretical bounds on how well locality is preserved when embedding data from _d_ into _m_ dimensions by using various types of random projections.

The fly also assigns tags to odors through random projections (step 2 in [Fig. 1A](https://science.sciencemag.org/content/358/6364/793#F1); 50 PNs _→_ 2000 KCs), which provides a key clue to the function of this part of the circuit. There are, however, three differences between the fly algorithm and conventional LSH algorithms. First, the fly uses sparse, binary random projections, whereas LSH functions typically use dense, Gaussian random projections that require many more mathematical operations to compute. Second, the fly expands the dimensionality of the input after projection (_d_ « _m_), whereas LSH reduces the dimensionality (_d_ » _m_). Third, the fly sparsifies the higher-dimensionality representation by a WTA mechanism, whereas LSH preserves a dense representation.

In the supplementary materials ([_13_](https://science.sciencemag.org/content/358/6364/793#ref-13)), we show analytically that sparse, binary random projections of the type in the fly olfactory circuit generate tags that preserve the neighborhood structure of input points. This proves that the fly’s circuit represents a previously unknown LSH family.

We then empirically evaluated the fly algorithm versus traditional LSH ([_10_](https://science.sciencemag.org/content/358/6364/793#ref-10), [_11_](https://science.sciencemag.org/content/358/6364/793#ref-11)) on the basis of how precisely each algorithm could identify nearest neighbors of a given query point. To perform a fair comparison, we fixed the computational complexity of both algorithms to be the same ([Fig. 1C](https://science.sciencemag.org/content/358/6364/793#F1)). That is, the two approaches were fixed to use the same number of mathematical operations to generate a hash of length _k_ (i.e., a vector with _k_ nonzero values) for each input ([_13_](https://science.sciencemag.org/content/358/6364/793#ref-13)).

We compared the two algorithms for finding nearest neighbors in three benchmark data sets: SIFT (_d_ = 128), GLOVE (_d_ = 300), and MNIST (_d_ = 784) ([_13_](https://science.sciencemag.org/content/358/6364/793#ref-13)). SIFT and MNIST both contain vector representations of images used for image similarity search, whereas GLOVE contains vector representations of words used for semantic similarity search. We used a subset of each data set with 10,000 inputs each, in which each input was represented as a feature vector in _d_\-dimensional space. To test performance, we selected 1000 random query inputs from the 10,000 and compared true versus predicted nearest neighbors. That is, for each query, we found the top 2% (200) of its true nearest neighbors in input space, determined on the basis of Euclidean distance between feature vectors. We then found the top 2% of predicted nearest neighbors in _m_\-dimensional hash space, determined on the basis of the Euclidean distance between tags (hashes). We varied the length of the hash (_k_) and computed the overlap between the ranked lists of true and predicted nearest neighbors by using the mean average precision ([_19_](https://science.sciencemag.org/content/358/6364/793#ref-19)). We averaged the mean average precision over 50 trials, in which, for each trial, the random projection matrices and the queries changed. We isolated each of the three differences between the fly algorithm and LSH to test their individual effect on nearest-neighbors retrieval performance.

Replacing the dense Gaussian random projection of LSH with a sparse binary random projection did not hurt how precisely nearest neighbors could be identified ([Fig. 2A](https://science.sciencemag.org/content/358/6364/793#F2)). These results support our theoretical calculations that the fly’s random projection is locality-sensitive. Moreover, the sparse, binary random projection achieved a computational savings of a factor of 20 relative to the dense, Gaussian random projection (fig. S1) ([_13_](https://science.sciencemag.org/content/358/6364/793#ref-13)).

Fig. 2 Empirical comparison of different random projection types and tag-selection methods.

In all plots, the _x_ axis is the length of the hash, and the _y_ axis is the mean average precision denoting how accurately the true nearest neighbors are found (higher is better). (**A**) Sparse, binary random projections offer near-identical performance to that of dense, Gaussian random projections, but the former provide a large savings in computation. (**B**) The expanded-dimension (from _k_ to 20_k_) plus winner-take-all (WTA) sparsification further boosts performance relative to non-expansion. Results are consistent across all three benchmark data sets. Error bars indicate standard deviation over 50 trials.

When expanding the dimensionality, sparsifying the tag using WTA resulted in better performance than using random tag selection ([Fig. 2B](https://science.sciencemag.org/content/358/6364/793#F2)). WTA selected the top _k_ firing KCs as the tag, unlike random tag selection, which selected _k_ random KCs. For both, we used 20_k_ random projections for the fly to equate the number of mathematical operations used by the fly and LSH ([_13_](https://science.sciencemag.org/content/358/6364/793#ref-13)). For example, for the SIFT data set with hash length _k_ = 4, random selection yielded a 17.7% mean average precision, versus roughly double that (32.4%) using WTA. Thus, selecting the top firing neurons best preserves relative distances between inputs; the increased dimensionality also makes it easier to segregate dissimilar inputs. For random tag selection, we selected _k_ random (but fixed for all inputs) KCs for the tag; hence, its performance is effectively the same as doing _k_ random projections, as in LSH.

With further expansion of the dimensionality (from 20_k_ to 10_d_ KCs, closer to the actual fly’s circuitry), we obtained further gains relative to LSH in identifying nearest neighbors across all data sets and hash lengths ([Fig. 3](https://science.sciencemag.org/content/358/6364/793#F3)). The gains were highest for very short hash lengths, where there was an almost threefold improvement in mean average precision (e.g., for MNIST with _k_ = 4, 16.0% for LSH, versus 44.8% for the fly algorithm).

Fig. 3 Overall comparison between the fly algorithm and LSH.

In all plots, the _x_ axis is the length of the hash, and the _y_ axis is the mean average precision (higher is better). A 10_d_ expansion was used for the fly. Across all three data sets, the fly’s method outperforms LSH, most prominently for short hash lengths. Error bars indicate standard deviation over 50 trials.

We also found similar gains in performance when testing the fly algorithm in higher dimensions and for binary LSH ([_20_](https://science.sciencemag.org/content/358/6364/793#ref-20)) (figs. S2 to S3). Thus, the fly algorithm is scalable and may be useful across other LSH families.

Our work identified a synergy between strategies for similarity matching in the brain ([_21_](https://science.sciencemag.org/content/358/6364/793#ref-21)) and hashing algorithms for nearest-neighbors search in large-scale information retrieval systems. It may also have applications in duplicate detection, clustering, and energy-efficient deep learning ([_22_](https://science.sciencemag.org/content/358/6364/793#ref-22)). There are numerous extensions to LSH ([_23_](https://science.sciencemag.org/content/358/6364/793#ref-23)), including the use of multiple hash tables ([_11_](https://science.sciencemag.org/content/358/6364/793#ref-11)) to boost precision (we used one for both algorithms), the use of multiprobe ([_24_](https://science.sciencemag.org/content/358/6364/793#ref-24)) so that similar tags can be grouped together (which may be easier to implement for the fly algorithm because tags are sparse), various quantization tricks for discretizing hashes ([_25_](https://science.sciencemag.org/content/358/6364/793#ref-25)), and learning \[called data-dependent hashing ([_13_](https://science.sciencemag.org/content/358/6364/793#ref-13))\]. There are also methods to speed up the random projection multiplication, both for LSH schemes by fast Johnson-Lindenstrauss transforms ([_26_](https://science.sciencemag.org/content/358/6364/793#ref-26), [_27_](https://science.sciencemag.org/content/358/6364/793#ref-27)) and for the fly by fast sparse matrix multiplication. Our goal was to fairly compare two conceptually different approaches for the nearest-neighbors search problem; in practical applications, all of these extensions will need to be ported to the fly algorithm.

Some of the fly algorithm’s strategies have been used before. For example, MinHash ([_28_](https://science.sciencemag.org/content/358/6364/793#ref-28)) and winner-take-all hash ([_29_](https://science.sciencemag.org/content/358/6364/793#ref-29)) both use WTA-like components, though neither propose expanding the dimensionality; similarly, random projections are used in many LSH families, but none, to our knowledge, use sparse, binary projections. The fly olfactory circuit appears to have evolved to use a distinctive combination of these computational ingredients. The three hallmarks of the fly’s circuit motif may also appear in other brain regions and species ([Table 1](https://science.sciencemag.org/content/358/6364/793#T1)). Thus, locality-sensitive hashing may be a general principle of computation used in the brain ([_30_](https://science.sciencemag.org/content/358/6364/793#ref-30)).

Table 1 The generality of locality-sensitive hashing in the brain.

Shown are the steps used in the fly olfactory circuit and their potential analogs in vertebrate brain regions.

References and Notes
--------------------

1.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-1-1 "View reference 1 in text")
2.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-2-1 "View reference 2 in text")
3.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-3-1 "View reference 3 in text")
4.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-4-1 "View reference 4 in text")
5.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-5-1 "View reference 5 in text")
6.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-6-1 "View reference 6 in text")
7.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-7-1 "View reference 7 in text")
8.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-8-1 "View reference 8 in text")
9.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-9-1 "View reference 9 in text")
10.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-10-1 "View reference 10 in text")
11.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-11-1 "View reference 11 in text")
    
    A. Gionis, P. Indyk, R. Motwani, in _VLDB’99, Proceedings of the 25th International Conference on Very Large Data Bases_, M. P. Atkinson _et al_., Eds. (Morgan Kaufman, 1999), pp. 158–529.
    
12.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-12-1 "View reference 12 in text")
    
    H. Samet, _Foundations of Multidimensional and Metric Data Structures_ (Morgan Kaufmann Series in Computer Graphics and Geometric Modeling, Morgan Kaufmann, 2005).
    
13.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-13-1 "View reference 13 in text")Materials and methods are available as supplementary materials.
14.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-14-1 "View reference 14 in text")
    
    W. Johnson, J. Lindenstrauss, in _Conference on Modern Analysis and Probability_, R. Beals, A. Beck, A. Bellow, A. Hajian, Eds., vol. 26 of _Contemporary Mathematics_ (American Mathematical Society, 1984), pp. 189–206.
    
15.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-15-1 "View reference 15 in text")
16.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-16-1 "View reference 16 in text")
17.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-18-1 "View reference 18 in text")
18.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-19-1 "View reference 19 in text")
    
    Y. Lin, R. Jin, D. Cai, S. Yan, X. Li, in _2013 IEEE Conference on Computer Vision and Pattern Recognition_ (IEEE Computer Society, 2013), pp. 446–451.
    
19.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-20-1 "View reference 20 in text")
    
    M. S. Charikar, in _Proceedings of the Thirty-Fourth Annual ACM Symposium on Theory of Computing_, _STOC ’02_ \[Association for Computing Machinery (ACM), 2002\], pp. 380–388.
    
20.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-21-1 "View reference 21 in text")
    
    C. Pehlevan, D. B. Chklovskii, in _NIPS’15, Proceedings of the 28th International Conference on Neural Information Processing Systems_ (MIT Press, 2015), pp. 2269–2277.
    
21.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-22-1 "View reference 22 in text")
22.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-23-1 "View reference 23 in text")
23.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-24-1 "View reference 24 in text")
    
    Q. Lv, W. Josephson, Z. Wang, M. Charikar, K. Li, in _VLDB ’07, Proceedings of the 33rd International Conference on Very Large Data Bases_ (ACM, 2007), pp. 950–961.
    
24.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-25-1 "View reference 25 in text")
    
    P. Li, M. Mitzenmacher, A. Shrivastava, in _Proceedings of the 31st International Conference on Machine Learning_ (Proceedings of Machine Learning Research, 2014), pp. 676–684.
    
25.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-26-1 "View reference 26 in text")
    
    A. Dasgupta, R. Kumar, T. Sarlos, in _KDD ’11, The 17th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining_ (ACM, 2011), pp. 1073–1081.
    
26.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-27-1 "View reference 27 in text")
    
    A. Andoni, P. Indyk, T. Laarhoven, I. Razenshteyn, L. Schmidt, in _NIPS’15, Proceedings of the 28th International Conference on Neural Information Processing Systems_ (MIT Press, 2015), pp. 1225–1233.
    
27.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-28-1 "View reference 28 in text")
    
    A. Broder, in _Proceedings of the Compression and Complexity of Sequences 1997_ (IEEE Computer Society, 1997), p. 21.
    
28.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-29-1 "View reference 29 in text")
    
    J. Yagnik, D. Strelow, D. A. Ross, R.-s. Lin, in _2011 International Conference on Computer Vision_ (IEEE Computer Society, 2011), pp. 2431–2438.
    
29.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-30-1 "View reference 30 in text")
30.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-31-1 "View reference 31 in text")
31.  J. Pennington, R. Socher, C. D. Manning, in _EMNLP 2014: The 2014 Conference on Empirical Methods in Natural Language Processing_ (Association for Computational Linguistics, 2014), pp. 1532–1543.
    
32.  Y. Weiss, A. Torralba, R. Fergus, in _Advances in Neural Information Processing Systems 21_, D. Koller, D. Schuurmans, Y. Bengio, L. Bottou, Eds. (Curran Associates, 2009), pp. 1753–1760.
    
33.  H. Zhu, M. Long, J. Wang, Y. Cao, in _Proceedings of the Thirtieth AAAI Conference on Artificial Intelligence_ (AAAI Press, 2016), pp. 2415–2421.
    
34.  K. Zhao, H. Lu, J. Mei, in _Proceedings of the Twenty-Eighth AAAI Conference on Artificial Intelligence_ (AAAI Press, 2014), pp. 2874–2880.
    
35.  [↵](https://science.sciencemag.org/content/358/6364/793#xref-ref-49-1 "View reference 49 in text")

**Acknowledgments:**

For funding support, C.F.S. thanks the NSF (grant EAGER PHY-1444273), and S.N. thanks the Army Research Office (grant DOD W911NF-17-1-0045). All authors thank A. Lang and J. Berkowitz for helpful comments on the manuscript. Code and data are available at

[https://bitbucket.org/navlakha/flylsh](https://bitbucket.org/navlakha/flylsh)

.

  
  
from Hacker News https://ift.tt/31OwscI