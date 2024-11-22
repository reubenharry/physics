## Measure theory

The paper *Exact Bayesian Inference by Symbolic Disintegration* motivates measure theory nicely:


> The nineteenth-century mathematicians who wanted to know how big a set was were hoping for a definition with four properties

> 1. The size of an interval should be its length.
> 2. The size of a set should be invariant under translation.
> 3. The size of a union of disjoint sets should be the sum of the individual sizes.
> 4. Any subset of the real line should have a size.

> Not all four properties can be satisfied simultaneously. But if we limit our attention to measurable subsets of the real line, we can establish the first three properties. The measurable subsets are the smallest collection of sets of reals that contains all the intervals and is closed under complement, countable intersection, and countable union. The one and only function on the measurable sets that has the first three properties is the Lebesgue measure.

Measure theory lives in the category `Meas`. The objects are measurable spaces $(X, \Sigma_X)$, where $X$ is a set and $\Sigma_X$ is a collection of subsets of $X$ closed under compliment and finite union. Morphisms are measurable functions, which means a function $f : X \to Y$ such that for $U \in \Sigma_Y$, $f^{-1}(U) \in \Sigma_X$.

A probability measure on $X$ is a function $\mu : \Sigma_X \to [0,1]$ such that $\mu(X)=1$ and $\mu(\bigcup(S_i)) = \sum \mu(S_i)$, where $\bigcup$ means disjoint countable union. Probability measures can be pushed forward through a measurable function in the obvious way.

It is straightforward to define a Lebesgue integral - see the above paper, and this coincides with the Riemann integral wherever they are both defined. The Lebesgue integral is more general.

Measures (with some restrictions) are one-to-one with integrators, so we will abuse notation and write $\mu(f)$ to be the integral of $f$ with measure $\mu$. 

### Radon-Nikodym derivative

If $\mu$ and $\nu$ are measures on a measurable space $(X, \Sigma_X)$, and $\nu$ is absolutely continuous with respect to $\mu$, then there exists a measurable function $f : X \to \R$ such that $\nu(S) = \int_S f d\mu$ (i.e. $\mu(f)|_S$) for all $S \in \Sigma_X$. The converse also holds.

One conventionally defines the Radon-Nikodym $\frac{d\nu}{d\mu} := f$.

The main relevance of this is that a probability density function is such a Radon-Nikodym derivative.

