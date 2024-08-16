$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$



## Cohomology

Homology is concerned with a countable set of functors $F_i$ mapping manifolds to simplicial complexes (roughly), and a natural transformation, namely the boundary operator $\delta_i : F_i \to F_{i-1}$.

Cohomology is concerned with a countable number of contravariant functors $F^i$, mapping manifolds to spaces of differential forms, and a natural transformation, namely the exterior derivative $d: F^{i-1} \to F^i$.

The duality between these comes from Stokes' theorem, which given the inner product between a simplicial complex $\gamma$ and a form $\omega$
 
$$ \langle \gamma, \omega \rangle := \int_\gamma \omega$$

says that $d$ and $\delta$ are adjoint:

$$
\langle \delta\gamma, \omega \rangle = \langle \gamma, d\omega \rangle
$$

A crucial consequence is that $d^2=0$.

## The cohomology groups

Dual to homology groups, we have for a given manifold $\mathcal{M}$:

$H^i = \ker(d^i)/im (d^{i-1})$ for $i \in \Z$, where $d^i$ is the exterior derivative acting on the i-forms.

Each $H^i$ gives information about the space. $H^0 = B^0/\{0\} = B^0$ is the vector space of functions that are constant on each connected component of $\mathcal{M}$, since a 0-form $df = \partial_\mu fdx^\mu$ is closed iff the partial derivatives all vanish. So it measures connectedness.

In a similar vein, $H^1$ measures *simple* connectedness, which means existence of all homotopies between paths. When a space is simply connected, closed forms can be integrated along any path to define their integral, so exact and closed forms coincide and $H^1 = \{0\}$.

**Characterizing exactness** 

For $S$ a *compact* (therefore boundaryless, i.e. $\partial S = 0$) manifold, and $\phi : S \to \mathcal{M}$, and $\omega = df$, we have:

$$
\int_S \phi^*\omega = \int_S \phi^*df = \int_S d(\phi^*f) = \int_{\partial S} \phi^*f = 0
$$

where we have invoked the naturality of $d$. 

