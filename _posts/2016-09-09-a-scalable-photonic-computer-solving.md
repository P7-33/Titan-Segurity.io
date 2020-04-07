---
title: 'A scalable photonic computer solving the subset sum problem'
date: 2020-02-03T03:13:00+01:00
draft: false
---

![](https://advances.sciencemag.org/sites/default/files/highwire/advances/6/5.cover-source.gif "A scalable photonic computer solving the subset sum problem | Science Advances")  

Abstract
--------

The subset sum problem (SSP) is a typical nondeterministic-polynomial-time (NP)–complete problem that is hard to solve efficiently in time with conventional computers. Photons have the unique features of high propagation speed, strong robustness, and low detectable energy level and therefore can be promising candidates to meet the challenge. Here, we present a scalable chip built-in photonic computer to efficiently solve the SSP. We map the problem into a three-dimensional waveguide network through a femtosecond laser direct writing technique. We show that the photons sufficiently dissipate into the networks and search for solutions in parallel. In the case of successive primes, our approach exhibits a dominant superiority in time consumption even compared with supercomputers. Our results confirm the ability of light to realize computations intractable for conventional computers, and suggest the SSP as a good benchmarking platform for the race between photonic and conventional computers on the way toward “photonic supremacy.”

INTRODUCTION
------------

NP-complete problems ([_1_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-1)) are typically defined as the problems solvable in polynomial time on a nondeterministic Turing machine (NTM), which indicates that these problems are computationally hard on conventional electronic computers, a general type of deterministic Turing machines. The subset sum problem (SSP) with practical application in resource allocation ([_2_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-2)) is a benchmark NP-complete problem ([_3_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-3)), and its intractability has been harnessed in cryptosystems resistant to quantum attacks ([_4_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-4), [_5_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-5)). Given a finite set _S_ of _N_ integers, the SSP asks whether there is a subset of _S_ whose sum is equal to the target _T_. Apparently, the number of subset grows exponentially with the problem size _N_, which leads to an exponential time scaling and thus strongly limits the size of the problem that can be tackled in reality.

Despite the immense difficulty, some researchers attempt to solve NP-complete problems in polynomial time with polynomial resource. A memcomputing machine ([_6_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-6), [_7_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-7)) as powerful as an NTM has been demonstrated, while the ambitious claim is not valid in a realistic environment with inevitable noise ([_8_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-8)). Designs of an NTM, where the magical oracles ([_1_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-1), [_9_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-9), [_10_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-10)) are realized by simultaneously exploring all computation paths, are proposed ([_11_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-11), [_12_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-12)). In the cost of space or material, parallel exploration provides an alternative to decrease time consumption. As time is irreversible, not reusable and completely out of our charge, it is reasonable to trade physical resources for it. Besides the above NTM proposals, similar measurements have been taken, for instance, the increasingly powerful electronic supercomputers with an integration of an increasing number of processors ([_13_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-13)) and molecule-based computation using large quantities of DNAs or motor molecules ([_14_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-14)–[_18_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-18)). Furthermore, optimized algorithms are applied to specific instances ([_19_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-19)–[_21_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-21)).

Although improvements have been made, conventional electronic computers are ultimately limited by heat dissipation problem ([_16_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-16)), which is also a possible limitation for memcomputing machines consisting of commercial electronic devices ([_8_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-8)). The molecule-based computation is limited by the slow movement ([_16_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-16)–[_18_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-18)) or the long reaction process ([_14_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-14), [_15_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-15)). Quantum computation is still hindered by decoherence and scalability ([_22_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-22), [_23_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-23)). Other proposals are still in the stage of theory ([_11_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-11), [_12_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-12), [_24_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-24)–[_26_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-26)). However, we notice that photons have been extensively applied in proof-in-principle demonstrations of supercomputing ([_27_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-27)) even without quantum speed-up, including an NP problem such as prime factorization ([_28_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-28)) and NP-complete problems such as traveling salesman problem ([_29_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-29)), Hamiltonian path problem ([_30_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-30)–[_32_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-32)), and dominating set problem ([_33_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-33)). The #P-complete problem, boson sampling ([_34_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-34)–[_39_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-39)), other computational functions ([_40_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-40)), and algorithms ([_41_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-41), [_42_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-42)) are also demonstrated in a photonic regime. The successful applications imply that photons are potential excellent candidates to solve the SSP.

Here, we present a photonic computer constructed with chips serving as processing units to solve the SSP in a physically scalable fashion. Like the current signal in electronic computers or the molecule in molecular computers, photons contained in the optical source are treated as individual computation carriers. They travel in chips along buried waveguide networks to perform parallel computations. The specific instances of the problem are successfully encoded into the networks according to particular rules. The existence of target sums is judged by the arrival of photons to the corresponding output ports of the networks. We further investigate its scalability and performance in time consumption, showing the photon-enabled advantages.

RESULTS
-------

### Configuration of the photonic computer for the SSP

The proposed photonic computer solving the SSP can be classified as a non–Von Neumann architecture (see the Supplementary Materials for its role in the evolution of computers). As shown in [Fig. 1A](https://advances.sciencemag.org/content/6/5/eaay5853#F1), the photonic computer consists of an input unit, a processing unit, and an output unit. The input unit is used to generate horizontally polarized photons at 810 nm. Photons are then coupled into the processing unit to dissipate into the waveguide network to execute the computation task. After photons are emitted from the processing unit, the evolution results are read out by the output unit. Here, the processing unit is an analog to the central processing unit (CPU) of an electronic computer, playing a key role in the computation. In the following, we will discuss the design of the processing unit from mathematical and physical implementation aspects to illuminate its capability of solving the SSP.

Fig. 1 Schematic of the design and setup.

(**A**) A power-adjustable and horizontally polarized optical source is guaranteed by the quarter-wave plate (QWP), half-wave plate (HWP), and polarization beam splitter (PBS) in the input unit. The photons at 810 nm are prepared and coupled into the network in the processing unit and then travel to generate all possible subset sums. The evolution results at the output ports are retrieved by the charge-coupled device (CCD) to testify the existence of the corresponding sums. (**B**) The abstract network for the specific instance {2, 5, 7, 9} is composed of three different kinds of nodes representing split junctions, pass junctions, and converge junctions. Split junctions (hexagonal nodes) divide the stream of photons into two portions. One portion moves vertically, and the other travels diagonally. Pass junctions (circular white nodes) allow the photons to proceed along their initial directions. Converge junctions (circular yellow nodes) play a role in transferring photons from diagonal lines to vertical lines. Although the circular yellow nodes overlap with the hexagonal nodes in the abstract network, they are physically separate, as shown in (A). Photons traveling diagonally from a split junction to the next split junction represent including an element into the summation. The value of the element is equal to the number of junctions between two subsequent rows of split junctions, as denoted by the integers on the left. The generated subset sums are equal to the spatial positions of the output signals, as the port numbers denote. (**C**) The _x-y_ view of the top left corner of the waveguide network in (A) and the abstract network in (B) is composed of the three basic junctions whose _x-z_ views are shown in (**D**) to (**F**). The split junction is realized by a modified three-dimensional beam splitter where a coupling distance of 10 μm, a coupling length of 1.8 mm, and a vertical decoupling distance of 25 μm are deliberately selected, leading to a desirable splitting ratio. The unbalanced output of split junctions, revealed by the intensity distribution in (D), is designed to compensate the bending loss caused by the subsequent arc cm⌢ and arc nf⌢ in (C). The converge junction is almost a mirror-image split junction except with a different coupling length of 3.3 mm. The residual in port _g_ is small enough to be ignored. A vertical decoupling distance of 25 μm guarantees an excellent pass junction whose extinction ratio is around 24 dB, as the intensity distribution in (F) presents.

The processing unit can be represented by an abstract network composed of nodes and lines, which is primarily based on the proposal of Nicolau _et al._ ([_16_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-16)), while physical implementation has to be designed to fit integrated photonics. As the network for the specific instance {2, 5, 7, 9} in [Fig. 1B](https://advances.sciencemag.org/content/6/5/eaay5853#F1) shows, there are three different types of nodes representing split junctions, pass junctions, and converge junctions. Note that although the circular yellow nodes overlap with the hexagonal nodes in the abstract network, they are physically separate, as the waveguide network in [Fig. 1A](https://advances.sciencemag.org/content/6/5/eaay5853#F1) presents. Once the photons enter the network from the top node, the computation process is activated. The photons are split into two portions at hexagonal nodes (split junctions), traveling vertically and diagonally. When meeting the circular white nodes (pass junctions), the photons proceed along the original directions. Meanwhile, the circular yellow nodes (converge junction), located at the end of the diagonal routes that start from the former row of hexagonal nodes, are responsible for transferring photons from diagonal lines to vertical lines before the next splits.

The specific SSP is encoded into the network according to particular arithmetical and scalable rules: (i) The vertical distance (measured as the number of nodes) between two subsequent rows of hexagonal nodes is equal to the value of the element from the set {2, 5, 7, 9}, as denoted by the integers on the left. (ii) The diagonal routing leads to a horizontal displacement of photons, whose magnitude is also equal to the integer on the left. The diagonal movement of photons represents that the corresponding element is included into the summation. On the contrary, the vertical movement means that the element is excluded from the summation. (iii) The value of the ultimate sums is equivalent to the spatial position of the output signals, as denoted by the port numbers. For example, the path for port 14, highlighted by a translucent gray band, reveals that only elements 5 and 9 contribute to the subset sum 14. Owing to the vast parallelism, the photons arrive at the output ports with all possible subset sums generated.

We fabricate the processing unit in Corning Eagle XG glass with femtosecond laser direct writing technique (see Materials and Methods). The top left corner of the waveguide network in [Fig. 1A](https://advances.sciencemag.org/content/6/5/eaay5853#F1) and the abstract network in [Fig. 1B](https://advances.sciencemag.org/content/6/5/eaay5853#F1) are depicted in detail in [Fig. 1 (C to F)](https://advances.sciencemag.org/content/6/5/eaay5853#F1). As we can see, the split junction is realized by a modified three-dimensional beam splitter, where the two waveguides first couple evanescently (red segment) and then decouple with one of the waveguides climbing upward and the other proceeding along the initial direction. To avoid extra loss, a vertical decoupling distance of 25 μm is deliberately selected. Meanwhile, the coupling length and coupling distance are set to 1.8 mm and 10 μm, respectively, to achieve the desirable splitting ratio. As the intensity distribution in [Fig. 1D](https://advances.sciencemag.org/content/6/5/eaay5853#F1) reveals, the modified beam splitter is unbalanced, which is on the purpose of compensating the bending loss caused by the subsequent arc cm⌢ and arc nf⌢.

The converge junction is almost the mirror-image split junction except with a different coupling length of 3.3 mm. The photons in path _fg_ should be completely transferred to path _eh_ in an ideal case, and the residual induced by the imperfect fabrication is minimized. The output intensity at port _g_ is less than 3% of that at port _h_. The pass junction is implemented in the form of one waveguide crossing over the other at a decoupling vertical distance of 25 μm. As the output intensity in [Fig. 1F](https://advances.sciencemag.org/content/6/5/eaay5853#F1) reveals, the three-dimensional architecture ensures an excellent pass junction whose extinction ratio is around 24 dB. Supported by the powerful fabrication capability of femtosecond laser writing technique ([_43_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-43), [_44_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-44)), we are able to map the abstract network of the SSP into a three-dimensional photonic chip.

### Experimental demonstration

We demonstrate the computation of the SSP at the specific cases of {3, 7, 11} and {3, 7, 9, 11}. As shown in [Fig. 2 (A and C)](https://advances.sciencemag.org/content/6/5/eaay5853#F2), the evolution results are read out from a one-shot image, where the photons appear in a line of spots. Every single spot is an accepted witness of the existence of the corresponding sum (denoted by the integer below the spot) if the experiments are trusted. Because the involved problem size is not too large, we check the reliability of our experimental results by enumeration and conclude that all the spots observed are supposed to appear and that none of the expected results is absent.

Fig. 2 Experimental read-out of computing results.

(**A**) Experimental read-out of evolution results of the case {3, 7, 11}. Every observable spot certifies the existence of the subset sum denoted by the integer below. (**B**) Normalized intensity distribution of the case {3, 7, 11} in experiment and theory. Here, an axis break is applied to display data points with a value of zero and the logarithmic coordinate simultaneously. The theoretical results are either 0 or 0.125, while the experimental results have a fluctuant distribution. A reasonable threshold can be easily found to classify the experimental outcomes into appearance (beyond the threshold) and absence (below the threshold, which is highlighted with slash filling pattern). A wide tolerance band (filled by slash) allows a wide range of threshold with a lower bound of 0.00209 and an upper bound of 0.05891. (**C**) Experimental read-out of evolution results of the case {3, 7, 9, 11}. (**D**) Normalized intensity distribution of the case {3, 7, 9, 11} in experiment and theory. Theoretical results are either 0 or 0.0625. A wide tolerance band (filled by slash) allows a wide range of threshold with a lower bound of 0.00127 and an upper bound of 0.00661.

The reliability of our experiments is further investigated by a comprehensive analysis of the intensity distribution, as presented in [Fig. 2 (B and D)](https://advances.sciencemag.org/content/6/5/eaay5853#F2). We calculate the theoretical distribution through a lossless model consisting of balanced split junctions, perfect pass junctions, and ideal converge junctions. Therefore, the theoretical outcomes can be regarded as benchmarks of the SSPs. For the case of {3, 7, 11}, the theoretical result is either 0 or 0.125, while it is either 0 or 0.0625 in the case of {3, 7, 9, 11}. In this theoretical regime, zero intensity indicates that a sum does not exist; otherwise, it exists.

We apply a threshold to analyze the retrieved intensity for every output port. A valid appearance can be identified if the intensity goes beyond a reasonable threshold; otherwise, an absence can be confirmed (highlighted by solidus pattern). The tolerant intervals of the thresholds applicable in our experiment are presented with bands filled with a solidus in [Fig. 2 (B and D)](https://advances.sciencemag.org/content/6/5/eaay5853#F2), straightforward revealing the lower bounds and the upper bounds. Beneficial from the good signal-to-noise ratio obtained in our experiments, there is a wide tolerant band to accept a large range of thresholds, which implies the great accuracies of our experiments and verifies the feasibility of our approach.

### Time-consumption budget

We find that the optical source launched into the photonic circuit has a notable influence on the performance of our photonic computer. Note that the photonic supremacy in time consumption over other schemes is achieved by classical light (a stream of photons), not quantum light. We obtain the same evolution results with both classical light and quantum light, and the heralded single-photon source fails to outperform the classical light. This phenomenon is attributed to the fact that a bunch of photons arrive together in the case of classical light, while heralded single-photon source only launches one photon at a time. Under these circumstances, it takes longer time with quantum light to collect enough signal photons to be distinguished from the environment, leading to a worse performance than classical light and making it more challenging to surpass electronic computers (see the Supplementary Materials).

To show the photon-enabled advantages, we further investigate the time-consumption performance in the case of classical light. Here, the computing time is determined by the propagation speed of photons and the longest path in the waveguide network. Owing to the fast movement of flying photons and the compactness of the chip-based networks, it only takes the processing units a fraction of 1 ns to accomplish the computations in our experiments, which has already surpassed many representative electronic computers emerging in these decades (see the Supplementary Materials).

Furthermore, the potential of our approach is explored in the context of successive primes by comparing with other competitors (see Materials and Methods for time estimation of different approaches), as shown in [Fig. 3](https://advances.sciencemag.org/content/6/5/eaay5853#F3). It is noticed that the photonic computer has a significant advantage over the molecular computation, which is attributed to the similar time scaling resulting from the similar configuration of the computing networks, and the superiority of photons in moving speed over molecules, i.e., ∼2 × 1011 mm/s for 810 nm photons in waveguides and ∼5 × 10−3 mm/s for actin filaments ([_16_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-16)). Although faster biological molecules are reported in a latest research ([_18_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-18)), they are still on the long journey of chasing after photons.

Fig. 3 Time consumption performance.

The comparison of estimated computing time between the photonic computer and other competitors in the case of successive primes {2, 3, 5, 7, …}. The molecular computer is beaten by the photonic computer all the time. The electronic competitors working in a brute-force manner are surpassed at _N_ = 6, _N_ = 12, and _N_ = 28. As problem size increases, the superiority of photonic computer is enhanced, with the computing time of several orders of magnitude shorter than the rivals.

The time consumption of representative electronic competitors with the conventional Von Neumann architecture, characterized by floating point operations per second (FLOPS) ([_45_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-45)), is also presented. It is found that the photonic computer outperforms the state-of-the-art CPU ([_46_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-46)) at a small size that is probably accessible in subsequent experimental demonstrations. Compared with the graphics processing unit (GPU) ([_47_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-47)), the photonic computer exceeds it until _N_ = 12. Apparently, it is increasingly challenging to beat an increasingly strong competitor. Nevertheless, the most powerful supercomputer ([_13_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-13)), Summit, composed of an enormous number of CPUs and GPUs, can be also surpassed at a modest size of 28. Besides, the superiority of the photonic computer is reinforced with the growth of problem size, as the trend reveals. Even at a medium size, our approach consumes many orders of magnitude shorter computing time than the molecular and electronic rivals, exhibiting strong competitiveness in solving the SSP in the case of successive primes (see Materials and Methods for the speed-up of our photonic computer).

DISCUSSION
----------

In summary, we demonstrate a photonic computer solving the SSP by mapping the problem into a waveguide network in a three-dimensional architecture. With the demonstrated standardized structure of basic junctions, regular configuration of the network, and the mature femtosecond laser writing technique, the SSP can be encoded into a physical network and conveniently solved in a scalable fashion. The computational power is further analyzed by investigating the time-consumption performance. The results suggest that, for successive primes, photonic computers are very likely to beat the most powerful supercomputer with a near-future accessible problem size. Other performances, such as signal-to-noise ratio and Fisher information, are also discussed (see the Supplementary Materials).

The photon-enabled advantage in solving the SSP can be understood from the unique features of light. First, light is essentially a stream of photons, which can be sufficiently used to probe all the paths in parallel, by being dissipated into a large network with very small fraction of light in each path (can be down to single-photon level). Second, the ultimate speed of flying photons makes the evolution time very short in the designed structures, even for a large and complicated photonic network. Third, photons can be confined in a very limited space with the technique of integrated photonics, which is beneficial to both the computing speed and scalability. Last but not least, interference is a unique strength of photons, whereas we cannot see its contribution to the speed-up of the proposed photonic computer. Nevertheless, it can be potentially used to achieve a reconfigurable photonic computer for different SSPs in the future (see the Supplementary Materials).

Besides the fundamental interest of racing with conventional electronic computers, it would be more fascinating to map many real-life problems into the frame of solving the SSP, which may boost the building of this photonic computer toward industrialization. It is also possible, but still open, to solve other NP problems in this purpose-built photonic computer. In light of the fact that any NP problem can be reduced to an NP-complete problem efficiently ([_3_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-3)), any NP problem is able to be mapped to the proposed network in principle. Therefore, a photonic solution of the SSP implies possible solutions of a wide range of NP problems. Moreover, photon-enabled unique feature may also show its strength in other new computing architectures ([_48_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-48), [_49_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-49)).

MATERIALS AND METHODS
---------------------

### Photonic chip fabrication

Waveguide networks in three-dimensional architecture were written by the femtosecond laser with a repetition rate of 1 MHz, a central wavelength of 513 nm, a pulse duration of 290 fs, and a pulse energy of 190 nJ. Before radiating into the borosilicate substrate at a depth of 170 μm, the laser beam was shaped by a cylindrical lens and then focused by a 100× objective with a numerical aperture of 0.7. During the fabrication, the translational stage moved in _x_, _y_, and _z_ directions according to the user-defined program at a constant speed of 15 mm/s. The careful measurements and characterization on the geometric parameter dependence of the three types of junction, such as coupling length, coupling distance, decoupling distance, and curvature, were taken to optimize the performance to form the standard elements.

### Estimation of computing time

For both molecular computation and our approach, the computing time was determined by the moving speed of computation carrier (i.e., molecules and photons) and the longest path in the network. For example, in the case of {2, 5, 7, 9} shown in [Fig. 1](https://advances.sciencemag.org/content/6/5/eaay5853#F1), the longest path is the one linking to port 23, which represents the sum of all the elements in the set. According to the geometrical parameters and the scalable rules of our waveguide network, it is easy to calculate the length of the longest path. The propagating speed of photons is estimated on the basis of the refractive index of Corning Eagle XG ([_50_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-50)) and the refractive index change induced by femtosecond laser writing ([_51_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-51)). The structural parameters of molecular computation were derived from the experiment by Nicolau _et al._ ([_16_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-16)). The faster molecules, actin filaments, were chosen to compare with our approach.

The running time taken by conventional electronic computers working in a brute-force mode, searching the entire solution space consisting of all possible subsets, to solve the SSP was estimated by multiplying FLOPS by the total number of arithmetic operations. The data of FLOPS adopted in our research are either the peak performance or theoretical performance of the corresponding electronic machine. Performance degradation ([_46_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-46)) in practical scenario was neglected.

### Speed-up of the photonic computer

Given a set of _N_ elements, the number of subsets grows exponentially with _N_. According to the definition of the SSP, it requires us to verify every possible subset. If we regard the verification of a subset as a subtask, the number of subtasks or the number of computation operations increases at an exponential rate.

For a conventional electronic computer working sequentially, all subtasks are executed in sequence. Therefore, the total computing time is equivalent to the product of the number of computation operations and the unit time taken by a single operation, growing at an exponential rate. For our photonic computer, which works in a parallel mode, all subtasks can be executed simultaneously. In our implementations, each subset is mapped to a path of the photonic circuits. With light beam (a stream of photons) being split and propagating along all possible paths, all subsets were verified at the same time. On such an occasion, the total computing time only depends on the verification of the largest subset.

Here, the verification of the largest subset corresponds to the movement of photons from the input port to the output port through the longest path. As a result, the computing time is equal to the traveling time of photons in the longest path, growing at a sub-exponential rate, which is slower than that of electronic computers. Moreover, as photons have an ultrahigh propagating speed and the integrated photonic circuit has a compact structure, the computing process is further sped up.

SUPPLEMENTARY MATERIALS
-----------------------

Supplementary material for this article is available at [http://advances.sciencemag.org/cgi/content/full/6/5/eaay5853/DC1](http://advances.sciencemag.org/cgi/content/full/6/5/eaay5853/DC1)

The evolution of computers and the role of non–Von Neumann architecture

The influence of optical source on time consumption

Time-consumption performance

Signal-to-noise ratio

Fisher information

The role of interference

Fig. S1. The role of non–Von Neumann architecture.

Fig. S2. Time-consumption performance.

Fig. S3. Signal-to-noise ratio.

Reference ([_52_](https://advances.sciencemag.org/content/6/5/eaay5853#ref-52))

This is an open-access article distributed under the terms of the [Creative Commons Attribution-NonCommercial license](http://creativecommons.org/licenses/by-nc/4.0/), which permits use, distribution, and reproduction in any medium, so long as the resultant use is **not** for commercial advantage and provided the original work is properly cited.

REFERENCES AND NOTES
--------------------

1.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-1-1 "View reference 1 in text")
    
    M. R. Garey, D. S. Johnson, _Computers and Intractability: A Guide to the Theory of NP-Completeness_ (W. H. Freeman & Co., 1979).
    
2.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-2-1 "View reference 2 in text")
3.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-3-1 "View reference 3 in text")
    
    R. M. Karp, Reducibility among combinatorial problems, in _Complexity of Computer Computations_, R. E. Miller, J. W. Tatcher, Eds. (The IBM Research Symposia Series, Springer, 1972), pp. 85–103.
    
4.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-4-1 "View reference 4 in text")
    
    T. Okamoto, K. Tanaka, S. Uchiyama, Quantum public-key cryptosystems, in _Advances in Cryptology-CRYPTO 2000_, M. Bellare, Ed. (Springer, 2000), pp. 147–165.
    
5.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-5-1 "View reference 5 in text")
6.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-6-1 "View reference 6 in text")
7.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-7-1 "View reference 7 in text")
8.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-8-1 "View reference 8 in text")
9.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-9-1 "View reference 9 in text")
10.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-10-1 "View reference 10 in text")
11.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-11-1 "View reference 11 in text")
12.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-12-1 "View reference 12 in text")
    
    S. Dolev, Y. Nir, Optical implementation of bounded non-deterministic Turing machines. U.S. Patent 7,130,093 B2 (2006).
    
13.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-13-1 "View reference 13 in text")
14.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-14-1 "View reference 14 in text")
15.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-15-1 "View reference 15 in text")
16.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-16-1 "View reference 16 in text")
17.  G. Heldt, Ch. Meinecke, S. Steenhusen, T. Korten, M. Groß, G. Domann, F. Lindberg, D. Reuter, St. Diez, H. Linke, St. E. Schulz, Approach to combine electron-beam lithography and two-photon polymerization for enhanced nano-channels in network-based biocomputation devices, in _34th European Mask and Lithography Conference_ (SPIE, 2018), vol. 10775.
    
