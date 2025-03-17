
Recall that a [group](groups.md) is a one-object [category](categories.md). If the space of maps from the object to itself is a manifold, we have what is known as a continuous group, or more commonly, a **Lie group**. The study of functors from groups (representation theory) is particularly interesting for Lie groups, since they have tangent spaces at their identity (a confluence of calculus (tangents) and group theory (identity) respectively).

This mathematics is both beautiful and central to physical applications.
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$
!!! Resources
	
	https://scholar.harvard.edu/files/noahmiller/files/representation-theory-quantum.pdf are a very clear condensation of Peter Woit's book on representation theory for physics.

A representation is a functor $\pi$ from a [group](groups.md) (viewed as a single object category) to a category of vector spaces, let's say HILB, the category of Hilbert spaces. If you unpack this, you see that the single object of the image category, namely the group $G$, must map to a particular vector space $V$, and that the morphisms, which are the group elements $g$ map to invertible linear operators $\pi(g)$, which in a given basis, can then be written as matrices.

An irreducible representation (onto a complex vector space) is one which has no non-trivial sub-representations. 

Since representations are functors, we have a notion of maps between them, namely natural transformations. (In this context, these are sometimes known as intertwining maps). Concretely, for representations $\rho_1 : G \to (V_1 \to V_1), \rho_2 : G \to (V_2 \to V_2)$, a natural transformation is a map $f : V_1 \to V_2$ such that $\forall g \in G: f \circ \rho_1(g) = \rho_2(g) \circ f$.

Schur's lemma tells us (statement and proof from nLab):

For irreducible representations $V, W$, and $\phi : V \to W$ a natural transformation, specified by a linear transform of the same name, $\phi=0$ or $\phi$ is iso.

The proof neatly exploits basic properties of linear algebra:

1. $\ker(S)$ is invariant under $\pi_1$ (Proof: Consider $x \in \ker S$. Then $0 = (\pi_2(f)\circ S)(x) = (S\circ \pi_1(f))(x) = S(\pi_1(f)(x))$, so $\pi_1(f)(x) \in \ker S$. $\square$)
2. $im(S)$ is invariant under $\pi_2$ (Consider $x \in im(S)$. Then $Sy = x$ so $\pi_2(f)(Sy) = \pi_2(f)x = S(\pi_2(f)y)$, so $\pi_2(f)x \in im(S)$)
3. Both are therefore subrepresentations of $\pi_1$ .
4. By the assumption of irreducibility of $\pi_1$, $\ker(S)$ is either empty or the full space.
5. If the latter, $S=0$. If the former, im(S) is the whole space by rank-nullity, so $S$ is an isomorphism.

Schur's lemma has the following corollaries:

- For $V = W$, $S = c\cdot I$. Proof:
  1. invoke fundamental theorem of algebra to obtain eigenvalue $c$ of $S$.
  2. $S - cI$ is a map between $\pi_1$ and $\pi_2$. *By Schur's lemma*, it must be either full or $0$.
  3. It can't be full because its kernel is non-empty (since $v_c$ is eigenvector of $S$).
  4. So it's 0, and then $S - cI = 0 \Rightarrow S = cI$

- the irreducible representations of an Abelian (aka commutative) group are 1D. Proof: Invoke corollary 1 for $S = \pi(g)$ for any $g$.

