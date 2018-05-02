---
layout: post
title: Convexity of the Kullback-Leibler divergence
comments: true
---
# Convexity of the Kullback-Leibler divergence

We begin with the function $\gamma(u,v) = u\ln(u/v)$, where $u,v\ge0$ are real numbers. We assume that $\gamma(0,0) = 0$. The derivatives are

$$
\frac{\partial \gamma}{\partial u} = 1 + \ln(u/v), \qquad
\frac{\partial \gamma}{\partial v} = -u/v
$$

and

$$
\frac{\partial^2 \gamma}{\partial u^2} = 1/u, \quad
\frac{\partial^2 \gamma}{\partial v^2} = u/v^2, \quad
\frac{\partial^2 \gamma}{\partial u \partial v} = -1/v
$$

To prove that $\gamma(u,v)$ is convex, we must evaluate the quadratic form $(x,y)^T H (x,y)$ for arbitrary $x,y \in \mathbb R$, where $H$ is the Hessian. Since

$$(x,v)^T H (u,v) = \frac{(vx - uy)^2}{uv^2} \ge 0$$

it follows that $\gamma(u,v)$ is convex.

Since $\gamma(u,v)$ is convex, we can compute its Legendre transform. It is possible to do this with respect to $u$, to $v$, or both.

Let us begin with the conjugate w.r.t. $u$,

$$\gamma^*(\xi, v) = \sup_u (\xi u - \gamma(u,v))$$

The derivative of $\xi u - \gamma(u,v)$ w.r.t. $u$ is $\xi - \ln(u/v) - 1$, which becomes zero for $u = v\mathrm e^{\xi - 1}$. Hence

$$\gamma^*(\xi, v) = v\mathrm e^{\xi - 1}$$

Now consider the conjugte w.r.t. $v$:

$$\gamma^*(u, \eta) = \sup_v (\eta v - \gamma(u,v))$$

The derivative of $\eta v - \gamma(u,v)$ w.r.t. $v$ is $\eta + u/v$, which is zero for $v = -u/\eta$. Since $u,v$ must be positive,

$$\gamma^*(u, \eta) = \begin{cases}
    \infty & \eta \ge 0 \\
    -u - u\ln(-\eta) & \eta < 0
\end{cases}$$

Finally, we consider the Legendre transform of both $u$ and $v$:

$$\gamma^*(\xi,\eta) = \sup_{u,v}(\xi u + \eta v - \gamma(u,v))$$

The critical points of $\xi u + \eta v - \gamma(u,v)$ satisfy the simultaneous equations

$$\xi - \ln(u/v) - 1 = 0, \qquad \eta + u / v = 0$$

If $\xi \ne \ln(-\eta) + 1$ it is impossible to satisfy both equations simultaneously. Therefore the Legendre transform has a singular domain, consisting of the values $\xi,\eta$ that satisfy the equation $\xi = \ln(-\eta) + 1$. If this equality holds, all the points $u,v$ satisfying $u/v = -\eta$ are critical.

*The Legendre transform of $\gamma(u,v)$ with respect to both arguments seems to be very degenerate. Therefore I did not study it any further.*

## The Kullback-Leibler divergence

Let $u_i,v_i \ge 0$. There are two ways of defining the Kullback-Leibler (KL) divergence:

$$\mathrm{KL}(u||v) = \sum_i u_i \ln(u_i/v_i)$$

or

$$\mathrm{KL}'(u||v) = \sum_i (u_i \ln (u_i/v_i) - u_i + v_i)$$

Typically $u,v$ are probability distributions satisfying $\sum_i u_i = \sum_i v_i = 1$, in which case $\mathrm{KL}(u||v) = \mathrm{KL}'(u||v)$.

As we have shown above, $u_i \ln (u_i/v_i) = \gamma(u_i,v_i)$ is convex in $u_i,v_i$. Since $\mathrm{KL}(u||v)$ and $\mathrm{KL}'(u||v)$ are sums of convex functions and linear terms, they are convex. In addition, convexity is preserved under affine constrains, because if two points satisfy an affine constrain (equality or inequality), the points in the line segment joining them also satisfy the constrain. Therefore the KL divergence remains convex in presence of linear constrains such as $\sum_i u_i = \sum_i v_i = 1$.

## Legendre transforms of the KL in absence of constrains

