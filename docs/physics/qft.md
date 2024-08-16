QFT is simply quantum physics where the state of a system is a field. This raises a swarm of difficulties, but also a host of important and unifying physical ideas, between quantum physics, relativity and statistical mechanics. It is the language of the fundamental theories of physics (that are currently confirmed).

!!!Resources

	*Quantum Field Theory in a Nutshell* is a remarkably good textbook. A majority of the material here is a direct adaptation.
	
	Also good: https://nicf.net/articles/qft-free-fields/

## Notation

We follow the notational conventions of [relativity](relativity.md).
## Dimensions

Working in natural units, we have $\hbar = c = 1$. Since they are dimensionless, we get:

$$
(MLT)^0 = D[\hbar] = ML^2T^{-1} \Rightarrow M = T/L^2
$$

and 

$$
(MLT)^0 = D[c] = LT^{-1} \Rightarrow L = T
$$

so $T = L = M^{-1} = E^{-1}$

So large energy scale (UV) means small length scale, and small energy (IR) means large length.

## Basic derivations with path integrals

!!! Note

	Refer to the [quantum](quantum.md) notes for how path integrals work.

Suppose we have a Lagrangian:

$$
\mathcal{L}(a, b, c) = \frac{1}{2}(b^2 -m^2a^2 )+c\cdot a
$$
so that $\mathcal{L}(\phi(x),\partial \phi(x), J(x)) = \frac{1}{2}((\partial\phi)^2(x) -m^2\phi^2(x) )+J(x)\phi(x)$ is what we integrate over, i.e.:

$$
Z(J) := \langle q_F | U(T) | q_I \rangle = \int D\phi e^{i\int d^4x L(\phi(x), \partial \phi(x), J(x))} := e^{iW(J)}
$$
Here $D\phi$ indicates an integral ranging over all functions $\phi$ with boundaries $\phi(0)= q_I$ and $\phi(T)=q_F$. The integral in the exponent ranges over all space, and time $[0,T]$.

$J$ is understood as an excitation of the field $\phi$.

Basic properties of Gaussian integrals allow us to derive:

$$W(J) = -(1/2)\int\int d^4x d^4y J(x)D(x-y)J(y) 
$$
with 

$$
D(x) = \int \frac{d^4k}{(2\pi)^4}\frac{e^{ik\cdot (x-y})}{k^2-m^2+i\epsilon} = -i\int \frac{d^3k}{(2\pi)^32\omega_k}(e^{-i(\omega_kt-k\cdot x)}\theta(x^0) + e^{i(\omega_kt-k\cdot x)}\theta(-x^0) )
$$
TODO: compare to D in (1) of 1.4
### Force 

Suppose $J(\overrightarrow x, t) = \delta^3(x-x_1) + \delta^3(x-x_2):= J_1(x) + J_2(x)$.

Taking $|q_I\rangle=|q_F\rangle = |0\rangle$, so that $e^{-W(J)} = \langle 0 | e^{-iHT} |0 \rangle = e^{-iE_0T}$, where $E_0$ is the ground state energy of the system in question, a simple calculation shows that:

$$
E = -\int \frac{d^3k}{(2\pi)^3}\frac{e^{i\overrightarrow k(\overrightarrow x_1 - \overrightarrow x_2)}}{\overrightarrow k^2 + m^2} < 0
$$
??? Calculation

	Ignore the $J_iJ_i$ terms, and consider the $J_1J_2$ term. Plugging in the definition of $D$, we have:
	
	$$W(J) = -(1/2)\int\int d^4x d^4y \delta^3(x-x_1)D(x-y)\delta^3(x-x_2)
	$$
	
	$$
	= -(1/2)\int dx^0dy^0D(x_1-x_2) 
	$$
	
	
	$$
	= -(1/2)\int dx^0dy^0\int \frac{dk^0}{2\pi}e^{ik^0(x-y)^0}\int \frac{d^3k}{(2\pi)^3}\frac{e^{i\overrightarrow k \cdot (\overrightarrow x_1 - \overrightarrow x_2)}}{k^2-m^2+i\epsilon} 
	$$
	
	
	$$
	= (1/2)\int dx^0\int \frac{d^3k}{(2\pi)^3}\frac{e^{i\overrightarrow k \cdot (\overrightarrow x_1 - \overrightarrow x_2)}}{k^2+m^2+i\epsilon}  
	$$

	so that with $iW = -iE_0T$, recalling that $dx^0$ ranges over $[0,T]$, observing that $\overrightarrow k^2 + m^2$ is positive so that $\epsilon$ can be taken to $0$, and counting both the $J_1J_2$ and $J_2J_1$ terms, we obtain:

	$$
	E = -\int\frac{d^3k}{(2\pi)^3}\frac{e^{i\overrightarrow k \cdot (\overrightarrow x_1 - \overrightarrow x_2)}}{k^2+m^2}
	$$
	TODO: finish

Observing that with $J=0$, i.e. in the absence of imposed excitations, $E_0=0$, we see that the energy is lowered.


"Physically", we think of the two delta functions as sources/sinks of a particle, so that the exchange of a particle produces an attractive force. TODO: better understanding needed

TODO: statistical mechanics invoked?

## Free theory

##

Recalling 

$$
T^\nu_\mu = \frac{\partial \mathcal{L}}{\partial (\partial_\nu \phi)}\frac{\partial \phi}{\partial x_\mu} - \delta^\nu_\mu\mathcal{L}
$$

