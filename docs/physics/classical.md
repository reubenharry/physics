
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

This is a *continuity equation*.

??? Advanced

	This comment assumes familiarity with [differential forms](../maths/differential_geometry)

	One consequence is that $Q(N) = \int_N \star J$, which is an integral over an $M-1$ dimension surface (where $M$ is the dimension of the full space, or spacetime) depends only on the homotopy class of $N$, since for $N$ and a deformation to $N'$, $Q(N)-Q(N') = \int_N \star J = \int d \star J = \int 0 = 0$.

	An important special case is for constant time slices $N$ of Minkowski space, in which case the homotopy statement amounts to conservation of $Q$ over time.

### Examples

For a particle theory, with $\phi(a : \R^3, t : \R) : \R^3$,  with $\mathcal{L}(\phi, \dot \phi, t) = \frac{1}{2}m\dot \phi(a,t)^2$, let our transformation be $\phi(a,t) = \phi(0,t)+a$. Then $J^\mu = 0$, since $\dot \phi(a,t) = \dot \phi(0,t)$ which does not depend on $a$, and $K^\mu = m\dot q$, so $j^\mu = m\dot q$, and $m\partial_\mu  \dot q = 0 \Rightarrow \frac{d}{dt}\dot q = 0$ (noting that $\partial_\mu = \pd{}{t}$), so *momentum is conserved*.

Similarly, for the transformation $\phi(a,t) = \phi(0,t+a)$ and $t(a) = a + t(0)$, we find that $\pd{\mathcal{L}(\phi(a,x), \partial_\mu\phi(a,x))}{a}|_{a=0} = \pd{\mathcal{L}}{t}$, so that $J^\mu = \mathcal{L} = \frac{1}{2}m\dot q^2$. $K^\mu = m\dot q^2$, so $j^\mu = \frac{1}{2}m\dot q^2 = \mathcal{H}$, i.e. the Hamiltonian, or energy of the system.

Now consider a rotation, so $\phi(a,t) = U(a)\phi(0,t)$, where $U(r)$ is a rotation transform around some axis, say $\hat n$. The [Lie algebra](../maths/representations.md) of the 3D rotation group consists of transformations which in coordinates look like $\phi(a,t) = \phi(0,t) + a \hat n \times \phi(0,t)$. This gives $j^\mu = p \cdot (n \times \phi) - 0 = n \cdot (\phi \times p)$ which is the inner product of the angular momentum with the axis of rotation.

For fields, the same reasoning holds. Consider a spacetime translation $x(a) = x + a$ and any Lagrangian $\mathcal{L}$. Then $j^\mu_\nu = \pd{\mathcal{L}}{(\partial_\nu \phi)}\pd{\phi}{x_\mu} - \delta^\mu_\nu\mathcal{L}$. In this context, $T := j$ is known as the energy-momentum tensor. The corresponding conserved quantities are $E = \int d^3 x T^0_0$ and $P_i = \int d^3 x T^0_i$ .

## Kinetic and potential terms

In Cartesian coordinates, a typical Lagrangian is of the form $\mathcal{L}(x, \dot x) = T(\dot x) - V(x) = \frac{1}{2}m\dot x^2 - V(x)$, where $T$ is the kinetic energy and $V$ is the potential energy. 

$V$ can be an arbitrary function.

$T$ usually takes the form above (and there are generic arguments why it should), but *only in Cartesian coordinates*. If your coordinates were the angles of the two arms in a double pendulum, for example, it would no longer have this form. 

Moreover, this separability into two terms is a feature of non-relativistic mechanics.

Force is defined as the negative gradient of the potential, i.e. $F = -\nabla V$. Physically, the name is appropriate, since if you are modeling e.g. a ball falling in a gravitational field, the force $F$ in the equation $m \ddot x = F$ is how hard gravity is pushing the ball downwards.

## Hamiltonian mechanics

The Lagrangian is a function of the tangent bundle. A [Legendre transform](/maths/differential_geometry) gives us a function of the cotangent bundle, namely:

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

In this setting, $F = \frac{dp}{dt}$.

### Liouville's theorem

Volumes in phase space are preserved under the flow induced by the differential equation above.

By dint of this incompressibility, we have a continuity equation, namely:

$$
\frac{d}{dt}\rho = -\nabla \cdot (\rho \cdot \dot x) = \sum_i \pd{}{q^i}(\rho \dot q^i) + \pd{}{p_i}(\rho \dot p_i) = 0
$$

