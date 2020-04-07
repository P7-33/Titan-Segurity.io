---
title: 'The Case for Bayesian Deep Learning'
date: 2020-01-12T02:47:00+01:00
draft: false
---

In many situations, the predictive distribution we want to compute is given by

\\begin{equation\*} p(y|x, \\mathcal{D}) = \\int p(y|x, w) p(w|\\mathcal{D}) dw \\,. \\quad\\quad\\quad\\quad\\quad\\quad\\quad\\quad\\quad (1) \\end{equation\*}

The outputs are \\(y\\) (e.g., class labels, regression values, ... ), indexed by inputs \\(x\\) (e.g. images, spatial locations, ...), the weights (or parameters) of the model \\(f(x; w)\\) are \\(w\\), and \\(D\\) are the data. Eq. (1) represents a _Bayesian model average_ (BMA). Rather than bet everything on one hypothesis — with a single setting of parameters \\(w\\) — we want to use every possible setting of parameters, weighted by their posterior probabilities. This process is called _marginalization_ of the parameters \\(w\\), since the predictive distribution of interest no longer conditions on \\(w\\). This is not a controversial equation, but a direct expression of the sum and product rules of probability. The BMA represents _epistemic uncertainty_ — that is, uncertainty over which setting of weights (hypothesis) is correct, given limited data. Epistemic uncertainty is sometimes referred to as _model uncertainty_, in contrast to _aleatoric uncertainty_ coming from noise in the measurement process. One can naturally visualize epistemic uncertainty in regression, by looking at the spread of the predictive distribution as we move in \\(x\\) space. As we move away from the data, there are many more functions that are consistent with our observations, and so our epistemic uncertainty should grow.

In classical training, one typically finds the _regularized maximum likelihood_ solution

\\begin{equation\*} \\hat w = \\arg\\max\_w \\log p(w|\\mathcal{D}) = \\arg\\max\_w (\\log p(\\mathcal{D}|w) + \\log p(w) + \\text{constant}). \\quad\\quad\\quad\\quad\\quad\\quad\\quad\\quad\\quad (2) \\end{equation\*}

This procedure is sometimes called _maximum a-posteriori (MAP) optimization_, as it involves maximizing a posterior. \\(\\log p(\\mathcal{D}|w)\\) is the log likelihood, formed by relating the function we want to learn \\(f(x;w)\\) to our observations. If we are performing classification with a softmax link function, \\(-\\log p(\\mathcal{D}|w)\\) corresponds to the cross entropy loss. If we are are performing regression with Gaussian noise, such that \\(p(\\mathcal{D}|w) = \\prod\_{j=1}^{n} p(y\_j | w, x\_j) = \\prod\_{j=1}^{n} \\mathcal{N}(y\_j; f(x\_i;w),\\sigma^2)\\), then \\(-\\log p(\\mathcal{D}|w)\\) is a scaled MSE loss. In this context, the prior p(w) acts as a _regularizer_. If we choose a flat prior, which has no preference for any setting of the parameters \\(w\\) (it does not assign any feasible setting any more prior density than any other), then it will have no effect on the optimization solution. On the other hand, a flat prior may have a major effect on _marginalization_. Indeed, even though MAP involves a posterior and a prior, and an instantiation of Bayes rule, it is not at all Bayesian, since it is performing optimization to bet everything on a single hypothesis \\(f(x;\\hat{w})\\).

We can view classical training as performing approximate Bayesian inference, using the approximate posterior \\(p(w | \\mathcal{D}) \\approx \\delta(w=\\hat{w})\\), where \\(\\delta\\) is a Dirac delta function that is zero everywhere except at \\(\\hat{w}\\). In this case, we recover the standard predictive distribution \\(p(y|x,\\hat{w})\\). From this perspective, many alternatives, albeit imperfect, will be preferable hypothesis — with a single setting of parameters \\(w\\) — we want to use every possible setting of including impoverished Gaussian posterior approximations for \\(p(w|\\mathcal{D})\\), even if the posterior or likelihood are actually highly non-Gaussian and multimodal.

