# Exploring Deep Neural Networks via Layer-Peeled Model: Minority Collapse in Imbalanced Training

## Metadata
Authors: Cong Fang, Hangfeng He, Qi Long, Weijie Su
Affiliation: Peking University, University of Pennsylvania
Journal: PNAS
Link: https://www.pnas.org/doi/10.1073/pnas.2103091118

## Summary

Observed that minority classes that only occupy a small (about $\frac{1}{100}$) ratio of training dataset exhibits "Minority Collapse" where minority class features are indistinguishable from each other and thus cannot be classified. This fundamentally limits the ability of deep neural networks trained with CE loss to correctly classify between underrepresented classes. It is also the paper that proposed to use the layer-peeled model for neural collapse analysis.

## Motivation
Use the layer-peeled model from Neural Collapse to explain why imbalanced datasets are harmful for neural network classifier performance. Furthermore, explore from a theoretical standpoint how this phenomenon can be mitagated through oversampling of minority classes.

## Main Findings
Consider a dataset of 2 different class sizes: the first $K_A$ majority classes each contain $n_A$ training samples while the remaining $K_B$ minority classes have $n_B$ training samples. Let $R=\frac{n_A}{n_B}>1$ be the imbalance ration, then

![image](../imgs/Minority%20Finding%202.png)

The required $R$ is smaller for models trained with larger weight decay constants:

<p align='center'>
    <img src="../imgs/Minority%20Cos%20R.png" alt= “” width="50%" height="50%">
</p>

While the empirical findings indicates that there exists a constant $R_0>0$ such that minority collapse for all $R>R_0$, the authors only theoretically showed minority collapse for $R\rightarrow \infty$:

<p align='center'>
    <img src="../imgs/Minority%20Theorem%205.png" alt= “” width="100%" height="100%">
</p>

## Mathematical Techniques
TBD

## Further Work

## Citation

```
@article{
doi:10.1073/pnas.2103091118,
author = {Cong Fang  and Hangfeng He  and Qi Long  and Weijie J. Su },
title = {Exploring deep neural networks via layer-peeled model: Minority collapse in imbalanced training},
journal = {Proceedings of the National Academy of Sciences},
volume = {118},
number = {43},
pages = {e2103091118},
year = {2021},
doi = {10.1073/pnas.2103091118},
URL = {https://www.pnas.org/doi/abs/10.1073/pnas.2103091118},
eprint = {https://www.pnas.org/doi/pdf/10.1073/pnas.2103091118},
abstract = {In this paper, we introduce the Layer-Peeled Model, a nonconvex, yet analytically tractable, optimization program, in a quest to better understand deep neural networks that are trained for a sufficiently long time. As the name suggests, this model is derived by isolating the topmost layer from the remainder of the neural network, followed by imposing certain constraints separately on the two parts of the network. We demonstrate that the Layer-Peeled Model, albeit simple, inherits many characteristics of well-trained neural networks, thereby offering an effective tool for explaining and predicting common empirical patterns of deep-learning training. First, when working on class-balanced datasets, we prove that any solution to this model forms a simplex equiangular tight frame, which, in part, explains the recently discovered phenomenon of neural collapse [V. Papyan, X. Y. Han, D. L. Donoho, Proc. Natl. Acad. Sci. U.S.A. 117, 24652–24663 (2020)]. More importantly, when moving to the imbalanced case, our analysis of the Layer-Peeled Model reveals a hitherto-unknown phenomenon that we term Minority Collapse, which fundamentally limits the performance of deep-learning models on the minority classes. In addition, we use the Layer-Peeled Model to gain insights into how to mitigate Minority Collapse. Interestingly, this phenomenon is first predicted by the Layer-Peeled Model before being confirmed by our computational experiments.}}
```