we calculate the energy density $T^0_0 = \frac{\partial \mathcal{L}}{\partial (\partial_0 \phi)}\frac{\partial \phi}{\partial x_0} - \mathcal{L} = \frac{1}{2}(\partial_0\phi\partial_0\phi+(\partial_i\phi\partial^i\phi)+m^2\phi^2)=\frac{1}{2}(\pi^2 + (\nabla\phi)^2 + m^2\phi^2)$

##

We start with a typical classical free theory, e.g. the scalar case:

$$
\mathcal{L}(\phi)(x) = \frac{1}{2}((\partial\phi)^2(x) -m^2\phi^2(x) )
$$

Quantizing the derivation of the Klein-Gordon equation and its solution from the notes on [mechanics](classical.md), we have:

$$
\phi(x) := \int d^3p \frac{1}{(2\pi)^3\sqrt{2\omega_p}}(\hat a_pe^{ip\cdot x} + \hat a^\dag_pe^{-ip\cdot x})
$$

(and similarly for $\pi(x)$), with:

$$[\hat\phi(x), \hat\pi(y)] = i\delta^3(x-y)$$

Omitting hats going forward, we have a 4-momentum operator:

$$
H = P^0 := \frac{1}{2}\int d^3 (\pi(x) + (\delta_x\phi)^2 + m^2\phi^2) \\
= \frac{1}{2}\int d^3p \frac{p^0}{(2\pi)^3}(a^\dag_pa_p + \frac{1}{2}(2\pi)^3\delta^3(0))
$$

so that:

$$
[H, a^\dag_p] = \omega_pa^\dag_p
$$

We then define $|0\rangle$ by the property $\forall p, a_p|0\rangle = 0$, which exists since $H$ is bounded below.

Eigenvectors of $P^\mu$ are generated by

$|p\rangle := \sqrt{2\omega_p}a^\dag_p|0\rangle $

which is an eigenstate of $H$ with $\omega_p$ and of $P$ with $p$. **We consider such states particles**, noting their energy momentum relationship.

Similarly in position space:

$$
|x\rangle := \phi(x)|0\rangle = (\int d^3p \frac{1}{(2\pi)^3\sqrt{2\omega_p}}(a_pe^{ip\cdot x} + a^\dag_pe^{-ip\cdot x}))|0\rangle \\
= \int d^3p \frac{1}{(2\pi)^32\omega_p}|p\rangle e^{-ip\cdot x}
$$

## Interacting theory

$$
H = H_0 + H_{int}
$$

and with $H_I := U_0(t)H_{int}U_0^\dag(t)$, we can propagate a system through time with:

$$S = e^{-i\int_{-\infty}^\infty dt'H_I(t')} \\
= \sum \frac{(-i)^n}{n!}T(\int dt_1 H_I(t_1)\ldots \int dt_n H_I(t_n))
$$

where $T(A(t_1)B(t_2)) = A(t_1)B(t_2)$ if $t_1 > t_2$, else $B(t_2)A(t_1)$.

## Green's function

The Green's function of an operator is characterized (up to some proportionality constant) by

$$
O\circ G = \delta
$$



## Divergences

$P^\mu$ contains a divergence due to $\delta^3(0)$ and another due to large $p^\mu$. Understanding that

$$\delta(p) = \lim_{L\to \infty}\int_Ldxe^{ipx}
$$

we see that $\delta(0)$ tends to an infinite volume integral $\int_{\R^3}d^3x$. So this is a problem of large length scale, and hence small energy. We call it an **infrared (IR) divergence**, and handle it by considering e.g. the *density* of ground state energy $\epsilon_0 := E_0/V$ rather than the full ground state energy $E_0 := \langle 0 | P^0|0\rangle$, which keeps track of the size of the space.

The second divergence in $P^0$ is from large $p$, so is a high energy divergence, hence **ultraviolet** (UV). Here the solution requires more subtlety.


## Particles, categorically

Recall that a representation is a functor from a group (viewed as a one object category whose morphisms are the group elements) to a category of Hilbert spaces $\mathit{HILB}$.

Given a representation $F_1 : G \to \mathit{HILB}$, states of a physical system are rays in $H := F_1(G)$.

The irreps of $F_1$ are interpreted physically as particles, whose states therefore live in subspaces of $H$, so that the whole system is determined by the state of all the particles.

The dynamics of the physical system is captured by a natural transformation $F_1 \mapsto F_2$. Spelled out, this is precisely an intertwining map between representations, i.e. a function $S$ such that $S \circ F_1(g) = F_2(g) \circ S$. In other words, the dynamics are symmetry preserving: you can change viewpoint before or after the dynamics, and you get the same result.

We now invoke Schur's lemma to great effect, in two ways.

First by a corollary of Schur's lemma, which tells us that if $U$ is a natural transformation $F_1 \to F_1$, then the irreps are exactly the eigenspaces of $U$. Since energy $H$ generates $U$, we can label particles by their energy.

Second, Schur's lemma tells us that the only natural transformations between irreps are $1$ (i.e. the identity) or $0$. This means that particles cannot simply change into other particles (without some other interaction).

This only applies to irreps, so there are certainly non-trivial natural transformations between tensor products of irreps, e.g. $H_1 \otimes H_2 \to H_3$. Feynman diagrams denote precisely these natural transformations.


## Fock space

Direct sum of Hilbert spaces $H, H\otimes H, H\otimes H \otimes H\ldots$

So $a_2^\dag a_1^\dag|0\rangle$ is a state that lives in $H \otimes H$.
HMM is that right?

$|2\rangle \in H \otimes H$.
    IS THAT RIGHT??

OR:
$|11\rangle \in H \otimes H$.