# Relativity 

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
  MathJax.Hub.Config({
  tex2jax: {
    inlineMath: [['$','$'], ['\\(','\\)']],
    displayMath: [['$$','$$']],
    processEscapes: true,
    processEnvironments: true,
    skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
    TeX: { equationNumbers: { autoNumber: "AMS" },
         extensions: ["AMSmath.js", "AMSsymbols.js"] }
  }
  });
  MathJax.Hub.Queue(function() {
    // Fix <code> tags after MathJax finishes running. This is a
    // hack to overcome a shortcoming of Markdown. Discussion at
    // https://github.com/mojombo/jekyll/issues/199
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
  });

  MathJax.Hub.Config({
  // Autonumbering by mathjax
  TeX: { equationNumbers: { autoNumber: "AMS" } }
  });

</script>


$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$

# Relativity

!!! References 

    - *Special Relativity and Classical Field Theory: The Theoretical Minimum*  
    - Physics from Symmetry, Jakob Schwichtenberg

## Notation

We use $\overrightarrow x$ to indicate a vector in $\mathbb{R}^3$, and $x$ to indicate a vector in $\mathbb{R}^4$.

We'll refer to spacetime with 1 time dimension and 3 space dimensions as (3,1)d spacetime. 

## Spacetime

If we view space and time together as a vector space (just doing this in itself makes no claims about relativistic vs. classical mechanics), then we can think about motions of point-masses as trajectories in this space. We call this vector space *space-time*, and a point in it an *event*. A line segment in it is a *world line*. Often it is useful to visualize it graphically as a *space-time diagram*, often in 2D, with 1 spatial dimension and 1 time dimension. Conventionally time is the vertical axis. 


<!-- The trajectory of light makes a world line which looks like a straight line, since it has constant speed. -->

Of course, we are free to choose coordinates in many ways. Newton's first law amounts to the claim that there is *some* set of coordinates for which objects under no force move in straight lines (inertial coordinates). Moreover, given one such set of coordinates, certain transformations give us new coordinates which are also inertial.

<!-- don't change the laws of physics, in the sense that the same differential equation determines them. Moreover, the rule is that for an object with no external forces, its velocity is constant, which corresponds to a straight line trajectory in spacetime. -->

Inertial transforms should form a group (closed under composition and are associative, invertible, have identity). Secondly, since they map lines to lines, they must also be linear (or at least affine) maps.

They should also preserve distance, as defined by a metric $g$. If this metric is the Eucliean metric (i.e. the dot product on space, and similarly on time) then the transformations that preserve the metric (and therefore the measure of distance) form what is known as the Galilean group. These are rotations and translations (both in time and space), and boosts $(x,t)\mapsto(x-vt,t)$ or $v$ is a real number, or as a matrix: 

$$ G(v) = 
% \begin{bmatrix} t' \\\\ x'
% \end{bmatrix} 
\begin{bmatrix} 1 & 0 \\\\ -v & 1
\end{bmatrix}
% \begin{bmatrix} t \\\\ x
% \end{bmatrix} 
$$

Physically, a boost changes between the reference frame of you, and a person moving away from you at a constant speed. That is, suppose that I'm standing at a point one a railroad. Party B is traveling away from me on a train at a constant velocity. There is then a frame corresponding to what party B neasures, and a transform from my frame to hers.

## Relativistic physics

Relativistic physics is entirely classical in the sense described above. The crucial difference is the metric on spacetime. In general (i.e. in the general theory of relativity), the metric $g(x)$ may have different values at different points $x$ in spacetime, and in fact, generally the metric will imply a connection on the [tangent bundle](../physics/gaugetheory.md) which has non-zero curvature. In one important special case (special relativity), the metric is constant everywhere and is the Minkowski metric: 

$$
\eta := \begin{bmatrix}
-1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$

This is for a 4D spacetime, with 1 time dimension (the first row/column) and 3 space dimensions. Distance is then defined by $||x|| = \eta^{\mu\nu}x_\mu x_\nu$. 


!!! Note

  There is also another convention, in which the metric is 

  $$
  \eta := \begin{bmatrix}
  1 & 0 & 0 & 0 \\
  0 & -1 & 0 & 0 \\
  0 & 0 & -1 & 0 \\
  0 & 0 & 0 & -1
  \end{bmatrix}
  $$

  Presumably in the future, people will invent a way of describing the metric which doesn't allow this ambiguity, but for the present, it's common to have to switch between these conventions.