- suppose $\forall f \in G, [H, \pi(f)] = 0$. Then the irreducible representations making up $\pi$ are eigenspaces of $H$. (Proof omitted, but it's not hard)


<!-- - For irreducible unequal $\pi\_1, \pi\_2: (\forall g: S\circ \pi\_1(g) =  \pi\_2(g) \circ S) \Rightarrow S = 0 $ -->
<!-- For irreducible $\pi: (\forall g: S\circ \pi(g) =  \pi(g) \circ S) \Rightarrow S = \lambda I$ -->

<!-- Note that this amounts to saying that an endomorphism on a representation $\pi$ in the category of representations is, provided the underlying field is algebraically closed, a multiple of the identity. (To see this, observe that a morphism in the category of representations is a natural transformation, and a natural transformation between functors from a single object category is specified by a single object, call it $S$ with the commuting property above). -->

<!-- The proof is direct, as all categorical proofs are. We will simply show that $K := ker(S-\lambda I)$ is a non-empty subrepresentation. From that it follows that $K=V$, by the assumption of irreducibility, and from that, $S-\lambda I=0 \Rightarrow S = \lambda I$, as desired. We know that $K$ is non-empty by the fundamental theorem of algebra (we're working on a complex vector space), so it only remains to show it is a subrepresentation: -->

<!-- $$ v \in K \Rightarrow (S-\lambda I)v = 0 \Rightarrow (S-\lambda I)\pi(g)v = \pi(g)(S-\lambda I)v = \pi(g)0 = 0 $$ -->



The question we generally want to solve is: what are the irreducible representations of a given group. 

## Lie groups


The representations of Lie groups, which are groups whose set of elements form a manifold, are of particular interest.

Consider for example the sphere as $S$ and the rotations of the sphere as the functions on $S$. This Lie group is referred to as $SO(3)$. 

As with manifolds generally, it's occasionally useful to think in terms of coordinates. In this case, each element of $SO(3)$ can be described by a *special orthogonal matrix* (i.e. a 3x3 matrix with determinant 1), which explains the name of the group.

## Lie algebras

What is interesting about Lie groups is that calculus now comes into the picture. We can consider the tangent space of the sphere at its distinguished base point, the identity function (which in coordinates is the identity matrix). For present purposes, think of the tangent space as being populated by elements of the form $\frac{d}{dt}f(t)|_{t=0}$, where $f(t) : \R \to G$ and $f(0)=I$.

Then suppose $X \in g$. Then $1 + \frac{1}{N}X + O(\frac{1}{N^2})$ is in $G$ for large $N$, so

$$
\lim_{N \to \infty} (1 + \frac{1}{N}X + O(\frac{1}{N^2}))^N = $$

$$ \lim_{N \to \infty} (1 + \frac{1}{N}X)^N = e^X \in G
$$

So the exponential maps from the Lie algebra $so(3)$ to the Lie group $SO(3)$. But the map isn't surjective unless $G$ is connected (which is the topological property that there's a path between any two points on the manifold).

Next note that $xe^{tX}x^{-1} \in G$, so $\frac{d}{dt}(xe^{tX}x^{-1})|_{t=0} = xXx^{-1} \in g$.

But then $e^{tY}Xe^{e-tY} \in G$, so

$$
\frac{d}{dt}(e^{tY}Xe^{e-tY})|_{t=0} = YX - XY = [Y,X] \in g
$$

So the Lie algebra is closed under the commutator.

We say that the tangent space of a Lie group is a *Lie algebra*.
As it turns out, different Lie groups may have the same Lie algebra. In particular, the group of complex 2D rotations $SU(2)$ and the group of real 3D rotations $SO(3)$ are not isomorphic, but their Lie algebras are.

## SO(3)

We can deduce a lot about the Lie algebra of $SO(3)$. Its elements are linear operators $V^3 \to V^3$, which exponentiate to obtain elements of $SO(3)$.

Since

$$
0 = \frac{d}{dt}(1)|_{t=0} = \frac{d}{dt} e^{tX}e^{tX^T}|_{t=0}
$$

$$
= (e^{tX}Xe^{tX^T} + e^{tX}X^Te^{tX^T} )|_{t=0} = X + X^T
$$

we see that $X$ is skew-Hermitian.

Since $\det(e^X) = e^{Tr(X)}$, $X$ must be traceless.

Actually all skew-Hermitian traceless matrices are in the Lie algebra, so it's spanned by three operators conventionally called $L_i$.

By the linearity of the derivative, real linear combinations of $so(3)$ are in $so(3)$, so $L_i$ are basis elements of a real $V^3$ space. We say that rotations are generated by the exponential map applied to these *generators of rotation*.

### O(1,3)

This is the group of linear transforms that preserve the Minkowski metric, i.e. $||x|| = x^0x^0 - x^1x^1 - x^2x^2 - x^3x^3$. These are known as Lorentz transformations. It's a 6D manifold, and its Lie algebra is spanned by 6 operators, which are the generators of boosts and rotations. These are $K_i$ and $J_i$ respectively.

??? Derivation


    The defining property is $\Lambda^T\eta\Lambda = \eta$. We first observe that $-1 = \det(\Lambda) = \det(\Lambda^T\eta\Lambda) = \det(\Lambda)^2\det(\eta) = -\det(\Lambda)^2$, so that $\det(\Lambda) = \pm 1$.

    Further, $-1 = \eta_{00} = (\Lambda^T\eta\Lambda)_{00} = \eta_{\mu\nu}\Lambda^\mu_0\Lambda^\nu_0 = -\Lambda^0_0\Lambda^0_0 + \Lambda^i_0\Lambda^i_0$, so that $\Lambda^0_0 = \Lambda^0_0 = \pm \sqrt{1 + \Lambda^i_0\Lambda^i_0}$.

    This splits the manifold of Lorentz transformations into 4 parts, based on whether $\det{\Lambda}$ is positive and whether $\Lambda_0^0$ is positive. The sector containing the identity is the one where $\det{\Lambda} = 1$ and $\Lambda_0^0 > 0$.

    We now construct the Lie algebra of this sector.

    To first order $\Lambda^\mu_\rho = \delta^\mu_\rho + \epsilon K ^\mu_\rho$, so again to first order, $(\delta^\mu_\rho + \epsilon K ^\mu_\rho)\eta_{\mu\nu}(\delta^\nu_\sigma + \epsilon K^\nu_\sigma)  =  \eta_{\mu\nu} + \epsilon K^\rho_\mu\eta_{\rho\nu} + \epsilon \eta_{\mu\rho}K^\rho_\nu = \eta_{\mu\nu}$. This gives us the condition $K^T\eta + \eta K = 0$, or $\{K, \eta\}=0$. Considing a (1,1) subspace, this reduces to solving:

    $$
    \begin{bmatrix}
    0 && -1
    \\
    -1 && 0
    \end{bmatrix}
    \begin{bmatrix}
    a && b
    \\
    c && d
    \end{bmatrix}
    +
    \begin{bmatrix}
    a && b
    \\
    c && d
    \end{bmatrix}
    \begin{bmatrix}
    0 && -1
    \\
    -1 && 0
    \end{bmatrix}
    = 0
    $$

    which is solved by $K = \begin{bmatrix} 0 && i \\ i && 0 \end{bmatrix}$, or in the full space, by 

    $$
    \begin{bmatrix}
    0 && i && 0 && 0
    \\
    i && 0 && 0 && 0
    \\
    0 && 0 && 0 && 0
    \\
    0 && 0 && 0 && 0
    \end{bmatrix}
    $$

    We then exponentiate to obtain 

    $$
    \Lambda_1(\phi) = e^{i\phi K_1} = \sum_{n=0}^\infty \frac{i^n\phi^nk^n_1}{n!} = \cosh(\phi)I + i\sinh(\phi)k_1
    $$

    $$ = \begin{bmatrix}
    \cosh(\phi) && -\sinh(\phi)
    \\
    -\sinh(\phi) && \cosh(\phi)
    \end{bmatrix}
    $$

    In 4d spacetime, we have three of these, namely

    $$
    \begin{bmatrix}
    \cosh(\phi) && -\sinh(\phi) && 0 && 0
    \\
    -\sinh(\phi) && \cosh(\phi) && 0 && 0
    \\
    0 && 0 && 1 && 0
    \\
    0 && 0 && 0 && 1
    \end{bmatrix}
    $$

    and

    $$
    \begin{bmatrix}
    \cosh(\phi) && 0 && -\sinh(\phi) && 0
    \\
    0 && 1 && 0 && 0
    \\
    -\sinh(\phi) && 0 && \cosh(\phi) && 0
    \\
    0 && 0 && 0 && 1
    \end{bmatrix}
    $$

    and the obvious third one.

    The other 3 generators are the $SO(3)$ rotations.

It turns out we have, for $N^\pm = \frac{1}{2}(J_i \pm iK_i)$, that $[N^+, N^-] = 0$ and $[N^\pm, N^pm] = i\epsilon_{ijk}N^\pm_k$, so that the Lie algebra $so(1,3) \cong so(3) \oplus so(3) \cong su(2) \oplus su(2)$.

If we understand these Lie algebra's irreducible representations, then we understand the irreducible Lie group representations of the covering group of the Lorentz group.

#### Irreps of SO(1,3)

Since $so(1,3) \iso su(2) \oplus su(2)$, we can consider the irreps of $su(2)$, which are labelled by a single half-integer. The lowest weight irrep is therefore $(0,0)$, which means that $N^+$ and $N^-$ must be real numbers (1x1 matrices). To satisfy any non-trivial commutation relation, we must therefore have $N^\pm = 0$, so $e^{iN}=1$. So Lorentz transforms all map to the identity here.

## Adjoint representations

Since the Lie algebra of a group is itself a vector space, we can consider representations of the group on it. In particle, for $g$ in the group, and $X$ in the Lie algebra, let $\pi(g)(X) = gXg^{-1}$. This is the *adjoint representation*; think of it as a representation we get for free.

## The representations of $U(1)$

This group is commutative, so we know that its irreducible representations are 1D. Thus any arbitrary representation is a direct sum of 1D representations, so in matrix form is a diagonalizable matrix.

But we can say more.

We work from the parametrization of $U(1)$ as $e^{i\theta}$ and let $f(\theta) = \pi(e^{i\theta}$)

$$
\frac{d}{d\theta}f(\theta) = \lim_{\Delta\theta \mapsto 0} \frac{\pi(e^{i(\theta + \Delta\theta)}) - \pi(e^{i\theta})}{\Delta\theta}
$$

$$
= \lim_{\Delta\theta \mapsto 0} \frac{\pi(e^{i\theta}e^{\Delta\theta}) - \pi(e^{i\theta})}{\Delta\theta}
$$

$$
= \lim_{\Delta\theta \mapsto 0} \frac{\pi(e^{i\theta})\pi(e^{\Delta\theta}) - \pi(e^{i\theta})}{\Delta\theta}
$$

$$
= \pi(e^{i\theta})\lim_{\Delta\theta \mapsto 0} \frac{\pi(e^{\Delta\theta}) - 1}{\Delta\theta}
$$

$$
= f(\theta)\lim_{\Delta\theta \mapsto 0} \frac{f(\Delta\theta+0) - f(0))}{\Delta\theta}
$$

