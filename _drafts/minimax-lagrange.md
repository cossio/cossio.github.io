---
layout: post
title: Constrained minimax
comments: true
---
# Constrained minimax

## The saddle problem with constrains

Let $f:X\times Y\rightarrow\mathbb R$ be a saddle-function (convex in $x$, concave in $y$), where $X\in\mathbb R^n$ and $Y\in\mathbb R^m$ are convex sets. We consider a restricted domain $\Omega \subset X\times Y$ defined by the constrains

$$g_i(x,y) \le 0, \quad i= 1,\dots,p$$
$$h_j(x,y) = 0, \quad j= 1,\dots,q$$

where the functions $g_i:X\times Y\rightarrow\mathbb R$ are convex in both arguments, and the functions $h_j:X\times Y\rightarrow\mathbb R$ are affine. Then $\Omega$ is a convex set. Furthermore we assume that the functions $f,g_i,h_j$ are all differentiable.

The sets $\Omega(x,\cdot)\subset Y$ and $\Omega(\cdot,y)\subset X$ defined by

$$\Omega(x,\cdot)=\{y \in Y : (x,y) \in \Omega\},\quad x\in X$$
$$\Omega(\cdot,y)=\{x \in X : (x,y) \in \Omega\},\quad y\in Y$$

are also convex.

In this note we investigate the minimax and maximin problems,

$$f^{(1)} = \max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y), \qquad
  f^{(2)} = \min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)$$

## Lagrangian formalism

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

$$\min_{x\in\Omega(\cdot,y)} f(x,y) = \max_{\lambda \ge 0} \max_\nu G(y,\lambda,\nu)$$
$$\max_{y\in\Omega(x,\cdot)} f(x,y) = \min_{\lambda \le 0} \min_\nu H(x,\lambda,\nu)$$

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

The left-hand sides of these equations contain the original maximin and minimax problems under constrains that couple the variables $x$ and $y$. The right-hand sides contain new maximin and minimax problems in terms of the Lagrangian, where the coupling constrains have disappeared.


### Optimizing over $\lambda,\nu$

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

Comparing this to the previous Lagrangian optimizations derived for $f^{(i)},i=1,2$, we obtain the following equalities,

$$\max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)
= \max_{y\in Y}\min_{x\in X}\max_{\lambda \ge 0}\max_\nu L(x,y,\lambda,\nu)$$

$$\min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)
= \min_{x\in X}\max_{y\in Y}\min_{\lambda \le 0}\min_\nu L(x,y,\lambda,\nu)$$

## All affine constrains

Let $\lambda^{(i)},\nu^{(i)},x^{(i)},y^{(i)}, i=1,2$ be optimal points of the Lagrangian maximin and minimax problems, respectively,

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y)
= L(x^{(1)}, y^{(1)}, \lambda^{(1)}, \nu^{(1)})$$

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)
= L(x^{(2)}, y^{(2)}, \lambda^{(2)}, \nu^{(2)})$$

It follows that:

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y)
= \max_{y\in Y}\min_{x\in X}L(x,y, \lambda^{(1)}, \nu^{(1)})$$

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)
= \min_{x\in X}\max_{y\in Y}L(x,y, \lambda^{(2)}, \nu^{(2)})$$

Suppose now that both the $g_i(x,y)$ and the $h_j(x,y)$ are affine in $x,y$, for all $i,j$. Then $L(x,y,\lambda,\nu)$ is a saddle-function in $x,y$ (convex in $x$ and concave in $y$) for any fixed $\lambda,\nu$. It follows that,

$$\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)
= \max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu),
\quad\text{for all }\lambda,\nu$$

The optimal value is attained at a saddle-point $(x^*,y^*)$ of $L(x,y,\lambda,\nu)$ w.r.t. $x,y$. Note that $(x^*,y^*)$ depend on $\lambda,\nu$. A saddle-point is also a critical point, hence:

$$\nabla_x L(x^*,y^*,\lambda,\nu)
= \nabla_x f(x^*,y^*) + \sum_i\lambda_i\nabla_x g_i + \sum_j\nu_j\nabla_x h_j = 0$$
$$\nabla_y L(x^*,y^*,\lambda,\nu)
= \nabla_y f(x^*,y^*) + \sum_i\lambda_i\nabla_y g_i + \sum_j\nu_j\nabla_y h_j = 0$$

Conversely if $(x^*,y^*)$ satisfies these stationarity conditions for a given $\lambda,\nu$, it is a saddle-point of $L(x,y,\lambda,\nu)$ w.r.t. $x,y$. Note that the gradients $\nabla g_i$ and $\nabla h_j$ are constants (because these functions are affine) and therefore the argument variables $x,y$ can be ommitted.



These stationarity equations are also the conditions for $x^*,y^*$ to be a critical point of $f$ within $\Omega$.

We have

$$\begin{aligned}
\min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)
&\le \min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,0,\nu) \\
&\le \max_\nu\min_{x\in X}\max_{y\in Y} L(x,y,0,\nu) \\
&\le \max_{\lambda \ge 0}\max_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu) \\
&=   \max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)
\end{aligned}$$

which implies

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y) \le
  \max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y)$$

$$\min_{x\in X}\max_{y\in Y}\min_{\lambda \le 0}\min_\nu L(x,y,\lambda,\nu)
$$

## References

1. Boyd, Stephen P., and Lieven Vandenberghe. Convex Optimization. Cambridge, UK ; New York: Cambridge University Press, 2004. Specially Chapter 5 on Lagrangian duality.
2. [The minimax inequality and saddle-points]({{ site.baseurl }}{% post_url 2018-04-24-minimax %})