18.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-18-1 "View reference 18 in text")
19.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-19-1 "View reference 19 in text")
20.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-21-1 "View reference 21 in text")
    
    K. Koiliaris, C. Xu, A faster pseudopolynomial time algorithm for subset sum, in _Proceedings of the Twenty-Eighth Annual ACM-SIAM Symposium on Discrete Algorithms_ (SIAM, 2017), pp. 1062–1072.
    
21.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-22-1 "View reference 22 in text")
    
    W. L. Chang, T. T. Ren, M. Feng, L. C. Lu, K. W. Lin, M. Guo, Quantum algorithms of the subset-sum problem on a quantum computer, in _2009 WASE International Conference on Information Engineering_ (IEEE, 2009), pp. 54–57.
    
22.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-23-1 "View reference 23 in text")
23.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-24-1 "View reference 24 in text")
24.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-26-1 "View reference 26 in text")
25.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-27-1 "View reference 27 in text")
26.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-28-1 "View reference 28 in text")
27.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-29-1 "View reference 29 in text")
28.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-30-1 "View reference 30 in text")
29.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-32-1 "View reference 32 in text")
30.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-33-1 "View reference 33 in text")
31.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-34-1 "View reference 34 in text")
32.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-39-1 "View reference 39 in text")
33.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-40-1 "View reference 40 in text")
34.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-41-1 "View reference 41 in text")
35.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-42-1 "View reference 42 in text")
36.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-43-1 "View reference 43 in text")
37.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-44-1 "View reference 44 in text")
    
    R. Osellame, G. Cerullo, R. Ramponi, _Femtosecond Laser Micromachining: Photonic and Microfluidic Devices in Transparent Materials_ (Springer, 2012), vol. 123.
    
