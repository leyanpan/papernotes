# On The Implicit Bias Towards Depth Minimization In Deep Neural Networks

## Metadata
Authors: Tomer Galanti, Liane Galanti, Ido Ben-Shaul
Affiliation: MIT CBMM, Tel Aviv University
Link: https://arxiv.org/pdf/2202.09028.pdf
Conference: Conference on the Mathematical Theory of Deep Neural Networks, DEEPMATH, 2022.
## Summary
Observed that Stochastic Gradient Descent (SGD) has implicit bias towards **solutions with low effective depth** when training deep neural networks, i.e. the layer features becomes NCC separable w.r.t. the class labels at an early layer. Shows that low-depth solutions enables better generalization through theoretical analysis.

## Main findings
For a given dataset and neural network architecture (MLP, CNN), any network with $L\geq L_0$ trained using SGD and weight decay will NCC separate the features (with small error) in the first $L_0$ layers regardless of $L$. $L_0$ is approximately equal to the Minimal NCC depth for the given architecture.

Showed that the generalization error of the trained model has an upper bound improves with lower effective depth of the trained model relative to the minimal effective depth of the model architecture w.r.t. a larger noisy dataset from the same distribution. Due to the observation that $L_0$ remains constant regardless of $L$ the bound is also mostly independent from the model depth $L$.

Experimentally showed that 1. the effective depth of the trained model is independent of model depth. 2. Corrupted labels increase effective depth for given error $\epsilon$

## Mathematical Details and Techniques
The main theorem in this paper is the following:

**Proposition 1** let $m\in \mathbb{N},p\in(0,\frac{1}{2}),\alpha \in(0, 1), \epsilon \in (0, 1)$. Assume that the error of the learning algorithm is $\delta_m^1$-uniform. Assume that $S_1,S_2\sim P_B(m)$. Let $h_{S_1}^\gamma$ be the output of the learning algorithm given access to a dataset $S_1$ and initialization $\gamma$, Then, $$\mathbb{E}_{S_1}\mathbb{E}_{\gamma}[err_P(h^\gamma_{S_1})]\leq \mathbb{P}_{S_1,S_2,\tilde{Y}_2}[\mathbb{E}_\gamma[d_{S_1}^\epsilon(h_{S_1}^\gamma)]\geq d_{min}^\epsilon(\mathcal{G},S_1\cup\tilde{S}_2)]+(1+\alpha)p+\delta_m^1+\delta_{m,p,\alpha}^2$$
* $\tilde{Y}_2$ is a set of labels for $S_2$ that differes from the correct labels by $pm$ labels
* $P_B(m)$: $m$ points from the true distribution $P$
* $d_{min}^\epsilon(\mathcal{G},S_1\cup\tilde{S}_2)$ is the minimum effective depth of neural network architecture $\mathcal{G}$ to NCC fit $S_1\cup\tilde{S}_2$ with error at most $\epsilon$
* $d_{S_1}^\epsilon(h_{S_1}^\gamma)$ is the effective depths of model $h_{S_1}^\gamma$ trained on $S_1$ with initial weight $\gamma$ that NCC fits $S_1$ with error at most $\epsilon$
* $\delta_m^1$-uniform: With probability $\geq 1-\delta_m^1$ over the choice of $S_1,S_2\sim P_B(m)$, the labels and indices of mistaken labels of trained model $h_{S_1}^\gamma$ over $S_2$ are uniformly distributed as a function of the initialization $\gamma$.
* $\delta_{m,p,\alpha}^2:=\mathbb{P}_{S_1,S_2\sim P_B(m),\tilde{Y}_{2,p}}[\exists q\geq (1+\alpha)p:d^\epsilon_{min}(\mathcal{G},S_1\cup\tilde{S}_{2,p})>\mathbb{E}_{\tilde{Y}_{2,q}}[d^\epsilon_{min}(\mathcal{G},S_1\cup\tilde{S}_{2,q})]]$
    * This term representes the assumption that more noise in the dataset require more effective depth to fit
    * In words, $\delta_{m,p,\alpha}^2$ is the probability of drawing $pm$ noisy labels which would cause the minimal effective depth to increase beyond the expected minimal effective depth of even more noisy labels ($qm$)
* $p$ is a guess on how much error the trained model have on $S_2$
* Why is $\epsilon$ not a term in this bound?

## Further Questions
1. Does weight decay affect the effective depth of the trained network?
2. Will the network always find the minimal depth that achieves NCC separability?
    * For exmaple, generate random weights for a $L_0$ layer network of the same architecture and see if the model is always able to achieve high-NCC accuracy at layer $L_0$
3. Can we use the features from the first layer that achieves NCC separability?
## Citation
