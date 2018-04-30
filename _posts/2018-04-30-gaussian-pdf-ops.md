---
layout: post
title: Product and division of Gaussian densities
comments: true
---
# Product and division of Gaussian densities

Let

$$\phi(x,\nu) = \frac{1}{\sqrt{2\pi \nu}}\exp\left(-\frac{x^2}{2\nu}\right)$$

be the univariate Gaussian probability density function (PDF) centered at 0. The Guassian PDF centered at $\mu$ is $\phi(x-\mu,\nu)$.

The product of two such densities is given by:

$$\phi(x-\mu_1;\nu_1) \phi(x-\mu_2;\nu_2) = \phi(x-\mu;\nu) \phi(\mu_1-\mu_2,\nu_1+\nu_2)$$

where

$$m=\frac{\nu_1m_2+\nu_2m_1}{\nu_1+\nu_2},\qquad\nu=\frac{\nu_1\nu_2}{\nu_1+\nu_2}$$

Note that the product is not normalized due to the factor $\phi(\mu_1-\mu_2,\nu_1+\nu_2)$.
