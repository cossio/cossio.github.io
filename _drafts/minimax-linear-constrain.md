---
layout: post
title: A minimax problem with linear constrains
comments: true
---

Let $f:X\rightarrow\mathbb R, g:Y\rightarrow\mathbb R$ be convex differentiable functions, where $X,Y\subset\mathbb R^n$ are convex compact sets. We consider the minimax and maximin problems:

$$f^{(1)} = \min_{x\in X}\max_{y\in Y} (f(x) - g(y)), \qquad
  f^{(2)} = \max_{y\in Y}\min_{x\in X} (f(x) - g(y))$$

subject to the constrains,

$$A(x-y) = 0$$

where $A\in\mathbb R^{m\times n}$ is a matrix. We say that $(x,y)\in\Omega$ (or that $(x,y)$ is feasible) if $x\in X,y\in Y$ and $A(x-y)=0$. $\Omega$ is called the set of feasible points. We also define the sets obtained from $\Omega$ by fixing one of the coordinates $x$ or $y$,

$$\Omega(x,\cdot) = \{y\in Y|(x,y)\in\Omega\}, \quad
  \Omega(\cdot,y) = \{x\in X|(x,y)\in\Omega\}.$$

With this notation, the minimax and maximin problems can be written as:

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} (f(x) - g(y)), \quad
  \max_{y\in Y}\min_{x\in\Omega(\cdot,y)} (f(x) - g(y))$$

# Well-posedness

Here we show that the problem is well posed. Let $x^{(i)}\in X,y^{(i)}\in Y,i=1,2$ be extremizers of $f$ and $g$,

$$\min_{x\in X} f(x) = f(x^{(1)}),\qquad \max_{x\in X} f(x) = f(x^{(2)})$$

$$\min_{y\in Y} g(y) = g(y^{(1)}),\qquad \max_{y\in Y} g(y) = g(y^{(2)})$$

Since $X,Y$ are compact and $f,g$ continuous, $x^i,y^i,i=1,2$ are guaranteed to exist. It follows that,

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} (f(x) - g(y))
\ge \min_{x\in X} (f(x) - g(y^{(2)})) = f(x^{(1)}) - g(y^{(2)})$$

$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} (f(x) - g(y))
\le \max_{y\in Y} (f(x^{(2)}) - g(y)) = f(x^{(2)}) - g(y^{(1)})$$

Therefore the outer extremizations are bounded.

# Lagrangian formalism

Define the Lagrangian

$$L(x,y,\lambda)=f(x)-g(y)+\lambda^T A(x-y)$$

and the Lagrange dual functions

$$G(y,\lambda)=\min_{x\in X}L(x,y,\lambda),\qquad
  H(x,\lambda)=\max_{y\in Y}L(x,y,\lambda)$$

Since $A(x-y)=0$ for $(x,y)\in\Omega$, it follows that

$$G(y,\lambda)\le L(x,y,\lambda)=f(x)-g(y)\le H(x,\lambda)
\qquad\forall(x,y)\in \Omega$$

Since these inequalities hold for all $(x,y)\in\Omega$ and for all $\lambda$, it follows that

$$\max_\lambda G(y,\lambda)\le\min_{x\in\Omega(\cdot,y)}
(f(x)-g(y)), \qquad\forall y\in Y$$

$$\min_\lambda H(x,\lambda)\ge\max_{y\in\Omega(x,\cdot)}
(f(x)-g(y)), \qquad\forall x\in X$$

If Lagrangian duality holds, we obtain equality signs here instead of inequalities.

$$\max_\lambda\max_{y\in Y}\min_{x\in X}L(x,y,\lambda)
\le \max_{y\in Y}\min_{x\in\Omega(\cdot,y)}(f(x)-g(y))$$

$$\min_\lambda\min_{x\in X}\max_{y\in Y}L(x,y,\lambda)\ge\max_{y\in\Omega(x,\cdot)}
(f(x)-g(y))$$

