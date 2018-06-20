---
layout: post
title: Moments of the truncated bivariate Gaussian 
comments: true
---

Let

$$\phi\left(y_{1},y_{2}\right)=\frac{1}{2\pi\sqrt{1-\rho^{2}}}\exp\left(-\frac{y_{1}^{2}+y_{2}^{2}-2\rho y_{1}y_{2}}{2\left(1-\rho^{2}\right)}\right)$$

be the standardized bidimensional Gaussian distribution, where $\rho = \langle y_1 y_2\rangle$ is the correlation coefficient. The standardization means that $\langle y_1\rangle = \langle y_2\rangle = 0$ and $\langle y_1^2\rangle = \langle y_2^2\rangle = 1$, which can always be achieved by translating and scaling.

We consider the truncation of this distribution to a rectangle $a_1 \le y_1 \le b_1$, $a_2 \le y_2 \le b_2$. Let

$$z=\int_{a_{1}}^{b_{1}}\mathrm{d}y_{1}\int_{a_{2}}^{b_{2}}\mathrm{d}y_{2}\,\phi\left(y_{1},y_{2}\right)$$

be the partition function of the truncated distribution, and

$$M(t_1,t_2) = \frac{1}{z} \int_{a_{1}}^{b_{1}}\mathrm{d}y_{1}\int_{a_{2}}^{b_{2}}\mathrm{d}y_{2}\,\phi\left(y_{1},y_{2}\right)\mathrm{e}^{t_{1}y_{1}+t_{2}y_{2}}$$

the moment-generating function.

Defining $\xi_1=y_1-t_1-\rho t_2$ and $\xi_2=y_2-t_2-\rho t_1$ it is easy to verify the following identity:

$$t_{1}y_{1}+t_{2}y_{2}-\frac{y_{1}^{2}+y_{2}^{2}-2\rho y_{1}y_{2}}{2\left(1-\rho^{2}\right)}=\frac{1}{2}\left(t_{1}^{2}+t_{2}^{2}+2\rho t_{1}t_{2}\right)-\frac{\xi_{1}^{2}+\xi_{2}^{2}-2\rho\xi_{1}\xi_{2}}{2\left(1-\rho^{2}\right)}$$

It follows that

$$zM=\mathrm{e}^{\frac{1}{2}\left(t_{1}^{2}+t_{2}^{2}+2\rho t_{1}t_{2}\right)}\int_{a_{1}^{*}}^{b_{1}^{*}}\mathrm{d}\xi_{1}\int_{a_{2}^{*}}^{b_{2}^{*}}\mathrm{d}\xi_{2}\,\phi\left(\xi_{1},\xi_{2}\right)$$

where $a_{1}^{*}=a_{1}-t_{1}-\rho t_{2}$, $b_{1}^{*}=b_{1}-t_{1}-\rho t_{2}$, $a_{2}^{*}=a_{2}-t_{2}-\rho t_{1}$, $b_{2}^{*}=b_{2}-t_{2}-\rho t_{1}$.

The moments are obtained by differentiating $M$ w.r.t. $t_i$ and evaluating at $t_1=t_2=0$. Recall the calculus rule for the derivative of a definite integral w.r.t to a parameter:

$$\frac{\partial}{\partial p}\int_{a\left(p\right)}^{b\left(p\right)}f\left(p,x\right)\mathrm{d}x=\int_{a\left(p\right)}^{b\left(p\right)}\frac{\partial f\left(p,x\right)}{\partial p}\mathrm{d}x+f\left(p,b\left(p\right)\right)b^{\prime}\left(p\right)-f\left(p,a\left(p\right)\right)a^{\prime}\left(p\right)$$

Then:

$$\begin{aligned}
z\frac{\partial M}{\partial t_{1}} & = 
\frac{\partial}{\partial t_{1}}\int_{a_{1}^{*}}^{b_{1}^{*}}\mathrm{d}\xi_{1}\int_{a_{2}^{*}}^{b_{2}^{*}}\mathrm{d}\xi_{2}\,\phi\left(\xi_{1},\xi_{2}\right) \\
  &=\int_{a_{1}}^{b_{1}}\mathrm{d}\xi_{1}\frac{\partial}{\partial t_{1}}\int_{a_{2}^{*}}^{b_{2}^{*}}\mathrm{d}\xi_{2}\,\phi\left(\xi_{1},\xi_{2}\right)-\int_{a_{2}}^{b_{2}}\mathrm{d}\xi_{2}\,\phi\left(b_{1},\xi_{2}\right)+\int_{a_{2}}^{b_{2}}\mathrm{d}\xi_{2}\,\phi\left(a_{1},\xi_{2}\right) \\
  &=\rho\int_{a_1}^{b_1}\phi(\xi_1,a_2)\mathrm{d}\xi_1 - \rho\int_{a_1}^{b_1}\phi(\xi_1,b_2)\mathrm{d}\xi_1 - \int_{a_2}^{b_2}\phi(b_1,\xi_2)\mathrm{d}\xi_2 + \int_{a_2}^{b_2}\phi(a_1,\xi_2)\mathrm{d}\xi_2
\end{aligned}$$

This is equivalent to Eq. 5 in Ref. 1. The problem of computing $\left\langle y_1\right\rangle$ originally involved bidimensional integrations. Observe that now it as been reduced to the computation of one-dimensional integrations. However, we still need to compute $z$, which still involves two-dimensional integrations.


# References

1. Muthén, Bengt. “Moments of the Censored and Truncated Bivariate Normal Distribution.” British Journal of Mathematical and Statistical Psychology 43, no. 1 (1990): 131–43. https://doi.org/10.1111/j.2044-8317.1990.tb00930.x.