$$ = f(\theta) (\frac{df(\theta)}{d\theta}|_{\theta=0}) $$



so for $R = (\frac{d\pi(e^{i\theta})}{d\theta}|_{\theta=0})$, we have $f(\theta) = e^{R\theta} $

But given that $1 = f(1) = \pi(e^{i\theta}) = f(2\pi) = \pi(e^{i\theta 2\pi}) = e^{2\pi R}$

we conclude that $R = ik$, for $k \in \Z$.

So the irreducible representations of $U(1)$ are $\pi_k(e^{i\theta}) = e^{ik\theta}$ for $k\in \Z$.

So not only is any representation an eigendecomposable operator, but the spectrum takes values in $\Z$.


## The representations of $SU(2)$

There is exactly one irreducible representation of $SU(2)$ for each vector space $V^{(2n+1)}$ for $2n\in Z$. This can be established by a Dirac-style ladder operator argument.

## The representations of $SO(3)$

It turns out that the irreducible representations of $SO(3)$ (the *real* orthogonal matrices with $\det 1$) map to odd dimensional Hilbert spaces. 

$SO(3)$ and $SU(2)$ are not isomorphic, but $su(2)$ and $so(3)$ are. That isomorphism is given by $L_i \to \sigma_i$, since we know that $\sigma_i$ and $L_i$ are both 3D real vector spaces of operators that behave the same with respect to the commutator (i.e. the Lie bracket).

