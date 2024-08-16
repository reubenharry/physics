https://www.damtp.cam.ac.uk/user/tong/relativity/three.pdf are good notes.

## Dimensions

Dimensions are a "type system" for the natural world. Just like in computer science, understanding the types of the values being manipulated both avoids simple bugs and gets you surprisingly far in solving problems. 

I'll use the notation of types for dimensions, e.g. $(x : L)$ to mean: the variable $x$ has dimensions of $L$ (length).


Units, like meters, are values which have a dimension.  For example:

- mass: $M$
- length: $L$
- time: $T$
- speed: $LT^{-1}$
- acceleration: $LT^{-2}$
- energy: $ML^2T^{-2}$

## Rules 

You can't add quantities with different dimensions. So for physical quantities $x : A$ and $y : B$, if you see $x+y$, this means that $A=B$.

You **can** multiply then. For $x : A$ and $y : B$, $xy : AB$.

Quantities whose dimension is $M^0L^0T^0$ or similar are *dimensionless*.

### The type system is a vector space

What sort of thing is a dimension? It can be written as $M^{\alpha}L^{\beta}T^{\gamma}$ (if those are our fundamental dimensions, but there could be others, depending on the problem), where $\alpha,\beta,\gamma$ are rational. So what a dimension really is is a point in an $m$ dimensional vector space over the rational field.

For example, instead of writing that $\hbar : ML^2T^{-1}$, we could write $\hbar : (1,2,-1)$.

Using this notation, multiplying $x : D_1$ and $y : D_2$ gives $xy : D_1+D_2$. 

Multiplying $x : D_1$ by a nondimensional quantity $y$ (i.e. a quantity whose dimension is the $0$ vector) gives, as we would expect, $xy : D_1+0 = D_1$. 

Raising $x : D_1$ to a rational dimensionless quantity $y$ gives $x^y :: yD_1$.

## More rules


You can't exponentiate a dimensional quantity, because, by the power series expansion of the exponential, you can see that you would be adding incommensurate quantities, like $M+M^2...$ for example.

**Angles** are dimensionless - to see that, note that you can add $2\pi$, a dimensionless quantity, to an angle.

**Probabilities** are dimensionless.  Probability densities have dimensions such that integrating over them gives a dimensionless quantity. So for example, a distribution over a physical area will have a density with dimensions $L^{-2}$.

**Calculus** If $x$ has some dimension, an infinitesimal $dx$ has the same dimension. If $x$ has dimension $X$ and $y$ has dimension $Y$, then $\frac{dx}{dy}$ has dimension $XY^{-1}$. Thinking about this is very helpful in thinking about what sort of thing a derivative is.


### Buckingham Pi Theorem

Suppose you have a value you want to calculate and you know it's a function of $n$ variables, each with their own dimension. You could consider a different vector space, spanned by these $n$ variables. Your first sanity check should be that the dimension of the value you want to produce is in the span of the variables.

Further, note that there's a full rank transformation from your new $n$ dimensional ("dimension" in the vector space sense) vector space to the $m$ dimensional vector space of fundamental dimensions that you care about (e.g. M, L, T). By rank-nullity, the dimension of the kernel is $n-m$.

What does that mean? It means that there are $n-m$ orthogonal (so they can't be written in terms of each other) quantities ("dimension" in the type sense) which all become dimensionless under the transformation. So you can *nondimensionalize* your system and write it in $p$ groups, each of which is a dimensionless quantity.

### Dimensional analysis

Suppose you know that quantity (x : X) is a function of (y : Y) and (z: Z). You could have it be a function of more things, it wouldn't change the basic idea. Then you know that the relation, if it exists, takes the form $x = C(t : 0)y^{\alpha}z^{\beta}$ such that $X = Y^{\alpha}Z^{\beta}$.

Expressing $X$ in terms of $Y, Z$ is a linear algebra exercise. First write the matrix with columns expressing $Y$ and $Z$ in your fundamental dimensions (in the unit sense of "dimension"). Invert it and apply to $X$ to get $Y^{\alpha}Z^{\beta}$.

# Physical applications

Since $\frac{1}{2}mv^2$ is a term in both a Lagrangian and a Hamiltonian, we know that Lagrangians and Hamiltonians have dimensions $ML^2T^{-2}$. 

Since the action $S$ is the time integral of a Lagrangian, it must have dimensions $ML^2T^{-1}$.

Since the path integral has the form $e^{S/\hbar}$, $\hbar : ML^2T^{-1}$.

In relativity, $L$ and $T$ are equated, because the speed of light is dimensionless.

<!-- The domain of Quantum Mechanics has characteristic scale of dimension $=ML^2T^{-1}$ on order of $\hbar$, and scale of dimension $V=L/T << c$ -->