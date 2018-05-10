---
layout: post
title: A minimax with linear constrains
comments: true
---
# A minimax with linear constrains

Let $f:X\rightarrow\mathbb R, g:Y\rightarrow\mathbb R$ be convex differentiable functions, where $X,Y\subset\mathbb R^n$ are convex compact sets. We consider the minimax and maximin problems:

$$f^{(1)} = \min_{x\in X}\max_{y\in Y} (f(x) - g(y)), \qquad
  f^{(2)} = \max_{y\in Y}\min_{x\in X} (f(x) - g(y))$$

subject to the constrains,

$$A(x-y) = 0,\quad x,y\ge 0, \quad \sum_i x_i = \sum_i y_i = 1$$

where $A\in\mathbb R^{m\times n}$ is a matrix. We say that $(x,y)\in\Omega$ (or that $(x,y)$ is feasible) if it satisfies the above constrains, and $\Omega$ is called the set of feasible points. We also define the subsets obtained from $\Omega$ by fixing one of the coordinates $x$ or $y$,

$$\Omega(x,\cdot) = \{y\in Y|(x,y)\in\Omega\}, \quad
  \Omega(\cdot,y) = \{x\in X|(x,y)\in\Omega\}.$$

With this notation, the minimax and maximin problems can be written as:

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} (f(x) - g(y)), \quad
  \max_{y\in Y}\min_{x\in\Omega(\cdot,y)} (f(x) - g(y))$$

## Well-posedness

Here we show that the problem is well posed. Let $x^\ast\in X,y^\ast\in Y$ be minimizers of $f,g$,

$$\min_{x\in X} f(x) = g(x^\ast),\qquad\min_{y\in Y} g(y) = g(y^\ast)$$

Then

$$\max_{y\in\Omega(x,\cdot)} (f(x) - g(y)) \le f(x) - g(y^\ast)$$

## Lagrangian formalism

Define the Lagrangian,

$$\begin{aligned}L(x,y,\lambda,\alpha,\beta,\gamma,\delta)
&= f(x)-g(y) + \sum_{k,i}\lambda_kA_{ki}(x_i-y_i) \\
&+\sum_i(\alpha_ix_i-\beta_iy_i)
+\gamma\left(\sum_ix_i - 1\right) - \delta\left(\sum_iy_i - 1\right) \\
&= f(x)-g(y) + h(x,\lambda,\alpha,\gamma) - h(y,\lambda,\beta,\delta)
\end{aligned}$$

where

$$h(x,\lambda,\alpha,\gamma) = \sum_{k,i}\lambda_k A_{ki}x_i + \sum_i\alpha_ix_i + \gamma\left(\sum_ix_i - 1\right)$$

For all $(x,y)\in\Omega$, we have the following two useful properties:

* If $\alpha_i\ge0\ge\beta_i$ for all $i$, then $L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \ge f(x)-g(y)$.
* If $\alpha_i\le0\le\beta_i$ for all $i$, then $L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \le f(x)-g(y)$.

These properties follow from the fact that $(x,y)\in\Omega$ imply $\sum_i x_i=\sum_iy_i=1$ and $\sum_iA_{ki}(x_i-y_i)=0$ for all $k$. Now define the Lagrangian dual functions,

$$G(x,\lambda,\alpha,\beta,\gamma,\delta)
= \max_{y\in Y} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

$$H(y,\lambda,\alpha,\beta,\gamma,\delta)
= \min_{x\in X} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

We have that:

$$\min_{x\in X} (f(x) + h(x,\lambda,\alpha,\gamma))
= \gamma - \hat f(-\lambda A-\alpha-\gamma)$$
$$\min_{y\in Y} (g(y) + h(y,\lambda,\beta,\delta))
= \delta - \hat g(-\lambda A-\beta-\delta)$$

where $\hat f,\hat g$ are the Legendre transforms of $f,g$. Hence,

$$G(x,\lambda,\alpha,\beta,\gamma,\delta)
=f(x)+h(x,\lambda,\alpha,\gamma) - \delta + \hat g(-\lambda A-\beta-\delta)$$

$$H(y,\lambda,\alpha,\beta,\gamma,\delta)
=\gamma - \hat f(-\lambda A-\alpha-\gamma)-g(y)-h(y,\lambda,\beta,\delta)$$