The map from $SU(2)$ to $SO(3)$ is surjective but two-to-one; the former is a double cover of the latter. An easy way to see this is to parametrize $SO(3)$ as $\theta \hat{n}$, where $\theta \in \pi$ is a rotation and $\hat{n}$ is a unit vector giving the axis of rotation. Then every point in the sphere is an element of $SO(3)$, and **antipodal points are identified**. Topologically, this means that $SO(3)$ has a non-contractible path.

Meanwhile $SU(2)$ elements live on the norm-1 surface of the 4D sphere, which is the 3D sphere, and has no non-contractible paths. So the map between them maps two separate antipodal points in $SU(2)$ to a single antipodal point in $SO(3)$. And since we know there is only one spin-1 representation of $SU(2)$, this map is it.




<!-- The Lie algebra for boosts has $K^T\eta = -\eta K$, and solving then exponentiating:

$$-1 = \det \eta = \det(\Lambda)\det(\eta)\det \Lambda \\
\Rightarrow \det \Lambda = \pm 1$$



$$
\begin{bmatrix}
\cosh(\theta) && -\sinh(\theta)
\\
-\sinh(\theta) && \cosh(\theta) 
\end{bmatrix}
$$

 -->

## Particles, categorically

<!-- Recall that a representation is a functor from a group (viewed as a one object category whose morphisms are the group elements) to a category of Hilbert spaces $\mathit{HILB}$. -->

TODO: give context

Given a representation $F_1 : G \to \mathit{HILB}$, states of a physical system are rays in $H := F_1(G)$.

The irreps of $F_1$ are interpreted physically as particles, whose states therefore live in subspaces of $H$, so that the whole system is determined by the state of all the particles.

The dynamics of the physical system is captured by a natural transformation $F_1 \mapsto F_2$. Spelled out, this is precisely an intertwining map between representations, i.e. a function $S$ such that $S \circ F_1(g) = F_2(g) \circ S$. In other words, the dynamics are symmetry preserving: you can change viewpoint before or after the dynamics, and you get the same result.

We now invoke Schur's lemma to great effect, in two ways.

First by a corollary of Schur's lemma, which tells us that if $U$ is a natural transformation $F_1 \to F_1$, then the irreps are exactly the eigenspaces of $U$. Since energy $H$ generates $U$, we can label particles by their energy.

Second, Schur's lemma tells us that the only natural transformations between irreps are $1$ (i.e. the identity) or $0$. This means that particles cannot simply change into other particles (without some other interaction).

This only applies to irreps, so there are certainly non-trivial natural transformations between tensor products of irreps, e.g. $H_1 \otimes H_2 \to H_3$. Feynman diagrams denote precisely these natural transformations.