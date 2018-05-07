---
layout: post
title: Constrained minimax
comments: true
---
# Constrained minimax

## Problem statement and preliminary definitions

Let $X\subset\mathbb R^n,Y\subset\mathbb R^m$ be convex compact sets, $f:X\times Y\rightarrow\mathbb R$ a saddle-function (convex in $x$, concave in $y$). We consider a restricted domain $\Omega \subset X\times Y$ defined by the constrains

$$h_j(x,y) = 0, \quad j= 1,\dots,q$$

where $h_j:X\times Y\rightarrow\mathbb R$ are affine functions. Then $\Omega$ is convex. Furthermore we assume that the functions $f,h_j$ are all differentiable. Denote the first-derivative functions using,

$$f^1(x,y) = \nabla_x f(x,y),\quad h^1_j(x,y) = \nabla_x h_j(x,y)$$
$$f^2(x,y) = \nabla_y f(x,y),\quad h^2_j(x,y) = \nabla_y h_j(x,y)$$

Note that $f^1,h^1_j$ are functions $X\times Y\rightarrow \mathbb R^n$ while $f^2,h_j^2$ are functions $X\times Y\rightarrow\mathbb R^m$.

The sets $\Omega(x,\cdot)\subset Y$ and $\Omega(\cdot,y)\subset X$ defined by

$$\Omega(x,\cdot)=\{y \in Y : (x,y) \in \Omega\},\qquad x\in X$$
$$\Omega(\cdot,y)=\{x \in X : (x,y) \in \Omega\},\qquad y\in Y$$

are also convex. By definition

$$(x,y)\in\Omega \iff y\in\Omega(x,\cdot) \land x\in\Omega(\cdot,y)$$

Without loss of generality we assume that for all $x\in X$ there is a $y\in Y$ such that $(x,y)\in\Omega$, and that for all $y\in Y$ there is a $x\in X$ such that $(x,y)\in\Omega$. There is no loss of generality, because if for some $x'\in X$ there is no $y\in X$ such that $(x',y)\in\Omega$, then we can remove $x'$ from $X$ without changing the problem (a similar argument applies for $Y$).

In this note we investigate the minimax and maximin problems

$$\min_{x\in X}\max_{y\in\Omega(x,\cdot)}f(x,y) \qquad \text{(minimax)}$$
$$\max_{y\in Y}\min_{x\in\Omega(\cdot,y)}f(x,y) \qquad \text{(maximin)}$$

Under the regularity conditions given above for $f,h$, we will show that the two problems lead to the same solution.

## The extremizer functions $\hat x$ and $\hat y$

By the regularity assumptions on $f,h$, there exist differentiable functions $\hat x(y),\hat y(x)$ such that,

$$\min_{x\in \Omega(\cdot,y)} f(x,y) = f(\hat x(y),y), \quad \forall y\in Y$$
$$\max_{y\in \Omega(x,\cdot)} f(x,y) = f(x,\hat y(x)), \quad \forall x\in X$$

We assume that $f$ has no "flat" regions within $\Omega$, and that therefore the functions $\hat x,\hat y$ are uniquely defined. Stationarity of $f$ within $\Omega$ w.r.t $x$ or $y$ implies that there exist Lagrange multipliers $\alpha_j,\beta_j$ such that

$$f^1(\hat x,y) + \sum_j \alpha_j h_j^1(\hat x,y) = 0, \quad \forall y\in Y$$
$$f^2(x,\hat y) + \sum_j \beta_j  h_j^2(x,\hat y) = 0, \quad \forall x\in X$$

These equations state that the gradient of $f$ must lie in the space spanned by the gradient of the constrains (hence the value of $f$ cannot change without violating these constrains). Since $f$ is convex-concave and $h$ affine, these equations determine $\hat x$ and $\hat y$ uniquely. Note that $\alpha_j$ depends on $y$ while $\beta_j$ depends on $x$.

## Saddle-points

A point $(x^*,y^*)\in\Omega$ satisfying

$$f(x^*,y^*) \le f(x,y^*)\qquad \forall x\in\Omega(\cdot,y^*)$$
and
$$f(x^*,y^*) \ge f(x^*,y)\qquad \forall y\in\Omega(x^*,\cdot)$$

is called a saddle-point of $f$ in $\Omega$. It follows that $x^* = \hat x(y^*)$ and $y^* = \hat y(x^*)$.

Imagine a two dimensional plot where the points $X$ are represented on the horizontal axis and the points $Y$ are represented in the vertical axis. In this plot, we draw the curves $x = \hat x(y)$ and $y = \hat y(x)$. Then the saddle-points are the intersections of these two curves.