Since the first inequality holds for all $\lambda,y$ and the second for all $\lambda,x$, it follows that

$$\max_\lambda\max_{y\in Y}\min_{x\in X}L(x,y,\lambda)\le f(x)-g(y)$$

$$\min_\lambda\min_{x\in X}\max_{y\in Y}L(x,y,\lambda)\ge f(x)-g(y)$$



Provided $x\in X,y\in Y$, it is easy to see that

$$\min_{\lambda}L(x,y,\lambda)
= \begin{cases}
  f(x) - g(y) & (x,y)\in\Omega \\
  -\infty     & (x,y)\notin\Omega
\end{cases}$$

$$\max_{\lambda}L(x,y,\lambda)
= \begin{cases}
  f(x) - g(y) & (x,y)\in\Omega \\
  \infty     & (x,y)\notin\Omega
\end{cases}$$

Therefore,

$$f^{(1)} = \min_{x\in X}\max_{y\in Y}
\min_{\lambda} L(x,y,\lambda,\alpha,\beta)$$

$$f^{(2)} = \max_{y\in Y}\min_{x\in X}
\max_{\lambda} L(x,y,\lambda,\alpha,\beta)$$

$L$ is affine in $\lambda$ for fixed $x,y$, convex in $x$ for fixed $y,\lambda$, and concave in $y$ for fixed $x,\lambda$. Therefore, assuming that the optimum lies in the interior of the domain, it is possible to reorder some of these Lagrangian optimizations to obtain,

$$f^{(1)} = \min_{\lambda}\min_{x\in X}\max_{y\in Y}L(x,y,\lambda,\alpha,\beta)$$

$$f^{(2)} = \max_{\lambda}\max_{y\in Y}\min_{x\in X}L(x,y,\lambda,\alpha,\beta)$$

Therefore Lagrangian duality holds for this problem (see also the book of Bertsekas 1999, Proposition 3.3.7). 

The Lagrangian is _additively separable_ in $x,y$, _i.e._, it is a sum of terms none of which depends on both $x$ and $y$. Defining $h(x,\lambda) = \lambda^T A x$, it follows that:

$$L(x,y,\lambda,\alpha,\beta)=f(x)-g(y)+h(x,\lambda)-h(y,\lambda)$$
 
Since the constrains are linear, the solution simplifies by use of the Legendre transforms of $f,g$:

$$\hat f(\xi) = \max_{x\in X}(\xi^T x-f(x)),\qquad
  \hat g(\eta)= \max_{y\in Y}(\eta^Ty-g(y))$$

It follows that:

$$\min_{x\in X} (f(x) + h(x,\lambda)) = -\hat f(-A^T\lambda)$$

$$\min_{y\in Y} (g(y) + h(y,\lambda)) = -\hat g(-A^T\lambda)$$

Then, for fixed $\lambda$, $L$ satisfies the minimax equality,

$$\begin{aligned}
\min_{x\in X}\max_{y\in Y} L(x,y,\lambda)
&= \max_{y\in Y}\min_{x\in X} L(x,y,\lambda) \\
&= \min_{x\in X} (f(x) + h(x,\lambda))-\min_{y\in Y} (g(y) + h(y,\lambda)) \\
&= \hat g(-A^T\lambda) - \hat f(-A^T\lambda)
\end{aligned}$$

Therefore,

$$f^{(1)} = \min_{\lambda} (\hat g(-A^T\lambda) - \hat f(-A^T\lambda))$$

$$f^{(2)} = \max_{\lambda} (\hat g(-A^T\lambda) - \hat f(-A^T\lambda))$$

# References

1. A problem of this form is considered by [Minka, Thomas P. “The EP Energy Function and Minimization Schemes.” Technical report, 2001](https://tminka.github.io/papers/ep/minka-ep-energy.pdf).
2. [Bertsekas1999] Bertsekas, Dimitri P. Nonlinear Programming. 2nd ed. Athena Scientific, 1999.