where $\hat g,\hat f$ are the Legendre transforms of $f,g$.

Again, suppose that $(x,y)\in\Omega$. Then,

* If $\alpha_i\ge0\ge\beta_i$ for all $i$, then $G(x,\lambda,\alpha,\beta,\gamma,\delta) \ge L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \ge f(x)-g(y)$.
* If $\alpha_i\le0\le\beta_i$ for all $i$, then $H(y,\lambda,\alpha,\beta,\gamma,\delta) \le L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \le f(x)-g(y)$.

Since these inequalities hold for all $(x,y)\in\Omega$, it follows that,

* If $\alpha_i\ge0\ge\beta_i$ for all $i$, then $G(x,\lambda,\alpha,\beta,\gamma,\delta) \ge \max_{y\in\Omega(x,\cdot)}(f(x)-g(y))$.
* If $\alpha_i\le0\le\beta_i$ for all $i$, then $H(y,\lambda,\alpha,\beta,\gamma,\delta) \le \min_{x\in\Omega(\cdot,y)}(f(x)-g(y))$.

Provided some mild regularity conditions are satisfied, we can assume that strong duality holds:

$$\min_{\lambda,\gamma,\delta}\min_{\alpha\ge0}\min_{\beta\le0}
G(x,\lambda,\alpha,\beta,\gamma,\delta) = \max_{y\in\Omega(x,\cdot)}(f(x)-g(y)),
\quad \forall x\in X$$

$$\max_{\lambda,\gamma,\delta}\max_{\alpha\le0}\max_{\beta\ge0}
H(y,\lambda,\alpha,\beta,\gamma,\delta) = \min_{x\in\Omega(\cdot,y)}(f(x)-g(y)),
\quad \forall y\in Y$$

It follows that

$$f^{(1)} = \min_{x\in X}
\min_{\lambda,\gamma,\delta}\min_{\alpha\ge0}\min_{\beta\le0}
G(x,\lambda,\alpha,\beta,\gamma,\delta)$$

$$f^{(2)} = \max_{y\in Y}
\max_{\lambda,\gamma,\delta}\max_{\alpha\le0}\max_{\beta\ge0}
H(y,\lambda,\alpha,\beta,\gamma,\delta)$$

Substituting the expressions found above for $G,H$ and reordering the optimizations,

$$\begin{aligned}
f^{(1)}&=\min_{\lambda,\gamma,\delta}\min_{\alpha\ge0}\min_{\beta\le0}
\min_{x\in X}(f(x)+h(x,\lambda,\alpha,\gamma)-\delta+\hat g(-\lambda A-\beta-\delta)) \\
&= \min_{\lambda,\gamma,\delta}\min_{\alpha\ge0}\min_{\beta\le0}
(\gamma-\hat f(-\lambda A-\alpha-\gamma)-\delta+\hat g(-\lambda A-\beta-\delta))\\
f^{(2)}&=\max_{\lambda,\gamma,\delta}\max_{\alpha\le0}\max_{\beta\ge0}
\max_{y\in Y}(-g(y)-h(y,\lambda,\beta,\delta)+\gamma-\hat f(-\lambda A-\alpha-\gamma)) \\
&= \\
\end{aligned}$$

$$\begin{aligned}
H(y,\lambda,\alpha,\beta,\gamma,\delta)
&=\min_{x\in X} L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \\
&=-\hat f(-\lambda A-\alpha-\gamma)-g(y)-h(y,\lambda,\beta,\delta)
\end{aligned}$$


----

We have that:

$$\min_{x\in X} (f(x) + h(x,\lambda,\alpha,\gamma))
= -\hat f(-\lambda A-\alpha-\gamma)$$
$$\min_{y\in Y} (g(y) + h(y,\lambda,\beta,\delta))
= -\hat g(-\lambda A-\beta-\delta)$$

where $\hat f,\hat g$ are the Legendre transforms of $f,g$. Hence,

$$G(x,\lambda,\alpha,\beta,\gamma,\delta)
=f(x)+h(x,\lambda,\alpha,\gamma) + \hat g(-\lambda A-\beta-\delta)$$

$$H(y,\lambda,\alpha,\beta,\gamma,\delta)
=-\hat f(-\lambda A-\alpha-\gamma)-g(y)-h(y,\lambda,\beta,\delta)$$

