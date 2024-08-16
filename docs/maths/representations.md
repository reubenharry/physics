
Recall that a [group](groups.md) is a one-object [category](categories.md). If the set of maps from the object to itself is 
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

It turns out that the irreducible representations of $SO(3)$ (the *real* orthogonal matrices with $\det 1$) are the functors to odd dimensional Hilbert spaces. 

TODO: check/fix above



$SO(3)$ and $SU(2)$ are not isomorphic, but $su(2)$ and $so(3)$ are. That isomorphism is given by $L_i \to \sigma_i$, since we know that $\sigma_i$ and $L_i$ are both 3D real vector spaces of operators that behave the same with respect to the commutator (i.e. the Lie bracket).

The map from $SU(2)$ to $SO(3)$ is surjective but two-to-one. An easy way to see this is to parametrize $SO(3)$ as $\theta \hat{n}$, where $\theta \in \pi$ is a rotation and $\hat{n}$ is a unit vector giving the axis of rotation. Then every point in the sphere is an element of $SO(3)$, and **antipodal points are identified**. Topologically, this means that $SO(3)$ has a non-contractible path.

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