!!! Notation

  The distance between events $x$ and $y$ is $s^2 := ||x-y||$, using the Minkowski metric. Whether the events could be connected by a photon (*lightlike* separated), could be connected by a slower particle (*timelike* separated) or could not be connected (*spacelike* separated, and so causally independent) depends on whether $s^2$ is equal, less or greater than $0$ respectively.

The group of metric preserving transformations is therefore different, and forms what is known as the Lorentz group. It is the group of linear transforms $\Lambda$ such that $\Lambda^T\eta\Lambda = \eta$.

This choice of $g(x)=\eta$ has a number of significant consequences, which are the substance of special relativity.


**First**, there is a maximum speed. To see this, observe that the distance between two events is $k = -(c\Delta t)^2 + (\Delta x)^2 + (\Delta y)^2 + (\Delta z)^2$, where $c$ is a dimensionality constant with dimensions of velocity, so that when $k=0$, we have $c^2 = \frac{(\Delta x)^2 + (\Delta y)^2 + (\Delta z)^2}{(\Delta t)^2}$. In the limit of $\Delta$ small therefore, $c^2 = v^2$, where $v$ is the velocity in space. This is an upperbound, i.e. $|c| \geq |v|$, so physically speaking, nothing moves faster than this velocity $c$.

A consequence of this maximum speed is locality: objects at different points in space cannot be influenced by objects at arbitrarily far points from them.

**Second**, the interesting Lorentz transformations (i.e. not rotations or translations of space) are hyperbolic rotations of spacetime. That is, in (1,1)d:

$$
G(v) = \begin{bmatrix} \cosh \zeta(v) && \sinh \zeta(v) \\ -\sinh\zeta(v) && \cosh\zeta(v) \end{bmatrix}
$$

where $\zeta(v) = \tanh^{-1}(v/c)$ and $c$ is a dimensional constant (which is found empirically to be the speed of light).

One can see that time and space intermingle, which is the really counterintuitive part of special relativity: what one observer views as space, another views as time. 

Furthermore, an object moving with velocity $c$ will appear to have the same velocity in all frames. 

??? Experiment

  Experimentally, it was found that light travels at this maximum speed, and is indeed frame invariant, which was the key evidence for special relativity.

**Third**, distance in space, and distance in time, are both frame dependent. These are commonly referred to as the phenomena of length contraction and time dilation.

**Fourth**, simultaneity is frame dependent. Events which happen at the same time according to one observer (i.e. in one inertial frame) happen at different times according to another.

**Fifth**, velocities do not sum: $G(u)\circ G(v) = G(\frac{u+v}{1+\frac{uv}{c^2}})$. That is, a person running at 90% of the speed of light on top of a train which is going at 90% of the speed of light is not going faster than the speed of light.

## Dimensions

The existence of a frame independent maximum speed means that there is a canonical way to convert a time $t$ into a length $ct$.

It is typical to set $c=1$, and make it dimensionless, so that $t$ and $x$ both have dimensions of length.




<!-- 
  : really this should be in classical physics
Recall that classical physics gives a procedure for starting from a pair of spacetime points $(p_1, p_2)$ (the start and end point of a particle trajectory), and determining the path that has these points as its boundary $P(p_1,p_2)$.

The procedure has the property that it commutes with metric-preserving linear maps $L$. That is, $L(P(p_1,p_2))=P(L(p_1), L(p_2))$.
  : really two metrics are preserved classically
  In non-relativistic physics, there is a metric on space, and a separate metric on time, both of which must be preserved.  -->






### Dimensions


This means we can regard time and length as having the same dimensions, and take $c$ to be a dimensionless constant.

<!-- 
While the Minkovski metric is preserved, the Euclidean metric on space alone (or time alone) need not be. The physical consequence is that a change in reference frame may alter the Euclidean distance between points in space, or points in time.
  : examples and check




 Moreover, the rule is that for an object with no external forces, its velocity is constant, which corresponds to a straight line trajectory in spacetime.

Inertial transforms are ones which switch between inertial reference frames. The difference between Newtonian and relativistic mechanics boils down to the nature of these transforms. -->

<!-- What are we happy to assume about them? Firstly, they should form a group (closed under composition and are associative, invertible, have identity). Secondly, they map lines to lines, since lines represent free solutions to the equations of motion, so they must also be linear maps. -->

<!-- Obvious examples are shifts of the time axis, and shifts and rotations of space. Again, these exist in either relativistic or classical mechanics. -->



<!-- There is an intuitive correspondence between boosts and trajectories. To see this, suppose that I'm standing at a point one a railroad. Party B is traveling away from me on a train at a constant velocity. There is then a frame corresponding to party B, and a transform from my frame to hers. -->