Now we want to compute the Legendre transform of the KL divergence. If the arguments $u_i,v_i$ are not constrained to be normalized, we can compute the Legendre transform simply as a sum of the Legendre transforms of $\gamma(u_i,v_i)$ for each term. This method relies on the assumption that the KL is a sum of functions depending on independent variables. If the normalization constrain were enforced, this assumption breaks down. Thus, if the normalization constrain is not enforced, we obtain

$$\begin{aligned}
    \mathrm{KL}^*(\xi || v)
        &= \sup_u \left( \sum_i \xi_i u_i - \sum_i u_i \ln(u_i/v_i) \right) \\
        &= \sum_i \sup_{u_i} ( \xi_i u_i - u_i \ln(u_i/v_i)) \\
        &= \sum_i \gamma^*(\xi_i, v_i) = \sum_i v_i \mathrm e^{\xi_i - 1}
\end{aligned}$$

Similarly,

$$\begin{aligned}
\mathrm{KL}^*(u || \eta) &= \sup_v \left( \sum_i \eta_i v_i - \sum_i u_i \ln(u_i/v_i) \right) \\
    &= \sum_i \gamma^*(u_i, \eta_i) \\
    &= -\sum_i u_i\ln(-\eta_i) - \sum_i u_i, \qquad \eta < 0
\end{aligned}$$

provided $\eta_i < 0$ for all $i$. Using the formula for the Legendre transform of a function plus an affine term, we obtain

$$\begin{aligned}
\mathrm{KL}^{\prime\ast}(\xi||v) 
    &= \mathrm{KL}^*(\xi + \mathbf 1|| v) - \sum_i v_i 
     = \sum_i (\mathrm e^{\xi_i} - 1) v_i \\
\mathrm{KL}^{\prime\ast}(u||\eta) 
    &= \mathrm{KL}^*(\eta - \mathbf 1|| v) + \sum_i u_i 
     = -\sum_i u_i\ln(1-\eta_i),
     \qquad \eta < 1
\end{aligned}$$

where $\mathbf 1$ is a vector with all entries equal to 1.

### Variational definitions

By the duality of the Legendre transform, we obtain the following variational definitions of the KL divergence:

$$\begin{aligned}
\mathrm{KL}(u||v)
    &= \sup_\xi \left( \sum_i \xi_i u_i - \mathrm{KL}^*(\xi||v) \right)
        = \sup_\xi \left( \sum_i \xi_i u_i - \sum_i v_i \mathrm e^{\xi_i - 1} \right) \\
    &= \sup_{\eta < 0} \left( \sum_i \eta_i v_i - \mathrm{KL}^*(u||\eta) \right)
        = \sup_{\eta < 0} \left( \sum_i \eta_i v_i + \sum_i u_i \ln(-\eta_i) \right) +      \sum_i u_i
\end{aligned}$$

Similarly,

$$\begin{aligned}
\mathrm{KL}'(u||v)
    &= \sup_\xi \left( \sum_i \xi_i u_i - \sum_i (\mathrm e^{\xi_i} - 1) v_i \right) \\
    &= \sup_{\eta < 1} \left(\sum_i \eta_i v_i + \sum_i u_i\ln(1-\eta_i) \right)
\end{aligned}$$

In spite of the fact that we have obtained the Legendre transform of the KL divergence ignoring the normalization constrains, these variational definitions are obviously valid in the particular case that $\sum_i u_i = \sum_i v_i = 1$.

## Legendre transform with constrains

Let $\Omega$ be the set of normalized probability distributions. The constrains $\sum_i u_i = 1\land u_i \ge 0$ can be written concisely as $u \in \Omega$. Due to the normalization constrain, the KL divergence is no longer a sum of independent terms, because variations in a probability term $u_i$ must be accompanied by balanced variations in other terms $u_j$ so as to maintain the sum $\sum_i u_i = 1$ constant.

We must now compute,

$$\mathrm{KL}^*(\xi || v) = \sup_{u \in \Omega}
    \left( \sum_i \xi_i u_i - \sum_i u_i \ln(u_i/v_i) \right)$$

Note that the domain of optimization is now restricted to $\Omega$. The normalization constrain can be dealt with via Lagrangian multipliers. Let

$$L_1(u,v,\lambda) = \sum_i \xi_i u_i - \sum_i u_i \ln(u_i/v_i) + \lambda \sum_i u_i$$

