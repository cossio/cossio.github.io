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

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y), \qquad
  \min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)$$

## Lagrangian formalism

Define the Lagrangian,

$$L(x,y,\lambda,\nu) = f(x,y) + \sum_i\lambda_i g_i(x,y) + \sum_j\nu_j h_j(x,y)$$

For all $(x,y)\in\Omega$:

* If $\lambda_i \ge 0$ for all $i$, then $L(x,y,\lambda,\nu) \le f(x,y)$.
* If $\lambda_i \le 0$ for all $i$, then $L(x,y,\lambda,\nu) \ge f(x,y)$.

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

For example, since $f(x,y)$ is convex in $x$ (concave in $y$), the $g_i(x,y)$ are convex in both arguments, and the $h_j(x,y)$ are affine, the problems 

$$\min_{x\in\Omega(\cdot,y)} f(x,y),\qquad \max_{y\in\Omega(x,\cdot)} f(x,y)$$

are a convex minimization problem and a concave maximization problem, respectively. In this case a sufficient condition for strong duality is the Slater constrain qualification (see Ref. 1), which is usually met in practice.

It follows that

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y)
= \max_{y\in Y}\max_{\lambda \ge 0} \max_\nu G(y,\lambda,\nu)$$

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)
= \min_{x\in X}\min_{\lambda \le 0} \min_\nu H(x,\lambda,\nu)$$

Substituting the definitions of the Lagrange dual functions,

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y)
= \max_{y\in Y}\max_{\lambda \ge 0}\max_\nu\min_{x\in X} L(x,y,\lambda,\nu)
\qquad\text{(lagrangian-maximin)}$$

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)
= \min_{x\in X}\min_{\lambda \le 0}\min_\nu\max_{y\in Y} L(x,y,\lambda,\nu)
\qquad\text{(lagrangian-minimax)}$$

The left-hand sides of these equations contain the original maximin and minimax problems under constrains that couple the variables $x$ and $y$. The right-hand sides contain new maximin and minimax problems in terms of the Lagrangian, where the coupling constrains have disappeared.

$L$ is affine in $\lambda,\nu$ for fixed $x,y$. Moreover, $L$ is convex in $x$ for fixed $\lambda\ge0,\nu,y$, and concave in $y$ for fixed $\lambda\le0,\nu,x$. Therefore, we can reorder the optimizations of the Lagrangian in the following manner:

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y)
= \max_{y\in Y}\min_{x\in X}\max_{\lambda \ge 0}\max_\nu L(x,y,\lambda,\nu)$$

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)
= \min_{x\in X}\max_{y\in Y}\min_{\lambda \le 0}\min_\nu L(x,y,\lambda,\nu)$$

For fixed $x,y$, the optimizations in $\lambda,\nu$ can be carried out analytically. Since,

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

it follows that,

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

This confirms the equivalence of the Lagrangian optimizations to the original minimax/maximin problems. We can see that if $(x^*,y^*,\lambda^*,\nu^*)$ are the optimal coordinates of one of the Lagrangian optimizations (the minimax or the maximin), then $(x^*,y^*)\in\Omega$ and $\lambda_i^* g_i(x^*,y^*)=0$ for all $i$.

Noting that $\max$ always commutes with $\max$ (and $\min$ with $\min$), we can reorder the optimizations in equations `(lagrangian-maximin)` and `(lagrangian-minimax)` once more, to obtain:

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y)
= \max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)$$

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)
= \min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)$$

Let $(x_i^*,y_i^*,\lambda_i^*,\nu_i^*)$, $i=1,2$ be optimal coordinates of the minimax and maximin Lagrangian optimizations, respectively:

$$\max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)
= L(x_1^*,y_1^*,\lambda_1^*,\nu_1^*)$$

$$\min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)
= L(x_2^*,y_2^*,\lambda_2^*,\nu_2^*)$$

Then,

$$\max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)
= \max_{y\in Y}\min_{x\in X} L(x,y,\lambda_1^*,\nu_1^*)$$

$$\min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)
= \min_{x\in X}\max_{y\in Y} L(x,y,\lambda_2^*,\nu_2^*)$$

## All affine constrains

Suppose now that the $g_j(x,y)$ are affine in $x,y$, for all $j$. Then $L(x,y,\lambda,\nu)$ is saddle-function in $x,y$ (convex in $x$ and concave in $y$) for any fixed $\lambda,\nu$.

Since $L(x,y,\lambda,\nu)$ is a saddle-function in $x,y$ for any fixed $\lambda,\nu$, the optimizations

$$\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)
= \max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)$$

are equivalent for any fixed $\lambda,\nu$, and the optimal value is attained at a saddle-point $(x^*,y^*)$ of $L(x,y,\lambda,\nu)$ w.r.t. $x,y$. Note that $(x^*,y^*)$ depend on $\lambda,\nu$. A saddle-point is also a critical point, hence:

$$\nabla_x L(x,y,\lambda,\nu)
= \nabla_x f(x^*,y^*) + \sum_i\lambda_i\nabla_x g_i + \sum_j\nu_j\nabla_x h_j = 0$$
$$\nabla_y L(x,y,\lambda,\nu)
= \nabla_y f(x^*,y^*) + \sum_i\lambda_i\nabla_y g_i + \sum_j\nu_j\nabla_y h_j = 0$$

Conversely if $(x^*,y^*)$ satisfies these stationarity conditions for a given $\lambda,\nu$, it is a saddle-point. Note that the gradients $\nabla g_i$ and $\nabla h_j$ are constants (because these functions are affine) and therefore the argument variables $x,y$ can be ommitted.

Suppose that $(x^1,y^1,\lambda^1,\nu^1)$ are the optimal coordinates of the maximin Lagrangian optimization, and $(x^2,y^2,\lambda^2,\nu^2)$ the optimal coordinates of the minimax Lagrangian optimization. Then,

$$\max_{\lambda \ge 0}\max_\nu\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu)
= \max_{y\in Y}\min_{x\in X} L(x,y,\lambda^1,\nu^1)$$

$$\min_{\lambda \le 0}\min_\nu\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)
= \min_{x\in X}\max_{y\in Y} L(x,y,\lambda^2,\nu^2)$$

The optimal coordinates $(x^*,y^*,\lambda^*,\nu^*)$ of the Lagrangian optimizations must then satisfy,

$$\nabla_x L = \nabla_x f(x,y) + \sum_i\lambda_i^*\nabla_xg_i(x,y) + \sum_j\nu_j^*\nabla_xh_j(x,y) = 0$$
$$\nabla_y L = \nabla_y f(x,y) + \sum_i\lambda_i^*\nabla_yg_i(x,y) + \sum_j\nu_j^*\nabla_xh_j(x,y)=0$$



Then

$$\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\nu) = \min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\nu)$$

for all $\lambda,\nu$.

Suppose now that there are no inequality constrains coupling both variables (that is, we ignore the $g_i$'s). We only consider the affine equality constrains $h_j(x,y)=0$. The Lagrangian simplifies to,

$$L(x,y,\nu) = f(x,y) + \sum_j \nu_j h_j(x,y)$$

and, as derived above,

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y)
= \max_{y\in Y}\max_\nu\min_{x\in X} L(x,y,\nu)
= \max_{y\in Y}\min_{x\in X}\max_\nu L(x,y,\nu)$$

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y)
= \min_{x\in X}\min_\nu\max_{y\in Y} L(x,y,\nu)
= \min_{x\in X}\max_{y\in Y}\min_\nu L(x,y,\nu)$$

By the minimax inequality,

$$\max_{y\in Y}\max_\nu\min_{x\in X} L(x,y,\nu) \le \min_{x\in X}\max_{y\in Y}\max_\nu L(x,y,\nu)$$
$$\min_{x\in X}\min_\nu\max_{y\in Y} L(x,y,\nu) \ge \max_{y\in Y}\min_{x\in X}\min_\nu L(x,y,\nu)$$


Suppose now that the $g_i(x,y)$ are affine. Then $L$ is convex in $x$ and concave in $y$, for fixed $\lambda,\nu$.



If the point $x^*,y^*,\lambda^*,\nu^*$ is a solution of the right-hand side of one of these equations, and if $x^*$ lies in the interior of $X$, $y^*$ in the interior of $Y$, $\lambda^* \ne 0$, then this point must be a critical point of the Lagrangian. Differentiating $L$ w.r.t. $x$ and $y$ we obtain the required stationarity conditions,

$$\nabla_x f(x^*,y^*) +
\sum_i\lambda_i\nabla_x g_i(x^*,y^*) +
\sum_j\nu_j\nabla_x h_j(x^*,y^*) = 0$$
$$\nabla_y f(x^*,y^*) +
\sum_i\lambda_i\nabla_y g_i(x^*,y^*) +
\sum_j\nu_j\nabla_y h_j(x^*,y^*) = 0$$

while differentiating $L$ w.r.t. $\lambda$ or $\nu$ simply returns the feasibility conditions $g_i(x^*,y^*)\le0$ and $h_j(x^*,y^*)=0$.


Suppose we only have affine equality constrains, $h_j(x,y) = 0$, and ignore the inequality constrains $g_i(x,y) \le 0$.

Then $L(x,y,\nu)$ is convex in $x$, concave in $y$, and linear in $\nu$. It follows that $L$ has a saddle-point. The minimax problems,

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y) =
\max_{y\in Y}\max_\nu\min_{x\in X} L(x,y,\nu)$$

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y) =
\min_{x\in X}\min_\nu\max_{y\in Y} L(x,y,\nu)$$

are then equivalent, and both find the saddle-point of $L$.

Note that the consideration of affine constrains alone, only refers to the constrains that involve *both* $x$ and $y$. Any constrain involving $x$ only ($y$ only)$ can be incorporated into the definition of $X$ ($Y$).

## References

1. Boyd, Stephen P., and Lieven Vandenberghe. Convex Optimization. Cambridge, UK ; New York: Cambridge University Press, 2004. Specially Chapter 5 on Lagrangian duality.
