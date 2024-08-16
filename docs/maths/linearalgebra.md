$$
\newcommand{\R}{\mathbb{R}}
\newcommand{\C}{\mathbb{C}}
$$

Linear algebra is the study of vector spaces.

Vector spaces are sets in which elements can be added together, and scaled by elements of an underlying field (such as $\R$ or $\C$). If $F$ is a field, denote a vector space over $F$ by $V(F)$.

So if $X$ and $Y$ are in a vector space $V(\R)$, so is $aX$, $X + Y$ and $aX + bY$, for $a,b \in \R$.

The most obvious example is 3D (or indeed 2D) space, where points are the vectors.

### $0$

A vector space must always contain an additive identity $0$, so that $v+0 = 0+v = v$.

### Basis

A basis of a vector space $V(F)$ is a set of elements $e_i \in V(F)$ such that every other element can be written **uniquely** as a weighted sum $\sum_i a^ie_i$, for $a^i \in F$.

Once we choose a basis for $V(F)$, every vector is uniquely specified by a list of numbers in $F$.


### Dimension

The minimal number of elements in *some* basis is the **dimension** of a given vector space.

Any two vector spaces with the same *finite* dimension $d$ are isomorphic.

### Subspaces

A subspace is a subset of a vector space which is *closed under the operations of the vector space*, namely addition of elements and multiplication of elements with scalars. This is a stronger statement than just being a subset.

The set containing only the origin $0$ is always a subspace of any vector space.

### Linear maps

A linear map is a structure preserving map from one vector space to another. That is, for vectors $v_i \in V(F)$ and numbers $a^i \in F$,  $f(\sum_i a^iv_i)=a^i\sum_i f(v_i)$. 

It can be entirely specified by what it does to basis elements, since for $X\in V$, $f(X)=f(\sum_i a^ie_i)=\sum_i a^if(e_i)$.

Write $X \multimap Y$ for a linear map from $X$ to $Y$.

The kernel of a linear map $f : A \multimap B$ is the subset $K \subset A$ such that $\forall v\in K$, $f(v) = 0$, for $0 \in B$. The range is the subset $R \subset B$ such that $\forall v \in R, \exists u \in A, f(u)=v$. It is easy to show that both the kernel and range are subspaces, i.e. closed under weighted sums.


**Rank-nullity theorem**: $\dim(\ker\phi)+\dim(im~\phi)=\dim(V)$ for $\phi : V\to W$.

$\phi$ having a kernel which is the zero subspace is equivalent to $\phi$ being an injective map.

### Category of vector spaces

The category FVECT has finite vector spaces (all over the same field $F$) as objects, and linear maps as morphisms.

### Matrices

*Once we choose a basis* for every vector space, each vector can be written as a list of numbers in the underlying field, and morphisms $f : V^n \to V^m$ can be written as a rectangle $F$ of numbers with $n$ columns and $m$ rows, where the $n$-th column denotes the vector in $V^m$ to which the the $n$-th basis vector of $V^n$ is mapped.

These rectangles are known as *matrixes* or *matrices*. $F_{ij}$ denotes the element of the matrix at row $i$ and column $j$.

!!! Note

    The correspondence between a linear map $f : A \multimap B$ and a matrix $F$ depends on the choice of basis, both in $A$ and $B$.

Composition in the category $f\circ g$ then corresponds to an operation on matrixes known as *matrix multiplication*. If $F$ and $G$ are the matrices corresponding to $f$ and $g$, then we write $FG$ as the matrix corresponding to $f \circ g$, which can be shown to equal:

$$
(FG)_{ij} = \sum_k F_{ik}G_{kj}
$$


### Index notation

It's often very handy to talk about matrices by talking about an arbitrary element $A_{ij}$. To be clear, this is implicitly a universal quantification. For example, if I write $(IA)_{ij}=A_{ij}$, I mean: $\forall i\forall j: (IA)_{ij}=A_{ij}$.

