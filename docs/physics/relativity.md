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

IMPORT python notebook

!!! References 

    - *Special Relativity and Classical Field Theory: The Theoretical Minimum*  
    - [Wikipedia](https://en.wikipedia.org/wiki/Derivations_of_the_Lorentz_transformations).

## Notation

We use $\overrightarrow x$ to indicate a vector in $\mathbb{R}^3$, and $x$ to indicate a vector in $\mathbb{R}^4$.
## Spacetime

If we view space and time together as a single space (just doing this in itself makes no claims about relativistic vs. classical mechanics), then we can think about motions of particles as paths in this space.

  todo: really this should be in classical physics
Recall that classical physics gives a procedure for starting from a pair of spacetime points $(p_1, p_2)$ (the start and end point of a particle trajectory), and determining the path that has these points as its boundary $P(p_1,p_2)$.

The procedure has the property that it commutes with metric-preserving linear maps $L$. That is, $L(P(p_1,p_2))=P(L(p_1), L(p_2))$.
  TODO: really two metrics are preserved classically
  In non-relativistic physics, there is a metric on space, and a separate metric on time, both of which must be preserved. 

Further, straight lines 

Special relativity is entirely classical in the sense described above. The crucial difference is the metric on spacetime:

$$ 
\eta = \begin{bmatrix}
-1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$

Paths must now respect this metric. The *Lorentz* group is the group of 
TODO: how does it relate to poincare group?

Empirically, this is a much better model that non-relativistic physics, although the difference is most marked at high velocities.

## Consequences of the new metric

### Addition of velocities 

### A maximum speed

todo

Empirically, this maximum speed turns out to be precisely the speed of light, and indeed, experiments confirm that it is the same in all frames. We write this speed as $c$.

TODO incorporate:

  The distance between events $x$ and $y$ is $s^2 := ||x-y||$, using the Minkowski metric. Whether the events could be connected by a photon (lightlike separated), could be connected by a slower particle (timelike separated) or could not be connected (spacelike separated, and so casually independent) depends on whether $s^2$ is equal, greater or less than $0$.



### Dimensions

The existence of a frame independent maximum speed means that there is a canonical way to convert a time $t$ into a length $ct$.

This means we can regard time and length as having the same dimensions, and take $c$ to be a dimensionless constant.


### Dilation and contraction

While the Minkovski metric is preserved, the Euclidean metric on space alone (or time alone) need not be. The physical consequence is that a change in reference frame may alter the Euclidean distance between points in space, or points in time.
  TODO: examples and check




 Moreover, the rule is that for an object with no external forces, its velocity is constant, which corresponds to a straight line trajectory in spacetime.

Inertial transforms are ones which switch between inertial reference frames. The difference between Newtonian and relativistic mechanics boils down to the nature of these transforms.

What are we happy to assume about them? Firstly, they should form a group (closed under composition and are associative, invertible, have identity). Secondly, they map lines to lines, since lines represent free solutions to the equations of motion, so they must also be linear maps.

Obvious examples are shifts of the time axis, and shifts and rotations of space. Again, these exist in either relativistic or classical mechanics.

However, classically there are no transforms that disturb simultaneity

TODO glue

<!-- There is an intuitive correspondence between boosts and trajectories. To see this, suppose that I'm standing at a point one a railroad. Party B is traveling away from me on a train at a constant velocity. There is then a frame corresponding to party B, and a transform from my frame to hers. -->

For simplicity, suppose space is 1D, so that spacetime is 2D. Then the non-relativistic model of boosts uses the transform $(x,t)\mapsto(x-vt,t)$. That is, the position (here in 1 dimension) that I call $x$, the train passenger calls $x-vt$. Here, $v$ is the velocity of the train. In matrix form:

$$ \begin{bmatrix} t' \\\\ x'
\end{bmatrix} \begin{bmatrix} 1 & 0 \\\\ -v & 1
\end{bmatrix} \begin{bmatrix} t \\\\ x
\end{bmatrix} $$

Einstein notes that this the assumption that this Galilean transform preserves inertial frames contradicts a second principle, that the speed of light is invariant across frames. The problem is pretty clear: if I perceive the speed of light moving away from me as $c$, then surely you should perceive it as $c-v$. But then the speed of light is relative.

The key idea of special relativity is to postulate that Galilean transforms do not preserve inertial frames, but rather a new kind of transform, Lorentzian transforms, do.

### The Lorentz transform

Einstein notes that this the assumption that this Galilean transform preserves inertial frames contradicts a second principle, that the speed of light is invariant across frames. The problem is pretty clear: if I perceive the speed of light moving away from me as $c$, then surely you should perceive it as $c-v$. But then the speed of light is relative, and that has problematic consequences (i.e. it's not empirically true).

The key idea of special relativity is to postulate that Galilean transforms do not preserve inertial frames, but rather a new kind of transform, Lorentzian transforms, do.

We can actually derive what the Lorentzian transform must be, given the assumption that the speed of light is constant, and that the transforms are linear and form a group. (In fact, this derivation predates Einstein, I think, but he was the first to really understand its physical significance.). But let's bypass the derivation. In which case, this is a Lorentz transform:

$$L(v) = \begin{bmatrix}\frac{1}{\sqrt{1 - \frac{v^{2}}{c^{2}}}} & - \frac{v}{c^{2} \sqrt{1 - \frac{v^{2}}{c^{2}}}}\\- \frac{v}{\sqrt{1 - \frac{v^{2}}{c^{2}}}} & \frac{1}{\sqrt{1 - \frac{v^{2}}{c^{2}}}}\end{bmatrix}$$

Geometrically, you can visualize this is as what happens when you tilt the plane of a 2D space-time diagram such that the $x=t$ line goes *into* the page (but project the resulting plane onto your 2D plane).

On simplification, we find that 

$$G(u)\circ G(v) = G(\frac{u+v}{1+\frac{uv}{c^2}})$$

So for relatively small speeds, the situation resembles the Galilean one.

The consequences of switching to Lorentz transforms are huge. One is that two events which are simultaneous in one frame need not be in another.

We also get length contraction and time dilation, where 3-length and "1-time" depend on the frame.

We can actually derive what the Lorentzian transform must be, given the assumption that the speed of light is constant. (In fact, this derivation predates Einstein, I think, but he was the first to really understand its physical significance.)

??? Derivation

    Still working with 1D space, what we're looking for is a matrix:

    $$\begin{bmatrix} t' \\ x'
    \end{bmatrix} \begin{bmatrix} \gamma & \delta \\ \beta & \alpha
    \end{bmatrix} \begin{bmatrix} t \\ x
    \end{bmatrix}$$

    TODO


## TODO: group theoretic picture on $\Lambda$

### Simple Lagrangian

The action (i.e. the integral of the Lagrangian over a trajectory) should be coordinate independent. This suggests a good proposal for the action, recalling that $d\tau = \sqrt{(dt)^2-(dx)^2} = dt\sqrt{1-(\frac{dx}{dt})^2}$:

$$ A = -m\int d\tau = -m\int c^2\sqrt{1-\frac{||\dot{X}||^2}{c^2}}dt := -m\int \mathcal{L}dt $$


So that gives the Lagrangian as $-mc^2\sqrt{1-\frac{||\dot{X}||^2}{c^2}}$

Modulo the factors with $m$ and $c$, this is the arc-length of the path in spacetime.

Taking the first order terms of the binomial expansion to approximate $(1+a)^{\frac{1}{2}}$ by $1+\frac{1}{2}a$, we get a reduction to classical case at small speeds.

## Energy-momentum 4-vector

**Under construction**

## Charge-current 4-vector

A current in physics usually (although often not presented like this) refers to a 4-vector $J$ that is a function of spacetime and satisfies a continuity equation, so:

$$
\partial_\mu J^\mu = 0
$$

(in the Minkowsi metric!). If $S$ is space, this implies for $Q(t) = \int_{S} J^0(t, x)$ that

$$
\dot Q(t) = \int_S\partial_0J^0 = -\int_S \partial_kJ^k = 0
$$

The last step is by Stokes' theorem, with the assumption that $J$ vanishes on the boundary as it goes to infinity.

So we have a conserved quantity of the system as a whole (not a function of position).