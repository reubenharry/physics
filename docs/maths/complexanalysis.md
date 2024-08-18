$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$


## Complex derivatives

For a real function $f : \RR^2\to\RR^2$, we have that the total derivative is a linear map $T(a)$ such that:

$$ ||f(a+h) - f(a) - T(a)(h)|| = o_{lim_{h\to0}}(||h||) $$

with $\frac{\partial f_i(a)}{\partial x_j}=T_{ij}$.

For $g : \C \to \C$, differentiability is defined the same way, with the crucial difference that $T$ is linear in the 1D vector space over a *complex* field (rather than linear in a 2D vector space over the real field), i.e. $T$ is always a operator corresponding to multiplication by a complex number. Multiplication by a complex number corresponds to the following matrix:

$$ \begin{bmatrix} x & y & \\\\ -y & x & \end{bmatrix} $$

(The reason for this is that a complex number corresponds to a stretch followed by a rotation; composition of this results in a matrix of the above form).

As a result,

$$ \frac{\partial f_1(a)}{\partial x_1} = \frac{\partial f_2(a)}{\partial x_2} $$

and

$$ \frac{\partial f_1(a)}{\partial x_2} = -\frac{\partial f_2(a)}{\partial x_1} $$

These are the Cauchy-Riemann equations, which the real and imaginary parts of your complex function need to satisfy in order to be complex-differentiable.

## Complex functions

For a function $f$, a pole is a zero of $\frac{1}{f}$. It is a point at which the function $f$ is not defined, or rather: $f$ is only defined on the complex point with the locations of the poles removed.

A holomorphic function is a complex function which is complex differentiable in a neighborhood of every point in its domain. Every holomorphic function is analytic: this is an essential difference to real analysis: roughly, if a complex function is once differentiable, it is infinitely differentiable.

A function whose only singularities are poles is meromorphic.

A pole of $f$ has order $m$ if there exists a polynomial $p$ of order $m$ such that $fp$ is holomorphic on the complex plane.

A branch cut is a line on which a function is not defined, rather than just an isolated point. For example, $\ln$ has a branch cut along the entire negative real axis.

## Contour integrals

These are line integrals of holomorphic functions around a loop in the complex plane. Cauchy's integral theorem (which follows from Stokes' theorem) states that these are invariant under homotopy of paths. 

A simple example of a contour integral:

$$ \oint_C z^kdz$$

Because the domain is the whole real plane (no punctures), we can assume WLOG that the path is the unit circle $\gamma$ around the origin. Then suppose $\theta$ is defined such that $z=e^{i\theta}$, so that $dz = d(e^{i\theta})= ie^{i\theta}d\theta$. Then

$$ \oint_{\gamma} (e^{i\theta})^kie^{i\theta}d\theta = i\oint_{\gamma} e^{i(k+1)\theta}d\theta$$

This evaluates to $2\pi i$ if $k=-1$ but otherwise to $0$. This fact lets us compute more complex contour integrals, like:

$$ \oint_{\gamma} \frac{e^z}{z^5}dz = \oint_{\gamma} \frac{\sum_{k=0}^{\infty}z^k}{z^5k!}dz = \oint_{\gamma} z^{-1}4!dz = \frac{\pi i}{12}    $$

In the above derivation, we expressed $e^z$ by its Taylor series, distributed the integral over the sum (which we can do because the function converges uniformly on the support of $\gamma$) and then noted that only the term $\frac{z^4}{z^54!}$ survives, by the above result.

In a very similar vein:

$$ 
\oint_{\gamma} \frac{f(z)}{z^2}dz = \oint_{\gamma} \frac{f(0)+f'(0)z+\ldots}{z^2}dz = 2\pi if'(0)  
$$

## Residue theorem

The homotopy invariance of integrals of holomorphic functions along paths in the complex plane implies that a path along a loop is $0$ as long as there is no obstruction to contracting the loop, i.e. no poles.

It turns out that, more generally, for a loop $\gamma$:

$$
\int _\gamma f(z)dz = 2\pi i \sum_{j} Res(f,\xi_j)
$$

where $\xi_j$ are the poles inside $\gamma$ and the residue $Res(f, \xi_j) := \frac{1}{(m-1)!}\frac{d^{m-1}}{dz^{m-1}}((z-\xi)^mf(z))|_{z=\xi}$

## Using complex analysis to solve real integrals

A useful approach is to take an integral on the real line, extend it to a loop going through the complex plane, and then using the residue theorem to solve it.  One then makes an argument that as the real part is extended in length, it dominates the complex integral, so that the solved contour integral and the original real integral agree in the limit of a range of integration $\lim_{a \to \infty}[-a,a]$. 

## Laurent series

This is the expansion of a complex function $f$ at a point $c$ as:

$$
f(z) = \sum^{n=\infty}_{n=-\infty} a_n (z-c)^n
$$

with 

$$
a_n = \frac{1}{2\pi i}\int_\gamma \frac{f(z)}{(x-c)^{n-1}}dz
$$

for a loop $\gamma$.

The principal part of a function $f$ is all the terms of the series with $n < 0$. 