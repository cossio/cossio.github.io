---
layout: post
title: Constrained minimax
comments: true
---
# Constrained minimax

## Definitions

We consider a minimax problem of the form,

$$\min_{x\in X} \max_{y\in Y} f(x,y)$$

subject to constrains

$$g_i(x,y) \le 0, \quad i = 1,\dots,p$$
$$h_j(x,y)   = 0, \quad j= 1,\dots,q$$

where $f,g_i,h_j$ are functions $X\times Y\rightarrow\mathbb R$. Here $X\subset \mathbb R^n, Y\subset\mathbb R^m$ are convex sets.

We will assume that $f$ is a saddle-function (convex in $x$, concave in $y$), that the $g_i$ are convex (in all arguments) and that the $h_j$ are affine functions. Furthermore, we assume that $f$ and $g_i,i=1,\dots,p$ are differentiable (since $h_j$ is affine it is automatically differentiable).

Let $\Omega$ be the set of points $(x,y)\in X\times Y$ such that $g_i(x,y)\le0$ for all $i=1,\dots,p$ and $h_j(x,y)=0$ for all $j=1,\dots,q$. Define,

$$\Omega(x,\cdot)=\{(x,y): y \in Y \land g_i(x,y)\le 0 \,\forall i \land h_j(x,y) = 0\, \forall j\}$$
$$\Omega(\cdot,y)=\{(x,y): x \in X \land (x,y) \in \Omega\}$$

Similarly, let $\Omega^*$ be the set of points $(x,y)\in X\times Y$ such that $g_i(x,y)<0$ (notice the strict inequality) for all $i=1,\dots,p$.

Let $\mathcal D$ be the set of points $(x,y)\in X\times Y$ that satisfy $g_i(x,y) \le 0$ for all $i = 1,\dots,p$.

## Conditions for optimality

Define the functions $\xi:Y\rightarrow X$ and $\eta:X\rightarrow Y$ implicitly via the equations:

$$\min_{x\in \Omega(\cdot,y)} f(x,y) = f(\xi(y),y)$$
$$\max_{y\in \Omega(x,\cdot)} f(x,y) = f(x,\eta(x))$$

Alternatively, we can employ the criticality conditions to obtain:

$$\left.\nabla_x f(x,y)\right|_{x=\xi(y)} + \sum_j \alpha_j \left.\nabla_x h_j(x,y)\right|_{x=\xi(y)} = 0$$
$$\left.\nabla_y f(x,y)\right|_{y=\eta(x)} + \sum_j \beta_j \left.\nabla_y h_j(x,y)\right|_{x=\eta(x)} = 0$$

where $\alpha_j,\beta_j$ are Lagrange multipliers and

$$h_j(\xi(y),y)  = 0 \quad j = 1,\dots,q$$
$$h_j(x,\eta(x)) = 0 \quad j = 1,\dots,q$$

Then

$$\begin{aligned}
\frac{\partial}{\partial x} \left(f(x,\eta(x)) + \sum_j \alpha_j h(x,\eta(x))\right)
&= \frac{\partial}{\partial x} \left(f(x,y) + \sum_j \alpha_j h(x,y)\right) \\
&\qquad +\frac{\partial}{\partial y}\left(f(x,y) + \sum_j \alpha_j h(x,y)\right)_{y=\eta(x)}
\frac{\partial \eta}{\partial x} \\
&= \frac{\partial}{\partial x} \left(f(x,y) + \sum_j \alpha_j h(x,y)\right)
\end{aligned}$$

### Saddle-points

Let $\rho^*$ be the optimal value of the minimax. Suppose that it is attained at a point $(x^*,y^*)$, so that $f(x^*,y^*) = \rho^*$. Furthermore, suppose that $(x^*,y^*)$ is an interior point of $\mathcal D$. This means that $g_i(x^*,y^*) < 0$ (note the strict inequality) for all $i = 1,\dots,p$.

$$\nabla_x f + \sum_j \alpha_j \nabla_x h_j = 0$$
$$\nabla_y f + \sum_j \alpha_j \nabla_y h_j = 0$$