The difference between a classical and Bayesian approach will depend on how sharply peaked the posterior \\(p(w|\\mathcal{D})\\) becomes. If the posterior is sharply peaked, there may be almost no difference, since a point mass may then be a reasonable approximation of the posterior. However, deep neural networks are typically very underspecified by the available data, and will thus have diffuse likelihoods \\(p(\\mathcal{D}|w)\\). Not only are the likelihoods diffuse, but different settings of the parameters correspond to a diverse variety of compelling explanations for the data. Indeed, Garipov et al. \[5\] shows that there are large valleys in the loss landscape of neural networks, over which parameters incur very little loss, but give rise to high performing functions which make meaningfully different predictions on test data. Zołna et al. \[33\] also demonstrates the variety of good solutions that can be expressed by a neural network posterior. This is exactly the setting when we _most_ want to perform a Bayesian model average, which will lead to an ensemble containing many different but high performing models, for better accuracy and better calibration than classical training.

The recent success of _deep ensembles_ \[12\] is not discouraging, but indeed strong motivation for following a Bayesian approach. Deep ensembles involves MAP training of _the same architecture_ many times starting from different random initializations, to find different local optima. Thus _using these models in an ensemble is an approximate Bayesian model average_, with weights that correspond to models with high likelihood and diverse predictions. Instead of using a single point mass to approximate our posterior, as with classical training, we are now using multiple point masses in good locations, enabling a better approximation to the integral in Eq.~(1) that we are trying to solve. The functional diversity is important for a good approximation to the BMA integral, because we are summing together terms of the form \\(p(y|x,w)\\); if two settings of the weights \\(w\_i\\) and \\(w\_j\\) each provide high likelihood (and consequently high posterior mass), but give rise to similar models, then they will be largely redundant in the model average, and the second setting of parameters will not contribute much to the integral estimate.

While a recent report \[22\] shows that deep ensembles appear to outperform some particular approaches to Bayesian neural networks, there are two key reasons behind these results that are actually optimistic for Bayesian approaches. First, the deep ensembles being used are finding many different basins of attraction, corresponding to diverse solutions, which enables _a better approximation to a Bayesian model average_ than the specific Bayesian methods considered in Ovadia et al. \[22\], which focus their modelling effort on a _single_ basin of attraction. The second is that the deep ensembles require retraining a network from scratch many times, which incurs a great computational expense. If one were to control for computation, the approaches which focus on a single basin may be preferred.

There is an important distinction between a Bayesian model average and some approaches to ensembling. The Bayesian model average assumes that _one_ hypothesis (one setting of the weights) is correct, and averages over models due to an inability to distinguish between hypotheses given limited data \[19\]. As we observe more data, the posterior collapses, and the Bayesian model average converges to the maximum likelihood solution. If the true explanation for the data is actually a _combination_ of hypotheses, the Bayesian model average may then perform worse as we observe more data. Some ensembling methods instead work by enriching the hypothesis space, and thus do not collapse in this way. Deep ensembles, however, are finding different MAP or maximum likelihood solutions, corresponding to different basins of attraction, starting from different random initializations. Therefore the deep ensemble will collapse when the posterior concentrates, as with a Bayesian model average. Since the hypothesis space is highly expressive for a modern neural network, posterior collapse in many cases is desirable.

Regarding priors, the prior that matters is the prior in _function space_, not parameter space. In the case of a Gaussian process \[e.g. 28\], a vague prior would be disastrous, as it is a prior directly in function space and would correspond to white noise. However, when we combine a vague prior over parameters \\(p(w)\\) with a structured function form \\(f(x;w)\\) such as a convolutional neural network (CNN), we induce a structured prior distribution over functions \\(p(f(x;w))\\). Indeed, the inductive biases and equivariance constraints in such models is why they work well in classical settings. We can sample from this induced prior over functions by first sampling parameters from \\(p(w)\\) and then conditioning on these parameters in \\(f(x;w)\\) to form a sample from \\(p(f(x;w))\\) \[e.g., 29, Ch 2\]. Alternatively, we can use a neural network kernel with a Gaussian process, to induce a structured distribution over functions \[30\].