38.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-45-1 "View reference 45 in text")
39.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-46-1 "View reference 46 in text")
    
    P. Gepner, D. L. Fraser, V. Gamayunov, Evaluation of the 3rd generation Intel Core processor focusing on HPC applications, in _Proceedings of the International Conference on Parallel and Distributed Processing Techniques and Applications_ (World-Comp, 2012), pp. 1–6.
    
40.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-47-1 "View reference 47 in text")
41.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-48-1 "View reference 48 in text")
42.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-49-1 "View reference 49 in text")
43.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-50-1 "View reference 50 in text")
44.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-51-1 "View reference 51 in text")
45.  [↵](https://advances.sciencemag.org/content/6/5/eaay5853#xref-ref-52-1 "View reference 52 in text")

**Acknowledgments:** **Funding:** The authors thank Jian-Wei Pan for helpful discussions. This research was supported by the National Key R&D Program of China (2019YFA0308700, 2017YFA0303700), the National Natural Science Foundation of China (61734005, 11761141014, 11690033, and 11774222), the Science and Technology Commission of Shanghai Municipality (STCSM) (17JC1400403), the Shanghai Municipal Education Commission (SMEC) (2017-01-07-00-02- E00049), and the Program for Professor of Special Appointment at Shanghai Institutions of Higher Learning (Grant GZ2016004). X.-M.J. acknowledges additional support from a Shanghai talent program. **Author contributions:** X.-M.J. and H.P.Z. conceived the project. X.-M.J. supervised the project. X.-Y.X. and X.-M.J. designed the experiment. X.-Y.X. fabricated the photonic chips. X.-Y.X., X.-L.H., Z.-M.L., J.G., Z.-Q.J., Y.W., R.-J.R., and X.-M.J. performed the experiment and analyzed the data. X.-Y.X. and X.-M.J. wrote the paper with input from all the other authors. **Competing interests:** The authors declare that they have no competing interests. **Data and materials availability:** All data needed to evaluate the conclusions in the paper are present in the paper and/or the Supplementary Materials. Additional data related to this paper may be requested from the authors.

*   Copyright © 2020 The Authors, some rights reserved; exclusive licensee American Association for the Advancement of Science. No claim to original U.S. Government Works. Distributed under a Creative Commons Attribution NonCommercial License 4.0 (CC BY-NC).

  
  
from Hacker News https://ift.tt/31bRUtk