$$
= \sum_i \pd{\rho}{q^i}\dot q^i + \pd{\rho}{p_i}\dot p_i + \rho(\sum_i \pd{}{q^i}\pd{\mathcal{H}}{p^i} - \pd{}{p^i}\pd{\mathcal{H}}{q^i} ) = 0
$$

$$
= \sum_i \pd{\rho}{q^i}\dot q^i + \pd{\rho}{p_i}\dot p_i = \{H, \rho\} = \dot x \cdot \nabla_x \rho := iL\rho
$$

### Symplectic geometry

This is the geometrical structure associated with classical mechanics; using this language, one can restate the above results more abstractly.

Geometrically, the configuration space, of which the Lagrangian is a function, is the tangent bundle, while phase space is the cotangent bundle. The evolution of a system can be described by a map from the cotangent bundle to itself.

Let $\mathcal{M}$ be the $n$ dimensional manifold on which states of your physical system live. Then $TM$, the tangent bundle, is the configuration space, and $T^*M$, the cotangent bundle, is the phase space. More concretely, points in $T^*M$ are pairs $(q,p)$, for $p : \mathcal{M}$ and $q : T^*_pM$. 

Recall that $T^*M$ is itself a ($2n$ dimensional) manifold, on which we may define differential forms.

In fact, there is a map $\theta$:

$$
\theta_{(q,p) : T^*M} : T_zT^*M \to \R
$$

$$
\theta_{(q,p) : T^*M} = p \circ d\pi_1
$$

To understand this, recall that $p$ is a linear map from $T_pM$ to $\R$, and $d\pi_1 : TT^*Q \to TQ$ is the differential of the projection map $\pi_1(q,p) = q$. So we have a $\theta : M \to T^*M$, which is a differential 1-form.


In canonical coordinates, we find:

$$
\theta(p,q) := -p_idq^i
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

## Work

Work is the integral of force over a path in the configuration space, where in the general case, force may be position dependent (and even time dependent):

$$
W = \int (F(x(t)) \cdot v(t))dt \int F \cdot ds
$$

for a displacement $s$. As this suggest, $F$ should more abstractly be viewed as a 1-form, i.e. an object which can be integrated along paths.

This equals the change in kinetic energy:

$$
\int (F(x(t)) \cdot v(t))dt = \int m\int \ddot x \cdot \dot x dt
$$ 

$$
= \int m\int \frac{d}{dt}(\frac{1}{2}\dot x^2)dt = \frac{1}{2}m\dot x^2|_{t_1}^{t_2} = K(t_1) - K(t_2) 
$$

## Perturbations, classically

!!! Note

	This section relies heavily on the material on [Fourier transforms](../maths/fourier.md), in particular the sections on causality and LTI systems. 

Consider a system with a Hamiltonian $H(t) = H_0 + H_1(t)$, where only the second term depends on $t$. If the second term is small, we can proceed linearly.

As an (important) example, suppose our system has a small time varying force $F(t)$, so that we can write the (approximate) solution $x(t)$ as a linear function of $F$:

$$
x(t) = L(F)(t)
$$

We know that $L$ must be a causal system, and it is LTI by assumption, so it can be written as $f \mapsto \chi * f$, for a function $\chi(t)$ with $\chi(t)=0$ for $t <0$ (this requirement on $\chi$ is easy to show by writing out the definition of convolution and the property of a causal system as mapping causal functions to causal functions).

As it turns out, the imaginary part of $\chi$ is related to the change in energy, and is therefore known as the dissipative part of the response function. To see this:

We calculate that the change in energy is:

$$
\Delta E \approx \int F \cdot dx = \int F(t) \dot x dt
$$

$$
= \int d\omega d\omega' dt (-i\omega)F(\omega)F(\omega') \chi(\omega)e^{i(\omega+\omega')t}
$$

which we obtained by substituting in $F(t) = \int d\omega F(\omega)e^{i\omega t}$ and $x(t) = \int d\omega \chi(\omega)e^{i\omega t}$ and similar, and where I ignored constants of proportionality.

Thus by integrating over $dt$ to obtain a delta function in the typical way, we find:

$$
\Delta E \approx \int d\omega (-i\omega)\chi(\omega)F|(\omega)|^2 
$$

Now since $\Delta E$ and $F$ are both real, $\chi(\omega)$ must be real, so that 

$$
\Delta E \approx \int \omega  Im(\chi)(\omega) |F(\omega)|^2d\omega
$$

So $\Delta E$ is only **a function of the imaginary part of $\chi$**.
