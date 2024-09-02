## Sets

A set is a collection of mathematical objects. For example $X := \{0, 1\}$ is the set containing two *elements*, namely $0$ and $1$. Sets can contain other sets, and can be finite or infinite.

Famously, you have to be careful about how you define sets. For example, the set of all sets is [not well defined](https://en.wikipedia.org/wiki/Russell%27s_paradox).

## Functions

A *function* from a set $X$ to a set $Y$ is a "machine" which, when you give it any element of $X$, gives you back an element of $Y$. We write $f(x) = y$ to mean "the result of inputting $x$ into the function $f$ is $y$.

A function $f$ is an injection if 

$$
\forall x_1,x_2 \in X, x_1\neq x_2 \Rightarrow f(x_1)\neq f(x_2)
$$

A function is a surjection if 

$$
\forall y \in Y, \exists x \in X, y = f(x)
$$

A bijection is a function that is an injection and a surjection.

### The category of sets

Sets form the category SET, with sets as the objects and functions as the morphisms.

This category has products 

$$X \times Y := \{(x,y) | x\in X, y \in Y \}$$

and coproducts (disjoint unions).

It has an initial object (the empty set) and a terminal object (any singleton set, all of which are isomorphic).

The isomorphisms in SET are the bijections. (This is the [Cantor-Schröder-Bernstein](https://en.wikipedia.org/wiki/Schr%C3%B6der%E2%80%93Bernstein_theorem) theorem)

## Numbers

Some important sets include $\mathbb{N}$, $\mathbb{Z}$, $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$, respectively the natural numbers, integers, rationals, reals and complex numbers.

We say that two sets have the same size (aka *cardinality*) if there is an isomorphism between them. This applies even to infinite sets, with famously counterintuitive results like that the set of even integers is the same size as the set of integers.

Crucially, $\mathbb{Z}$ and $\mathbb{R}$ are **not** the same size (but $\mathbb{R}$ and $\mathbb{C}$ are).

## Countability

A set is countably infinite (aka infinite and countable) if it is isomorphic (in SET) to $\mathbb{N}$. 

## The integers

The main intuition to bear in mind is that $\mathbb{Z}$ is discrete - each number has a neighbour.

## The rationals

The rationals are *dense*, which is to say that for any two numbers $a,b : \mathbb{Q}$, there's a number $c : \mathbb{Q}$ between them, so you can't talk about the neighbour of a number.

## The reals

$\mathbb{R}$ is uncountably infinite, so is bigger than the rationals.

$\sqrt{2}$ is an example of a number which is in $\mathbb{R}$ but not in $\mathbb{Q}$, proving that the two sets are not isomorphic. See wikipedia for a [proof](https://en.wikipedia.org/wiki/Square_root_of_2#Proofs_of_irrationality).

<!-- ## Fields

**Under construction**

### Addition and multiplication

**Under construction**

## The complex numbers

One can think of this as a 2D vector space over the real field. That is, each number in $\mathbb{C}$ is a pair of two reals. 

However, the really important thing is how the field works.

**Under construction**

### Complex Conjugate

**Under construction**



 -->