The Kronecker delta $\delta_{ij}$ corresponds to the identity matrix $I$. That is, $\forall i\forall j, I_{ij}=\delta_{ij}$. This plays extremely nicely with multiplication by the identity matrix, so that $(IA)_{ij}=\sum_k\delta_{i=k}A_{kj}=A_{ij}$, as you would want.

The Einstein-summation convention is to write for example $\sum_{j} A_{ij}B_{jk}$ as $A_{ij}B_{jk}$. So, variables which appear once are bound by universal quantification, and variables which appear twice are bound by a sum.

The dot product is then $x_ix_i$. Also, $A_iB_j$ is the index version of $A\otimes B$, the tensor product.


Note that $A_{ij}$ is a scalar, so for example $A_{ij}B_{jk} = B_{jk}A_{ij}$ even though $AB \neq BA$. In a nutshell, this is what makes it so useful. You can reason about individual entries in the matrix.

!!! Note

    Note that you'll sometimes see the indices as superscripts, and in fact, there's a whole story about covariant and contravariant tensors that comes up in [Riemannian geometry](/maths/differential_geometry). But for now, I'll just abuse conventions and write all indices with subscripts.


<!-- These have some important features which  -->


### Inverses

Finding the inverse of a linear map, or the inverse of a matrix, is often very useful. For example, suppose we have: $AX=B$, where $A$ and $B$ are known matrices, and $X$ is unknown. This sort of equation is confusingly known as a system of linear equations. Solving it is the same as multiplying both sides by $A^{-1}$ if it exists (it may not).

A bijective linear map is an isomorphism: i.e. composes with an inverse to form the identity, in both directions. This raises an important point: an arbitrary linear map $\phi$ need not have an inverse $\phi^{-1}$.

A matrix is invertible iff it sends bases to bases.

### Linear Operators

Linear operators are linear maps from a vector space to itself (endomorphisms). A lot of things can be proven about them, and certain concepts are specific to them (as opposed to linear maps in general), like determinants, eigensystems, and the characteristic polynomial.

### Eigenobjects

The eigenspace of an operator $T$ at a field element $\lambda$ is $\ker(T-\lambda I)$. So, the subspace of $V$ where for all elements $v$ in it, if you apply $T$, you get back $\lambda v$. Eigenspaces are invariant subspaces of $\phi$. A sum of eigenspaces is direct. If $V$ is the sum of eigenspaces of $\phi$, $V$ has a basis of eigenvectors of $\phi$, and for some basis, $\phi$ has a diagonal matrix. This is equivalent to saying that there is a basis in the linear operator can be expressed in a very nice and "untangled" form, as a stretching along each dimension of the space. 

A 1D eigenspace is spanned by a single vector, which up to a multiplicative constant is referred to as an eigenvector $v$. If $\phi v = \lambda v$ for some scalar $\lambda$, then $\lambda$ is referred to as an eigenvalue.

Not all maps are diagonalizable. If $\phi : V\to V$ has dim(V) distinct eigenvalues, $\phi$ is diagonalizable.

### Determinants

The determinant is the product of all the eigenvalues of a linear map. Note that it's defined in terms of a linear map, not a matrix, so it's basis independent. However, it can be calculated from a matrix (in any basis), and this is typically the best way to find it.

If the determinant is $0$, then one of the eigenvalues is $0$, so the map has a non-zero kernel.

If you're working in a basis of eigenvectors of a given map $\phi$, that map is simply a stretch in each dimension. So the determinant measures the volume gained under the map. This is why it turns up in the change of variables formula (see [calculus](calculus.md)).

<!-- Along those lines, here's a horrible geometric way of viewing the determinant: A volume function is a multilinear alternating map $\alpha : V^n\to F$. Alternating means that $\alpha(v_1...v_n)=0$ if any $v_i=v_j$. The set of volume functions $\alpha$ of a given type forms a vector space over $F$ of dimension 1. For a non-zero volume function $\alpha$, its value is 0 iff its input is not a basis. So volume functions let us check basis-hood. The determinant of a linear operator $\phi$ is the ratio $\frac{\alpha(\phi(v_1)...\phi(v_n))}{v_1...v_n}$ for any non-zero volume function $\alpha$. Also, the determinant of a matrix $A$ is the sum of the product of each possible route from top to bottom of the matrix, choosing each column only once. These two definitions of the determinant align. -->