Bayesian or not, the prior, just like the functional form of a model, or the likelihood, will certainly be imperfect, and making unassailable assumptions will be impossible. Attempting to avoid an important part of the modelling process because one has to make assumptions, however, will often be a worse alternative than an imperfect assumption. There are many considerations one might have in selecting a prior. Sometimes a consideration is invariance under reparametrization. Parametrization invariance is also a question in considering regularizers, optimization procedures, model specification, etc., and is not specific to whether or not one should follow a Bayesian approach. Nonetheless, I will make some brief additional remarks on these questions.

If we truly have a vague prior over parameters, perhaps subject to some constraint for normalization, then our posterior reflects essentially the same relative preferences between models as our likelihood, for it is a likelihood scaled by a factor that does not depend on \\(w\\) outside some basic constraints. In computing the integral for a Bayesian model average, each setting of parameters is weighted by the quality of the associated function, as measured by the likelihood. Thus the model average is happening in function space, and is invariant to reparametrization. In the context of many standard architectural specifications, there are also some additional benefits to using relatively broad zero-mean centred Gaussian priors, which help provide smoothness in function space by bounding the norm of the weights. But this smoothness is not a central reason to follow a Bayesian approach, as one could realize similar advantages in performing MAP optimization. Bayesian methods are fundamentally about marginalization as an alternative to optimization.

Moreover, vague priors over parameters are also often a reasonable description of our a priori subjective beliefs. We want to use a given functional form, which is by no means vague, but we often do not have any strong a priori preference for a setting of the parameters. It is worth reiterating that a vague prior in parameter space combined with a highly structured model such as a convolutional neural network does _not_ imply a vague prior in function space, which is also why classical training of neural networks provides good results. Indeed, vague parameter priors are often preferable to entirely ignoring epistemic uncertainty, which would be the standard alternative. In fact, ignoring epistemic uncertainty is a key reason that standard neural network training is _miscalibrated_. By erroneously assuming that the model (parameter setting we want to use) is completely determined by a finite dataset, the predictive distribution becomes _overconfident_: for example, the highest softmax output of a CNN that has undergone standard training (e.g. MAP optimization) will typically be much higher than the probability of the corresponding class label \[7\]. Importantly, ignoring epistemic uncertainty also leads to worse accuracy in point predictions, because we are now ignoring all the other compelling explanations for the data. While improvements in calibration are an empirically recognized benefit of a Bayesian approach, the enormous potential for gains in _accuracy_ through Bayesian marginalization with neural networks is a largely overlooked advantage.

There are also many examples where flat priors over parameters combined with _marginalization_ sidestep pathologies of maximum likelihood training. Priors without marginalization are simply regularization, but Bayesian methods are not about regularization \[17, Ch 28\]. And there is a large body of work considering approximate Bayesian methods with uninformative priors over parameters (_but not functions_) \[e.g., 3, 2, 21, 1, 6, 17, 14, 20\]. This approach is well-motivated, marginalization is still compelling, and the results are often better than regularized optimization.

By accounting for epistemic uncertainty through uninformative _parameter_ (but not function) priors, we, as a community, have developed Bayesian deep learning methods with improved calibration, reliable predictive distributions, and improved accuracy \[e.g., 15, 20, 4, 25, 10, 24, 11, 18, 27, 9, 32\]. MacKay \[16\] and Neal \[20\] are particularly notable early works considering Bayesian inference for neural networks. Seeger \[26\] also provides a clear tutorial on Bayesian methods in machine learning. Of course, we can always make better assumptions — Bayesian or not. We should strive to build more interpretable parameter priors. There are works that consider building more informative parameter priors for neural networks by reasoning in function space \[e.g., 27, 31, 13, 8\]. And we should also build better posterior approximations. Deep ensembles are a promising step in this direction.

