
## Gauge theories

[Fiber bundles](../maths/topology.md) are the objects on which gauge theories are defined, which are the field theories that describe modern physics, from electromagnetism (a $U(1)$ bundle), Yang-Mills (a g-bundle where g is a more general, non-Abelian, Lie group) to general relativity (a tangent bundle).

The idea is that the field which the action takes as argument is a connection on the bundle, known in physics as a gauge field, so that the connection (and in turn curvature of the space) is a dynamic variable. For example, in electromagnetism the curvature is the electromagnetic field strength, and the bundle has spacetime as the base manifold and fibers of $U(1)$. For general relativity, we work with a tangent bundle, for which the base manifold is spacetime, which has a canonical connection, and curvature is Riemamnian curvature.

## General

For a G-bundle $E$, i.e. a bundle with fibers isomorphic to some group $G$, a group action $g(x) = e^{ic(x)^aA_a}$, a physical field $\phi \in \Gamma(E)$, a gauge field $A$, a gauge transformation is the map:

$$
\phi(x) \mapsto g(x)\phi(x)
$$

$$
A_\mu(x) \mapsto g(x)A_\mu(x)g(x)^{-1} - i\partial_\mu g(x)g(x)^{-1}
$$

In particular, the covariant derivative operator $D_\mu\phi(x)^i = \partial_\mu\phi(x)^i -iA^a_\mu(x)(T_a)^i_j\phi^j(x)$ commutes with the action of $g$ (i.e. $D_\mu(g(x)\phi(x))= g(x)D_\mu\phi(x)$).

A gauge theory has a Lagrangian with a kinetic term defined by the covariant derivative so that the entire action is gauge transformation invariant.

### Quantum

The path integral formulation of quantum physics gives a setting where we have a distribution over connections. Typically, one is interested in gauge invariant quantities, such as the expectation of the trace of the [holonomy](../maths/differential_geometry.md) of the connection around a loop, known as a Wilson loop. That is, one ranges over all possible connections, and for each, calculates the linear map on the group induced by parallel transport (i.e. lifting the loop onto the fibers), and then takes the trace of that.

## Electromagnetism as a gauge theory

Choose $U(1)$ as our gauge group. Then from the above, we see that the transformation is $\phi(x)\mapsto e^{i\Lambda(x)}\phi(x)$


Clearly this does not preserve a standard kinetic term in the action:

$$
\phi(x) \mapsto e^{i\Lambda(x)}\phi(x)
\\ \Rightarrow \partial_\mu\phi(x) \mapsto e^{i\Lambda(x)}(\partial_\mu\phi(x) + i\partial_\mu\Lambda(x)\phi(x))
$$

Since the kinetic term is quadratic, we would want the result instead to be $e^{i\Lambda(x)}\partial_\mu\phi(x)$, which we can achieve by introducing a gauge field $A$ with $A_\mu(x) \mapsto A_\mu(x) + \partial_\mu\Lambda(x)$, and instead of $\partial_\mu$, having $D_\mu := \partial_\mu\phi(x)-iA_\mu(x)\phi(x)$.


## Differential forms for electromagnetism

We start with the Yang-Mills Lagrangian for a $U(1)$ bundle:

$$
\mathcal{L}(A) := \frac{1}{2}||dA||^2 + \langle A,  J \rangle
$$

where the norm is meant under the inner product on forms $\langle A, B \rangle = A \wedge \star B$. Then we obtain Maxwell's equations easily by least action:

$$
0 = \delta S[A] = \frac{1}{2}(d\delta A \wedge \star dA + dA \wedge \star d\delta A) + \delta A \wedge \star J
$$

which is, by symmetry of the inner product

$$
= d\delta A \wedge \star dA  + \delta A \wedge \star J
$$