<!-- This notion of the determinant as a sum of products of elements in a matrix can be derived from the product of eigenvalues viewpoint, by changing into a particular kind of basis involving generalized eigenspaces, since the map might not be diagonalizable (see Jordan normal form). -->

### Characteristic Polynomial

The characteristic polynomial $p_{\phi}$ of a linear operator $\phi : \C^n\to\C^n$:

$$
p_{\phi}(\lambda) = \det (\phi-\lambda I) = \prod_i^m(\lambda-\lambda_i)^{v_i}
$$

Here's the idea: the determinant of $(\phi-\lambda I)$ is some polynomial in $\lambda$ (a scalar), and any root of that polynomial is a value of $\lambda$ for which the determinant is $0$ and hence for which the map $\phi-\lambda I$ has a non-zero kernel, which means $\exists v: (\phi-\lambda I)v = 0 \Rightarrow \phi(v)=\lambda v$, which is precisely what it means for $v$ to be an eigenvector. So the roots of the characteristic polynomial are the eigenvalues of $\phi$. Because we're working with complex numbers, every polynomial has a root, so there's always an eigenvector.

$\lambda$ is an eigenvalue of $\phi$ iff $\det(\lambda I - \phi)=0$. This is a means to calculate every eigenvalue, since $\det(\lambda I - \phi)=0$ is a polynomial in terms of $\lambda$. Since all complex polynomials have a root, by the fundamental theorem of algebra, a complex linear map always admits an eigenvalue. Not so for real linear maps.

Worth dwelling on this: the point is that if we work in a vector space over an algebraically closed field, i.e. the complex field, then endomorphisms (i.e. operators) always have eigenvectors. This is part of the reason why quantum physics happens in complex vector spaces.

### Triangular Matrices

An upper triangular matrix (all entries at or below the diagonal are 0) represents in the standard basis an operator with the property that $Ae_j \in span(e_1...e_j)$ for all $e_j$. All complex linear operators admit a triangular matrix for some choice of basis.

### Nilpotent operators

