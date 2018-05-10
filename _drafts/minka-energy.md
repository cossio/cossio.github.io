---
layout: post
title: Energy function of Expectation Propagation
comments: true
---
# Energy function of Expectation Propagation

This note contains some comments about the energy function proposed by Minka for expectation propagation (EP). For simplicity we consider discrete variables $\mathbf x$. The goal is to obtain an approximation to the posterior:

$$p(\mathbf x|D) \propto p(\mathbf x) \prod_i t_i (\mathbf x)
\approx p(\mathbf x) \prod_ i \tilde t_i (\mathbf x)$$

using functions $\tilde t_i (\mathbf x)$ from an exponential family

$$\tilde t_i (\mathbf x) = \exp \left( \sum_j \tau_{ij} f_j (\mathbf x) \right)$$

for some parameters $\tau_{ij}$.

## The primal energy function

Minka defines a *primal energy function*,

$$\begin{aligned}
\mathcal J (\hat p, q)
&= \sum_i \sum_{\mathbf x} \hat p_i (\mathbf x) \ln \frac{\hat p_i (\mathbf x)}{t_i (\mathbf x) p (\mathbf x)} - (n - 1) \sum_{\mathbf x} q (\mathbf x) \ln \frac{q (\mathbf x)}{p (\mathbf x)}
\\
&= \sum_ i \mathrm{KL} (\hat p_i (\mathbf x)||t_i (\mathbf x) p (\mathbf x)) - (n - 1) \mathrm{KL} (q (\mathbf x) || p(\mathbf x))
\end{aligned}$$

By the convexity of the Kullback-Leibler (KL) divergence, $\mathcal J(\hat p,q)$ is convex in $\hat p$ and concave in $q$.

Minka proposes the following minimax optimization to obtain $\hat p, q$:

$$\min_{\hat p_i}\max_q \mathcal J (\hat p, q)$$

subject to the following constrains on $\hat p_i, q$:

$$\hat p_i(\mathbf x) \ge 0, \qquad q(\mathbf x) \ge 0$$

$$\sum_{\mathbf x}\hat p_i (\mathbf x) = 1,\qquad \sum_{\mathbf x}q\left(\mathbf x\right) = 1$$

$$\sum_{\mathbf x} f_j (\mathbf x) \hat p_i (\mathbf x) = \sum_{\mathbf x} f_j (\mathbf x) q(\mathbf x)$$

The first two constrains are simply the conditions for $\hat p_i,q$ to be normalized probability distributions, while the third constrain is the moment-matching condition.

### Questions

I have some unresolved questions at this point. Is the following equality true?

$$\min_{\hat p_i}\max_q \mathcal J (\hat p, q)
= \max_q\min_{\hat p_i} \mathcal J (\hat p, q)\qquad \text{(?)}$$

If this equality does not hold, then what kind of point does EP reach? The $\min\max$, the $\max\min$, or both?

## KL duality

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

(Note the usage of the assumption $\sum_\mathbf x p(\mathbf x)=1$).

To verify that this is a maximum, note that $\mathcal Q(p,q,\nu)$ is a concave function of $\nu$ (the log-sum-exp function).

An alternative derivation follows from noting that this variational formula of the KL divergence uses the Legendre transform of the KL w.r.t. to the first argument.

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

subject to the constrains above on $\hat p,q$.

## Lagrangian formalism

Define the Lagrangian,

$$\begin{aligned}
\mathcal L
&= \mathcal J(\hat p, q)
+\sum_i \alpha_i \left(\sum_\mathbf x \hat p_i(\mathbf x) - 1\right)
+\beta \left(\sum_\mathbf x q(\mathbf x) - 1\right) \\
&+\sum_{ij} \gamma_{ij} \sum_\mathbf{x} (\hat p_i(\mathbf x) - q(\mathbf x))f_j(\mathbf x) \\
&-\sum_i\sum_\mathbf x \delta_i(\mathbf x)\hat p_i(\mathbf x)
-\sum_\mathbf x \theta(\mathbf x)q(\mathbf x)
\end{aligned}$$

The distributions $\hat p^*,q^*$ solve the minimax problem stated above, if and only if there exist numbers $\alpha_i,\beta,\gamma_{ij},\delta_i(\mathbf x),\theta(\mathbf x)$ such that $\hat p^*,q^*$ solve the equations

$$\frac{\partial\mathcal L}{\partial \hat p} = 0
\quad \text{and} \quad
\frac{\partial \mathcal L}{\partial q} = 0$$

## References

1. Thomas P. Minka, “The EP Energy Function and Minimization Schemes” (Technical report, 2001) ([link](https://tminka.github.io/papers/ep/minka-ep-energy.pdf)).
2. Minka, Thomas P. “Expectation Propagation for Approximate Bayesian Inference.” In Proceedings of the Seventeenth Conference on Uncertainty in Artificial Intelligence, 362–369. UAI’01. San Francisco, CA, USA: Morgan Kaufmann Publishers Inc., 2001. ([link](http://dl.acm.org/citation.cfm?id=2074022.2074067)).
3. Žaković, Stanislav, Costas Pantelides, and Berc Rustem. “An Interior Point Algorithm for Computing Saddle Points of Constrained Continuous Minimax.” Annals of Operations Research 99, no. 1–4 (December 1, 2000): 59–77. ([link](https://doi.org/10.1023/A:1019284715657)).
4. [Log-sum-exp]({% post_url 2018-04-20-log-sum-exp %})
5. [Log-sum-exp]({% post_url 2018-05-01-KL-divergence %})