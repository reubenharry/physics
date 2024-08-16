# Condensed Matter Physics

This is the application of quantum statistical physics to matter. A typical example would be to study a metal, and understand its different phases, equilibrium properties, symmetries and so on, with the goal of predicting/engineering measurable properties like conductivity.

It is an appealing subject because it is phenomonologically rich (many unpredictable things happen in systems that are simple to describe), these phenomena are actually observed experimentally, and it involves nice physics (quantum field theories, topology, gauge theories, phase transitions, emergence).

## Example: Fermi gas

Given a system $H = \sum_k e_k\hat c^\dagger \hat c$, we will calculate the expected number of particles $N = -\frac{\partial F}{\partial \mu}$.

We work with the grand canonical ensemble, so $Tr(e^{-\beta (H + \mu N)})$, so that in path integral form, we have:

$$
\int D[\bar\psi,\psi]e^{-\int_0^\beta d\tau\sum_k\hat\psi_k(\tau)(\partial_\tau + \epsilon_k - \mu)\psi_k(\tau)}
$$

todo

??? Derivation 

todo 



or in frequency space:

$$
S = \beta \sum_{k,n}\bar \psi_{k,n}(-i\omega_n + \xi_k)\psi_{k,n}
$$

So that $Z = \prod_{k,n}\beta(-i\omega_n+\xi_k)$ and $N = T\sum_{k,n}\frac{1}{i\omega_n - \xi_n}$.

We then perform a contour integral to obtain $N = \sum_k\frac{1}{e^{\beta \xi_k}+1}$, as expected.

??? Derivation

todo

# Superconductors

Phenomenologically, superconductivity is a phase of some metals characterized by effects including the expulsion of magnetic fields from the interior of the metal in question (Meissner effect) and a non-decaying current.

Reasonably good models exist for *some* cases of superconductivity, but even there, it's fraught with difficulty.

## Models

To model it, one can hard-code an attractive force between the fermions of your model, in which case is it not hard to show that the electrons pair into *Cooper pairs*, and that the ground state has $B=0$ (part of the Meissner effect). These bosons Bose-condense in the ground state under the critical temperature. 

The *BCS* theory is a model of how a material might actually give rise to such an effective force. It is only correct for certain classes of superconductors, while for others, the mechanism is unknown. In BCS, the electrons interact with the phonons - in other situations, we often disregard this interaction because electrons are much lighter (Born-Oppenheimer approximation). 

This phonon-electron interaction gives rise to an effective low energy Hamiltonian with an attractive force on Fourier space fermions, 
    which regime
    ??

One can then take a mean field approximation of this Hamiltonian. 


# Questions!

13.27: getting the constants right

14.32

p267: all poles are simple poles

Exercises a) and b)

15.35

p281: the non-interacting regime: can we go through it please?

Legendre integral




in what sense is the mean field theory a weak coupling theory?

" This should not come as a big surprise, because we
already learned that the superconducting ground state is characterised
by a broken phase rotation symmetry, which implies fluctuations in the
particle number."

"It is straightforward to convince yourself that in order to turn a product
of two creation operators into a (diagonal) number operator, the transformation needs to contain a superpositions of particle and hole states"

"It is straightforward to verify that these equations imply the famous
expression for the BCS wave function:"

"These processes can only take place if
a Cooper pair sits next to an empty site. In that case, the electrons gain
a bit of kinetic energy in their virtual excursions, in direct analogy to
the kinetic energy gain that gave rise to antiferromagnetic interactions
in the repulsive-U Hubbard model."
    - but don't they want to lose energy?

    "The virtual hopping allowed the system to gain kinetic energy, and as a result neighbouring spins favoured an anti-aligned
    arrangement."

phase coherent vs spin coherent

is excited state over bcs 0 order param?

in what sense does the bcs wavefunction represent a bose-condensed state? surely many different k?

In the BCS model, the number of particles was not a conserved quantity.

As ∆ becomes non-zero, the vacuum energy in equation (12.12) is
lowered by the gain in interaction energy associated with the emerging, ordered, superconducting phase.

eq 11.15

n and phase conjugate

Where did the A come from in the tight binding model in the first place?
    Why wasn't it there before?

    in what sense can we argue about the value of A in the ground state?? is A part of the state of the system?

Why the gauge transform in 10.28? how does this help?

What does it mean for chemical potential to be integrated into the Hamiltonian??

