---
layout: post
title: Exchangeable random variables
comments: true
---

The similarity factor between two distributions $P_\alpha,P_\beta$ is defined as (Ref. 1):

$$\mathrm{Sim} [P_\alpha,P_\beta] = \min_\lambda \sum_\sigma P_\alpha(\sigma)^{1-\lambda}P_\beta(\sigma)^\lambda$$

Suppose $P_\alpha,P_\beta$ are known, and $N$ points are drawn from one of them. Given the dataset of the $N$ points, we wish to infer whether they were drawn from $P_\alpha$ or $P_\beta$. The log-likelihood that the $N$ points came from $\gamma (=\alpha,\beta)$ is:

$$\sum_{i=1}^N \log P_\alpha(\sigma_i)$$

Assuming equal priors, we infer that the sequence comes from $P_\alpha$ or $P_\beta$ accodording which gives the maximum likelihood. The probability that the sequences come from $\alpha$ but we mistake them as coming from $\beta$ is given by:

$$P(\text{error}) = \sum_{\sigma_1,\dots,\sigma_N} \Theta\left(\sum_{i=1}^N \log\frac{P_\beta(\sigma_i)}{P_\alpha(\sigma_i)}\right)
\prod_{i=1}^N P_\alpha(\sigma_i)$$

where $\Theta(x)$ is Heaviside's Theta function.

Morea _et al._ claim  that $P(\text{error})$ has the following asyntotic behavior for large $N$,

$$\lim_{N\rightarrow\infty}\frac{1}{N}\log P\left(\text{error}\right)=\log\left[\min_{\lambda}\sum_{\sigma}P_{\alpha}\left(\sigma\right)^{1-\lambda}P_{\beta}\left(\sigma\right)^{\lambda}\right]$$

I tried to prove this below, but it is not 100% clear to me yet. This is what I think the proof looks like.

We use the following integral representation of Heaviside's Theta function,

$$\Theta\left(x\right)=\lim_{\epsilon\rightarrow0^{+}}\frac{1}{2\pi i}\int_{-\infty}^{\infty}\frac{\mathrm{e}^{ix\tau}}{-i\epsilon+\tau}\mathrm{d}\tau$$

Then

$$\begin{aligned}
\frac{1}{N}\log P(\text{error})&=\frac{1}{N}\log\sum_{\sigma_{1},\dots,\sigma_{N}}\Theta\left(\sum_{i=1}^{N}\log\frac{P_{\beta}(\sigma_{i})}{P_{\alpha}(\sigma_{i})}\right)\prod_{i=1}^{N}P_{\alpha}\left(\sigma_{i}\right)\\&=\frac{1}{N}\log\left\{ \frac{1}{2\pi i}\lim_{\epsilon\rightarrow0^{+}}\int_{-\infty}^{\infty}\frac{\exp\left[N\log\sum_{\sigma}P_{\alpha}\left(\sigma\right)^{1-i\tau}P_{\beta}\left(\sigma\right)^{i\tau}\right]}{-i\epsilon+\tau}\mathrm{d}\tau\right\}
\end{aligned}$$

By the Cauchy theorem, the integration over $\tau$ from $-\infty$ to $\infty$ can be transformed into an equivalent integral over a contour $C$, that goes from $-\infty$ to $0$, then to $i$, then $K+i$ for some large real $K$, the returns to the real axis at $K$ and finally goes to $\infty$. The saddle-point of the exponent occurs in the segment from $0$ to $i$. Then by the method of steepest descent, we obtain somthing close to the formula above, but not quite :(

# References

1. Mora, Thierry, Aleksandra M. Walczak, William Bialek, and Curtis G. Callan. “Maximum Entropy Models for Antibody Diversity.” Proceedings of the National Academy of Sciences 107, no. 12 (March 23, 2010): 5405–10. https://doi.org/10.1073/pnas.1001705107. (Supporting Information)

I have not found any other reference where this similarity measure is used.