where $\hat g,\hat f$ are the Legendre transforms of $f,g$.

----




Substituting the definitions of $G,H$,

$$f^{(1)}
= \min_{x\in X}\min_{\lambda,\gamma,\delta}\min_{\alpha\ge0}\min_{\beta\le0}
\max_{y\in Y} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

$$f^{(2)}
= \max_{y\in Y}\max_{\lambda,\gamma,\delta}\max_{\alpha\le0}\max_{\beta\ge0}
\min_{x\in X} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

The optimizations can be reordered in the following manner:

$$f^{(1)} = \min_{\lambda,\gamma,\delta}\min_{\alpha\ge0}\min_{\beta\le0}
\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

$$f^{(2)} =
\max_{\lambda,\gamma,\delta}\max_{\alpha\le0}\max_{\beta\ge0}
\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

We perform the optimizations w.r.t. $x,y$ first, maintaining the Lagrange multipliers fixed. We have,

$$\begin{aligned}
\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)
&=
\end{aligned}$$

## Equivalence of minimax and maximin problems

Let us define:

$$h(x,\lambda,\alpha,\gamma) = \sum_{k,i}\lambda_kA_{ki}x_i + \sum_i\alpha_ix_i + \gamma\left(\sum_ix_i - 1\right)$$

Notice that $h$ is affine in $x$ for fixed $\lambda,\alpha,\gamma$, and affine in $\lambda,\alpha,\gamma$ for fixed $x$. The Lagrangian can be written in the form:

$$L(x,y,\lambda,\alpha,\beta,\gamma,\delta)
= f(x)-g(y) + h(x,\lambda,\alpha,\gamma) - h(y,\lambda,\beta,\delta)$$

Suppose that the Lagrangian multipliers are fixed, and consider the saddle-point optimizations:

$$\begin{aligned}
  \min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)
&=\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \\
&=\min_{x\in X} (f(x) + h(x,\lambda,\alpha,\gamma))
 -\min_{y\in Y} (g(y) + h(y,\lambda,\beta,\delta))
\end{aligned}$$

Let $\hat f(\xi),\hat g(\eta)$ be the Legendre transforms of $f,g$. Then,

$$\min_{x\in X} (f(x) + h(x,\lambda,\alpha,\gamma))
= -\hat f(\lambda A + \alpha + \gamma) - \gamma$$

$$\min_{y\in Y} (g(y) + h(y,\lambda,\beta,\delta))
= -\hat g(\lambda A + \beta + \delta) - \delta$$

where $\lambda A$ is the vector with entries $\sum_k \lambda_k A_{ki}, i=1,\dots,n$. It follows that

$$f^{(1)} = \min_{\lambda}\left(
 \min_{\beta\le0,\delta} (\hat g(\lambda_kA_k + \beta + \delta)  + \delta)
-\max_{\alpha\ge0,\gamma}(\hat f(\lambda_kA_k + \alpha + \gamma) + \gamma)
\right)$$

$$f^{(2)} = \max_\lambda\left(
 \max_{\beta\ge0,\delta} (\hat g(\lambda_kA_k + \beta + \delta) + \delta)
-\min_{\alpha\le0,\gamma}(\hat f(\lambda_kA_k + \alpha + \gamma)  + \gamma)
\right)$$

Using the inverse Legendre transform,

$$f^{(1)} = \min_{\lambda}\left(
 \min_{\beta\le0,\delta} (\hat g(\lambda_kA_k + \beta + \delta)  + \delta)
-\max_{\alpha\ge0,\gamma}(\hat f(\lambda_kA_k + \alpha + \gamma) + \gamma)
\right)$$

$$f^{(2)} = \max_\lambda\left(
 \max_{\beta\ge0,\delta} (\hat g(\lambda_kA_k + \beta + \delta) + \delta)
-\min_{\alpha\le0,\gamma}(\hat f(\lambda_kA_k + \alpha + \gamma)  + \gamma)
\right)$$

## References

1. Boyd, Stephen P., and Lieven Vandenberghe. Convex Optimization. Cambridge, UK ; New York: Cambridge University Press, 2004. Specially Chapter 5 on Lagrangian duality.
2. A problem of this form is considered by [Minka, Thomas P. “The EP Energy Function and Minimization Schemes.” Technical report, 2001](https://tminka.github.io/papers/ep/minka-ep-energy.pdf).