<!-- For simplicity, suppose space is 1D, so that spacetime is 2D. Then the non-relativistic model of boosts uses the transform $(x,t)\mapsto(x-vt,t)$. That is, the position (here in 1 dimension) that I call $x$, the train passenger calls $x-vt$. Here, $v$ is the velocity of the train. In matrix form:

$$ \begin{bmatrix} t' \\\\ x'
\end{bmatrix} \begin{bmatrix} 1 & 0 \\\\ -v & 1
\end{bmatrix} \begin{bmatrix} t \\\\ x
\end{bmatrix} $$ -->

<!-- 
### The Lorentz transform

Einstein notes that this the assumption that this Galilean transform preserves inertial frames contradicts a second principle, that the speed of light is invariant across frames. The problem is pretty clear: if I perceive the speed of light moving away from me as $c$, then surely you should perceive it as $c-v$. But then the speed of light is relative, and that has problematic consequences (i.e. it's not empirically true).

The key idea of special relativity is to postulate that Galilean transforms do not preserve inertial frames, but rather a new kind of transform, Lorentzian transforms, do.

We can actually derive what the Lorentzian transform must be, given the assumption that the speed of light is constant, and that the transforms are linear and form a group. (In fact, this derivation predates Einstein, I think, but he was the first to really understand its physical significance.). But let's bypass the derivation. In which case, this is a Lorentz transform:

$$L(v) = \begin{bmatrix}\frac{1}{\sqrt{1 - \frac{v^{2}}{c^{2}}}} & - \frac{v}{c^{2} \sqrt{1 - \frac{v^{2}}{c^{2}}}}\\- \frac{v}{\sqrt{1 - \frac{v^{2}}{c^{2}}}} & \frac{1}{\sqrt{1 - \frac{v^{2}}{c^{2}}}}\end{bmatrix}$$

Geometrically, you can visualize this is as what happens when you tilt the plane of a 2D space-time diagram such that the $x=t$ line goes *into* the page (but project the resulting plane onto your 2D plane).

On simplification, we find that 

$$G(u)\circ G(v) = G(\frac{u+v}{1+\frac{uv}{c^2}})$$ -->

<!-- So for relatively small speeds, the situation resembles the Galilean one.

The consequences of switching to Lorentz transforms are huge. One is that two events which are simultaneous in one frame need not be in another.

We also get length contraction and time dilation, where 3-length and "1-time" depend on the frame.

We can actually derive what the Lorentzian transform must be, given the assumption that the speed of light is constant. (In fact, this derivation predates Einstein, I think, but he was the first to really understand its physical significance.)

??? Derivation

    Still working with 1D space, what we're looking for is a matrix:

    $$\begin{bmatrix} t' \\ x'
    \end{bmatrix} \begin{bmatrix} \gamma & \delta \\ \beta & \alpha
    \end{bmatrix} \begin{bmatrix} t \\ x
    \end{bmatrix}$$

     -->



### Simple particle Lagrangian

The action (i.e. the integral of the Lagrangian over a trajectory) should be coordinate independent. This suggests a good proposal for the action, recalling that 

$$d\tau = \sqrt{(dt)^2-(dx)^2} = dt\sqrt{1-(\frac{dx}{dt})^2}$$

we define

$$ A := -m\int d\tau = -m\int c^2\sqrt{1-\frac{||\dot{X}||^2}{c^2}}dt := -m\int \mathcal{L}dt $$


So that gives the Lagrangian as $-mc^2\sqrt{1-\frac{||\dot{X}||^2}{c^2}}$

Modulo the factors with $m$ and $c$, this is the arc-length of the path in spacetime.

Taking the first order terms of the binomial expansion to approximate $(1+a)^{\frac{1}{2}}$ by $1+\frac{1}{2}a$, we get a reduction to classical case at small speeds.

## Energy-momentum 4-vector

**Under construction**

## Charge-current 4-vector

A current in physics usually refers to a 4-vector $J$ that is a function of spacetime and satisfies a continuity equation, so:

$$
\partial_\mu J^\mu = 0
$$

(in the Minkowsi metric). If $S$ is space, this implies for $Q(t) = \int_{S} J^0(t, x)$ that

$$
\dot Q(t) = \int_S\partial_0J^0 = -\int_S \partial_kJ^k = 0
$$

The last step is by Stokes' theorem, with the assumption that $J$ vanishes on the boundary as it goes to infinity.

So we have a conserved quantity of the system as a whole (not a function of position).

## Field theories

As mentioned, the finite speed of light implies locality, which is to say that the value of an event should only depend on the values of events in its past light cone.

Viewed algorithmically, this is to say that time evolution is comonadic. Imagine for example that your system is a discrete 1d chain of points, so a list of values like $l=[1,4,5\ldots]$. Then the values of the future list is some $[f(l_r,i=0), f(l_r,i=1), f(l_r,i=2)]$ where $l_r$ is some limited range of values around $l[i]$.

Field theories are a natural way to encode locality, by having an integrand that is a function of the field at a single point, i.e. $x \mapsto \mathcal{L}(\phi(x), \partial_\mu\phi(x), x)$.

## Lagrangians

The Lagrangians of field theories must transform under change of coordinates according to representations of the Lorentz group. This constraint provides a way to determine the fundamental laws of physics.

The simplest case is the $(0,0)$ [representation](../maths/representations.md) of $SO(1,3)$, which is trivial (all group elements map to the identity). So the Lagrangian must be invariant.


### Deriving Lagrangians 

By assumption, the general form of a free (interaction-less) Lagrangian will be:

$$
\mathcal{L}(\phi)(x) = A\phi(x)^0 + B\phi(x)^1 + C\phi(x)^2 + D\partial_\mu\phi + E\partial_\mu\phi\partial^\mu\phi + F\phi\partial_\mu\phi
$$

We'll use symmetry considerations to throw out more terms.

#### Scalar

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
\phi(x) = \int d^4p\frac{1}{(2\pi)^3} \delta(p^2-m^2)\Theta(p_0)(a(p)e^{-ip\cdot x}+b(p)e^{ip\cdot x})
$$

(where $b=a^\dagger$ would ensure the field's output is real).

Physically, we only want positive energy solutions, which is the source of $\Theta(k_0)$.

We then rewrite the measure, with the standard notation of $\omega_p = \sqrt{p^2+m^2}$:


$$
\int d^4p \delta(p^2-m^2) \Theta(p_0)f(\hat p, p_0) \\
=\int d^4p \delta(p_0^2 - \omega_p^2) \Theta(p_0)f(\hat p, p_0) \\
=\int d^4p \delta((p_0-\omega_p)(p_0+\omega_p)) \Theta(p_0)f(\hat p, p_0) \\
=\int d^4p\frac{1}{2p_0}(\delta(p_0-\omega_p)+\delta(p_0+\omega_p)) \Theta(p_0)f(\hat p, p_0) \\
=\int d^4p\frac{1}{2p_0}\delta(p_0-\omega_p) f(\hat p, p_0) \\
=\int d^3p\frac{1}{2\omega_p}f(\hat p, \omega_p) $$

so that 

$$
\phi(x) = \int d^3p \frac{1}{(2\pi)^3\omega_p}(a(p)e^{-ip\cdot x}+b(p)e^{ip\cdot x})
$$

Meanwhile, the Hamiltonian is 

$$
\frac{\partial \mathcal L(\phi)}{\partial (\partial_0\phi)}\partial_0\phi - \mathcal{L} \\
= (\partial_0\phi)^2 - \frac{1}{2}(\partial_\mu\phi(x)\partial^\mu\phi(x) - m^2\phi^2(x))
$$

#### Under construction: other Lorentz representations

### Mass and energy

Dimensionally, we note that energy has dimensions $E = ML^2T^{-2}$, so with $L$ and $T$ equated, $E = M$. This means that mass and energy are of the same type, or if you prefer, that a term $mc^2$ has dimensions of energy.

Indeed, we see that solutions to the Klein-Gordon equation must have $p^2 = m^2$, or $p_0^2 - p^ip_i = m^2c^4$, so that with no momentum, we obtain $E = p_0 = mc^2$.

<!-- $$
\mathcal{L}(\phi, \partial \phi) = \frac{1}{2}(\partial^\mu\phi\partial_\mu \phi - m\phi^2)
$$

so that the Euler=Lagrange equations give

$$
(\partial^2 + m^2)\phi = 0
$$

We then solve in the Fourier way, so $\phi(x,t) = e^{i(\omega t - k\cdot x)}$

with $\omega^2 = k^2 + m^2$. -->

Note that $\omega$ is the energy (up to Planck's constant, which we set to $1$), so putting in dimensional constants, we have $E^2 = p^2c^2 + m^2c^4$, and with momentum $0$, $E = mc^2$.


<!-- ##

Transformations of reference frame must preserve the metric. This is the Poincare group diag (1, -1,-1,-1).

i.e. 

$$
x^T\eta x = (\Lambda x)^T\eta (\Lambda x) \Rightarrow \eta = \Lambda^T\eta\Lambda
$$

General form:

$$
Λ = e^{iJ\cdot \theta + iK\cdot \Phi}
$$ -->