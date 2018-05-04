---
layout: post
title: Michaelis-Menten kinetics of reversible reactions
comments: true
---
# Michaelis-Menten kinetics of reversible reactions

Consider an enzyme $E$ catalyzing a reversible reaction, with the scheme

$$S+E\rightleftarrows SE \rightleftarrows P+E$$

Let $k_1,k_{-1}$ be the forward and backward rates of the reaction $S+E\rightleftarrows SE$, and let $k_2,k_{-2}$ be the forward and backward rates of the reaction $SE\rightleftarrows P+E$.

Then,

$$\begin{aligned}
\frac{\mathrm d [S]}{\mathrm d t} &= -k_1 [S][E] + k_{-1}[SE] \\
\frac{\mathrm d [P]}{\mathrm d t} &= -k_{-2}[P][E] + k_2 [SE] \\
\frac{\mathrm d [E]}{\mathrm d t} &= (k_2+k_{-1}) [SE] - k_1[S][E] - k_{-2}[P][E] \\
\frac{\mathrm d [SE]}{\mathrm d t} &= k_1 [S][E] + k_{-2}[P][E] - (k_{-1} + k_2) [SE]
\end{aligned}$$

Let $E_T = [E] + [SE]$ be the total enzyme mass. From the equations above we readily obtain mass conservation of total enzyme:

$$\frac{\mathrm d E_T}{\mathrm d t} = \frac{\mathrm d [E]}{\mathrm d t} + \frac{\mathrm d [SE]}{\mathrm d t} = 0$$

We now make a quasi-steady state assumption:

$$\begin{aligned}
\frac{\mathrm d[SE]}{\mathrm dt} = k_1[S][E] + k_{-2}[P][E] - (k_{-1}+k_2) [SE] = 0
\end{aligned}$$

Substituting $[SE]=E_T-[E]$, we obtain

$$[E] = \frac{k_{-1}+k_2}{k_1[S] + k_{-2}[P] + k_{-1} + k_2} E_T$$

it follows that

$$v = k_1 [S][E] - k_{-1} [SE]$$

The rate of product formation is given by:

$$v = \frac{\mathrm d[P]}{\mathrm dt} = k_2[SE] - k_{-2}[P][E]$$

Substituting the values of $[SE],[E]$ found above,

$$\begin{aligned}
v &= k_2 E_T - (k_2 + k_{-2}[P]) [E] \\
&= k_2 E_T - \frac{(k_{-1}+k_2)(k_2 + k_{-2}[P])}{k_1[S] + k_{-2}[P] + k_{-1} + k_2}E_T \\
&= \frac{k_1k_2[S]-k_{-1}k_{-2}[P]}{k_1[S]+k_{-2}[P]+k_{-1}+k_2}E_T
\end{aligned}$$

Defining $V_f = k_2E_T$, $V_b = k_{-1}E_T$, $K_S=(k_{-1}+k_2)/k_1$, $K_P=(k_{-1}+k_2)/k_{-1}$, we obtain:

$$v = \frac{V_f[S]/K_S - V_b[P]/K_P}{[S]/K_S+[P]/K_P}$$

## References

1. Klipp, Edda, Wolfram Liebermeister, Christoph Wierling, and Axel Kowald. Systems Biology: A Textbook. Second, Completely revised and enlarged edition. Weinheim: Wiley-VCH Verlag GmbH & Co. KGaA, 2016. §4.1.4.3
