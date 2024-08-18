
$\newcommand{\pd}[2]{\frac{\partial #1}{\partial #2}}$

$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$

Think of a physical system as a map $A \to B$, from a space $A$ to a space $B$. 

As an example, a particle can be modelled with $\phi : A \to B$, for $A$ being time, and $B$ being space,  so that $\phi(t)$ is the position of a particle at a given time.

A field theory has $A$ be a position in space or spacetime, and $B$ the same.

## Least action

The fundamental idea of classical physics is that, from the space $A \to B$ of all possible systems, and for a region $T$ of space in $A$, the actual system that describes nature is determined by minimizing a functional $S : A \to (A \to B) \to \mathbb{R}$, i.e.[^1] $\delta S(x) = 0$, where:

$$S(T)(\phi) := \int_T\mathcal{L}(\phi(x), \pd{}{x^i} \phi(x)^j, x)dt$$

for the *Lagrangian* $\mathcal{L} : (B, A \otimes B, A) \to \mathbb{R})$, which we can choose in different ways, depending on the system. One can also view $S$ as the solution to an ODE.

[^1]: Here $\delta$ refers to the variation (with respect to any function $f : T \to C$), so that $\delta G(x) = \frac{d}{ds}G(x(t)+sf(t))|_{s=0} := \frac{d}{ds}G(x_s(t))|_{s=0}$.


!!! Note

    One can make this more precise by considering the manifold $A \to B$ more carefully.

As a simple example with $A = \R$ and $B = \R^3$, i.e. $A$ as time and $B$ as space, consider $\mathcal{L}(\phi,\dot \phi, t) = \frac{1}{2}m\dot \phi^2(t)$ and the time interval $T$:

$$
% \delta S(x) = \int_T \frac{d}{ds}\mathcal{L}(x(t)+sf(t), \frac{d}{dt}(x(t)+sf(t)))|_{s=0}
0 = \delta S(x) = \int_T \frac{d}{ds}\frac{1}{2}m\dot x_s^2(t)dt|_{s=0} \\
= \int_T m\dot x_s(t) \dot f(t) \\
= -\int_T m\ddot x_s(t) f(t) \\
$$

TODO CHECK ^^

Where in the last step, we integrate by parts, and **crucially** assume that the boundary term is $0$. Since this holds for all $f$, we have $\ddot x = 0$.

The physical interpretation is that an object acted on by no forces (namely for the free Lagrangian, $\frac{1}{2}m\dot x^2$), an object maintains constant velocity. Or, if we think of the system as a line in spacetime, it is a straight line.

More generally, minimizing $S$ yields the [Euler-Lagrange](https://en.wikipedia.org/wiki/Euler%E2%80%93Lagrange_equation) condition that $\forall t, (\frac{\partial L}{\partial q}(t) - \frac{d}{dt}\frac{\partial L}{\partial \dot q}(t)) = 0$. Note that in the physical setting, the first and second term have the same dimensions.

If $S(q) = \int L(q)(t) dt$, and $L(q)(t) = m\dot q(t)^2/2 - V(q)$ then we obtain Newton's equation of motion:

$$
0 = \frac{\partial L}{\partial q}(t) - \frac{d}{dt}\frac{\partial L}{\partial \dot q}(t) = \frac{\partial V(q)}{\partial q}(t) -\frac{d}{dt}m\dot x
(t)$$

$$
\Rightarrow m\ddot q(t) =  - \frac{\partial V(q)}{\partial q}(t) = F(q)(t)
$$



## Invariants




Suppose that $\phi(a : \R,x : A) : B$ is a family of configurations of a system, i.e for each choice of $a$, $\phi(a,x)$ describes the state of the system at every point in space and time. Then we say that the system has a symmetry if $\frac{d\mathcal{L}(\phi(a,x), \partial_\mu\phi(a,x), x(a))}{da}|_{a=0} = \partial_\mu J^\mu$, since in that case, to first order, a change in $a$ will have no effect on the action, and therefore will map a solution of the equations of motion to a new solution.

Such symmetries imply an invariant. To see this, first note:

$$
\frac{d\mathcal{L}(\phi(a,x), \partial_\mu\phi(a,x))}{da}|_{a=0} = (\pd{\mathcal{L}}{\phi}-\partial_\mu\pd{\mathcal{L}}{(\partial_\mu\phi)})\pd{\phi}{a}|_{a=0} + \partial_\mu(\pd{\mathcal{L}}{(\partial_\mu\phi)}\pd{\phi}{a})|_{a=0}
$$


by virtue of the chain rule, commutation of partial derivatives and the product rule.

Suppose that the function $x \mapsto \phi(0,x)$ is "on-shell", i.e. satisfies the equations of motion. In that case, 


 $$\frac{d\mathcal{L}(\phi(a,x), \partial_\mu\phi(a,x))}{da}|_{a=0} = \partial_\mu\pd{\mathcal{L}}{(\partial_\mu\phi)}\pd{\phi}{a}|_{a=0} := \partial_\mu K^\mu$$
 




Then for $j^\mu := K^\mu - J^\mu$, we evidently have $\partial_\mu j^\mu = 0$, *as long as $x \mapsto \phi(0,x)$ follows the equations of motion*. We say that $j$ is the Noether current. Or in the language of forms, $d\star j = 0$.

??? Advanced

	This comment assumes familiarity with [differential forms](../maths/differential_geometry)

	One consequence is that $Q(N) = \int_N \star J$, which is an integral over an $M-1$ dimension surface (where $M$ is the dimension of the full space, or spacetime) depends only on the homotopy class of $N$, since for $N$ and a deformation to $N'$, $Q(N)-Q(N') = \int_N \star J = \int d \star J = \int 0 = 0$.

	An important special case is for constant time slices $N$ of Minkowski space, in which case the homotopy statement amounts to conservation of $Q$ over time.

### Examples

For a particle theory, with $\phi(a : \R^3, t : \R) : \R^3$,  with $\mathcal{L}(\phi, \dot \phi, t) = \frac{1}{2}m\dot \phi(a,t)^2$, let our transformation be $\phi(a,t) = \phi(0,t)+a$. Then $J^\mu = 0$, since $\dot \phi(a,t) = \dot \phi(0,t)$ which does not depend on $a$, and $K^\mu = m\dot q$, so $j^\mu = m\dot q$, and $m\partial_\mu  \dot q = 0 \Rightarrow \frac{d}{dt}\dot q = 0$, so *momentum is conserved*.

Similarly, for the transformation $\phi(a,t) = \phi(0,t+a)$ and $t(a) = a + t(0)$, we find that $\pd{\mathcal{L}(\phi(a,x), \partial_\mu\phi(a,x))}{a}|_{a=0} = \pd{\mathcal{L}}{t}$, and noting that $\partial_\mu = \pd{}{t}$, we see that $J^\mu = \mathcal{L} = \frac{1}{2}m\dot q^2$. $K^\mu = m\dot q^2$, so $j^\mu = \frac{1}{2}m\dot q^2 = \mathcal{H}$, i.e. the Hamiltonian, or energy of the system.

TODO rotation

Now consider an infinitesimal rotation. The [Lie algebra](../maths/representations.md) of the 3D rotation group consists of transformations which in coordinates look like $\phi(a,t)_i = \phi(0,t)_i + \epsilon_{ijk}\phi(0,t)_ja_k$. 

For fields, the same reasoning holds. Consider a spacetime translation $x(a) = x + a$ and any Lagrangian $\mathcal{L}$. Then $j^\mu_\nu = \pd{\mathcal{L}}{\partial(\partial_\nu \phi)}\pd{\phi}{x_\mu} - \delta^\mu_\nu\mathcal{L}$. In this context, $T := j$ is known as the energy-momentum tensor. The corresponding conserved quantities are $E = \int d^3 x T^0_0$ and $P_i = \int d^3 x T^0_i$ .



TODO CHECK



$$

$$


todo: integrate vvv and understand why true

For translational symmetry, we have the energy-momentum tensor $T$ as the current: 

$$
T^\nu_\mu = \frac{\partial \mathcal{L}}{\partial (\partial_\nu \phi)}\frac{\partial \phi}{\partial x_\mu} - \delta^\nu_\mu\mathcal{L}
$$

which we note gives $T^0_0$ to be the energy density $\pi \dot\phi - \mathcal{L}$, as per the Legendre transform.



### Field theories

We use $x$ to refer to a point in spacetime, and assume that this is the domain of our field $\phi$.

By assumption, the general form of a free (interaction-less) Lagrangian will be:

$$
\mathcal{L}(\phi)(x) = A\phi(x)^0 + B\phi(x)^1 + C\phi(x)^2 + D\partial_\mu\phi + E\partial_\mu\phi\partial^\mu\phi + F\phi\partial_\mu\phi
$$

We'll use symmetry considerations to throw out more terms.

### Scalar

In this case, we want invariance under the Lorentz group, so the $E$ and $C$ terms survive. The $A$ and $B$ terms don't affect the resulting equations of motions (beyond a constant).

Conventionally, we rescale to:

$$
\mathcal{L}(\phi)(x) = \frac{1}{2}(\partial_\mu\phi(x)\partial^\mu\phi(x) - m^2\phi^2(x))
$$

from which Euler-Lagrange gives 

$$
0 = (\partial_\mu\partial^\mu + m^2)\phi(x)
$$

Clearly anything of the form $ae^{\pm ip\cdot x}$ is a solution when $m^2=p^2$, and we take this as a basis, expressing a general solution, i.e.:

$$
\phi(x) = \int d^4k\frac{1}{(2\pi)^3} \delta(p^2-m^2)\Theta(k_0)(a(p)e^{-ip\cdot x}+b(p)e^{ip\cdot x})
$$

(where $b=a^\dagger$ would ensure the field's output is real).

Physically, we only want positive energy solutions, which is the source of $\Theta(k_0)$.

We then rewrite the measure, with the standard notation of $\omega_p = \sqrt{p^2+m^2}$:


$$
\int d^4k \delta(p^2-m^2) \Theta(k_0)f(\hat k, k_0) \\
=\int d^4k \delta(p_0^2 - \omega_k^2) \Theta(k_0)f(\hat k, k_0) \\
=\int d^4k \delta((k_0-\omega_k)(k_0+\omega_k)) \Theta(k_0)f(\hat k, k_0) \\
=\int d^4k\frac{1}{2k_0}(\delta(k_0-\omega_k)+\delta(k_0+\omega_k)) \Theta(k_0)f(\hat k, k_0) \\
=\int d^4k\frac{1}{2k_0}\delta(k_0-\omega_k) f(\hat k, k_0) \\
=\int d^3k\frac{1}{2\omega_k}f(\hat k, \omega_k) $$

so that 

$$
\phi(x) = \int d^3k \frac{1}{(2\pi)^3\omega_k}(a(p)e^{-ip\cdot x}+b(p)e^{ip\cdot x})
$$

Meanwhile, the Hamiltonian is 

$$
\frac{\partial \mathcal L(\phi)}{\partial (\partial_0\phi)}\partial_0\phi - \mathcal{L} \\
= (\partial_0\phi)^2 - \frac{1}{2}(\partial_\mu\phi(x)\partial^\mu\phi(x) - m^2\phi^2(x))
$$
FIX todo



## Hamiltonian mechanics

### Symplectic geometry

This is the geometrical structure associated with classical mechanics.

Let $\mathcal{M}$ be the $n$ dimensional manifold on which states of your physical system live. Then $TM$, the tangent bundle, is the configuration space, and $T^*M$, the cotangent bundle, is the phase space. More concretely, points in $T^*M$ are pairs $(p,q)$, for $p : \mathcal{M}$ and $q : T^*_pM$. 

Recall that $T^*M$ is itself a ($2n$ dimensional) manifold, on which we may define differential forms.

The idea is to view any particular Hamiltonian dynamics as a map from this space to itself, defined such that a differential form $\omega$ (specified below) is preserved under the map.

In particular, since we are in a category of smooth manifolds, the map will be a diffeomorphism $f$, and it will act on $\omega$ by the pullback $f^*\omega$.

What is $\omega$?

$$
\theta := -p_idq^i
$$

$$
\omega := d\theta = dq^i\wedge dp_i
$$

$$
\Omega := \omega^n = \omega \wedge  \omega...\wedge\omega 
$$

$\omega$ is known as the *symplectic form*, and $\Omega$ as the *volume form*. $\theta$ is invariant under changes of coordinate (since $p$ and $q$ transform inversely), and so $\omega$ and $\Omega$ are too.

Now for the flow. Given a function $f : T^*\mathcal{M}\to \R$, let $L(f)$ be the map such that $df = (\lambda x \mapsto \omega(L(f), x))$. Calling our Hamiltonian $H$, we consider paths on the manifold that follow $L(H)$.

Observe that in coordinates:

$$
\omega(L(f),L(g)) = \frac{\partial f}{\partial q^i}\frac{\partial g}{\partial p_i} - \frac{\partial f}{\partial p_i}\frac{\partial g}{\partial q^i} = \{f,g \}
$$

Also observe, if $f$ follows the flow of some $H$, that using the definition of $L$, and the property of a one-form $df(X) = X(f)$:

$$
\omega(L(f),L(H)) = df(L(H)) = L(H)(f) = \frac{\partial f}{\partial t}
$$

So we have the familiar statement of Hamiltonian mechanics:

$$
\frac{\partial f}{\partial t} = \{f, H\}
$$

so that $\frac{\partial H}{\partial t} = L(H)(H) = \{H,H\} = 0$ (energy preservation).

We also recover volume preservation: todo


<!--
$$
J^\mu(x)  = \pd{\mathcal{L}}{(\partial_\mu\phi_a)}(x)\Delta\phi_a(x) - F^\mu(\phi(x))
$$



where $\Delta\phi_a(x)=\lim_{a\to 0} (T_a(\phi)(x)-\phi(x))$. So for example, if $T(\phi)(x)=e^{a}\phi(x) \approx (1+a)\phi(x)$, $\Delta\phi_a(x) = a\phi(x)$.


The general statement relies on the idea that for a representation onto a space of functions, we call the infinitesimal additive shift from the old $\phi$ to the new $\phi'$ function $\delta \phi = \epsilon^rf_r^a(\phi, \partial_\mu\phi)$. 

TODO

more generally: action symmetry

For instance, if the transform is $\forall x, \phi(x) \mapsto \phi(x)\cdot e^{ia}$
todo
Then, if 

$$
\delta \mathcal{L}(\phi,