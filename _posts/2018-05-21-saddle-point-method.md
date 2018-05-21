---
layout: post
title: The method of steepest descent for approximating integrals
comments: true
---

Let $f(z)$ be an analytic function of the complex variable $z = x + iy$, with $x,y$ real. We write

$$f(z) = u(x,y) + iv(x,y)$$

where $u(x,y),v(x,y)$ are real. Since $f$ is analytic, the Cauchy-Riemann equations are satisfied:

$$u_x = v_y,\qquad u_y = -v_x$$

Suppose that $z_0 = x_0 + iy_0$ is a zero of $f'(z)$. By the Cauchy-Riemann equations, $f'(z) = u_x - iu_y = v_y + iv_x$. Thus $f'(z_0)=0$ implies 

$$u_x(x_0,y_0) = u_y(x_0,y_0) = v_x(x_0,y_0) = v_y(x_0,y_0) = 0$$

_i.e._, $(x_0,y_0)$ is a critical point of both $u(x,y)$ and $v(x,y)$. The Cauchy-Riemann equations also imply that $u$ and $v$ are harmonic, _i.e._, that the Laplace equations are satisfied:

$$u_{xx} + u_{yy} = v_{xx} + v_{yy} = 0$$

By Green's theorem, the value of an harmonic function at an interior point of the domain, equals the average of the function on a sphere or circle surrounding this point. It follows that harmonic functions cannot have interior maxima or minima. Assuming that $z_0$ is an interior point, it follows that $(x_0,y_0)$ is a saddle-point of both $u(x,y)$ and $v(x,y)$. Naturally, we call $z_0$ a saddle-point of $f$ as well.

Suppose that $z_0$ is a saddle-point of order $m-1,m\ge2$, _i.e._,

$$f'(z_0) = f''(z_0) = \dots = f^{(m-1)}(z_0) = 0$$

but $f^{(m)}(z_0) = a\mathrm e^{i\varphi},a>0$ and $\varphi$ real. If $z = z_0 + r\mathrm e^{i\theta}$, with $r>0$ and $\theta$ real, then

$$f(z) = f(z_0) + \frac{r^m}{m!}a\mathrm e^{i(m\theta + \varphi)} + \dots$$

$$u(x,y) = u(x_0,y_0) + \frac{r^m}{m!}a \cos(m\theta + \varphi) + \dots$$

$$v(x,y) = v(x_0,y_0) + \frac{r^m}{m!}a \sin(m\theta + \varphi) + \dots$$

The directions of the level curves $u = \text{const}$ and $v = \text{const}$ as they emanate from the point $(x_0,y_0)$ are the solutions of the equations $\cos(m\theta+\varphi) = 0$ and $\sin(m\theta+\varphi) = 0$, respectively, _i.e._,

$$\theta = -\frac{\varphi}{m} + \left(k + \frac{1}{2}\right)\frac{\pi}{m},
\quad k = 0,1,\dots,2m-1
\qquad (u = \text{const})$$

and

$$\theta = -\frac{\varphi}{m} + \frac{k\pi}{m}
\quad k = 0,1,\dots,2m-1
\qquad (v = \text{const})$$

respectively. Therefore there are $2m$ directions from $z_0$ where $u$ remains constant, and $2m$ directions where $v$ remains constant.

On the other hand, the directions of steepest descent of $u$ and $v$ are the solutions of the equations $\cos(m\theta+\varphi)=-1$ and $\sin(m\theta+\varphi)=-1$, respectively, while the solutions of the equations $\cos(m\theta+\varphi)=1$ and $\sin(m\theta+\varphi)=1$ give the directions of steepest ascent. The directions of steepest descent and ascent of $u$ coincide with the directions where $v$ is constant, and the directions of steepest descent and ascent of $v$ coincide with the directions where $u$ is constant. Therefore, for both $u$ and $v$, there are $2m$ steepest directions from $z_0$, $m$ of which are of steepest ascent and the other $m$ of steepest descent.

Near $z_0$, the $2m$ level curves of $v=v(x,y)$ divide the surface $u(x,y)$ into $m$ valleys below the saddle-point, that alternate with $m$ hills above the saddle-point.

Now consider a contour integral of the form:

$$I(\lambda) = \int_C g(z) \mathrm e^{\lambda f(z)}\mathrm dz$$

where $f$ and $g$ are analytic functions and $\lambda$ is a large positive parameter.

Suppose that $C$ can be deformed into a steepest descent path $v(x,y)=\text{const}=\Im f(z_0)$. On this new path we have

$$f(z) = f(z_0) - \tau$$

On a steepest path, $\tau$ is real. On a steepest _descent_ path, $\tau$ is positive. Moreover, $\tau$ is decreasing on the path segment that goes towards $z_0$ (at which point $\tau = 0$), and increasing on the path segment that goes away from $z_0$.

Along this path, the integrand becomes

$$g(z)\mathrm e^{\lambda f(z_0) - \lambda\tau}$$

Assuming that the orginal integrand can be expressed as a sum of integrals along paths of steepest descent from saddle-points, it follows that the calculation of $I(\lambda)$ is reduced to finding the asymptotic behavior of integrals of the form

$$\mathrm e^{\lambda f(z_0)} \int_0^T g(z)\frac{\mathrm dz}{\mathrm d\tau}\mathrm e^{-\lambda\tau}\mathrm d\tau$$

where $T$ is a positive real number.

Assuming that $z_0$ is a saddle-point of order $m-1$, we have

$$f(z) = f(z_0)-(z-z_0)^mf_1(z) = f(z_0) - \sum_{n=0}^\infty a_n(z-z_0)^{n+m}$$

where $a_0\ne0$. Comparing with the above expressions, it follows that $\tau = (z-z_0)^mf_1(z)$.

For small $\tau$, we have a convergent expansion of the form (see Ref. 1 for details):

$$g(z)\frac{\mathrm dz}{\mathrm d\tau}=\sum_{s=0}^\infty c_s \tau^{(s+1)/m - 1}$$

By Watson's lemma, we obtain an asymptotic expansion of the above integral by integrating this series term by term:

$$\int_0^T g(z)\frac{\mathrm dz}{\mathrm d\tau}\mathrm e^{-\lambda\tau}\mathrm d\tau \sim \sum_{s=0}^\infty c_s \lambda^{-(s+1)/m}\left(\Gamma\left(\frac{s+1}{m}\right) - \Gamma\left(\frac{s+1}{m},T\lambda\right)\right)$$


# References

1. Wong, R. Asymptotic Approximations of Integrals, 2001.
2. [Watson's lemma on Wikipedia](https://en.wikipedia.org/wiki/Watson%27s_lemma)