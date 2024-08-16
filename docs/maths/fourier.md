$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Z}{\mathbb{Z}}$

$\newcommand{\RR}{\mathbb{R}}$

$\newcommand{\C}{\mathbb{C}}$

$\newcommand{\N}{\mathbb{N}}$

  

Notes largely from [this **excellent** book](https://see.stanford.edu/materials/lsoftaee261/book-fall-07.pdf) and these [more concise but extremely useful notes](https://jeremykun.com/2012/04/25/the-fourier-series/).

  

## The general idea

  

A function $\R \to \R$ is a continuous version of an array, in the sense that for an array $v$, we have a discrete index for elements, e.g. $v_i$ is a number for $i \in \mathbb{N}$, while for a function, we have a continuous "index", e.g. $f(x)$ is a number for $x \in \mathbb{R}$.

  

Accordingly, functions form an inner product space, in the sense that for $f, g : \mathbb{R} \to \mathbb{R}$, $(af + bg)(x) = af(x) + bg(x)$ and $\langle f | g \rangle = \int f(x)^*g(x)dx$ (an analogue of the dot product for finite dimensional spaces).

  

Many of the important concepts from [the theory of inner product spaces](linearalgebra.md) apply. In particular, there is a self-adjoint operator, the second derivative $\frac{d^2}{dx^2}$, and a notion of changing to an orthonormal eigenbasis (the complex exponential functions $x \to e^{ikx}$) with a unitary linear operator $\mathcal{F}$ known as the Fourier transform.

  

This already encapsulates the key facts about the Fourier transform: it is unitary (Plancherel's theorem), its inverse is its conjugate transpose (Fourier inversion theorem), and it expresses a function as a sum/integral of its eigenvectors, which are the complex exponentials (standard definition of the Fourier transform).

  

[^1: One has to be careful about which functions are allowed. This is the side of Fourier analysis that involves analysis.]

  

This plays out in various different settings:

  
  

- $\mathcal{F}:(\R/n\Z\to\C)\to(\Z\to\C)$ is called the Fourier Series: that is, a (sufficiently nice) periodic function can be expressed as an (infinite) sum of complex exponentials. In other words, $e^{ki\pi x}$, for $k\in\Z$, is a basis for periodic functions.

  

- $\mathcal{F}:(\R\to\C)\to(\R\to\C)$ is called the Fourier Transform: that is, a (sufficiently nice) function can be expressed as an integral of complex exponentials. This is like a continuous analog of a basis.

  

- $\mathcal{F}:(V^n\to\C)\to(V^n\to\C)$ is called the Discrete Fourier Transform: is it a linear operator between finite dimension vector spaces, so can be expressed as a matrix.

  

- $\mathcal{F}:(\Z\to\C)\to(\R\to\C)$ is called the Discrete Time Fourier Transform.

  

<!-- - Even and odd functions: Any function can be expressed as a sum of an even function (a function where $f(-x)=f(x)$) and an odd function (where $f(-x)=-f(x)$). -->

  

A range of properties hold, *mutatis mutandis*, across all the cases. I'll state them by default for the Fourier transform:

  
  

- The transform is unitary. E.g. $||f||^2 = ||\mathcal{F}f||^2$. Unpacking that: $\int |f(t)|^2 dt = \int |\mathcal{F}f(k)|^2dk$, which is (depending on the community, and the degree of generality), Parseval's theorem, Plancherel's theorem or Rayleigh's identity. Here we're using the inner product of the space we're in, to define the norm $||\cdot ||$. Unitary transforms are invertible with $U^{*}=U^{-1}$, so we now know the inverse of the Fourier transform too.

  

- Define shifts and squashes as:

  

$$ \tau_af(x) = f(x-a)$$

  

$$\sigma_af(x) = f(ax) $$

  

Then the shift and stretch theorems:

  

$$ \left(\mathcal{F}\circ\tau_a\right)f = e^{-2\pi i a s}\mathcal{F} f$$

  

$$\left(\mathcal{F}\circ \sigma_a\right) f = \frac{1}{|a|}(\sigma_{\frac{1}{a}}\mathcal{F}f) $$

  

As an *extremely* useful special case, we have, writing $f^- = \lambda x \to f(-x)$:

  

$$ \mathcal{F}f^- = \mathcal{F}^{-1}f = (\mathcal{F}f)^- $$

  

- Differentiation:

  

$$ \mathcal{F}f' = 2\pi i s \mathcal{F}f $$

  

- Convolution

  

Define the convolution operator $*$ by:

  

$$ (f*g)(t) = \int_{-\infty}^{\infty}f(t-x)g(x)dx $$

  

Convolution forms a commutative monoid on functions, which, to unpack that statement, means that it yields a new function, is commutative (as can be shown by a change of variables of the above equation), is associative (shown similarly), and has an identity.

  

Furthermore, the Fourier transform induces a monoid homomorphism from this monoid to the product monoid of functions (i.e. the binary operation maps $f$ and $g$ to $fg$, and the unit is $1$). In particular, $\mathcal{F}(f*g)(k) = \mathcal{F}f\mathcal{F}g$. This is very useful in engineering and physics applications.

  

Deconvolution is then solving $f*g=h$ for $f$ given $g,h$, which (ignore division by $0$ issues) is given by $\mathcal{F}^{-1}(\frac{\mathcal{Fh}}{Fg})$

  

## Concrete details

  

I now give more concrete details of the points outlined above.

  

## Self-adjoint operators

  
  
  

Linear operators on the function space include the operator $p=\frac{d}{dt}$ (which physically is the momentum operator in quantum mechanics). This takes a function and gives back a new function. It is linear. It is also skew-self-adjoint (using integration by parts, and noting that the first term in the integration by parts disappears assuming a boundary condition that all functions in the space vanish at $\pm\infty$):

  

$$ \langle \frac{d}{dt}(f),g \rangle = \int_{-\infty}^{\infty}\frac{df(t)}{dt}g(t)dt = - \int_{-\infty}^{\infty}f(t)\frac{dg(t)}{dt}dt = -\langle f,\frac{d}{dt}(g) \rangle $$

  

But if an operator $A$ is skew-self-adjoint, then $iA$ must be self-adjoint (since $\langle iA x, y \rangle = -\langle x, (iA)^{\dagger}y \rangle = \langle x, Ay \rangle$).

  

$p$ being self-adjoint means that (a version of) the spectral theorem gives that it has an orthonormal eigenbasis. The functions $e^{ikt}$ are one such eigenbasis, for $k$ real. (Note that I'm using "basis" to include this uncountable set of functions - the full story requires more finesse).

  

### Orthogonality of complex exponentials

  

Let $T(x)$ be the complex conjugate of $x$. Orthogonality is shown as follows:

  

For $n,m \in \Z, n\neq$m:

$$ \langle e^{it2\pi m},e^{ti2\pi n}\rangle = \int_0^1 e^{ti2\pi m}T(e^{ti2\pi n}) $$

$$ = \int_0^1 e^{ti2\pi m}(e^{-ti2\pi n}) = \int_0^1 e^{ti2\pi (m-n)}$$

$$ = \frac{1}{i2\pi(m-n)}e^{i2\pi (m-n)} - \frac{1}{i2\pi(m-n)}e^{0} = \frac{e^{i2\pi (m-n)}-1}{i2\pi(m-n)} = 0$$.

  
  

## Even and Odd functions

  

Consider the operator $M$, such that $M(f)(x)=f(-x)$. This is Hermitian (and unitary). Being the square root of $I$, $1$ and $-1$ are the eigenvalues. The corresponding eigenspaces are the even and odd functions.

  

<!-- Consider the function space of functions $\R\to\R$ that can be integrated (with a finite result). -->

  

To spell that out more concretely. An even function $f_e$ is such that $f_e(-x)=f_e(x)$. An odd function $f_o$ is such that $f_o(-x)=-f_o(x)$.

  

Even and odd functions form respective subspaces: linear combinations of even functions are even, and likewise for odd.

  

Every function $f$ can be written as $\frac{f(x)+f(-x)}{2} + \frac{f(x)-f(-x)}{2}$, where the first term is even and the second is odd. So the whole space is a direct sum of the two subspaces.

  

The two subspaces are orthogonal:

  

$$
\langle f_e, f_o \rangle = \int_{-\infty}^{\infty} f_e(x)f_o(x)dx = \int_{0}^{\infty} f_e(x)f_o(x)dx + \int_{-\infty}^{0} f_e(x)f_o(x)dx
$$

  

$$
= \int_{0}^{\infty} f_e(x)f_o(x)dx + \int_{0}^{\infty} f_e(-x)f_o(-x)dx
$$

  

$$
= \int_{0}^{\infty} f_e(x)f_o(x)dx - \int_{0}^{\infty} f_e(x)f_o(x)dx = 0
$$

  

The integral of an odd function over the whole real line is $0$.

  

## Fourier Series

  

Note how the Fourier series is the projection of a periodic function onto an orthonormal basis of complex exponentials:

  

$$f(t) = \sum_{-\infty}^{\infty}\langle f, e^{2\pi i n t} \rangle e^{2\pi i n t}$$

  

Here, the inner product is on $L^2([0,1])$, so:

  

$$ \langle f, e^{2\pi i n t} \rangle = \int_0^1 f(t)e^{-2\pi i n t}dt $$

  

Functions which are not smooth (either discontinuous or possessing discontinuous $n$th derivative) require infinite sum of complex exponential basis elements, since finite sum of smooth functions is smooth.

## Fourier Transform

  
  

$$
f(x) = \int_{-\infty}^{\infty}\mathcal{F}f(k)e^{2\pi ikx}dk
$$

  

What is $\mathcal{F}f$? It's the Fourier transform of $f$. Here is the definition:

  

$$
\mathcal{F}f(k) = \int_{-\infty}^{\infty}f(x)e^{-2\pi ikx}dx
$$

  

$\mathcal{F}f$ is the Fourier transform of $f$, giving the representation of $f$ in the eigenbasis of the 2nd derivative operator.

  

$f$ is the inverse Fourier transform of $\mathcal{F}f$. The Fourier transform of $f(x)$ projects $f$ onto a basis of complex exponentials and the inverse Fourier transform of $f$ builds up $F^{-1}f$ from a basis. This duality between projection and linear combination is at first a little weird looking.

### Dirac Delta

  

This is a continuous analog to the Kronecker delta $\delta_{ij}$, which is $0$ except when $i=j$ and is then $1$. We want the same but in a continuous space. In particular, we want that $\int_{-\infty}^{\infty}\delta(x)dx=1$ and $\langle \delta_{x_0},f\rangle = f(x_0)$. No function has these properties, and the Dirac $\delta$ is actually a functional (see below), but it's useful and elegant.

  

### Inverse of $\mathcal{F}^{-1}$:

  

$$ (\mathcal{F}^{-1}(\mathcal{F}(f)))(t) = \int_{-\infty}^{\infty}\mathcal{F}f(k)e^{2\pi itk}dk $$

  

$$ = \int_{-\infty}^{\infty}\left( \int_{-\infty}^{\infty}f(x)e^{-2\pi ikx}dx \right)e^{2\pi itk}dk $$

  

$$ = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \left(e^{-2\pi itk} e^{2\pi ikx}dk \right) f(x) dx $$

  

$$ = \int_{-\infty}^{\infty}\delta_t f(x) dx = f(t) $$

  

Key properties:

  

$$ \mathcal{F}\delta(t-a) = e^{-2\pi i k a} $$

  

Note the consequence, via the shift theorem that $\mathcal{F}\delta(t) = 1$

  

### Extending Fourier analysis to linear functionals

  

There's a story about the analysis part of Fourier analysis, namely finding classes of functions for which the Fourier transform is a well defined unitary isomorphism. One clear problem is that we want things like the $\delta$ function to be such that $\mathcal{F}\delta = 1$, but it has none of the properties of a function. Not to mention the Fourier transform of, e.g. a complex exponential.

  

In summary, one common approach is to first take some quite restricted set of well-behaved functions (such as the Schwartz functions, which are functions which decay very rapidly) and then obtain "distributions" (not to be confused with the probabilistic sense), which are linear functionals on this restricted set.

  

More concretely, call the restricted set $\mathcal{S}$, and for a function $f$ such that $\forall h\in \mathcal{S}: \langle f, h \rangle \leq \infty$, let $T_f(g) = \langle f, g \rangle$, where $T_f \in \mathcal{T}$, the set of distributions, i.e. linear functionals $\mathcal{S}\to \C$.

  

Because of the infinite setting we're in, $\lambda f \to T_f$ is not an isomorphism (I believe), which is to say that there will be operators $T \in \mathcal{T}$ which do not come from dualizing a function in $\mathcal{S}$. The prominent example being $\delta$.

  

$\delta$ and the like we just define directly by their action on $f\in \mathcal{S}$. For example, $\delta f = f(0)$.

  

It's then straightforward to define the Fourier transform on $\mathcal{T}$ in the usual way you define things on dual objects, namely $(\mathcal{F}T)f = T(\mathcal{F}f)$.

  

What we get is the *extremely useful* ability to take things which integrate to infinity on the real line, and take the Fourier transform of them. In poor notation, people write $\langle T, f \rangle$ to mean $Tf$.

  

Terminological note: when $\mathcal{S}$ is the Schwartz functions, $\mathcal{T}$ is called the set of *tempered distributions*.

  

### Delta function as a distribution

  

What is the identity of the convolution monoid? It's $\delta$, since, as we know, $\mathcal{F}\delta = 1$. Making this concrete, we have that $\delta * f = f$.

  

Actually, extending this to distributions is a little tricky, because you can't take a product of arbitrary distributions, so you have to just define convolution of a distribution with a function in $\mathcal{S}$.

  

People often write $\delta(x-b)$ to mean $\tau_b\delta$, although this is not well-typed. With that in mind, the two key properties of $\delta$:

  

$$ f(x)\delta(x − b) = f(b)\delta(x − b) $$

  

$$f * \delta(x − b) = f(x − b)$$

  

### Fourier transform as unitary operator

  

Unitarity of Fourier transform is known as Parseval's theorem:

  

Taking any (appropriate) functions $f, g$, and writing $g(x) = \int_{-\infty}^{\infty}\mathcal{F}g(k)e^{2\pi i k x}dk$, we have:

  
  

$$ \langle f,g\rangle = \int_{-\infty}^{\infty}f(x)\overline{g}(x)dx$$

  

$$ = \int_{-\infty}^{\infty}f(x)\overline{\left(\int_{-\infty}^{\infty}\mathcal{F}g(k)e^{2\pi i k x}dk\right)}dx$$

  

$$ = \int_{-\infty}^{\infty}f(x)\left(\int_{-\infty}^{\infty}\overline{\mathcal{F}g}(k)e^{-2\pi i k x}dk\right)dx$$

  

$$ = \int_{-\infty}^{\infty}\mathcal{F}f(k)\overline{\mathcal{F}g}(k)dk = \langle \mathcal{F}f,\mathcal{F}g\rangle $$

  

## Discrete Fourier Transform

  

The operates on discrete n-periodic signals, which can be represented by vectors of length n. As such, it is just a linear map, written in Einstein notation as:

  

$$ (\mathcal{F}v)_m = e^{\frac{-2\pi i mn}{N}}v_n $$

  

(Note that the sum starts with $n=0$)

  

## Discrete Time Fourier Transform

  

$$ \mathcal{F}v_m = \sum_{n=-\infty}^{\infty} e^{-2\pi i mn}v_n $$

  

## N-dimensional Fourier transform

  

The Fourier transform (as well as its relatives) is easily extended to functions of type $\R^n\to\C$ (yielding functions of the same type). The definition, for $f$ of this type:

  

$$ \mathcal{F}f(\xi) = \int_{\R^n}f(x)e^{-2\pi i \langle x, \xi \rangle}dx $$

  

In this setting, we have some new facts. First, an extension of the shift theorem which more or less follows from the change of variables formula:

  

$$ \mathcal{F}f(Ax) = \frac{1}{|\det A |}\mathcal{F}f(A^{-T}\xi) $$

  

Second, separability:

  

$$ f=\bigotimes_nf_n \Rightarrow \mathcal{F}f = \bigotimes_n(\mathcal{F}f)_n $$

  

Note that the tensor product, in this setting is just: $(f \otimes g)(x) = f(x)g(x)$, so nothing conceptually fancy here.

  

## Various important functions and facts

  

### $\Pi$ and sinc

  

$\Pi_p$ is the function which is $1$ for $|x|\lt p$ and $0$ otherwise.

  

Its Fourier transform is $sinc(x)=\frac{\sin (\pi x)}{\pi x}$

  

### Gaussian function

  

Gaussian function $f(x)=e^{-\pi x^2}$ is fixed point of $\mathcal{F}$:

  

Showing that is a nice application of ODEs, using the notation from [these notes](odes.md) where $F$ is *not* $\mathcal{F}f$:

  
  

Start by observing that for $F(x(t),t)=-2\pi tx(t)$, the corresponding solution to the ODE $\frac{d\phi(x_0)(t)}{dt} = F(\phi(x_0)(t))$ is $\phi_F(1,t)=e^{-\pi t^2}$.

  

The goal is to show that

  

$$\mathcal{F}(\phi_F(1))(t)= \langle e^{2i\pi ts},\phi_F(1)(s) \rangle = \int_{-\infty}^{\infty}e^{2i\pi ts}\phi_F(1)(s)ds=\phi_F(1,t)$$

  

This amounts to the claim that the Gaussian is an eigenfunction of the Fourier transform. We do so as follows:

  
  

$$
\frac{d}{dt}\mathcal{F}(\phi_F(1))(t) = \int_{-\infty}^{\infty}\frac{d}{dt}e^{2i\pi ts}\phi_F(1)(s)ds$$

$$
= \int_{-\infty}^{\infty}-2\pi sie^{2i\pi ts}\phi_F(1)(s)ds = \int_{-\infty}^{\infty}ie^{2i\pi ts}\frac{d}{ds}\phi_F(1)(s)ds$$


$$ = \int_{-\infty}^{\infty}-(\frac{d}{ds}ie^{2i\pi ts})\phi_F(1)(s)ds = -2\pi t\int_{-\infty}^{\infty}e^{2i\pi ts}\phi_F(1)(s)ds = -2\pi t \mathcal{F}(\phi_F(1))(t)
$$

  

## Dirac Comb

  

The Dirac comb ${III}_p(x) = \sum_{n=-\infty}^{\infty}\delta(x-kp)$, in particular, $III_1:=III$ is also a fixpoint of $\mathcal{F}$, since, using the Poisson summation formula

  

$$\langle \mathcal{F}III,\phi\rangle = \sum_{n=-\infty}^{\infty} \mathcal{F}\phi(k) = \sum_{n=-\infty}^{\infty} \phi(k) = \sum_{n=-\infty}^{\infty} \langle \delta_k,\phi\rangle = \langle \sum_{n=-\infty}^{\infty} \delta_k,\phi\rangle = \langle III,\phi \rangle $$

  

Convolving with the comb, i.e. applying the function $(III *)$, periodizes.

  

Multiplying by the comb samples.

  

### Poisson summation formula

  

$$ \sum_{n=-\infty}^{\infty}f(n) = \sum_{k=-\infty}^{\infty}\mathcal{F}f(k) $$

  

## Linear Systems

  

A linear system $L$ is just a linear operator on a function space, taking $v(t)$ to $Lv(t)=w(t)$. Note that like an operator on a finite dimensional space, it can be characterized by how it acts on (the equivalent of) a basis, namely, let $h(x,y)=L\delta(x-y)$. Then:

  

$$ Lv(x) = \int_{-\infty}^{\infty}h(x,y)v(y)dy $$

  

Here, $h$ is known as the impulse response and $H=\mathcal{F}h$ as the transfer function.

  

### LTI systems

  

$L$ is linear and time invariant (LTI) if $L\tau_b=\tau_bL$.

  

$L$ being LTI is equivalent to $L=(h*)$ for some $h$. In that case, complex exponentials $e^{2\pi i st}$ are the eigenvectors, with eigenvalues $\mathcal{F}h(s)$. To see that, note that for $w=L(e^{2\pi i vx})=h*e^{2\pi i vx}$:

  

$$ \mathcal{F}^{-1}\left(\mathcal{F}(w)(k)\right) = \mathcal{F}^{-1}\left(\mathcal{F}h(k)\mathcal{F}(e^{2\pi ivk})\right)$$

$$
= \mathcal{F}^{-1}\left(H(k)\delta(k-v)\right) = \mathcal{F}^{-1}\left(H(v)\delta(k-v)\right)= H(v)e^{2\pi ivx} $$

  
  

## Sampling theory

  

### Limited functions

  

A function $f$ is time-limited at $L$ if for any $|t|\gt L$, $f(t)=0$.

  

A function $f$ is band-limited at $B$ if for any $|k|\gt B$, $\mathcal{F}f(k)=0$.

  

A function cannot be both time and band limited. To see this, suppose $f$ is bandlimited at $B$. Then $\mathcal{F}f = \Pi_B\mathcal{F}f$, which means that $f = \mathcal{F}^{-1}\mathcal{F}f = p\cdot sinc(pt)*f(t)$.

  

### Orthonormal basis of band-limited functions

  

Generalizing the above point, and taking $f$ bandlimited:

  

$$ f(x) = \mathcal{F}^{-1}(\mathcal{F}f)(x) = \mathcal{F}^{-1}(\Pi(\mathcal{F}f * III)(x)) $$

  

$$ = \left(\mathcal{F}^{-1}\Pi * \mathcal{F}^{-1}\mathcal{F}f\cdot \mathcal{F}III\right)(x) = (sinc * IIIf)(x)$$

  

$$ = \sum_{k=-\infty}^{\infty} f(k)sinc(x-k)$$

  

Note that the first step uses the compact support of $\mathcal{F}f$ (i.e. the band-limitedness of $f$), because it says: periodize and then chopping back does nothing. The significance of the above result is that a *countably* infinite set of *samples* of $f$ suffice to represent the whole function. That is cool and moreover, important.

  

It's further clear that the sampling rate is the reciprocal of the bandwidth, i.e. twice the max frequency (in absolute value). This is the Nyquist frequency.

  

One can also obtain a similar result in which a *periodic* bandlimited function is the sum of a *finite* number of quotients of trig functions (it's a bit more fiddly).

  

# Solving differential equations

  

## PDEs

  

A good example of the usefulness of convolution is that the solution to the heat equation (on an infinite rod), i.e. $u_t = \frac{1}{2}u_{xx}$ is

  

$$g(x,t)*u(x,0)$$

  

where $g(x,t)=\frac{1}{\sqrt{2\pi t}}e^{\frac{-x^2}{2t}}$, i.e. the PDF of a Gaussian with $\mu=0,\sigma^2=t$. We should understand the above equation as saying: take the initial heat distribution $u(x,0)$, and convolve it with the kernel $g(x,t)$ to move forward to time $t$.