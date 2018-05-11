---
layout: post
title: A minimax problem with linear constrains
comments: true
---

Let $f:X\rightarrow\mathbb R, g:Y\rightarrow\mathbb R$ be convex differentiable functions, where $X,Y\subset\mathbb R^n$ are convex compact sets. We consider the minimax and maximin problems:

$$f^{(1)} = \min_{x\in X}\max_{y\in Y} (f(x) - g(y)), \qquad
  f^{(2)} = \max_{y\in Y}\min_{x\in X} (f(x) - g(y))$$

subject to the constrains,

$$A(x-y) = 0,\quad x,y\ge 0, \quad \sum_i x_i = \sum_i y_i = 1$$

where $A\in\mathbb R^{m\times n}$ is a matrix. We say that $(x,y)\in\Omega$ (or that $(x,y)$ is feasible) if it satisfies the above constrains, and $\Omega$ is called the set of feasible points. We also define the sets obtained from $\Omega$ by fixing one of the coordinates $x$ or $y$,

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

Define the Lagrangian,

$$\begin{aligned}L(x,y,\lambda,\alpha,\beta,\gamma,\delta)
&= f(x)-g(y) + \lambda^T A(x-y) \\
&+ \alpha^T x - \beta^T y + \gamma(\bm1^Tx-1) - \delta(\bm1^Tx-1)
\end{aligned}$$

where $\bm1$ is the vector with all components equal to 1. Since $\sum_i x_i=\sum_iy_i=1$ and $\sum_iA_{ki}(x_i-y_i)=0$ for all $(x,y)\in\Omega$, it follows that:

* If $\alpha_i\ge0\ge\beta_i$ for all $i$, then $L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \ge f(x)-g(y)$.
* If $\alpha_i\le0\le\beta_i$ for all $i$, then $L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \le f(x)-g(y)$.

Now define the Lagrangian dual functions,

$$G(x,\lambda,\alpha,\beta,\gamma,\delta)
= \max_{y\in Y} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

$$H(y,\lambda,\alpha,\beta,\gamma,\delta)
= \min_{x\in X} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

Again, suppose that $(x,y)\in\Omega$. Then,

* If $\alpha\ge0\ge\beta$ for all $i$, then $G(x,\lambda,\alpha,\beta,\gamma,\delta) \ge L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \ge f(x)-g(y)$.
* If $\alpha\le0\le\beta$ for all $i$, then $H(y,\lambda,\alpha,\beta,\gamma,\delta) \le L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \le f(x)-g(y)$.

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

Substituting the definitions of the Lagrange dual functions and reordering the optimizations,

$$f^{(1)} = \min_{\lambda,\gamma,\delta}\min_{\alpha\ge0}\min_{\beta\le0}
\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

$$f^{(2)} = \max_{\lambda,\gamma,\delta}\max_{\alpha\le0}\max_{\beta\ge0}
\max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)$$

# Legendre transforms of $f$ and $g$

Since the constrains are linear, the solution simplifies by use of the Legendre transforms of $f,g$:

$$\hat f(\xi) = \max_{x\in X}(\xi^T x-f(x)),\qquad
  \hat g(\eta)= \max_{y\in Y}(\eta^Ty-g(y))$$

The Lagrangian can be written as,

$$L(x,y,\lambda,\alpha,\beta,\gamma,\delta) = f(x)-g(y)
+h(x,\lambda,\alpha,\gamma) - h(y,\lambda,\beta,\delta)$$

where,

$$h(x,\lambda,\alpha,\gamma) = \lambda^T A x + \alpha ^T x + \gamma(\bm1^Tx-1)$$

It follows that:

$$\min_{x\in X} (f(x) + h(x,\lambda,\alpha,\gamma))
=-\hat f(-A^T\lambda-\alpha-\gamma\bm1) - \gamma$$

$$\min_{y\in Y} (g(y) + h(y,\lambda,\beta,\delta))
=-\hat g(-A^T\lambda-\beta-\delta\bm1) - \delta$$

where $\hat f,\hat g$ are the Legendre transforms of $f,g$. Then, for fixed Lagrange multipliers, $L$ satisfies the minimax equality,

$$\begin{aligned}
\min_{x\in X}\max_{y\in Y} L(x,y,\lambda,\alpha,\beta,\gamma,\delta)
= \max_{y\in Y}\min_{x\in X} L(x,y,\lambda,\alpha,\beta,\gamma,\delta) \\
=\min_{x\in X} (f(x) + h(x,\lambda,\alpha,\gamma))
-\min_{y\in Y} (g(y) + h(y,\lambda,\beta,\delta)) \\
=\hat g(-A^T\lambda-\beta-\delta\bm1)  + \delta
-\hat f(-A^T\lambda-\alpha-\gamma\bm1) - \gamma
\end{aligned}$$

Therefore,

$$f^{(1)} = \min_{\lambda,\gamma,\delta}\min_{\alpha\ge0}\min_{\beta\le0}
(\hat g(-A^T\lambda-\beta-\delta\bm1)  + \delta
-\hat f(-A^T\lambda-\alpha-\gamma\bm1) - \gamma)$$

$$f^{(2)} = \max_{\lambda,\gamma,\delta}\max_{\alpha\le0}\max_{\beta\ge0}
(\hat g(-A^T\lambda-\beta-\delta\bm1)  + \delta
-\hat f(-A^T\lambda-\alpha-\gamma\bm1) - \gamma)$$

## References

1. A problem of this form is considered by [Minka, Thomas P. “The EP Energy Function and Minimization Schemes.” Technical report, 2001](https://tminka.github.io/papers/ep/minka-ep-energy.pdf).

