$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$


## Homology

Here's the idea informally. We have a boundary operator $\delta_n$ which maps an (n-dimensional) space to its (($n-1$)-dimensional) boundary. Since a boundary has no boundary, $\delta_{n-1}\circ\delta_n = \lambda x:\{\}$. 

So if a space is the boundary of a space, it has no boundary. Or:

$$
g \in im (\delta_n) \Rightarrow g \in \ker (\delta_{n-1})
$$

What about the converse? Is it the case that:

$$
g \in \ker (\delta_{n-1}) \Rightarrow g \in im (\delta_n)
$$

**Only when the space in question has no holes**. For example, a space that is a triangle with no interior (i.e a single hole) has no boundary, but is also not the boundary of anything, since the interior is not part of the space.

We want to formalize and generalize this insight, and that leads to homology groups. 

## Simplices

One way to make concrete the idea of boundaries is to work in a space isomorphic to the manifold of interest which basically consists of a bunch of triangles stuck together, known as a simplicial complex. Here, one can define a [free](/maths/categories/#free-objects) commutative group consisting of the points, lines, faces, volumes, etc of the simplical complex $S$.

A homeomorphism $S \to M$, for a topological space $M$ is a triangulation of $M$. Rather like putting things in coordinates, these provide a concrete realization of a manifold from which we can calculate. 

## Homology groups

For a topological space $X$, call the boundary operator $\delta_n$ if it is a group homomorphism that takes an n-dimensional simplex (viewed as a free abelian group) to its boundary, an (n-1) dim one. So the boundary of a line segment is a set of points. (We must take care of orientation so that for a line $ABC$ which is homeomorphic to $AC$, $\delta(ABC)=\delta(AB)+\delta(BC)=A-B+B-C = A-C = \delta(AC)$.)

Now let 

$$
H_n(X) := \frac{\ker \delta_n(X)}{\mathit{im}\space\delta_{n+1}(X)}
$$

This is the nth homology group.  Recalling that an Abelian group $G$ with $p \in \mathbb{N}$ generators is isomorphic to $(\bigoplus_{i=0}^r \Z) \oplus \Z_{k_1}\oplus \ldots \oplus \Z_{k_m}$ (for $p=r+m$) (see [group theory notes](groups.md)), we write $dim(G) := r$.

This is the number of n-holes, also known as $b_i := dim(H_i)$, the $i$-th **Betti number**. . The 0-holes are the number of connection components, a line missing in $\mathbb{R}^3$ would be a 1-hole, and a dot missing in $\mathbb{R}^3$ would be a 2-hole.

### Betti number

A fantastically useful theorem, for a simplicial complex $K$ and $N_r$ the number of $r$ dimensional simplices of $K$:

$$
\chi(K) := \sum_{r=0}^n(-1)^rN_r = \sum_{r=0}^{n}(-1)^r b_r
$$

$\chi$ generalizes the Euler characteristic (vertices - edges + faces), and the above shows that we can calculate it from the homology groups.

## Homotopy

Homotopy is the simplest possible measure of the holes of a manifold.

A 0-homotopy is a point. It is a map from the one element set onto the manifold.

A 1-homotopy is a line or "path" on the manifold. It is a map from $[0,1]$ onto the manifold.

A 2-homotopy (usually just called a homotopy) is a map from one path into another. This is a map from $[0,1]\times [0,1]$  onto the manifold, so a 2D surface on the manifold. Note that it is a map between 1-homotopies.

And so on.

One can also consider the compact homotopies, i.e. loops, so the maps $h_1 : S_1 \to M$, h_2 : $S_2 \to M$, etc. Here one typically fixes a basepoint, so that $h_1(0)= m\in M$.

The homotopy [group](groups.md) $\pi_i$ is formed by taking the compact homotopies quotiented by the $(i+1)$-homotopies. 

### Relationship to Homology

$H_1 = \pi_1/F$ where $F$ is the commutator subgroup (elements of the form $g = x_ix_jx_i^{-1}x_j^{-1}$ so that $x_ix_j = gx_jx_i$). In other words, we take $\pi_1$ which is in general not Abelian, and abelianize by quotienting out commutativity in order to arrive at $H_1$.

### Universal cover

In general, if a space $M$ has a first homotopy group $\pi$ that is non-trivial, we can "unloop", in the sense of finding a fiber bundle known as the universal cover $U$, which has a trivial homotopy group, and for which $U/\pi = M$. Intuitively, think of the circle $S_1$. It has a homotopy group $\Z$, but we can view it as $[0,1]/\Z$ (being a bit imprecise here), i.e. the line segment with its two ends connected.


