---
layout: post
title: Comment on Minka's energy function for Expectation Propagation
comments: true
---

This note contains some comments about the energy function proposed by Minka for expectation propagation (EP). For simplicity we consider discrete variables $\mathbf x$. The goal is to obtain an approximation to the posterior:

$$p(\mathbf x|D) \propto p(\mathbf x) \prod_{i=1}^N t_i (\mathbf x)
\approx p(\mathbf x) \prod_{i=1}^N \tilde t_i (\mathbf x)$$

using functions $\tilde t_i (\mathbf x)$ from an exponential family

$$\tilde t_i (\mathbf x) = \exp \left( \sum_j \tau_{ij} f_j (\mathbf x) \right)$$

for some parameters $\tau_{ij}$.

# The primal energy function

Minka defines a *primal energy function*,

$$\begin{aligned}
\mathcal J (\hat p, q)
&= \sum_{i=1}^N \sum_{\mathbf x} \hat p_i (\mathbf x) \ln \frac{\hat p_i (\mathbf x)}{t_i (\mathbf x) p (\mathbf x)} - (N - 1) \sum_{\mathbf x} q (\mathbf x) \ln \frac{q (\mathbf x)}{p (\mathbf x)}
\\
&= \sum_{i=1}^N \mathrm{KL} (\hat p_i||t_i p) - (N - 1) \mathrm{KL} (q||p)
\end{aligned}$$

By the convexity of the Kullback-Leibler (KL) divergence, $\mathcal J(\hat p,q)$ is convex in $\hat p$ and concave in $q$.

Minka proposes the following minimax optimization to obtain $\hat p, q$:

$$\min_{\hat p}\max_q\mathcal J (\hat p, q)$$

subject to the following constrains on $\hat p, q$:

$$\hat p_i(\mathbf x) \ge 0,\quad \hat q(\mathbf x)\ge 0,\quad \sum_\mathbf x\hat p_i(\mathbf x) = \sum_\mathbf x q(\mathbf x) = 1$$

$$\sum_{\mathbf x} f_j (\mathbf x) \hat p_i (\mathbf x) = \sum_{\mathbf x} f_j (\mathbf x) q(\mathbf x)$$

The first constrains make sure that $\hat p_i,q$ are normalized probability distributions. The last constrain is the _moment matching constrain_. The moment matching constrain couples the distributions $\hat p_i$ and $q$. I found it helpful to consider a more restricted problem, where we specify _a priori_ the moments of $f_j$ under $\hat p_i$ and $q$. We replace the moment-matching constrain by a simple moment constrain:

$$\sum_{\mathbf x} f_j (\mathbf x) \hat p_i (\mathbf x) = \sum_{\mathbf x} f_j (\mathbf x) q(\mathbf x) = F_j$$

with given values $F_j$. In the restricted problem the distributions $\hat p_i,q$ can be found by solving the following independent problems:

$$\min_{\hat p_i}\mathrm{KL} (\hat p_i||t_i p),\qquad
  \min_{q}\mathrm{KL} (q||p)$$

subject to $\hat p_i,q$ being normalized probability distributions and the moment constrains $\langle f_j\rangle_{\hat p_i} = \langle f_j\rangle_q = F_j$. Thus knowledge of $F_j$ uncouples the $\hat p_i,q$. If the moments of $f_j$ in the solution of the original problem are $F_j^\ast$, then the restricted problem yields the same solution provided we set $F_j = F_j^\ast$.

For a given $F_j$, the distributions $\hat p_i,q$ must have the forms (as follows from the standard Lagrangian method)

$$\begin{aligned}
\hat p_i(\mathbf{x}) &= t_i(\mathbf x)p(\mathbf x)\exp\left(-\lambda_i - \sum_j\gamma_{ij}f_j(\mathbf x)-1\right)\\
q(\mathbf x) &= p(\mathbf x)\exp\left(-\lambda-\sum_j\gamma_j f_j(\mathbf x)-1\right)
\end{aligned}$$

where $\lambda,\lambda_i$ follow from normalization, and $\gamma_{ij},\gamma_j$ must be chosen so as to satisfy the moment constrains $\langle f_j\rangle_{\hat p_i} = \langle f_j\rangle_q = F_j$. Let $\mathcal J(F)$ denote the value of $\mathcal J(\hat p,q)$ when $\hat p,q$ are substituted for these expressions. Then the optimal $F_j^\ast$ must be the minimizers:

$$\min_F \mathcal J(F) = \mathcal J(F^\ast)$$

Note that if the objective had been $\max_q\min_{\hat p} \mathcal J$ instead of $\min_{\hat p}\max_q \mathcal J$, we would have obtained that the optimal $F$ are _maximizers_ of $\mathcal J(F)$ instead of minimizers. Thus, unless $\mathcal J(F)$ was a constant independent of $F$ (or the domain of values of $F$ was a point), we obtain the strict inequality

$$\min_{\hat p}\max_q \mathcal J(\hat p,q) = \min_F \mathcal J(F) < \max_F \mathcal J(F) = \max_q\min_{\hat p} \mathcal J(\hat p,q)$$

where the optimizations w.r.t. $\hat p,q$ are carried out subject to the constrains in Minka's paper.

