$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$

Groups are one-object categories for which all morphisms are iso. Spelling this out, a groups is a set of maps, typically called $a, b, c\ldots$, including an identity typically written as $1$ or $e$. The maps can be composed to get e.g. $a\circ b$ (more typically written as $ab$), and inverted ($a^{-1}$), such that $aa^{-1}=1$.

Groups are simple enough to be quite well understood, and appear every when we want to think of transformations on a space. 

<!-- It is also more intuitive when understanding why complex (and quaternion) multiplication works the way it does: each complex number is really a linear transformation of the complex plane, and multiplication is composition. -->

## Category of groups

GRP, the category of groups, has groups as objects, and group homomorphisms as maps.

The kernel of a map $f : A \to B$ is the subset of $A$ (which turns out to be a sub*group*) such that for $a \in A, f(a) = 1 \in B$.

## Subgroups and Quotients

A subgroup is what you'd expect: as with a subspace of a linear map, recall that closure is important. That is, if $a,b \in H$, and $H$ is a subgroup of $G$, then $ab$ is in $H$ too. 

A subgroup $N \subset G$ is *normal* iff for $\forall n\in N, \forall g\in G, gng^{-1} \in N$.

A quotient $G/\sim$ is the space of equivalence classes of a space $G$ under some equivalence relation $\sim$. 

In particular, you can quotient a group by the equivalence relation implied by a normal subgroup. E.g. for $N \subset G$, and $a,b\in G$, let $a \sim b$ if $\exists n \in N, an = b$.

## First isomorphism theory

For groups $G$ and $H$, and $f : G \to H$:

- the kernel of $f$ is a *normal* subgroup of $G$
- the image of $f$ is a subgroup of $H$
- the image of $f$ is isomorphic to the $G / ker(f)$


<!-- ## Groups on numbers

Groups play an important role in describing the real and complex numbers.

To see this, note that for every real number $r$, there is a function $f_r(x) = x+r$. 

todo: the isomorphism between numbers and functions

$\mathbb{R}$ forms a group, in the sense that elements of the group are functions $f_n : \mathbb{R}\to \mathbb{R}$, where $f_n(x) = x+n$. As we see, $n \in \mathbb{R}$ labels these functions, with $f_n(e)=n+e = n$.

and $f_{p+q} = f_p \circ f_q$. This amounts to saying that the elements of the group are the reals, the group operation is addition, $0$ is the identity, and $x \mapsto -x$ is the inverse.

$\mathbb{R}$ also has a second group, with functions $f_n(x)=nx$, so that multiplication is the binary operation, $1$ is the identity, and $x \mapsto \frac{1}{x}$ is the inverse.

There is a group homomorphism between these two groups, given by $f := a \mapsto e^a$. E.g. $f(0)=1$.

The same holds true for the complex numbers. In this case, the additive group is just like you'd expect: shifts up and down, left and right, in the complex plane, each corresponding to a complex number. 

But the multiplicative group is more subtle, and this is the essence of why the complex numbers are different to just $\mathbb{R}^2$. The multiplicative group involves rotations too, so that for example, $e^{ix}$ is the complex number corresponding to the function in the multiplicative group which rotates counterclockwise. 

For $x=2\pi$, this is a 360 degree rotation, so $e^{2\pi i}=1$. Similarly, $e^{i\pi}=-1$.

For this reason, $\sqrt{-1}$ can be viewed as the number corresponding to the operation which when done twice, is a 180 degree rotation (counterclockwise). This is $e^{i\pi/4}$, which is just $i$.  -->

**Under construction**



