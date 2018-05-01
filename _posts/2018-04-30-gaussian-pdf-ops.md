---
layout: post
title: Product and division of Gaussian densities
comments: true
---
# Product and quotient of Gaussian densities

The product and quotient of Gaussian probability densities arise in multiple applications. For example, expectation propagation. Here I collect the formulas.

## Univariate

Let

$$\phi(x,\nu) = \frac{1}{\sqrt{2\pi \nu}}\exp\left(-\frac{x^2}{2\nu}\right)$$

be the univariate Gaussian probability density function (PDF) centered at 0. The Guassian PDF centered at $\mu$ is $\phi(x-\mu,\nu)$.

The **product of two univariate Guassian PDFs** is given by:

$$\phi(x-\mu_1;\nu_1) \phi(x-\mu_2;\nu_2) =
\phi(x-\mu;\nu) \phi(\mu_1-\mu_2,\nu_1+\nu_2)$$

where

$$m=\frac{\nu_1m_2+\nu_2m_1}{\nu_1+\nu_2},\qquad\nu=\frac{\nu_1\nu_2}{\nu_1+\nu_2}$$

Note that the product is not normalized due to the factor $\phi(\mu_1-\mu_2,\nu_1+\nu_2)$.

The **quotient of two univariate Gaussian PDFs** is given by:

$$\frac{\phi(x-\mu_1,\nu_1)}{\phi(x-\mu_2,\nu_2)} =
\frac{\phi(x-\mu,\nu)}{\phi(\mu_1 - \mu_2,\nu_2-\nu_1)} \frac{\nu_2}{\nu_1-\nu_2}$$

where

$$\mu = \frac{\mu_1\nu_2 - \mu_2\nu_1}{\nu_2 - \nu_1}, \qquad
\nu = \frac{\nu_1 \nu_2}{\nu_2 - \nu_1}$$
## Multivariate

We generalize the formulae above to the multivariate case. Let

$$\phi(\mathbf x; \mathbf \Sigma) =
(2\pi \det \mathbf\Sigma)^{-1/2} 
\exp\left(-\frac{1}{2} \mathbf x^T \mathbf \Sigma^{-1} \mathbf x\right)$$

If $\mathbf x$ is a one-dimensional vector this reduces to the univariate PDF.
The product of two densities is again of the Gaussian form. As before, it is not normalized:

$$\phi(\mathbf x - \mathbf u_1, \mathbf \Sigma_1)
  \phi(\mathbf x - \mathbf u_1, \mathbf \Sigma_1) =
\phi(\mathbf u_1 - \mathbf u_2, \mathbf \Sigma_1 + \mathbf \Sigma_2)
\phi(\mathbf x - \mathbf u, \mathbf \Sigma)$$

where

$$\mathbf \Sigma^{-1} = \mathbf \Sigma_1^{-1} + \mathbf \Sigma_2^{-1}$$
$$\mathbf u = (\mathbf \Sigma_1^{-1} + \mathbf \Sigma_2^{-1})^{-1} 
(\Sigma_1^{-1} \mathbf u_1 + \Sigma_2^{-1} \mathbf u_2)$$

TODO: Quotient of multivariate Gaussians.

## References

There are many derivations of these equations in the web. Here are some that I have found.

1. http://www.tina-vision.net/docs/memos/2003-003.pdf (product of $n$ PDFs)
2. http://www.gatsby.ucl.ac.uk/~turner/workshop/EPpapers/Minka%202007%20Quick%20EP%20reference.pdf (multivariate quotient for EP)
3. http://davmre.github.io/blog/statistics/2015/03/27/gaussian_quotient (multivariate quotient)
4. https://cs.nyu.edu/~roweis/notes/gaussid.pdf