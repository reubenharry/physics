
$\newcommand{\R}{\mathbb{R}}$

$\newcommand{\RR}{\mathbb{R}}$

$\newcommand{\C}{\mathbb{C}}$

$\newcommand{\N}{\mathbb{N}}$

  

For the application of medical imaging, you have the following setup. Assume you want to map out the internal density of some 2D region, i.e. find the density function $\mu(x) \in \R$, for $x\in \R$.

Characterize a line through the region by its angle and offset, respective $(\rho, phi)$, for $\rho \in \R$, $\phi \in [0,\pi]$.

We can also have a 2D line $\delta$ for $(\rho,\phi)$, written $\delta(\rho - x_1\cos\phi-x_2\sin\phi)$ which turns out, when integrated on $dx_1\wedge dx_2$ against a function $f$, to give the line integral of $f$ along that line.

You know that material density affects the speed of the rays you can send through the region, so we get the line integral for a given line, we have:

$$M(x_1,x_2) = \int_{\R^2} \mu(x_1,x_2)\delta(\rho - x_1\cos\phi-x_2\sin\phi)dx_1\wedge dx_2 $$

Set $\mathcal{R}\mu=M$. $\mathcal{R}$ is then called the Radon transform, and the goal of imaging is to find its inverse.

As it turns out, it's not hard to show that, for $\mathcal{F}$ the 2D Fourier transform, $\mathcal{F}\_{\rho}$ the 1D Fourier transform in $\rho$, and $(\xi_1,\xi_2) = (r\cos\theta, r\sin\theta)$:

$$ \mathcal{F}_{\rho}\mathcal{R}(\mu)(r,\phi) = \mathcal{F}\mu(\xi_1,\xi_2)$$

So we have a way of recovering $\mu$ from the mangling it undergoes by $\mathcal{R}$.