But we should not undermine the progress we are making so far. Bayesian inference is especially compelling for deep neural networks. Bayesian deep learning is gaining visibility because we are making progress, with good and increasingly scalable practical results. We should not discourage these efforts. If we are shying away from an approximate Bayesian approach because of some challenge or imperfection, we should always ask, _\`\`what is the alternative''?_ The alternative may indeed be a more impoverished representation of the predictive distribution we want to compute.

There are certainly many challenges to computing the integral of Eq. (1) for modern neural networks, including a posterior landscape which is difficult to navigate, and an enormously high (e.g., 30 million) dimensional parameter space. Many of the above papers are working towards addressing such challenges. We have been particularly working on recycling geometric information in the SGD trajectory for scalable approximate Bayesian inference \[9, 18\], exploiting large loss valleys \[5\], and creating subspaces of low dimensionality that capture much of the variability of the network \[9\]. Pradier et al. \[23\] also considers different approaches to dimensionality reduction, based on non-linear transformations. For exploring multiple distinct basins of attraction, we have been developing cyclical stochastic MCMC approaches \[32\], which could be seen as sharing many of the advantages of deep ensembles, but with an added attempt to also marginalize within basins of attraction.

_If you wish to cite this note in your scientific work, here is the bibliographic information:_

@article{wilson2019bayesian,

title={The Case for {B}ayesian Deep Learning},

author={Andrew Gordon Wilson},

note={Accessible at https://ift.tt/36MUibX},

journal={NYU Courant Technical Report},

year={2019}

}

[A PDF version is available here.](https://cims.nyu.edu/~andrewgw/caseforbdl.pdf)

References
----------

\[1\] James Berger et al. The case for objective Bayesian analysis. _Bayesian analysis_, 1(3): 385–402, 2006.

\[2\] James O Berger and Luis R Pericchi. The intrinsic Bayes factor for model selection and prediction. _Journal of the American Statistical Association_, 91(433):109–122, 1996.

\[3\] Merlise Clyde and Edward I George. Model uncertainty. _Statistical science_, pages 81–94, 2004.

\[4\] Yarin Gal and Zoubin Ghahramani. Dropout as a bayesian approximation: Representing model uncertainty in deep learning. In _international conference on machine learning_, pages 1050–1059, 2016.

\[5\] Timur Garipov, Pavel Izmailov, Dmitrii Podoprikhin, Dmitry P Vetrov, and Andrew Gordon Wilson. Loss surfaces, mode connectivity, and fast ensembling of DNNs. In _Neural Information Processing Systems_, 2018.

\[6\] Andrew Gelman, John B Carlin, Hal S Stern, David B Dunson, Aki Vehtari, and Donald B Rubin. _Bayesian data analysis_. Chapman and Hall/CRC, 2013.

\[7\] Chuan Guo, Geoff Pleiss, Yu Sun, and Kilian Q Weinberger. On calibration of modern neural networks. In _Proceedings of the 34th International Conference on Machine Learning-Volume 70_, pages 1321–1330. JMLR. org, 2017.

\[8\] Danijar Hafner, Dustin Tran, Alex Irpan, Timothy Lillicrap, and James Davidson. Reliable uncertainty estimates in deep neural networks using noise contrastive priors. _arXiv preprint arXiv:1807.09289_, 2018.

\[9\] Pavel Izmailov, Wesley J Maddox, Polina Kirichenko, Timur Garipov, Dmitry Vetrov, and Andrew Gordon Wilson. Subspace inference for Bayesian deep learning. In _Uncertainty in Artificial Intelligence_, 2019.

\[10\] Alex Kendall and Yarin Gal. What uncertainties do we need in Bayesian deep learning for computer vision? In _Advances in neural information processing systems_, pages 5574–5584, 2017.

\[11\] Mohammad Emtiyaz Khan, Didrik Nielsen, Voot Tangkaratt, Wu Lin, Yarin Gal, and Akash Srivastava. Fast and scalable bayesian deep learning by weight-perturbation in adam. _arXiv preprint arXiv:1806.04854_, 2018.

\[12\] Balaji Lakshminarayanan, Alexander Pritzel, and Charles Blundell. Simple and scalable predictive uncertainty estimation using deep ensembles. In _Advances in Neural Information Processing Systems_, pages 6402–6413, 2017.

\[13\] Christos Louizos, Xiahan Shi, Klamer Schutte, and Max Welling. The functional neural process. In _Advances in Neural Information Processing Systems_, 2019.

\[14\] D. J. MacKay. Bayesian interpolation. _Neural Computation_, 4(3):415–447, 1992.

\[15\] David JC MacKay. Bayesian methods for adaptive models. _PhD thesis, California Institute of Technology_, 1992.

\[16\] David JC MacKay. Probable networks and plausible predictions?a review of practical bayesian methods for supervised neural networks. _Network: computation in neural systems_, 6(3):469–505, 1995.

\[17\] David JC MacKay. Information theory, inference and learning algorithms. Cambridge university press, 2003.

\[18\] Wesley Maddox, Timur Garipov, Pavel Izmailov, Dmitry Vetrov, and Andrew Gordon Wilson. A simple baseline for bayesian uncertainty in deep learning. In _Advances in Neural Information Processing Systems_, 2019.

\[19\] Thomas P Minka. Bayesian model averaging is not model combination. _Available electronically at_ [http://www.stat.cmu.edu/minka/papers/bma.html](http://www.stat.cmu.edu/minka/papers/bma.html), 2000.

\[20\] R.M. Neal. Bayesian Learning for Neural Networks. Springer Verlag, 1996. ISBN 0387947248.

\[21\] Anthony O’Hagan. Fractional Bayes factors for model comparison. _Journal of the Royal Statistical Society: Series B (Methodological)_, 57(1):99–118, 1995.

\[22\] Yaniv Ovadia, Emily Fertig, Jie Ren, Zachary Nado, D Sculley, Sebastian Nowozin, Joshua V Dillon, Balaji Lakshminarayanan, and Jasper Snoek. Can you trust your model’s uncertainty? evaluating predictive uncertainty under dataset shift. _arXiv preprint arXiv:1906.02530_, 2019.

\[23\] Melanie F Pradier, Weiwei Pan, Jiayu Yao, Soumya Ghosh, and Finale Doshi-Velez. Latent projection bnns: Avoiding weight-space pathologies by learning latent representations of neural network weights. _arXiv preprint arXiv:1811.07006_, 2018.

\[24\] Hippolyt Ritter, Aleksandar Botev, and David Barber. A scalable Laplace approximation for neural networks. In _International Conference on Learning Representations (ICLR)_, 2018.

\[25\] Yunus Saatci and Andrew G Wilson. Bayesian GAN. In _Advances in neural information processing systems_, pages 3622–3631, 2017.

\[26\] Matthias Seeger. Bayesian modelling in machine learning: A tutorial review. _Technical report_, 2006.

\[27\] Shengyang Sun, Guodong Zhang, Jiaxin Shi, and Roger Grosse. Functional variational bayesian neural networks. _arXiv preprint arXiv:1903.05779_, 2019.

\[28\] Christopher KI Williams and Carl Edward Rasmussen. Gaussian processes for machine learning. the MIT Press, 2(3):4, 2006.

\[29\] Andrew Gordon Wilson. Covariance kernels for fast automatic pattern discovery and extrapolation with Gaussian processes. _PhD thesis, University of Cambridge_, 2014.

\[30\] Andrew Gordon Wilson, Zhiting Hu, Ruslan Salakhutdinov, and Eric P Xing. Deep kernel learning. In _Artificial Intelligence and Statistics_, pages 370–378, 2016.

\[31\] Wanqian Yang, Lars Lorch, Moritz A Graule, Srivatsan Srinivasan, Anirudh Suresh, Jiayu Yao, Melanie F Pradier, and Finale Doshi-Velez. Output-constrained bayesian neural networks. _arXiv preprint arXiv:1905.06287_, 2019.

\[32\] Ruqi Zhang, Chunyuan Li, Jianyi Zhang, Changyou Chen, and Andrew Gordon Wilson. Cyclical stochastic gradient MCMC for Bayesian deep learning. In _International Conference on Learning Representations_, 2020.

\[33\] Konrad Zołna, Krzysztof J Geras, and Kyunghyun Cho. Classifier-agnostic saliency map extraction. In _Proceedings of the AAAI Conference on Artificial Intelligence_, volume 33, pages 10087–10088, 2019.

  
  
from Hacker News https://ift.tt/2RlpU27