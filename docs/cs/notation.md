## Notation

The notation mostly follows what is standard in mathematics and physics; anything that might be unfamiliar to people with that background is described below. 

### Types

$$
3 : \mathbb{Z} 
$$

should be read as "3, which is an integer". Similarly

$$
f : A \to B
$$

should be read as "$f$, which is a function from $A$ to $B$".

Whenever you see $a : b$, it is a way of indicating what *type* of thing $a$ is, or equivalently, what space it "lives" in.

??? Note

    $3 \in \mathbb{Z}$ is used in roughly the same way here ("3 is in the set of integers"). For technical reasons that are not important here, this is not quite the same as $3 : \mathbb{Z}$.


### Partial application

Suppose I have a function $f$ of type $\R \to (\R \to \R)$, so a function which takes a real number and returns a function from $\R$ to $\R$. Then it makes sense to write e.g. $f(4)(5)$, where $4$ is the input to $f$, and $5$ is the input to $f(4)$, which is itself a function.
### Equality

$$
x := 3
$$

should be read as "x is defined to mean $3$".

### Lambda calculus

$\lambda x: f(x)$ denotes the function $x \mapsto f(x)$.

## Einstein summation

Einstein notation is used by default.

$$
a^ib_i := \sum_ia^ib_i
$$

## 

(5+)

todo: explain