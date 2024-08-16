
IMPORT

TODO: put category of representations here

todo spontaneous symmetry breaking:

limℎ→0lim𝑁→∞⟨𝑚⟩≠0

# Applications to physics

Representations have an immediate application in physics, since they describe how a symmetry acts on a space. This is important in classical physics (a representation of the Galilean group on spacetime preserves rest frames), relativistic physics (the representation of the Poincare group on spacetime preserves rest frames), but also in quantum mechanics, which is the relevant topic here.


As a first example, a physical statement about a quantum mechanical system like "The Hamiltonian is rotationally symmetric" translates to the mathematical statement that $[H,R]=0$ for all $R \in SO(3)$.
<!-- The groups of interest to physics are often continuous groups, like $SO(3)$.  -->

And once we have this mathematical statement, we know from the corollaries of Schur's lemma above that the eigenspaces of $H$, which of course are all important for the physics of the system, are precisely the irreducible representations of $SO(3)$, which are extremely well studied mathematically.

Physically speaking, the elements of the Lie algebra of the group correspond to generators of the symmetry, so for example $L_i$ lives in $so(3)$ and generates rotations of space. This is where angular momentum and its strange behavior comes from.

As a second example, we showed above that the representations of $S(1)$ are eigendecomposable, so energy takes integer eigenvalues in systems where the Hamiltonian has this symmetry. This is a simple case of quantization.


## Spin

It is reasonable to expect that a quantum system should not have a preferred orientation with respect to measurement. Taking this as a postulate and thinking physically, that means that for any rotation of the observation apparatus in 3D space, there should be a corresponding action on the Hilbert space of the system which cancels out the change. That is to say that there must be a representation of $SO(3)$ on the system.

We can define a representation $\pi$ of $SU(2)$ given a representation of $\phi$ of $SO(3)$, given the standard map $f : SU(2) \to SO(3)$, namely by $\pi = \phi \circ f$. But recall that $f$ is not injective, so its inverse isn't a representation, and so we can't automatically get a representation of $SO(3)$ from one of $SU(2)$. *However*, we only care about a representation up to a phase change since as far as measurement is concerned, quantum states are rays, not vectors. In this case, we can invert $f$ (choosing one of the two points) and then construct $\xi \circ f^{-1}$, where $\xi$ is a representation of $SU(2)$. $\xi \circ f^{-1}$ is a representation up to phase. In summary, we get all the representations spin(n) of $SU(2)$, for $n$ half-integer. That's the origin of spin, which is the spin 1/2 representation (up to phase) of $SO(3)$: a spin 1/2 representation *can* exist, and indeed it appears in nature.

TODO: clarify

<!-- xAn relevant example of a Lie group for physics is the collection of rotations of 3D space (this group is called SO(3) ), or the set of all inertial frame preserving transformations in classical or relativistic physics.  -->

## Spherical harmonics

There is also a representation of $SO(3)$ onto $L^2(S^2)$ (the space of functions from the circle to itself that are normalizable). This is the direct sum of all the irreducible representations. That means that we can write

$$
f(\theta, \phi) = \sum_l\sum_m \alpha^m_lY^m_l
$$

where we have decomposed an arbitrary $f \in L^2(S^2)$ into a  sum of functions on the subspaces corresponding to the irreducible representations. These are the spherical harmonics.

## Vector operators

(I have pieced the following together, and think it's roughly correct, but doesn't come directly from any source I could find).

The adjoint representation is what we're invoking when we talk about vector operators, in the following sense. Given the Lie algebra $so(3)$, which can be regarded as the real vector space $V^3$, we get the adjoint representation of $SO(3)$ on $so(3)$ being $R^T(\delta)V_iR(\delta)$. Now since we have classified the representations of $SO(3)$, we know that this must be the spin $n$ representation for $n$ half integer. For $n=0$, $V_i$ is a scalar, for $n=1$, a vector (note the correspondence with the indexing in the Wigner Eckart theorem).

If $[L_i, V_j] = ie^{ijk}V_k$, then $R^T(\delta)V_iR(\delta) = i\delta n_j[L_j, V_i] = V_i + \delta(n \times V)^i$, for small $\delta$, which indicates this is the spin 1 representation.

TODO: clarify

## 

Transformations of reference frame must preserve metric. This is the Poincare group diag (1, -1,-1,-1).

i.e. 

$$
x^T\eta x = (\Lambda x)^T\eta (\Lambda x) \Rightarrow \eta = \Lambda^T\eta\Lambda
$$

General form:

$$
Λ = e^{iJ\cdot \theta + iK\cdot \Phi}
$$