where $\lambda$ is the Lagrangian multiplier associated to the normalization constrain. Differentiating $L_1$ w.r.t. $u_i$ gives the stationarity condition

$$u_i = v_i \mathrm e^{\xi_i + \lambda - 1}
\quad \text{ where } \quad
\lambda = -\ln \sum_i v_i \mathrm e^{\xi_i - 1}$$

where the value of $\lambda$ follows from the normalization of $u_i$. Substituting into $\mathrm{KL}^*(\xi || v)$ we obtain,

$$\mathrm{KL}^*(\xi || v) = - \sum_i v_i \mathrm e^{\xi_i + \lambda - 1} (\lambda - 1) = 1 - \lambda = 1 + \ln \sum_i v_i \mathrm e^{\xi_i - 1}$$

Now we consider

$$\mathrm{KL}^*(u || \eta) = \sup_{v \in \Omega}
    \left( \sum_i \eta_i v_i - \sum_i u_i \ln(u_i/v_i) \right),
    \qquad \eta < 0$$

Differentiating the Lagrangian

$$L_2(u,v,\lambda) = \sum_i \eta_i v_i - \sum_i u_i \ln(u_i/v_i) + \lambda \sum_i v_i$$

w.r.t. $v_i$ gives the stationarity conditions

$$v_i = -\frac{u_i}{\eta_i+\lambda}
\quad \text{ where $\lambda$ satisfies }\quad
\sum_i \frac{u_i}{\eta_i+\lambda} = -1$$

Substituting,

$$\mathrm{KL}^*(u || \eta) =
    -\sum_i \frac{\eta_i u_i}{\eta_i+\lambda} - \sum_i u_i \ln(-\eta_i - \lambda),
    \qquad \eta < 0$$

Unfortunately there doesn't seem to be a simple closed expression for $\mathrm{KL}^*(u||\eta)$ due to the implicit nonlinear equation of $\lambda$.

As in the previous section, we can use the formula for the Legendre transform of a function plus an affine term, to obtain

$$\begin{aligned}
\mathrm{KL}^{\prime\ast}(\xi||v)
    &= \mathrm{KL}^*(\xi + \mathbf 1|| v) - 1
     = \ln \sum_i v_i \mathrm e^{\xi_i}\\
\mathrm{KL}^{\prime\ast}(u||\eta)
    &= \mathrm{KL}^*(\eta - \mathbf 1|| v) + 1
     = 1 - \sum_i \frac{(\eta_i - 1) u_i}{\eta_i+\lambda - 1} - \sum_i u_i \ln(1 - \eta_i - \lambda),
     \qquad \eta < 1
\end{aligned}$$

where $\mathbf 1$ is a vector with all entries equal to 1.

### More variational definitions

Taking the dual Legendre transform, we obtain additional variational definitions of the Kullback-Leibler divergence. These formulas assume that $\sum_i u_i = \sum_i v_i = 1$.

$$\begin{aligned}
\mathrm{KL}(u||v)
    &= \sup_\xi \left( \sum_i \xi_i u_i - \mathrm{KL}^*(\xi||v) \right) \\
    &= \sup_\xi \left( \sum_i \xi_i u_i - 1 - \ln \sum_i v_i \mathrm e^{\xi_i - 1} \right) \\
    &= \sup_\xi \left( \sum_i \xi_i u_i - \ln \sum_i v_i \mathrm e^{\xi_i} \right)
\end{aligned}$$

where the last equality follows from the change of variables $\xi \rightarrow \xi + 1$.

Similarly

$$\begin{aligned}
\mathrm{KL}(u||v)
    &= \sup_{\eta < 0} \left( \sum_i \eta_i v_i - \mathrm{KL}^*(u||\eta) \right) \\
\end{aligned}$$

Unfortunately this formula doesn't seem to be as helpful as the others, because as we noted above, we were unable to obtain a simple closed expression for $\mathrm{KL}^*(u||\eta)$.

## References

The formula 
$\mathrm{KL}(u||v) = \sup_\xi \left( \sum_i \xi_i u_i - \ln \sum_i v_i \mathrm e^{\xi_i} \right)$ is used in the derivation of an energy function for expectation propagation (EP):

* Minka, Thomas P. “The EP Energy Function and Minimization Schemes.” Technical report, 2001. https://tminka.github.io/papers/ep/minka-ep-energy.pdf.