## Saddle-critical points

We have:

$$\nabla_x f(x,\hat y(x)) = f^1(x,\hat y) + \nabla_x \hat y \cdot f^2(x,\hat y)$$
$$\nabla_y f(\hat x(y),y) = f^2(\hat x,y) + \nabla_y \hat x \cdot f^1(\hat x,y)$$

From the stationarity conditions derived above,

$$\nabla_x f(x,\hat y(x)) = f^1(x,\hat y) - \sum_j\beta_j\nabla_x\hat y \cdot h_j^2(x,\hat y)$$

$$\nabla_y f(\hat x(y),y) = f^2(\hat x,y) - \sum_j\alpha_j\nabla_y \hat x \cdot h_j^1(\hat x,y)$$

Since the equations $h_j(x,\hat y)=h_j(\hat x,y)=0$ are identities, it follows that:

$$\nabla_x h_j(x,\hat y(x)) = h_j^1(x,\hat y) + \nabla_x \hat y \cdot h_j^2(x,\hat y) = 0$$

$$\nabla_y h_j(\hat x(y),y) = h_j^2(\hat x,y) + \nabla_y \hat x \cdot h_j^1(\hat x,y) = 0$$

Hence,

$$\nabla_x f(x,\hat y(x)) = f^1(x,\hat y) + \sum_j \beta_j  h_j^1(x,\hat y)$$
$$\nabla_y f(\hat x(y),y) = f^2(\hat x,y) + \sum_j \alpha_j h_j^2(\hat x,y)$$

We now prove that the critical points of $f(x,\hat y(x))$ are in one-to-one correspondence with the critical points of $f(\hat x(y),y)$. More precisely, we show that,

* If $x^*\in X$ is a critical point of $f(x,\hat y(x))$, then $y^* = \hat y(x^*)$ is a critical point of $f(\xi(y),y)$, and $x^* = \hat x(y^*)$.
* If $y^*\in Y$ is a critical point of $f(\xi(y),y)$, then $x^* = \hat x(y^*)$ is a critical point of $f(x,\eta(x))$, and $y^* = \hat y(x^*)$.

Suppose that $\nabla_x f(x^*,\hat y(x^*)) = 0$. From the expression derived above for $\nabla_x f(x,\hat y(x))$, it follows that

$$f^1(x^*,y^*) + \sum_j \beta_j h_j^1(x^*,y^*) = 0$$

where $y^* = \hat y(x^*)$. This equation implies that $x^*$ is a stationary point of $f(x,y^*)$ w.r.t. $x$, subject to $x \in \Omega(\cdot,y)$. Therefore $\hat x(y^*) = x^*$ and $\alpha_j = \beta_j$. From $y^* = \hat y(x^*)$ we also have the stationary condition,

$$f^2(x^*,y^*) + \sum_j \beta_j h_j^2(x^*,y^*) = 0$$

Since $\beta_j = \alpha_j$, this implies $\nabla_y f(\hat x(y^*),y^*) = 0$. Therefore $y^*$ is a critical point of $f(\hat x(y),y)$. The proof in the other direction is similar. The result can be recast in the form of a double-implication:

**Theorem.** Let $(x^*,y^*)\in\Omega$. Then

$$\nabla_x f(x^*,\hat y(x^*)) = 0 \land y^* = \hat y(x^*) \iff
  \nabla_y f(\hat x(y^*),y^*) = 0 \land x^* = \hat x(y^*)$$

The points $(x^*,y^*)\in\Omega$ satisfyig these conditions will be called saddle-critical points.

## Saddle-critical points are saddle-points

Suppose that $(x^*,y^*)$ is a saddle-critical point. Then $x^* = \hat y(y^*)$ and $y^* = \hat x(x^*)$. Hence

$$\min_{x\in \Omega(\cdot,y^*)} f(x,y^*)
= \max_{y\in \Omega(x^*,\cdot)} f(x,y^*)
= f(x^*,y^*)$$

Hence $(x^*,y^*)$ is a saddle-point.

On the other hand, if $(x^*,y^*)$ is a saddle-point, it might not be critical if it lies at the boundary of the domain. If it is interior, then it must also be a saddle-critical point.

## Conditions for a saddle-critical point

In summary, the point $(x^*,y^*)\in\Omega$ is a saddle-critical point if and only if:

$$f^1(x^*,y^*) + \sum_j \lambda_j h_j^1(x^*,y^*) = 0$$
$$f^2(x^*,y^*) + \sum_j \lambda_j h_j^2(x^*,y^*) = 0$$

for some set of numbers $\lambda_j$.
