---
layout: post
title: Gauge transformations in the Potts model
comments: true
---

Consider sequences $\underline s = (s_1,s_2,\dots,s_L)$ of length $L$, where each of the $s_i$ is one of $1, 2, \dots, A$. Here $L,A$ are positive integers. Thus there are a total of $A^L$ sequences.

We define the *energy* of a sequence as:

$$H(\underline s|J,h) = -\sum_{ij}J_{ij}(s_i,s_j) - \sum_i h_i(s_i)$$

where $h_i(a)$ are called the *external fields* and $J_{ij}(a,b)$ the *coupling fields*.

The fields $J,h$ and $J',h'$ are *equivalent* if there exists a constant number $C$ such that $H(\underline s|J,h) = H(\underline s|J',h') + C$ for all sequences $\underline s$. This relation satisfies all the properties of an equivalence relation.

A transformation of the fields from $J,h$ to $J',h'$ is a *gauge transformation* if $J,h$ is equivalent to $J',h'$. The following transformations are gauge transformations.

**Symmetrization.** This gauge transformation obtains symmetric coupling fields, $J_{ij}'(a,b) = J_{ji}'(b,a)$.

$$J_{ij}'(a,b) = \frac{1}{2}\left(J_{ij}(a,b) + J_{ji}(b,a)\right)$$
$$h_i'(a) = h_i(a)$$

Note that $J'$ becomes symmetric: $J_{ij}'(a,b) = J_{ji}(b,a)$.

**Removal of self-couplings.** This gauge transformation obtains coupling fields with diagonal terms set to zero, $J_{ii}'(a,b) = 0$.

$$J_{ij}'(a,b) = \begin{cases}
    J_{ij}\left(a,b\right) & i\ne j\\
    0 & i=j
\end{cases}$$
$$h_i'(a) = h_i(a) + J_{ii}(a)$$

**Removal of average couplings.** This gauge transformation removes the average coupling between sites, making $\sum_y J_{ij}'(a,y)=\sum_y J_{ij}'(a,y)=0$ for all $a,b$.

$$J_{ij}'(a,b) = J_{ij}(a,b)-\frac{1}{A}\sum_x J_{ij}(x,b) - \frac{1}{A}\sum_y J_{ij}(a,y) + \frac{1}{A^2}\sum_{x,y}J_{ij}(x,y)$$
$$h_i'(a) = h_i(a) + \frac{1}{A}\sum_{i,j}\left(\sum_x J_{ji}(x,s_i) + \sum_y J_{ij}(s_i,y)\right)$$

**Removal of average external fields.** This transformation removes the average external field on each site, making $\sum_x h_i'(x) = 0$ for all $i$.

$$J_{ij}'(a,b) = J_{ij}(a,b)$$
$$h_i'(a) = h_i(a) - \frac{1}{A}\sum_x h_i(x)$$

## Zero-sum gauge

Take an arbitrary set of fields $J,h$ and apply the following gauge transformations, in this order:

1. Symmetrization
2. Removal of self-couplings.
3. Removal of average couplings.
4. Removal of average external fields.

The resulting set of fields, $J',h'$, are said to be in the zero-sum gauge. They satisfy:

- $J_{ij}(a,b) = J_{ji}(b,a)$ for all $i,j,a,b$;

- $J_{ii}(a,b)=0$ for all $i,a,b$;

- $\sum_y J_{ij}(a,y) = \sum_y J_{ij}(a,y)=0$ for all a,b,i,j.

- $\sum_a h_i(a)=0$ for all $a$.