A nilpotent operator $\phi : V\to V$ is one where for every $v \in V$, $\exists k : \phi^k(v)=0$. A nilpotent map is not diagonalizable (except if it's zero).

All nilpotent operators have a matrix of the form of blocks $J_i$, where each $J_i$ looks like a right shift operator: left column and bottom row of zeros, and then the identity. 

### Polynomials of operators

We can take polynomials of linear operators, in the sense of maps like $\phi^3+3\phi^4+7id$. Two polynomials of $\phi$, $f(\phi)$ and $g(\phi)$ commute.

### Inner product spaces

The inner product is an abstraction of the notion of an angle, and leads to some important concepts (self-adjoint operators) and powerful results, in particular the spectral theorem.


The inner product  $\langle u, v \rangle :V(F)\times V(F)\to F$ is linear in first argument, conjugate linear in its second, conjugate symmetric, positive real for $\langle v,v\rangle$ and non-degenerate ($\langle v,v\rangle = 0$ iff $v=0$).

The dot product is an example of an inner product: $u \cdot v := u_iv_i$.

The norm of v $= |\langle v,v\rangle|^{\frac{1}{2}}$. The absolute value is because the output of the inner product may be complex. A norm should always be a real number. That's sort of its whole raison d'etre.

We say that vectors are **orthogonal** if their inner product is $0$.


### Bra-ket notation

In an inner product space, a common notation is to write a vector as $|a \rangle$ and its transpose as $\langle a |$.


### Cauchy-Schwartz

$|\langle u,v\rangle| \leq ||u||\cdot||v||$. This can be used to prove the triangle inequality.

### Projection

An orthonormal (orthogonal and normal) basis $b_1...b_n$ has the nice intuitive property that the component of a vector $v$ along $b_i$ is $\langle v,b_i\rangle$.

The projection of $y$ onto a subspace given by the matrix $U$ of an operator is $U(U^TU)^{-1}U^T$. Note that when $U$ is invertible, $U(U^TU)^{-1}U^T = U(U^{-1}U^{-T})U^T = I$. Note also that projection is idempotent: $U(U^TU)^{-1}U^TU(U^TU)^{-1}U^T = U(U^TU)^{-1}((U^TU)(U^TU)^{-1})U^T = U(U^{-1}U^{-T})U^T$.


### Adjoint operators

Two operators $\phi:A\to B$ and $\phi^*: B\to A$, are adjoint iff $\langle \phi v, u \rangle = \langle v, \phi^* u \rangle$.

For a map $\phi$, the kernel of $\phi^*$ is equal to the perpendicular subspace to $im~\phi$. Proof: suppose $v\in\ker\phi^*$. Then $\langle \phi^*(v),u\rangle = 0 = \langle v,\phi(u)\rangle$, so $v \in \perp(im~\phi)$. Proof also runs backwards for other direction.


### The conjugate transpose of a matrix

How does the notion of an adjoint map translate back into the language of matrices? It corresponds to the notion of a matrix transpose (or in the more general complex setting, a conjugate transpose.)

The conjugate transpose $A^*$ of a matrix $A$ is defined as: $A^*_{ij}=\bar{A_{ji}}$. Fixing an *orthonormal* basis B, if one map $\phi$ has a matrix M and another map $\psi$ has matrix N which is the conjugate transpose of M, then $\phi$ and $\psi$ are adjoint, i.e. $\langle \phi(v), v\rangle = \langle v, \psi(v)\rangle$.

The eigenvalues of a self-adjoint map are real. This is because any eigenvalue must be equal to its complex conjugate, and this means it must be real.

### Spectral Theorem

Every complex linear map which is self-adjoint has an orthonormal basis of real eigenvectors.

This is incredibly important (see the notes on [quantum physics](../physics/quantum.md) and [Fourier transforms](fourier.md))

### Unitary operator

A unitary operator $U$ is one that preserves inner products, that is: $\langle v, u \rangle = \langle Uv, Uu \rangle$.

Unitary operators have the property that, since $\langle v, u \rangle = \langle Uv, Uu \rangle = \langle v, U^*Uu \rangle$, $U^*U=I$. This means that $U^{-1}=U^*$.

### Function spaces as inner product spaces

Here's one common inner product for a space of (integrable) functions of type $\R\to\C$: $\langle f,g\rangle = \int f(x)g(x)^*dx$

Eigenvectors of an operator in a function space are sometimes referred to as eigenfunctions.

The second derivative operator $\frac{d^2}{dt^2}$ is self-adjoint in such a space, and a generalization of the above spectral theorem gives an analogous result, namely that it has an orthonormal basis of eigenvectors (the complex exponentials).

### Cayley-Hamilton Theorem

$p_{\phi}(\phi)=0$. The characteristic polynomial with the operator itself as the argument is the $0$ matrix. This is useful both for the generalized eigendecomposition (see below), but also to invert operators. Namely:

$$p_{\phi} = aI + b\phi... = 0\Rightarrow I = \phi(K)\Rightarrow K = \phi^{-1}$$

### Singular value decomposition:

Every map $\phi:U\to W$ has a basis B of U and a basis B' of W such that the matrix of $\phi$ is diagonal with real entries, and then zero for the rest of the rectangle. Think of this as a generalization of eigenvectors beyond operators to all maps. So, for any matrix $A$, there exists orthonormal U and V, and diagonal $\Sigma$ such that $A=U\Sigma V$, and therefore

$$A^TA=(U\Sigma V)^T(U\Sigma V) = (V^T\Sigma^T U^T)(U\Sigma V) $$

which by the orthogonality of U and V (inverse of orthogonal matrix is transpose), and the diagonality of $\Sigma$ (equal to transpose),

$$ = V^T\Sigma (U^{-1}U)\Sigma V = V^T\Sigma^2 V$$

The singular values are the diagonals of $\Sigma$ which are the square root of the eigenvalues of $A^TA$, which exist by the spectral theorem.

### Positive semidefinite linear operators

A quadratic form $f(x) : R^n\to R$ is of the form $x^TAx = (A^Tx)^Tx = (x^TA^Tx)^T = x^TA^Tx$. Since every linear operator decomposes into a symmetric and antisymmetric part ($A = \frac{A+A^T}{2} + \frac{A-A^T}{2}$), $x^TAx = x^T(\frac{A+A^T}{2})x$, so in general we assume $A$ symmetric. A positive semidefinite matrix is one for which $x^TAx \geq 0$ for all $x$.

A positive definite ($x^TAx>0$) matrix is full rank, since otherwise we could choose $x$ such that $Ax=0$ and therefore $x^TAx=0$.

$A^TA$ is positive definite for any matrix $A$.

Note that if the eigenvalues of an operator $\phi$ are all positive, its diagonal matrix $\Lambda_{\phi}$ must be positive semidefinite, since the quadratic form $f(x)$ of $\Lambda_{\phi} = \sum_i\lambda_ix_i^2 > 0$.

### Tensors

A tensor is an element of a tensor product space. The tensor product $\otimes$ is the monoidal product of the category of finite dimensional vector spaces, with $\R$ as the unit. It is a reification of linear maps, such that $hom(A,B)$ is isomorphic to $A \otimes B$. Moreover, any multilinear map can be reduced to a canonical map into a tensor product space, followed by a linear map from the tensor product space.

In the category of sets, the monoidal product and the categorical product are the same, but in the category of finite dimensional vector spaces, they are not. This accounts for a lot of why quantum physics is intuitively confusing: it involves monoidal products of vector spaces, which don't have properties you'd expect from a categorical product. Things like entanglement derive from this.

### Generalized Eigendecomposition

A generalized eigenspace is set of vectors $v$ such that for *some* $k$, $(\phi - \lambda I)^kv=0$, for some eigenvalue $\lambda$. Indeed, $k$ needs to be at most dim(V) to kill $v$, so a generalized eigenspace $G(\lambda,\phi : V\to V)$ is just the kernel of $(\phi - \lambda I)^{dim(V)}$.

Recall that the characteristic polynomial $p_{\phi}(\lambda)$ of a linear operator $\phi$ is defined as:

$$
p_{\phi}(\lambda) = \prod_i^m(\lambda-\lambda_i)^{v_i}
$$

where $\lambda_i$ are the $m$ distinct eigenvalues of $\phi$ and $v_i$ their corresponding multiplicities. Then some algebra which I don't yet understand give us that

$$
ker(p_{\phi}(\lambda)) = \bigoplus_i^m ker\space (\phi-\lambda_iI)^{v_i}
$$
And the Cayley-Hamilton theorem gives that

$$
p_{\phi}(\phi) = 0 \Rightarrow ker\space p_{\phi}(\lambda) = \C^n
$$

So putting that together:

$$
\C^n = \bigoplus_i^m ker\space (\phi-\lambda_iI)^{v_i}
$$

This is the decomposition of $\C^n$ into a bunch of generalized eigenspaces. On each, $\phi-\lambda_i I$ is nilpotent. Moreover, the $\lambda_i$ are the eigenvalues of $\phi$, so for example, if $\forall i: v_i=1$, then $\phi$ is diagonalizable.

### $\Lambda+N$ Decomposition

This is the decomposition of any linear operator $\phi$ into the sum of a diagonalizable operator $\Lambda$ and a nilpotent operator $N$.  (A nilpotent operator $N$ is one such that $\exists k\in\mathbb{N}: N^j=0$ for $j\geq k$  ).

Why does any matrix admit this decomposition? The key to seeing this is to consider the generalized eigendecomposition of $\C^n=\bigoplus_i^m ker\space (\phi-\lambda_iI)^{v_i}$ according to $\phi$.

Then we define $\Lambda$ as follows:
$$
\forall v: v \in \ker (\phi-\lambda_iI)^{v_i}:  \Lambda v \mapsto \lambda_iv
$$
Since $\bigoplus_i^m ker\space (\phi-\lambda_iI)^{v_i}$ is a direct sum, $v$ always belongs in a single generalized eigenspace, and clearly it is diagonalizable (just choose any basis).

Now consider $N=\phi-\Lambda$. It follows easily that $N\Lambda=\phi\Lambda - \Lambda^2 = \Lambda\phi - \Lambda^2 = \Lambda N$. Moreover, if we once again use the fact that any vector $v$ has to be in one of the generalized eigenspaces:
$$
Nx = \phi x - \Lambda x = (\phi - \lambda_iI) x \Rightarrow N^nx = (\phi - \lambda_iI)^nx = 0
$$
if $n$ is sufficiently large, by the very definition of the generalized eigenspace as $ker(\phi-\lambda_i)^{v_i}$.

It only remains to prove uniqueness of the $\Lambda+N$ decomposition.

### Jordan Normal Form

A nilpotent linear operator $N$ can be represented as a block matrix with blocks of the form $\delta_{i+1=j}$.

A Jordan matrix $J(\lambda)$ takes the form $\delta_{i+1=j}+\lambda\delta_{i=j}$.

A matrix in Jordan Normal Form (JNF) consists of Jordan blocks $J(\lambda_i)$ for each generalized eigenvalue of the generalized eigendecomposition of the corresponding linear operator $\phi$.


### Matrix Exponentials

A *matrix exponential* is defined by the same series defintion as the normal exponential function:

$$
e^{At} = I + At + \frac{1}{2}(At)^2 + ... = \sum_{i=0}^{\infty}\frac{(At)^i}{i!}
$$

With some analysis, this can be shown to converge.

By the distributivity of differentiation over addition, it's clear that $\frac{de^{At}}{dt} = A + At... = Ae^{At}$.

We also get that $e^{t(A+B)}=e^{tA}e^{tB}$ **if** $AB=BA$.

The next step is to find a way to calculate arbitrary matrix exponentials. We can do so easily if we make use of the $\Lambda+N$ decomposition.

The reason this is useful is that the matrix exponential of a diagonal matrix is simply the exponential of the diagonal elements, that is: $(e^{\Lambda})_{ij} = \delta_{ij}\cdot e^{\Lambda_{ij}}$. Further, the exponential of a nilpotent matrix is only the first $k$ terms of the Taylor series defining the exponential, for $N^k=0$.

In addition, $\Lambda$ and $N$ commute. This is good, because then $e^A=e^{\Lambda}e^N$, which we can calculate easily and exactly.

Exponentiating a JNF matrix corresponds to exponentiating each block. Because taking integer powers of a nilpotent matrix is a kind of right shift operation on the matrix columns, and using the Taylor definition of the exponential, it's possible to show that:

$$
e^{tJ(\lambda)}_{ij}=\sum_{k=0}\delta_{i-j=k}\cdot \frac{e^{\lambda t}t^k}{k!}
$$

### Spectral Mapping Theorem

The spectral mapping theorem is that if $\lambda_i$ is an eigenvalue of $\phi$, then $e^{\lambda_i}$ is an eigenvalue of $e^{\phi}$.

Corollary:

$$
\det e^{\psi}=\prod_i\lambda_i(e^{\psi})=\prod_ie^{\lambda_i(\psi)}=e^{\sum_i\lambda_i(\psi)}=e^{tr(\psi)}
$$

The middle equality follows from the spectral mapping theorem.


### Cross product

The cross product in a 3-dimensional space is $(u\times v)_i=\epsilon_{ijk}u_jv_k$

Note that $(u\times v)_iu_i = \epsilon_{ijk}u_jv_ku_i=u_1u_2v_3-u_1u_3v_2+u_2u_3v_1-u_2u_1v_3+u_3u_1v_2-u_3u_2v_1=0$

Also note that $(u\times u)_i=u_ju_k-u_ku_j=0$

So the cross product of a two vectors $u\times v$ is orthogonal to $u$ and $v$, and the cross product of a vector with itself is $0$.

