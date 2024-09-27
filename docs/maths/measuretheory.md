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

It is straightforward to define an integral - see the above paper. Measures (with some restrictions) are one-to-one with integrators, so we will abuse notation and write $\mu(f)$ to be the integral of $f$ with measure $\mu$. 