The reasoning about photons: seems crazy


10.28

temperature assumed to be low compared to phonon energy (below 11.10)



Why are ordered states product states? Is that obvious?


exercise 7.9

why: +U \sum inˆi,↑nˆi,↓. as the hubbard approximation: i'm v confused

7.18

Why is this easy to see? If S_i measures the spin, then why wouldn't the Neel state be the most negative in energy?

The origin of the second term in 7.1

the exercise beneath 7.9

remind yourself about spin and its characterization

"Strongly correlated materials (for example, Mott insulators) simply cannot be understood in terms of single-electron states."
    we can't always diagonalize?


understanding fock space in the context of qho:
    doesn't seem like the additional particles change the dimension of the Hilbert space...

Why can the energy reference point be changeable? Doesn't this affect Goldstone's theorem?

------------------

# Summary of magnetism

Start with the tight binding model, including coulomb interaction

at large U, and at half filling (or slightly less), we have hubbard model, where we neglect the exchange term and the non-onsite direct term

we want to explore this in t-U space. 

we analyze this perturbatively, with t/U small:

    we attempt to find a unitary transformation e^iS such that the hamiltonian is block diagonal, with each block a different number of overlaps

    at second order, this gives the extended t-J model

        at half filling, mott insulator, where spin flips are the fundamental excitations

        at low energy and higher sectors, it is ferromagnetic

antiferromagnetic arises with direct term, because of the second order perturbation term being a hop
$$
H_{eff}^{(2)} = V + T_0 + \frac{1}{U}[T^+, T^-]
$$

ferromagmetic arises from exchange interaction being strong

we now consider ferromagnets and antiferromagnets on their own terms

for ferromagnets, groundstate is all parallel, and is the symmetry broken state is the groundstate

we can view the fourier transform of single flip states as the relevant eigevectors, so are the excitations, magnons, which are a goldstone boson, although with a quadratic dispersion relation


the corresponding analysis of the antiferromagnet is a fucking nightmare:

    we take opposite axes for the two sublattices, perform the primakoff-holstein transformation, fourier transform, and then bogoliubov

antiferromagnets can only occur on certain topologies, those which are separable into two distinct sublattices where neighbours of 1 are only neighbours of the other

    ground state is NOT neel state, but rather superposition of all neel states, and spontaneous symmetry breaking is exhibited

we now consider the weak coupling limit (meaning coulomb weak compared to kinetic energy). to do so, we appeal to mean-field theory, and take the state of each site to be independent, with an effective mean field.
































# Revision

filling of bands: when it conducts and when it insulates

inspect cheatsheet you made



## Condensed matter

### Bloch's Theorem

The idea is that given a periodic potential, which is to say a potential symmetric under the representation of a cyclic group of translations, there is a simultaneous basis of $H$ and translations $T_a$, of the form:

$$
\psi_{nk}(r) = e^{ik\cdot r}u(r)
$$

with $u$ periodic. This is obviously an eigenstate of $T_a$; the substantive claim is that there is an eigenbasis of $H$ of this form. These are **not** eigenstates of momentum.

**Physical consequences**

When modeling electrons in a solid, the ions tend to be much more massive than the electrons, so treating them as static, we model them as a periodic potential, and model the whole lattice as an n-torus too.

**Bands** In $\psi_{nk}$, the $n$ index is discrete and corresponds to the *band* while $k$ varies continuously (in the thermodynamic limit) across the Brilloun zone.

We view $\psi_{nk}$ as the wavefunction of an electron. $\hbar k$ is the *crystal momentum*, which is conversed only modulo a lattice vector.

**Proof outline of Bloch's theorem**

A cyclic group on a Hilbert space of functions acts like:

$$
T_a\psi(x) = \psi(x+a)
$$


A cyclic group is Abelian and therefore the irreps are 1D, with:

$$
T_a\phi(x) = 1^{\frac{1}{N}}\phi(x) = e^{i2\pi n/ N}\phi(x)
$$

where $N$ is the order of the group (i.e. the number of translations to get back to where you started.) and $n \in \Z$ up to $N$.

Assuming they commute with the Hamiltonian, the irreps are the eigenspaces of H, so it follows that for eigenfunctions of $H$:

$$
\phi(x+a) = e^{i2\pi n/N}\phi(x)
$$

