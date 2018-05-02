---
layout: post
title: Minimax with constrains
comments: true
---
# Minimax with constrains

## Problem statement

Let $f:X\times Y\rightarrow\mathbb R$ be a saddle-function \(convex in $x$ and concave in $y$\). Here $X\subset\mathbb R^n, Y\subset\mathbb R^m$ are convex sets. Consider the following constrained optimization problem:

$$\min_x\max_y f(x,y)$$

subject to

$$g_i(x,y) \le 0,\quad i = 1,\dots,r$$

where the functions $g_i:X\times Y \rightarrow\mathbb R$ are convex in both arguments $x,y$. 

Furthermore, we assume the following regularity conditions: That the functions $f$ and $g_i$, $i=1,\dots,r$ are differentiable in all arguments, and that the sets $X,Y$ are compact \(then $X\times Y$ is also convex and compact\).

Let us define the sets

$$\Omega = \{(x,y) \in X \times Y : g_i(x,y) \le 0 \text{ for } i = 1,\dots,r\}$$
$$\Omega(x,\cdot) = \{(x,y): y \in Y \land g_i(x,y) \le 0 \text{ for } i = 1,\dots,r\}$$
$$\Omega(\cdot,y) = \{(x,y): x \in X \land g_i(x,y) \le 0 \text{ for } i = 1,\dots,r\}$$

By our assumptions $\Omega$ and $\Omega(x,\cdot),\Omega(\cdot,y)$ are convex and compact. The optimization problem can be rewritten as:

$$\min_{x\in X} \max_{y \in \Omega(x,\cdot)} f(x,y)$$


## Conditions for optimality

Let $(x^*,y^*)\in\Omega$ be an optimal point.

$$\nabla$$

## References

1. Žaković, Stanislav, Costas Pantelides, and Berc Rustem. “An Interior Point Algorithm for Computing Saddle Points of Constrained Continuous Minimax.” Annals of Operations Research 99, no. 1–4 (December 1, 2000): 59–77. [DOI: 10.1023/A:1019284715657](https://doi.org/10.1023/A:1019284715657).