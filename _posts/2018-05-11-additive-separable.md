---
layout: post
title: Additively separable functions
comments: true
---

Additiviely separable functions are functions $F:X\times Y\rightarrow Z$ that can be written in the form

$$F(x,y) = f(x) + g(y)$$

for suitable functions $f:X\rightarrow Z,g:Y\rightarrow Z$.

I found the following lovely result in Ref. 1.

**Theorem.** $F:X\times Y\rightarrow Z$ is additively separable if and only if for all $a,c\in X,b,d\in Y$, it holds that $F(a,b) + F(c,d) = F(a,d) + F(c,b)$.

**Proof.** Suppose that $F(x,y) = f(x) + g(y)$. Then

$$\begin{aligned}
F(a,b) + F(c,d) &= f(a) + g(b) + f(c) + g(d) \\
&= f(a) + g(d) + f(c) + g(b) = F(a,d) + F(c,b)
\end{aligned}$$

Conversely, if $F(a,b) + F(c,d) = F(a,d) + F(c,b)$ for all $a,c\in X,b,d\in Y$, we define $f(x) = F(x,y_0),g(y)=F(x_0,y) - F(x_0,y_0)$, for some $x_0\in X,y_0\in Y$. Then

$$f(x) + g(y) = F(x,y_0) + F(x_0,y) - F(x_0,y_0) = F(x,y)$$

Q.E.D.

A different characterization stems from partial differentiation.

**Theorem.** A differentiable function $F:X\times Y\rightarrow Z$ is addditively separable if and only if

$$\frac{\partial F}{\partial x\partial y}=0$$

**Proof.** Obviously, if $F(x,y)=f(x)+g(y)$ then the PDE above holds. Conversely, suppose the PDE holds. This means that the function $\partial F/\partial x = h(x)$ is independent of $y$. Solving this differential equation gives $F(x,y) = f(x) + g(y)$, where $f(x) = \int h(x)\mathrm d x$ and $g(y)$ arises as an integration constant. Q.E.D.

**Theorem.** The point $(x^\ast,y^\ast)$ is a critical point of the additively separable function $F(x,y)=f(x)+g(y)$ if and only if $x^\ast$ is a critical point of $f$ and $y^\ast$ is a critical point of $g$.

**Proof.** This follows directly from $\partial F/\partial x = f'(x)$ and $\partial G/\partial y = g'(y)$. Q.E.D.

A more strong result is possible.

**Theorem.** The critical point $(x^\ast,y^\ast)$ of the additively separable function $F(x,y)=f(x)+g(y)$ is a local maximum if and only if $x^\ast$ is a local maximum of $f$ and $y^\ast$ a local maximum of $g$.

**Proof.** The result is obvious once we realize that the Hessian is diagonal,

$$H = \left[\begin{array}{cc}
\frac{\partial^{2}F}{\partial x^{2}} & \frac{\partial^{2}F}{\partial x\partial y}\\
\frac{\partial^{2}F}{\partial x\partial y} & \frac{\partial^{2}F}{\partial y^{2}}
\end{array}\right]=\left[\begin{array}{cc}
\frac{\partial^{2}F}{\partial x^{2}} & 0\\
0 & \frac{\partial^{2}F}{\partial y^{2}}
\end{array}\right]$$

because, as shown above,

$$\frac{\partial F}{\partial x\partial y}=0$$

Q.E.D.

## References

This note is almost a copy of the following resource.

1. Steven F. Bellenot, Additively separable functions: Functions of the form $F(x, y) = f(x) + g(y)$. [Link](https://www.math.fsu.edu/~bellenot/class/s05/cal3/proj/project.pdf)