Since the norm of $\phi$ is therefore invariant under translation, it must have the form:

$$
\phi(x) = e^{iB(x)}u(x)
$$

for $u(x)=u(x+a)$ and $B(x)\in \R$.


### Symmetry

When we talk about symmetries in the quantum context, we usually mean projective representations, in the sense the $\pi(g)|\phi\rangle = e^{ik}|\phi\rangle$ for $k \in \R$.

This is because we are interested in the Hilbert space only up to expectation values $|\langle \pi(g^{-1})\phi |A\pi(g)|\phi\rangle$, and the $e^{ik}$ cancels.

Recalling that we care about expectations, we can also look at the action of $g$ on operators, since $|\langle \pi(g^{-1})\phi |A\pi(g)|\phi\rangle = \langle \phi | B | \phi \rangle$ for $B = \pi(g^{-1})A\pi(g)$, so $B=A$, or equivalently $[A, \pi(g)] = 0, \forall g\in G$ is the condition of symmetry.

### Noether's theorem

From the perspective of a field Lagrangian, a transformation which adds $\delta_s\phi_a(x)$ is a symmetry of the action if $\delta_sL = \delta_\nu K^
\nu$, for $\nu$ a 4-vector index.

Noether's theorem says that such a symmetry implies a current $j^\nu$ with $\partial_\nu j^\nu = 0$. The upshot is that we obtain a global constant by integrating:

$$
0 = \int \partial_\nu j^\nu(x,t)dx = \int \partial_t j^0(x,t)dx + \int \partial_i j^i(x,t)dx
$$

$$
= \partial_\nu\int j^\nu(x,t)dx  + \int j^i(x,t)dS_i
$$

$$
:= Q(t)
$$

with the $\int j^i(x,t)dS_i$ term obtained by Stokes' theorem and typically vanishing at infinity.

**Proof**

A field that satisfies the equations of motion has (Euler-Lagrange equation):

$$
\frac{\partial L}{\partial \phi} - \partial_\nu \frac{\partial L}{\partial(\partial_\nu\phi)} = 0
$$

Therefore, a field which satisfies both a symmetry and the equation of motions has:

$$
\delta_sL = \frac{\partial\mathcal{L}}{\partial \phi}\delta_s\phi + \frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)}\delta_s(\partial_\nu \phi)
$$

$$
= \frac{\partial\mathcal{L}}{\partial \phi}\delta_s\phi + \frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)}\partial_\nu (\delta_s \phi)
$$

$$
= \frac{\partial\mathcal{L}}{\partial \phi}\delta_s\phi + \partial_\nu(\frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)} (\delta_s \phi)) - \partial_\nu\frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)} (\delta_s \phi)
$$

$$
= (\frac{\partial\mathcal{L}}{\partial \phi} - \partial_\nu\frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)} )\delta_s\phi + \partial_\nu(\frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)}\delta_s \phi)
$$

$$
=  \partial_\nu(\frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)}\delta_s \phi)
$$

So that we have for $j^\nu = \frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)}\delta_s \phi - K^\nu$:

$$\partial_\nu j^\nu = \partial_\nu(\frac{\partial\mathcal{L}}{\partial (\partial_\nu\phi)}\delta_s \phi) - \partial_\nu K^\nu = \delta_s L - \delta_s L = 0 \\ \square
$$

$j$ is the Noether current.

### Noether in a quantum setting

This is consistent with a quantum setting, as follows:



## Conservation

For unitary $U$ with $U = e^{iQ}$, and $[U,H] = 0$, we have $[Q,e^{iH}] = 0$, so that by the Ehrenfest theorem, the expectation of $Q$, an observable, is time-constant.

## Symmetry breaking

From notes:

> "Spontaneous symmetry breaking (SSB) is the phenomenon in which a stable state of a system (for example the ground state or a thermal equilibrium state) is not symmetric under a symmetry of its Hamiltonian, Lagrangian, or action."

Note that this implicitly invokes statistical mechanics, in the definition of "stable".

For a symmetry $U$ that commutes with $H$, and a non-symmetric state $|\phi\rangle$, we have $U|\phi\rangle \neq |\phi\rangle$ and $\langle H \rangle_{|\phi\rangle} = \langle U^{-1}HU \rangle_{|\phi\rangle} = \langle H \rangle_{U|\phi\rangle}$, so we have a collection of non-symmetric states that share an energy.

