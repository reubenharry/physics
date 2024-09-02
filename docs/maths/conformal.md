
!!! Resources

	https://www.amazon.com/Mathematical-Introduction-Conformal-Lecture-Physics/dp/3540686258

OR:

A function $f : \R^n \to \R^n$ is conformal if its Jacobian at any point is proportional to a rotation. 

For $n=2$, the [Cauchy-Riemann equations](complexanalysis.md) make clear that conformal transformation are precisely (invertible) complex analytic maps.

# or

A conformal transformation satisfies $g_{\mu\nu}(y(x)) = \Omega(x)g_{\mu\nu}(x)$, where $g$ on the left side is a function of the new coordinates $y$.
TODO: update ^^^

From just this constraint, we can derive a huge amount of information about the nature of conformal transformations, particularly in 2D.

For $y^\mu = x^\mu + \epsilon^\mu$, with $\epsilon$ small (i.e. considering only first order terms):

$$
g_{\mu\nu}(y) = \pd{x^\alpha}{y^\mu}\pd{x^\beta}{y^\nu} g_{\alpha\beta}(x) = (\pd{x^\alpha}{y^\mu}\pd{x^\beta}{y^\nu} - (\pd{\epsilon^\alpha}{y^\mu} + \pd{\epsilon^\beta}{y^\nu}))g_{\alpha\beta}(x)
$$

todo: what ^^^ ???

special conformal transformation as inversion, shift, inversion



