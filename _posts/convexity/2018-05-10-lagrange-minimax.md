---
layout: post
title: Lagrangian formalism for minimax problems
comments: true
---

Let $f:X\times Y\rightarrow\mathbb R$ be a saddle-function (convex in $x$, concave in $y$), where $X\in\mathbb R^n$ and $Y\in\mathbb R^m$ are convex sets. We consider a restricted domain $\Omega \subset X\times Y$ defined by the constrains

$$g_i(x,y) \le 0, \quad i= 1,\dots,p$$

$$h_j(x,y) = 0, \quad j= 1,\dots,q$$

where the functions $g_i:X\times Y\rightarrow\mathbb R$ are convex in both arguments, and the functions $h_j:X\times Y\rightarrow\mathbb R$ are affine. Then $\Omega$ is a convex set. Furthermore we assume that the functions $f,g_i,h_j$ are all differentiable.

The sets $\Omega(x,\cdot)\subset Y$ and $\Omega(\cdot,y)\subset X$ defined by

$$\Omega(x,\cdot)=\{y \in Y : (x,y) \in \Omega\},\quad x\in X$$

$$\Omega(\cdot,y)=\{x \in X : (x,y) \in \Omega\},\quad y\in Y$$

are also convex.

In this note we investigate the minimax and maximin problems,

$$f^{(1)} = \max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y),\qquad
  f^{(2)} = \min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)$$

# Lagrangian formalism

Define the Lagrangian,

$$L(x,y,\lambda,\nu) = f(x,y) + \sum_i\lambda_i g_i(x,y) + \sum_j\nu_j h_j(x,y)$$

For all $(x,y)\in\Omega$:

* If $\lambda_i\ge0$ for all $i$, then $L(x,y,\lambda,\nu) \le f(x,y)$.
* If $\lambda_i\le0$ for all $i$, then $L(x,y,\lambda,\nu) \ge f(x,y)$.

This follows from the fact that $(x,y)\in\Omega$ implies $g_i(x,y)\le0$ and $h_j(x,y)=0$.

Define the Lagrange dual functions

$$G(y,\lambda,\nu) = \min_{x\in X} L(x,y,\lambda,\nu), \qquad
  H(x,\lambda,\nu) = \max_{y\in Y} L(x,y,\lambda,\nu)$$

Let $(x,y)\in\Omega$. Then,

* If $\lambda_i\ge0$ for all $i$, then $G(y,\lambda,\nu) \le L(x,y,\lambda,\nu) \le f(x,y)$.
* If $\lambda_i\le0$ for all $i$, then $H(x,\lambda,\nu) \ge L(x,y,\lambda,\nu) \ge f(x,y)$.

Since these inequalities hold for all $(x,y)\in\Omega$, it follows that:

* If $\lambda_i\ge0$ for all $i$, then $G(y,\lambda,\nu) \le \min_{x\in\Omega(\cdot,y)} f(x,y)$.
* If $\lambda_i\le0$ for all $i$, then $H(x,\lambda,\nu) \ge \max_{y\in\Omega(x,\cdot)} f(x,y)$.

Provided certain regularity conditions are met, we can assume that strong duality holds:

$$\min_{x\in\Omega(\cdot,y)} f(x,y) = \max_{\lambda \ge 0}\max_\nu G(y,\lambda,\nu)$$

$$\max_{y\in\Omega(x,\cdot)} f(x,y) = \min_{\lambda \le 0}\min_\nu H(x,\lambda,\nu)$$

For example, since $f(x,y)$ is convex in $x$ and concave in $y$, the $g_i(x,y)$ are convex in both arguments, and the $h_j(x,y)$ are affine, the problems

$$\min_{x\in\Omega(\cdot,y)} f(x,y),\qquad \max_{y\in\Omega(x,\cdot)} f(x,y)$$

are a convex minimization problem and a concave maximization problem, respectively. In this case a sufficient condition for strong duality is the Slater constrain qualification (see Ref. 1), which is usually met in practice.

It follows that

$$f^{(1)} = \max_{y\in Y}\max_{\lambda \ge 0} \max_\nu G(y,\lambda,\nu),\quad
  f^{(2)} = \min_{x\in X}\min_{\lambda \le 0} \min_\nu H(x,\lambda,\nu).$$

