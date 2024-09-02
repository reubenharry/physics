
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

where in the last step, we integrate by parts, and **crucially** assume that the boundary term is $0$. Since this holds for all $f$, we have $\ddot x = 0$.

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


Suppose that $\phi(a : \R,x : A) : B$ is a family of configurations of a system, i.e for each choice of $a$, $\phi(a,x)$ describes the state of the system at every point in space and time. Additionally, suppose that $x(a) : \R \to A$ is a family of transformations of the space $A$.

Then we say that the system has a symmetry if $\frac{d\mathcal{L}(\phi(a,x), \partial_\mu\phi(a,x), x(a))}{da}|_{a=0} = \partial_\mu J^\mu$, since in that case, to first order, a change in $a$ will have no effect on the action, and therefore will map a solution of the equations of motion to a new solution.

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

For a particle theory, with $\phi(a : \R^3, t : \R) : \R^3$,  with $\mathcal{L}(\phi, \dot \phi, t) = \frac{1}{2}m\dot \phi(a,t)^2$, let our transformation be $\phi(a,t) = \phi(0,t)+a$. Then $J^\mu = 0$, since $\dot \phi(a,t) = \dot \phi(0,t)$ which does not depend on $a$, and $K^\mu = m\dot q$, so $j^\mu = m\dot q$, and $m\partial_\mu  \dot q = 0 \Rightarrow \frac{d}{dt}\dot q = 0$ (noting that $\partial_\mu = \pd{}{t}$), so *momentum is conserved*.

Similarly, for the transformation $\phi(a,t) = \phi(0,t+a)$ and $t(a) = a + t(0)$, we find that $\pd{\mathcal{L}(\phi(a,x), \partial_\mu\phi(a,x))}{a}|_{a=0} = \pd{\mathcal{L}}{t}$, so that $J^\mu = \mathcal{L} = \frac{1}{2}m\dot q^2$. $K^\mu = m\dot q^2$, so $j^\mu = \frac{1}{2}m\dot q^2 = \mathcal{H}$, i.e. the Hamiltonian, or energy of the system.

Now consider a rotation, so $\phi(a,t) = U(a)\phi(0,t)$, where $U(r)$ is a rotation transform around some axis, say $\hat n$. The [Lie algebra](../maths/representations.md) of the 3D rotation group consists of transformations which in coordinates look like $\phi(a,t) = \phi(0,t) + a \hat n \times \phi(0,t)$. This gives $j^\mu = p \cdot (n \times \phi) - 0 = n \cdot (\phi \times p)$ which is the inner product of the angular momentum with the axis of rotation.

For fields, the same reasoning holds. Consider a spacetime translation $x(a) = x + a$ and any Lagrangian $\mathcal{L}$. Then $j^\mu_\nu = \pd{\mathcal{L}}{(\partial_\nu \phi)}\pd{\phi}{x_\mu} - \delta^\mu_\nu\mathcal{L}$. In this context, $T := j$ is known as the energy-momentum tensor. The corresponding conserved quantities are $E = \int d^3 x T^0_0$ and $P_i = \int d^3 x T^0_i$ .




## Hamiltonian mechanics

The Lagrangian is a function of the tangent bundle. A Legendre transform gives us a function of the cotangent bundle, namely:

$$
H(\pd{\mathcal{L}}{\dot q}, q, t) = \dot q \pd{\mathcal{L}}{\dot q} - \mathcal{L}
$$

$$
\frac{dq}{dt} = \{q,H\} = \pd{H}{p}
$$

and

$$
\frac{dp}{dt} = \{p,H\} = -\pd{H}{q}
$$

where $\{f, g\} = \pd{f}{q}\pd{g}{p} - \pd{f}{p}\pd{g}{q}$ is the Poisson bracket.

This is the Hamiltonian formulation of classical mechanics: it describes a differential equation $\frac{d}{dt} \begin{pmatrix} q \\ p \end{pmatrix} = \begin{pmatrix} \pd{H}{p} \\ -\pd{H}{q} \end{pmatrix}$.


### Symplectic geometry

This is the geometrical structure associated with classical mechanics.

Geometrically, the configuration space, of which the Lagrangian is a function, is the tangent bundle, while phase space is the cotangent bundle. The evolution of a system can be described by a map from the cotangent bundle to itself.

Let $\mathcal{M}$ be the $n$ dimensional manifold on which states of your physical system live. Then $TM$, the tangent bundle, is the configuration space, and $T^*M$, the cotangent bundle, is the phase space. More concretely, points in $T^*M$ are pairs $(p,q)$, for $p : \mathcal{M}$ and $q : T^*_pM$. 

Recall that $T^*M$ is itself a ($2n$ dimensional) manifold, on which we may define differential forms.

In fact, there is a natural form $\theta$:

$$
\theta_{(p,q)} : T_xT^*M \to \R
$$

$$
\theta_{(p,q)} = p \circ d\pi_1
$$

where $\pi_1(q,p)=q$. Examination shows that this is well-typed.

In coordinates, we find:

$$
\theta := -p_idq^i
$$

**Under construction**: derivation

Any particular Hamiltonian dynamics is a map from the cotangent bundle to itself, and is defined such that the differential form $\omega := d\theta$ is preserved under the map.

Concretely, since we are in a category of smooth manifolds, the map will be a diffeomorphism $f$, and it will act on $\omega$ by the pullback $f^*\omega$. In coordinates:


$$
\omega := d\theta = dq^i\wedge dp_i
$$

$\omega$ is known as the *symplectic form*, and $\Omega := \omega^n = \omega \wedge  \omega..._n\wedge\omega$ is the *volume form*. 

<!-- $\theta$ is invariant under changes of coordinate (since $p$ and $q$ transform inversely), and so $\omega$ and $\Omega$ are too. -->

Now for the flow. Given a function $f : T^*\mathcal{M}\to \R$, let $L(f)$ be the map such that $df(x) \mapsto \omega(L(f), x)$. Calling our Hamiltonian $H$, we consider paths on the manifold that follow $L(H)$.

Observe that in coordinates:

$$
\omega(L(f),L(g)) = \frac{\partial f}{\partial q^i}\frac{\partial g}{\partial p_i} - \frac{\partial f}{\partial p_i}\frac{\partial g}{\partial q^i} = \{f,g \}
$$

Also observe, if $f$ follows the flow of some $H$, that using the definition of $L$, and the property of a one-form $df(X) = X(f)$:

$$
\omega(L(f),L(H)) = df(L(H)) = L(H)(f) = \frac{\partial f}{\partial t}
$$

So we have:

$$
\frac{\partial f}{\partial t} = \{f, H\}
$$

so that $\frac{\partial H}{\partial t} = L(H)(H) = \{H,H\} = 0$ (energy preservation).




<!-- $$
J^\mu(x)  = \pd{\mathcal{L}}{(\partial_\mu\phi_a)}(x)\Delta\phi_a(x) - F^\mu(\phi(x))
$$



where $\Delta\phi_a(x)=\lim_{a\to 0} (T_a(\phi)(x)-\phi(x))$. So for example, if $T(\phi)(x)=e^{a}\phi(x) \approx (1+a)\phi(x)$, $\Delta\phi_a(x) = a\phi(x)$.


The general statement relies on the idea that for a representation onto a space of functions, we call the infinitesimal additive shift from the old $\phi$ to the new $\phi'$ function $\delta \phi = \epsilon^rf_r^a(\phi, \partial_\mu\phi)$. 



more generally: action symmetry

For instance, if the transform is $\forall x, \phi(x) \mapsto \phi(x)\cdot e^{ia}$

Then, if  -->