For example, if $t_i$ are uniform distributions, then $\hat p_i,q$ are the same for any given $F$, and $\mathcal J(F)$ reduces to $\mathrm{KL} (\hat q \vert\vert p)$. The minimum is attained when $F_j=\langle f_j\rangle_p$, in which case $\mathcal J=0$. By the properties of the KL divergence, if $F_j\ne\langle f_j\rangle_p$, then $\mathcal J>0$. This example demonstrates how $\mathcal J(F)$ can depend on $F$ and therefore that the minimax and maximin problems are *not* equivalent.

This raises the question. *Does EP reach a pair of distributions that solve the minmax or the maxmin problem?*

# KL duality

Minka notes the following variational formula for the KL divergence (assuming $\sum_\mathbf x p(\mathbf x)=1)$:

$$\mathrm{KL}(p||q) = \max_\nu \mathcal Q(p,q,\nu)$$

where

$$\mathcal Q(p,q,\nu) = \sum_{\mathbf x} p(\mathbf x) \nu(\mathbf x) - \ln \sum_{\mathbf x} q(\mathbf x) \mathrm e^{\nu(\mathbf x)}$$

This can be shown directly by differentiation w.r.t. $\nu(\mathbf x)$. We have:

$$\frac{\partial\mathcal Q}{\partial\nu\left(\mathbf{x}\right)}=p(\mathbf{x})-\ln\sum_{\mathbf{x}}q(\mathbf{x})\mathrm{e}^{\nu(\mathbf{x})}$$

Thus the critical points are:

$$\nu^*(\mathbf x) = \ln(p(\mathbf x)/q(\mathbf x)) + \text{const}$$

where $\text{const}$ is independent of $\mathbf x$. Evaluating $\mathcal Q$ at this critical point gives,

$$\mathcal Q(p,q,\nu^*) = \sum_{\mathbf{x}}p(\mathbf{x})\ln\frac{p\left(\mathbf{x}\right)}{q\left(\mathbf{x}\right)}-\ln\sum_{\mathbf{x}}q(\mathbf{x})\frac{p\left(\mathbf{x}\right)}{q\left(\mathbf{x}\right)}=\sum_{\mathbf{x}}p(\mathbf{x})\ln\frac{p\left(\mathbf{x}\right)}{q\left(\mathbf{x}\right)}$$

(Note the usage of the assumption $\sum_\mathbf x p(\mathbf x)=1$). The arbitrary constant cancels.

To verify that this is a maximum, it suffices to note that $\mathcal Q(p,q,\nu)$ is a concave function of $\nu$ (the log-sum-exp function).

An alternative derivation follows from noting that this variational formula of the KL divergence is equivalent to the Legendre transform of the KL w.r.t. to the first argument.

## Energy function with KL duality

Employing the KL duality we obtain,

$$\mathcal J (\hat p,q) = \max_\lambda\min_\nu \mathcal A(\hat p,q,\lambda,\nu)
= \min_\nu\max_\lambda \mathcal A(\hat p,q,\lambda,\nu)$$

where

$$\begin{aligned}
\mathcal A(\hat p,q,\lambda,\nu) =
& \left\{
    \sum_i\sum_{\mathbf x} \hat p_i(\mathbf x)\lambda_i(\mathbf x) - \sum_i\ln \sum_\mathbf x t_i(\mathbf x)p(\mathbf x)\mathrm e^{\lambda_i(\mathbf x)}
\right. \\
& \left.
    -(n-1)\sum_\mathbf x q(\mathbf x)\nu(\mathbf x)
    -(n-1)\ln\sum_\mathbf x q(\mathbf x)\mathrm e^{\nu(\mathbf x)}
\right\}
\end{aligned}$$

Note that $\max_\lambda\min_\nu$ gives the same result as $\min_\nu\max_\lambda$, because the terms involving these variables are independent.

Therefore,

$$\min_{\hat p_i}\max_q \mathcal J (\hat p, q)
= \min_{\hat p_i}\max_q\max_\lambda\min_\nu \mathcal A(\hat p,q,\lambda,\nu)$$

subject to $\hat p,q$ being normalized probability distributions and the moment-matching constrain, while $\lambda,\nu$ are not constrained.

**To be continued ...**

## References

1. Thomas P. Minka, “The EP Energy Function and Minimization Schemes” (Technical report, 2001) ([link](https://tminka.github.io/papers/ep/minka-ep-energy.pdf)).
2. Minka, Thomas P. “Expectation Propagation for Approximate Bayesian Inference.” In Proceedings of the Seventeenth Conference on Uncertainty in Artificial Intelligence, 362–369. UAI’01. San Francisco, CA, USA: Morgan Kaufmann Publishers Inc., 2001. ([link](http://dl.acm.org/citation.cfm?id=2074022.2074067)).
3. Žaković, Stanislav, Costas Pantelides, and Berc Rustem. “An Interior Point Algorithm for Computing Saddle Points of Constrained Continuous Minimax.” Annals of Operations Research 99, no. 1–4 (December 1, 2000): 59–77. ([link](https://doi.org/10.1023/A:1019284715657)).
4. [Log-sum-exp]({% post_url convexity/2018-04-20-log-sum-exp %})
5. [Kullback-Leibler divergence]({% post_url convexity/2018-05-01-KL-divergence %})
6. Bertsekas, Dimitri P. Nonlinear Programming. 2nd ed. Athena Scientific, 1999.