and by a careful use of the product rule ($d(A\wedge B) = dA \wedge B + (-1)^{-1} A \wedge dB$ so that since  $0 = \int d (A \wedge B)$ by Stokes' theorem, $\int dA \wedge B = \int A \wedge dB$)

$$
= \delta A \wedge d\star dA + \delta A \wedge \star J
$$

$$
= \delta A \wedge (d\star dA + \star J)
$$

$$
\Rightarrow d\star dA = - \star J
$$


The electromagnetic field strength $F$ is a 2-form $F_{\mu\nu}dx^\mu \wedge dx^\nu$, which for example in flat spacetime has the matrix:

$$
\begin{bmatrix}
0 && E_x && E_y && E_z \\
-E_x && 0 && -B_z && B_y \\
-E_y && B_z && 0 && -B_x \\
-E_z && -B_y && B_x && 0 \\
\end{bmatrix}
$$

Or $E_i = F_{i0}, \quad B_i = 1/2\epsilon^{ijk} F_{jk}$

Maxwell's first two equations (traditionally $\nabla \cdot B = 0$ and $\partial_t B + \nabla\times E = 0$) follow from:

$$
dF = 0
$$

This is independent of not only coordinates, **but the metric too**.

As for the second two Maxwell's equations ($\nabla\cdot E = \rho$ and $\nabla\times B -\partial_t E = j$), we need a 1-form $J$, and then:

$$
d \star F = -\star J
$$

This *does* depend on the metric (via the Hodge star).

!!! Derivation

	As an example of the derivation, here are two terms, one from each side:

	$$
	\star(\rho dx^0) = \rho(dx^1 \wedge dx^2 \wedge dx^3)
	$$
	
	$$
	d\star F = d(\ldots + -E_zdx^1 \wedge dx^2 + \ldots) \\
	= \ldots - \frac{\partial E_z}{\partial x^3}dx^1 \wedge dx^2\wedge dx^3 + \ldots
	$$
	
	Similarly for other cases.

Note that $d(-\star J) = d(d \star F) = 0$, so $d\star J=0$, which is the continuity equation, since $d\star J$ is a top form on a spacetime manifold.

## Physical effect of Hodge star 

$\star F$ in components is like $F$, but with $E$ and $B$ components interchanged. So we have a *duality* between electricity and magnetism.

## Topology

In general, the space in which $F$ lives is $\ker(d_2)$.

If we express $F$ as $dA$, then $A$ need only be defined up to a closed form. So we are concerned with the space $\Omega_1 / im(d_0)$  (where $\Omega_i$ is the space of i-forms on the manifold).


As it turns out, the following sequence is exact:

$$
0 \to H^1 \to \Omega_1 / im(d_0) \to \ker(d_2) \to H^2 \to 0
$$

We see immediately that on a topologically trivial manifold (i.e. $\forall i, H^i = 0$), we have $\ker(d_2) = \Omega_1 / im(d_0)$.

## Chern-Simons theory

The form $CS = Tr(A\wedge dA + \frac{2}{3}A\wedge A\wedge A)$ has the property that $dCS = Tr(F\wedge F)$.

Then the action is:

$$
S_{CS}(A) = \frac{k}{4\pi}\int_\Sigma Tr(A\wedge dA + \frac{2}{3}A\wedge A\wedge A)
$$

For this to be well-defined in the QFT context, where the action appears in an exponential $e^{iS}$, we need $k$ to be an integer. This is seen by considering that if we regard $\Sigma$ as the boundary of a 4-manifold, then we have that, putting the same 4-manifold on either side of $\Sigma$: 

$$8\pi^2 = \int_Y Tr(F\wedge F) = \int_M Tr(F\wedge F) - \int'_M Tr(F\wedge F)$$

where the first equality follows from the integrality of the second Chern class over a cycle. This then fixes $k$ to be integer.

Note that the Chern-Simons Lagrangian is manifestly (read: as can be seen from the absence of a metric in the Lagrangian) metric independent. It is in fact a topological field theory, and can be expressed as a functor from a category of cobordisms (these are manifolds with boundaries on either end and are the morphisms) to a category of vector spaces.

## General relativity

A Riemannian manifold (a manifold with a metric) comes equipped with a natural connection, so the natural formulation of general relativity is to have an action that depends on the metric. This yields equations for the metric. 

## Elitzur's theorem

Elitzur's theorem states that in gauge theories (typically this is shown in the context of **lattice** gauge theories), the only operators that can have non-zero expectation values are invariant under local gauge transformations.

An important implication is that gauge symmetry cannot be spontaneously broken."
todo: incorp



## Lattice gauge theories