Substituting the definitions of the Lagrange dual functions,

$$f^{(1)} = \max_{y\in Y}\max_{\lambda \ge 0}\max_\nu\min_{x\in X} L(x,y,\lambda,\nu),\quad
  f^{(2)} = \min_{x\in X}\min_{\lambda \le 0}\min_\nu\max_{y\in Y} L(x,y,\lambda,\nu).$$

Since $\max$ always commutes with $\max$ and $\min$ with $\min$, we can reorder the optimizations to obtain:

$$f^{(1)} = \max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu),\quad
  f^{(2)} = \min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu).$$

Thus we have transformed the original maximin/minimax problems into equivalent maximin/minimax problems for the Lagrangian. Notably, in the original problem in $f$,we had constrains copuling both variables $x,y$. In the Lagrangian version, there are no constrains coupling these variables.

Therefore, we have shown that a minimax (maximin) problem in a saddle-function with convex constrains coupling both variables is equivalent to another minimax (maximin) problem where the coupling constrains are gone. However note that $L$ is no longer a saddle-function. So losing the coupling constrains comes at a cost.

## Optimizing over $\lambda,\nu$

Fix $x\in X,y\in Y$. We have

$$\max_{\lambda_i\ge0}\lambda_ig_i(x,y) = \begin{cases}
  0       & g_i(x,y)\le0 \\
  \infty  & g_i(x,y) > 0
\end{cases}
\qquad
\min_{\lambda_i\le0}\lambda_ig_i(x,y) = \begin{cases}
  0       & g_i(x,y)\le0 \\
  -\infty & g_i(x,y) > 0
\end{cases}$$

$$\max_{\nu_j}\nu_jh_j(x,y) = \begin{cases}
  0       & h_j(x,y) = 0 \\
  \infty  & h_j(x,y)\ne0
\end{cases}
\qquad
\min_{\nu_j}\nu_jh_j(x,y) = \begin{cases}
  0       & h_j(x,y) = 0 \\
  -\infty & h_j(x,y)\ne0
\end{cases}$$

Therefore,

$$\max_{\lambda \ge 0}\max_\nu L(x,y,\lambda,\nu) =
\begin{cases}
  f(x,y)  & (x,y)\in    \Omega \\
  \infty  & (x,y)\notin \Omega
\end{cases}$$

$$\min_{\lambda \le 0}\min_\nu L(x,y,\lambda,\nu) =
\begin{cases}
  f(x,y)  & (x,y)\in    \Omega \\
  -\infty & (x,y)\notin \Omega
\end{cases}$$

It follows that

$$f^{(1)}=\max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)
, \quad
  f^{(2)}=\min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)$$

Ntoe that these equalities do not depend on convexity assumptions or constrain qualifications. Comparing this to the previous Lagrangian optimizations derived for $f^{(i)},i=1,2$ (which do require convexity and constrain qualifications), we obtain the following equalities,

$$\max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)
= \max_{y\in Y}\min_{x\in X}\max_{\lambda \ge 0}\max_\nu L(x,y,\lambda,\nu)$$

$$\min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)
= \min_{x\in X}\max_{y\in Y}\min_{\lambda \le 0}\min_\nu L(x,y,\lambda,\nu)$$

This is as far as we can get.

# References

1. Boyd, Stephen P., and Lieven Vandenberghe. Convex Optimization. Cambridge, UK ; New York: Cambridge University Press, 2004. Specially Chapter 5 on Lagrangian duality.
2. [The minimax inequality and saddle-points]({{ site.baseurl }}{% post_url convexity/2018-04-24-minimax %})
3. Shimizu, K., and E. Aiyoshi. “Necessary Conditions for Min-Max Problems and Algorithms by a Relaxation Procedure.” IEEE Transactions on Automatic Control 25, no. 1 (February 1980): 62–66. [Link](https://doi.org/10.1109/TAC.1980.1102226). _Similarly to what I did here, this paper shows that the minimax problem with coupling constrains (subject to some convexity requirements) is equivalent to a Lagrangian minimax without coupling constrains. It is the only paper that I have found that considers the minimax problem with constrains coupling both variables._
