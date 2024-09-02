$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

$\newcommand{\N}{\mathbb{N}}$

## Types

Every mathematical object has a type[^1]. For instance, the integer $5$ has type $\Z$, and the function $x \mapsto x + 4$ has type $\Z \to \Z$ (or perhaps $(\R \to \R)$ depending on how we interpret $4$).

[^1: There are other ways of looking at things, but this kind of statement is fine at the level of detail we're concerned with.]

The pair $(4,5)$ has type $(\Z, \Z)$, while the pair $((x \mapsto x + 4), 5)$ has type $((\Z \to \Z), \Z)$. 

Conventionally, we write $4 : \Z$ to mean $4$ is an object with type $\Z$. 

It is often very convenient to clarify the types of a function by writing e.g. $\phi(x : A) : B$, which should be understood to mean: $\phi$ is a function evaluated at $x$ of type $A$, and returns a value $\phi(x)$ of type $B$. From this we infer that $\phi$ has type $A \to B$. 
## Quantifiers

The function $x \mapsto x$ really has type $(\forall a, (a \to a))$, in other words, for any *type* a, take a value of that type and return it.
## Higher order functions

The function $f(x)=x^2$ has type $\mathbb{R} \to \mathbb{R}$; it takes a number as argument. However, there are situations where we are interested in functions which take functions are arguments, or return functions as output.

For example, the function $map$ takes a function $f$ and a list $l$, and applies $f$ to each element of the list. So $map : \forall a, b: (a \to b) \to List(a) \to List(b)$, where if $C$ is a type, $List(C)$ is the type whose values are lists whose elements all have type $C$.

### Currying

A function can also return a function, for instance $f := x \mapsto (y \mapsto y + x)$ is a function which takes a number and returns a function which takes a second number and adds the first number to it. So $f(4)$ is an "add 4" function, so that $(f(4))(5)=9$. It has type $f : \Z \to (\Z \to \Z)$. 

When we write $f(4)$, we say that we have "partially applied" $f$ to $4$. 

We could also define a function $g := (x,y) \mapsto x+y : (\Z, \Z) \to \Z$.

$f$ and $g$ are isomorphic (in the category SET) and the functions mapping from $f$ to $g$ and back are known as uncurrying and currying respectively.

## Recursion and corecursion

## 