We can in general define an *order parameter* $\mathcal{O}$ with eigenvectors being these non-symmetric states, distinct non-zero eigenvalues, and non-zero expectation for symmetric states. For instance, in the case of a crystal, the collective position operator would do as $\mathcal{O}$.

In general, $\mathcal{O}$ won't commute with $H$, so eigenstates of $\mathcal{O}$ won't be eigenstates of $H$. 

Recalling that the equilibrium distribution is a probability distribution over energy eigenstates, this means that in a broken-symmetry state, the system is not in equilibrium.

However, at the thermodynamic limit ($N \to \infty$, $V \to \infty$), things work out as follows.

TODO


## Tensor product orthogonality in crystal

Letting two states be $\otimes_i |\phi_i\rangle$ and $\otimes_i |\psi_i\rangle$, we have $\langle\otimes_i  \phi_i| \otimes_i \psi_i\rangle = \Pi_i \langle \phi_i | \psi_i \rangle$ by definition of the inner product for tensor product spaces. 

But assuming that these states are invariant under a shifting operator, we have $\phi_i = \phi_j$, $\Pi_i \langle \phi_i | \psi_i \rangle = \langle \phi_0 | \psi_0 \rangle^N$, which is clearly either $0$ or $1$ in the limit of large $N$.

## Quotients

Suppose the symmetry of the system is a (projective) representation of a group $G$ on the Hilbert space (i.e. $\pi(g)|\phi\rangle = e^{ik}|\phi\rangle)$ for some $k \in \R$. 

Symmetry breaking states may still have a symmetry described by a subgroup $H \subset G$. For example, the group of continuous shifts in 1D has a discrete shift subgroup that preserves the crystalline states (which are the symmetry breaking states).

If $|\phi\rangle$ is a symmetry-breaking state, then for $g_1, g_2 \in G$,  $g_1|\phi\rangle = g_2|\phi\rangle$ if $g_1 = g_2h$ for $h \in H$. So we consider the quotient group $G/H$; its elements index the distinct broken symmetry states.

> "For continuous groups, the classification of broken symmetry states can also be expressed
in terms of the generators of the continuous symmetry transformations, defined in Eq. (1.5).
In this context, generators Q of which the broken-symmetry state under consideration is an
eigenstate, are called unbroken generators or unbroken Noether charges, and any finite transformation generated by Q is also unbroken. Conversely, generators that do not leave the state
invariant are called broken. The continuous symmetry group may be broken down to either a
continuous or a discrete subgroup, and even to the trivial group."

## Debye and density of states

We often use the measure $d\omega g(\omega)$, with $g(\omega) = 3(\frac{L}{2\pi})^3\frac{4\pi\omega^2}{v_s^3}$ to count normal modes.

For instance, the Debye approximation has $E = \int_0^{\infty} d\omega g(\omega) \langle H(\omega) \rangle$ 

which, expanding, becomes:

$$
E = \int_0^{\infty}d\omega g(\omega) \hbar\omega (\langle n(\omega) \rangle + \frac{1}{2}) = \int_0^{\infty}d\omega g(\omega)  (\frac{\hbar\omega}{e^{\frac{\hbar\omega}{kT}} + 1} + \frac{\hbar\omega}{2})
$$

## BKT

$$
H = \int (\nabla\phi)^2
$$

$$
\int \nabla\phi dl = 2\pi n
$$

so that $\nabla\phi = \frac{n}{r}$ (with $r$ as a polar coordinate).

Then 

$$
E \propto \log \frac{L}{\xi}
$$

where $L$ is the size of the whole lattice and $\xi$ is the lattice spacing (so the upper and lower bounds of the integral).

$$
S = \log (\frac{L}{\xi})^{2}
$$

cf. solution of poisson equation in 2D vs 3D

At low temperature, vortices are bound in pairs, while at high temperature, they are free. There's an analogy to insulating and conducting phases of a metal.

## Topology

"The topologically different paths of N particles in space-time form
a group structure (the fundamental group of the configuration
space) which is the permutation group SN in 3+1 dimensions, but
is the braid group BN in 2+1 dimensions."

"For further reading on category theory, a classic reference the classic
reference is MacLane [1971], which was written long before the idea of
topological quantum field theory was around. A beautiful masters thesis
by Bartlett [2005] discusses TQFTs from the category perspective"