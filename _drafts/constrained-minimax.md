---
layout: post
title: Constrained minimax
comments: true
---
# Constrained minimax

Let $f:X\times Y\rightarrow\mathbb R$ be a saddle-function (convex in $x$, concave in $y$). We consider a restricted domain $\Omega \subset X\times Y$ defined by the constrains

$$g_i(x,y) \le 0, \quad i = 1,\dots,p$$
$$h_j(x,y)   = 0, \quad j= 1,\dots,q$$

where $g_i:X\times Y\rightarrow\mathbb R$ are convex (in both arguments) and $h_j:X\times Y\rightarrow\mathbb R$ are affine. Then $\Omega$ is convex. Furthermore we assume that $f,g_i,h_j$ are all differentiable. Let

$$\Omega(x,\cdot)=\{y \in Y : (x,y) \in \Omega\},\qquad x\in X$$
$$\Omega(\cdot,y)=\{x \in X : (x,y) \in \Omega\},\qquad y\in Y$$

Since the $g_i$ are convex in both arguments and the $h_j$ are linear, it follows that $\Omega(x,\cdot)$ (for all $x\in X$) and $\Omega(\cdot,y)$ (for all $y\in Y$) are convex sets. By definition $(x,y)\in\Omega$ implies that $y\in\Omega(x,\cdot)$ and $x\in\Omega(\cdot,y)$. Moreover we assume that for all $x\in X$ there is a $y\in Y$ such that $(x,y)\in\Omega$, and that for all $y\in Y$ there is a $x\in X$ such that $(x,y)\in\Omega$. Thus, the sets $\Omega(x,\cdot),\Omega(\cdot,y)$ are always non-empty.

It will be convenient to define the set $\mathcal D$ as

$$\mathcal D = \{(x,y)\in \Omega: g_i(x,y) < 0\,\forall i\}$$

Notice that the inequality is strict.

Define the functions $\xi:Y\rightarrow X$ and $\eta:X\rightarrow Y$ implicitly via the equations:

$$\min_{x\in \Omega(\cdot,y)} f(x,y) = f(\xi(y),y)$$
$$\max_{y\in \Omega(x,\cdot)} f(x,y) = f(x,\eta(x))$$

It is important to notice that $f(x,y)$ with $x$ fixed as a function of $y\in\Omega(x,\cdot)$ is concave, while $f(x,y)$ with $y$ fixed as a function of $x\in\Omega(\cdot,y)$ is convex. Even though the values of $\xi(y)$ or $\eta(x)$ may not be unique (if $f$ has "flat" regions), we assume that we can define the functions $\xi(y),\eta(x)$ consistent with the extremizations above and such that $\xi(y),\eta(x)$ are differentiable. Moreover, we assume that if $(x,y)\in\mathcal D$ then $(\xi(y),y)\in\mathcal D$ and $(x,\eta(x))\in\mathcal D$ also. Intuitively, we assume that $f$ is extremized in "interior" points.

Then $\xi(y),\eta(x)$ satisfy the stationarity conditions

$$\left.\nabla_x f(x,y)\right|_{x=\xi(y)} + \sum_j \alpha_j(y) \left.\nabla_x h_j(x,y)\right|_{x=\xi(y)} = 0,\qquad \forall y\in Y$$
$$\left.\nabla_y f(x,y)\right|_{y=\eta(x)} + \sum_j \beta_j(x) \left.\nabla_y h_j(x,y)\right|_{y=\eta(x)} = 0,\qquad \forall x\in X$$

where $\alpha_j(y),\beta_j(x)$ are Lagrange multipliers. These equations simply state that the gradient of $f$ must point in a direction spanned by the gradients of the equality constrains, so that $f$ cannot increase/decrease without violating these constrains.

We have:

$$\begin{aligned}
\nabla_x f(x,\eta(x)) &= \left.\nabla_x f(x,y)\right|_{y=\eta(x)} + \nabla_x \eta(x) \cdot \left. \nabla_y f(x,y) \right|_{y=\eta(x)} \\
&= \left.\nabla_x f(x,y)\right|_{y=\eta(x)} - \sum_j \beta_j(x) \nabla_x \eta(x) \cdot \left.\nabla_y h_j(x,y)\right|_{y=\eta(x)} \\
\end{aligned}$$

$$\begin{aligned}
\nabla_y f(\xi(y),y) &= \left.\nabla_y f(x,y)\right|_{x=\xi(y)} + \nabla_y \xi(y) \cdot \left. \nabla_x f(x,y) \right|_{x=\xi(y)} \\
&= \left.\nabla_y f(x,y)\right|_{x=\xi(y)} - \sum_j \alpha_j(y) \nabla_y \xi(y) \cdot \left.\nabla_x h_j(x,y)\right|_{x=\xi(y)} \\
\end{aligned}$$

Since the equations $h_j(x,\eta(x))=0$ and $h_j(\xi(y),y)=0$ are identities, it follows that:

$$\nabla_x h_j(x,\eta(x)) = \left.\nabla_x h_j(x,y)\right|_{y=\eta(x)} + \nabla_x \eta(x)\cdot \left.\nabla_y h_j(x,y)\right|_{y=\eta(x)} = 0$$
$$\nabla_y h_j(\xi(y),y)  = \left.\nabla_y h_j(x,y)\right|_{x=\xi(y)}  + \nabla_y \xi(y)\cdot \left.\nabla_x h_j(x,y)\right|_{x=\xi(y)}  = 0$$

Therefore,

$$\begin{aligned}
\nabla_x f(x,\eta(x)) &= \left.\nabla_x f(x,y)\right|_{y=\eta(x)} + \sum_j \beta_j(x) \left.\nabla_x h_j(x,y)\right|_{y=\eta(x)} \\
\end{aligned}$$

$$\begin{aligned}
\nabla_y f(\xi(y),y) &= \left.\nabla_y f(x,y)\right|_{x=\xi(y)} + \sum_j \alpha_j(y) \left.\nabla_y h_j(x,y)\right|_{x=\xi(y)} \\
\end{aligned}$$

Now we will prove that the minimax problems:

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y) = \min_{x\in X} f(x,\eta(x))$$
$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)} f(x,y) = \max_{y\in Y} f(\xi(y),y)$$

are equivalent. Let $(x^*,y^*)\in\Omega$ be a solution of the first problem,

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)} f(x,y) = f(x^*,y^*)$$

It follows that $y^* = \eta(x^*)$ and $\nabla_x f(x^*,\eta(x^*)) = 0$.


The solutions are the stationary points of $f(x,\eta(x))$ and $f(\xi(y),y)$ (recall that we are only considering "interior" critical points), respectively. 


### Saddle-points

Let $\rho^*$ be the optimal value of the minimax. Suppose that it is attained at a point $(x^*,y^*)$, so that $f(x^*,y^*) = \rho^*$. Furthermore, suppose that $(x^*,y^*)$ is an interior point of $\mathcal D$. This means that $g_i(x^*,y^*) < 0$ (note the strict inequality) for all $i = 1,\dots,p$.

$$\nabla_x f + \sum_j \alpha_j \nabla_x h_j = 0$$
$$\nabla_y f + \sum_j \alpha_j \nabla_y h_j = 0$$