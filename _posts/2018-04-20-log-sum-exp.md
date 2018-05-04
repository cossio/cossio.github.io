---
layout: post
title: Log-Sum-Exp
comments: true
---
# Log-Sum-Exp

**Theorem.** The function $f\left(\mathbf{x}\right)=\ln\left(\sum_{i}\mathrm{e}^{x_{i}}\right)$ is convex.

**Proof.** Differentiating,

$$
\frac{\partial f}{\partial x_k} =
    \frac{\mathrm{e}^{x_{k}}}{\sum_{i}\mathrm{e}^{x_{i}}},
\quad
\frac{\partial f^2}{\partial x_k^2} =
    \frac{\sum_{i\ne k} \mathrm e^{x_k + x_i}}{\left(\sum_i\mathrm e^{x_i}\right)^2}
$$

$$
\frac{\partial f^2}{\partial x_k \partial x_l}
    = -\frac{\mathrm e^{x_k + x_l}}{\left(\sum_i\mathrm e^{x_i}\right)^2}
    \qquad (k\ne l)
$$

To show that the Hessian is positive-definite, evaluate the corresponding quadratic form for an arbitrary vector $\mathbf{v}$. Denoting $z_i = \mathrm e^{x_i}$, we have

$$\begin{aligned}
\sum_{kl}\frac{\partial f^2}{\partial x_k \partial x_l}v_k v_l
    &= \sum_k\frac{\partial f^2}{\partial x_k^2} v_k^2 + \sum_k \sum_{l\ne k}\frac{\partial f^2}{\partial x_k \partial x_l} v_k v_l \\
    &= \frac{\sum_k \sum_{i\ne k} z_k z_i v_k^2 - \sum_k \sum_{l\ne k} z_k z_{l}v_k v_l}{\left(\sum_i z_i \right)^2} \\
    &= \frac{\sum_{ki} z_k z_i v_k^2 - \sum_{kl} z_k z_l v_k v_l}{\left(\sum_i z_i\right)^2} \\
    &= \frac{\left(\sum_i z_i \right)\left(\sum_k z_k v_k^2\right) - \left(\sum_k z_k v_k\right)^2}{\left(\sum_i z_i\right)^2} \ge 0
\end{aligned}$$

The last inequality follows from the Cauchy-Schwartz inequality. See also pg. 74 of [Boyd2004].

**Theorem.** The function $g(\mathbf x) = \ln\left(\sum_i c_i \mathrm e^{a_i x_i}\right)$ is convex, where $a_i \in \mathbb R, c_i \in \mathbb R^+$.

**Proof.** $g(\mathbf x) = f(\mathbf a^T \mathbf x + \mathbf b)$, where $b_i = \ln c_i$. The result follows from the previous theorem and the invariance of convexity under composition with affine mappings.
See also [Boyd2004] §3.2.2.

**Theorem.** If the functions $g_i(\mathbf x)$ are convex, then $\ln \left( \sum_i \mathrm e^{g_i(\mathbf x)} \right)$ is convex.

**Proof.** See [Boyd2004] Example 3.14.

&nbsp;

## References

**[Boyd2004]** Stephen P. Boyd and Lieven Vandenberghe, Convex Optimization (Cambridge, UK ; New York: Cambridge University Press, 2004).
