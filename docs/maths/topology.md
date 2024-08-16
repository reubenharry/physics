$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$



## Topology

The obvious concrete example of a topology is the "usual" topology on $\R$, namely the set of sets of the form $(a,b) := \{y\in \R, y > a, y < b\}$, and all their (countable) unions.

Note the surprising fact that $(a,b)$ has no greatest point, while $[a,b] := \{y\in \R, y \geq a, y \leq b\}$, which is *not* open, does.

This notion of a toplogical structure on $\R$ is abstracted to an arbitrary topology on a set $S$, which is a set of subsets $U$ including $S$, $\{\}$, closed under countable unions and finite intersections. 

The subsets $U$ are known as the open sets. Open sets allow us to talk about **local** properties, i.e. properties that may not hold true on the largest set of the topology (i.e. the whole space), but hold on some set of open sets which *cover* the space (i.e. whose union is the full space).



A topology is already enough algebraic structure to define the notions of a *boundary*, and *compactness*.

## Boundaries

The interior $I(A)$ of a set $A$ is the largest open subset of $A$. The boundary is the complement of $I(A)$ in $A$. Have in mind the example of a disk and its boundary, a circle.

## Continuity

Topological spaces and maps between them form a category TOP. The maps are an abstraction of *continuous maps* as seen on the reals.

There is the usual analytic definition of continuous maps on $\R$ involving a metric, and limits. The topological definition is much more abstract: a function $f$ such that $f^{-1}(S)$ is open.

One can see the relationship to the usual definition on $\R$ by considering a discontinuous function like the step function. Take the inverse of an open interval like $(0.5,2)$ and note that it is $[1, \infty]$, which is not open on $\R$ by the usual topology. So this function, which is discontinuous in the usual sense, is also discontinuous in the abstract sense.

## Homeomorphisms

This is the word for isomorphisms in the category of topological spaces. So an equivalence between topological spaces.

## Compactness

There's a definition of compactness for real numbers, which is that a compact set is closed and bounded. (Note that $[\alpha,\infty]$ or $[-\infty,\beta]$ or $[-\infty,\infty]$ is closed but not bounded, so closed and bounded mean different things.)

There's a topological definition that's much more abstract, that any open cover of a compact set has a finite subcover (this is equivalent for reals to the above definition by the Heine-Borel theorem.) 

The important intuition - Terence Tao has a nice article on it - is that compactness is a property of infinite sets that are ``finite-ish''. Crucially, certain things that are true of functions on finite sets are true of *continuous* functions on compact sets.

## Topological invariants

These are functions on the category of topological spaces $f$, such that $f(S_1)\neq f(S_2) \Rightarrow S_1 \neq S_2$. Compactness and connectedness are two examples.

The Euler characteristic of a topological space $S$ is Vertices(K)-Edges(K)+Faces(K), where $K$ is **any** polyhedron homeomorphic (i.e isomorphic) to $S$. Obviously this is a topological invariant.

[Homology groups](homology.md) are another.

## Manifolds

Manifolds (of dimension $n$) are topological spaces $M$ that are locally **isomorphic** to a ball in $\R^n$. 

An important example of a space which is locally but not globally like $\R^n$  (in this case for $n=2$) is the surface of a ball, known as the 2-sphere.

## Fiber bundles

It is not the case in all categories that $A/B \times B \cong A$, which is to say that we have spaces $E$ such that $E/G \cong M$ but not $E \cong M \times G$. Fiber bundles are such spaces $E$.

A fiber bundle is a topological space $E$ that is locally a product $B \times F$, in the sense that, *locally*, any projection $\pi$ to $B$ can be factored as $p_1 \circ \phi$, with $\phi : E \to B \times F$ an isomorphism, and $p_1 (x,y) = x$.

Think of a mobius strip as a simple example that is non-trivial (in the sense of not being globally a product space). $E$ is the whole space, $B$ is a circle$, and $F$ is a real interval.

Note that $E$ in the above example is a manifold itself (lying over $B$ which is also a manifold). This is generally true: fiber bundles are manifolds.

When a notion of a quotient is applicable, one can also view a fiber bundle $E$ as a map $E \to B := E/F$. This makes clear the issue: we want that $E/F = B$, but while this is certainly true for the trivial bundle $E\times F$, it is also true for a larger class of non-trivial bundles.

It is often useful to work "in coordinates", in the sense of specifying a fiber bundle by its local map $\phi_a : E \to B \times U_a$ and where two open sets overlap (i.e. $U = U_a \cap U_b$), a map $\Phi_{ab}$ such that $(\Phi_{ab} : U_a \cap U_b \times F \to U_a \cap U_b \times F) \circ (\phi_a : E \to U_a \cap U_b \times F) = (\phi_b : E \to U_a \cap U_b \times F)$. $E$ can then be recovered as a quotient  $(\bigcup_{a\in I}U_a \times F)/ \sim $, where the equivalence relation is given by $\Phi_{ab}$.





