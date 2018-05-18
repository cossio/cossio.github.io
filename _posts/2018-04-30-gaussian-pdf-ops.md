---
layout: post
title: Product and division of Gaussian densities
comments: true
---
# Product and quotient of Gaussian densities

Products and quotients of Gaussian probability densities arise in multiple applications. For example, the expectation propagation (EP) algorithm of Thomas Minka.

Here I collect some useful equations.

## Univariate

Let

$$\phi(x,\nu) = \frac{1}{\sqrt{2\pi \nu}}\exp\left(-\frac{x^2}{2\nu}\right)$$

be the univariate Gaussian probability density function (PDF) centered at 0. The Guassian PDF centered at $\mu$ is $\phi(x-\mu,\nu)$.

Let $\mu_1,\mu_2,\nu_1,\nu_2, x \in \mathbb R$, $\nu_1,\nu_2 > 0$. 

The **product of two univariate Guassian PDFs** is given by:

$$\phi(x-\mu_1,\nu_1) \phi(x-\mu_2,\nu_2) =
\phi(x-\mu,\nu) \phi(\mu_1-\mu_2,\nu_1+\nu_2)$$

where

$$\mu=\frac{\nu_1\mu_2+\nu_2\mu_1}{\nu_1+\nu_2},\qquad\nu=\frac{\nu_1\nu_2}{\nu_1+\nu_2}$$

Note that the product is not normalized due to the factor $\phi(\mu_1-\mu_2,\nu_1+\nu_2)$.

The **quotient of two univariate Gaussian PDFs** is given by:

$$\frac{\phi(x-\mu_1,\nu_1)}{\phi(x-\mu_2,\nu_2)} =
\frac{\phi(x-\mu,\nu)}{\phi(\mu_1 - \mu_2,\nu_2-\nu_1)} \frac{\nu_2}{|\nu_1-\nu_2|}$$

where

$$\mu = \frac{\nu_1\mu_2 - \nu_2\mu_1}{\nu_1 - \nu_2}, \qquad
\nu = -\frac{\nu_1 \nu_2}{\nu_1-\nu_2}$$

Again, the quotient is of the Gaussian form but it is unnormalized. Interestingly, dividing by a Gaussian PDF is the same (up to constant factors) as multiplying times a Gaussian PDF with negative variance:

$$\frac{\phi(x-\mu_1,\nu_1)}{\phi(x-\mu_2,\nu_2)} \propto
\phi(x-\mu_1,\nu_1) \phi(x-\mu_2,-\nu_2)$$

## Multivariate

The formulae above are easily generalized to multivariate Gaussians. Assume that $\mathbf \mu_1,\mathbf \mu_1,\mathbf x \in \mathbb R^n$, $\mathbf \Sigma_1,\mathbf \Sigma_2 \in \mathbb R^{n \times n}$ and that $\mathbf \Sigma_1,\mathbf \Sigma_2$ are positive definite.

$$\phi(\mathbf x; \mathbf \Sigma) =
(2\pi \det \mathbf\Sigma)^{-1/2} 
\exp\left(-\frac{1}{2} \mathbf x^T \mathbf \Sigma^{-1} \mathbf x\right)$$

If $\mathbf x$ is a one-dimensional vector this reduces to the univariate PDF.
The product of two densities is again of the Gaussian form. As before, it is not normalized:

$$\phi(\mathbf x - \mathbf u_1, \mathbf \Sigma_1)
  \phi(\mathbf x - \mathbf u_1, \mathbf \Sigma_1) =
\phi(\mathbf x - \mathbf u, \mathbf \Sigma)
\phi(\mathbf u_1 - \mathbf u_2, \mathbf \Sigma_1 + \mathbf \Sigma_2)$$

where

$$\mathbf u = (\mathbf\Sigma_1^{-1} + \mathbf\Sigma_2^{-1})^{-1} (\Sigma_1^{-1} \mathbf u_1 + \Sigma_2^{-1} \mathbf u_2), \qquad
\mathbf \Sigma = (\mathbf \Sigma_1^{-1} + \mathbf \Sigma_2^{-1})^{-1}   $$

Since the univariate case is a special case of the multivariate case, we only give the proofs for the later.

**INCOMPLETE**

<!--TODO: Quotient of multivariate Gaussians. Proofs-->

## References

1. http://www.tina-vision.net/docs/memos/2003-003.pdf (product of $n$ PDFs)
2. http://www.gatsby.ucl.ac.uk/~turner/workshop/EPpapers/Minka%202007%20Quick%20EP%20reference.pdf (multivariate quotient for EP)
3. http://davmre.github.io/blog/statistics/2015/03/27/gaussian_quotient (multivariate quotient)
4. https://cs.nyu.edu/~roweis/notes/gaussid.pdf