$\newcommand{\R}{\mathbb{R}}$
## Distributions

  

Given a space $A$, a probability distribution is described by a function $f : A \to \R$, such that $\sum_{a \in A} f(a) = 1$ and $\forall a,(a) \geq 0$.

  

For example, the function $f$:

  

$$
0 \mapsto 0.3
$$

  

$$
1 \mapsto 0.7
$$

  

describes a distribution over the set $B=\{0, 1\}$. This function $f$ is known as the probability mass function (PMF) or probability density function (PDF) if the domain is $\R^n$.

  

We refer to the space of all possible distributions over $B$, known as the space of Bernoulli distributions, as $I(B)$. While $B$ is finite, $I(B)$ is infinite and in fact is a manifold.

  

!!! Note

  
	For each $p : [0,1]$, there is exactly one distribution $(0 \mapsto p, \quad 1 \mapsto (1-p))$ which lives in $I(B)$, so $[0,1] \cong I(B)$.

  
  

!!! Note

  

	When $A$ is a discrete space, this is all quite simple, but in a continuous space, the sum becomes an integral, and we have to be more careful. This is one of the applications of [measure theory](measuretheory.md). However, discrete probability distributions are enough to understand all the fundamental concepts of probability.

## A category of distributions


  $I$ is a functor. Concretely, consider SET (or a category of manifolds) as the domain. For every object $S$, $I(S)$ is an object of DIST; it is a space the points of which are distributions $f$. Ignoring technicalities, we'll use $f$ to also refer to the PDF of a given distribution.

The morphisms are given by the functor; for $g : M \to N$, we get $I(g) : I(M) \to I(N)$, defined by:



$$
I(g)(f)(y) = \sum_{x \in M} 1[g(x)=y]f(x)
$$

  

!!! Note


	Statisticians often talk about random variables, a term I try to avoid here. But, roughly, a random variable $X$ is a distribution over $\R$, and when they write $f(X)$ for some function $f : \R \to \R$, they really mean the distribution $I(f)(X)$.

### Joint distributions

  
A distribution $P : I(A\times B)$, over a product space $A \times B$, is known as a *joint* distribution.

  

Example:

  

$$

(A=1, B=1) : 0.3

$$

$$

(A=1, B=0) : 0.3

$$

$$

(A=0, B=1) : 0.3

$$

$$

(A=0, B=0) : 0.1

$$

  

??? Note

	The name is misleading because it suggests that it is composed of two distributions. It isn't.

  

#### Marginals as a special case

  

Given a joint distribution $P$, say the one given above, we can take the function $f = (a,b) \mapsto a$, and obtain $P_1 = I(f)(P)$. This is known as a *marginal distribution*. We say that the variable $B$ is *marginalized out*.

  

??? Note

	Obviously we could do the same for functions like $(a,b,c) \mapsto (a,c)$, and anything of this sort is referred to as a marginal distribution.


### Conditional distributions

A conditional distribution is a misleading name; it refers to a function $f$ from a set $A$ to a distribution over a set $B$. So given any $a \in A$, $f(a) \in I(B)$. 

Conditional distributions are the morphisms of a category, with spaces of distributions again being the objects. 

??? Note

	For readers familiar with category theory: this category is the Kleisli category of the probability monad. Probabilistic programming implicitly revolves around constructing morphisms in this category.

### Expectation

$E_{x \sim p}[f(x)] := \sum_x p(x)f(x)$, for a PDF $p$ and a function $f$ is the standard way of writing the *expectation*. It is a special case of a morphism in DIST, if we take 


## The geometry of distributions

  

<!-- Quite beautifully, differential geometry turns out to be the natural language to describe information.   (See the notes on [differential geometry] as a prerequisite).
-->
  

Given a set $S$, $I(S)$ is in fact a manifold, in the usual sense that every point on the manifold can be mapped to its parameters under some chart.

  

For example, if $S=\mathbb{R}$, then the unit normal distribution corresponds to a single point on the manifold. If we consider the submanifold of all normal distributions, one particular chart might map it to $(0,1)$, its mean and variance. So this submanifold is 2D.

The most importance fact about this manifold is that there is a canonical way to make it Riemannian, i.e. a canonical choice of metric tensor $g$, known as the Fisher information, which turns out to be the Hessian of the relative entropy:

  
$$

g_{ij} = E[\delta_i\log p(x;\theta)\delta_j\log p(x;\theta)]

$$


The upshot is that we can talk about the distance between distributions in a parametrization-invariant (i.e. coordinate free) way.

## PDF of function of random variable

  

Suppose $Y = g(X)$ and $g$ is increasing. Then $F_Y(y) = P(Y\leq y) = P(g(X)\leq y) = P(X\leq g^{-1}(y)) = F_X(g^{-1}(y))$.

  

Then $f_Y(y) = F'_Y(y) = \frac{d}{dy}F_X(g^{-1}(y)) = f_X(g^{-1}(y))\frac{d}{dy}g^{-1}(y) = f_X(g^{-1}(y))\frac{dg^{-1}(y)}{dy}$

  

Or:

  

$$ F_Y(A) = P(Y\in A) = P(g(X)\in A) = P(X\in g^{-1}(A)) = \int_{g^{-1}(A)}f_X(x)dx $$

  

By the general form of the substitution rule, we then have that

  

$$ P(Y\in A) = \int_{A}(f_X\circ g^{-1})(y)\cdot|J_{g^{-1}}(y)|dy $$

  

But $J_{g^{-1}}(y) = det D(g^{-1}(y)) = det (Dg(g^{-1}(y)))^{-1} = J_g(g^{-1}(y))^{-1}$ so

  

$$ P(Y\in A) = \int_{A}(f_X\circ g^{-1})(y)\cdot|J_g(g^{-1}(y))^{-1}|dy = \int_{A}\frac{(f_X\circ g^{-1})(y)}{|J_g(g^{-1}(y))^{-1}|}dy $$

  

So $\frac{d}{dy}P(Y\in A) = f_Y(y) = \frac{(f_X\circ g^{-1})(y)}{|J_g(g^{-1}(y))|}$

  

So $(f_X\circ g^{-1})(y) = f_Y(y)\cdot|J_g(g^{-1}(y))^{-1}|$

  

## Sum Random Variables by Convolving PDFs

  

$$ F_{X+Y}(z) = \int_{-\infty}^{\infty}\int_{-\infty}^{z-x} f_{(X,Y)}(x,y) dydx $$

  

$$ = \int_{-\infty}^{\infty}\int_{-\infty}^{z} f_{(X,Y)}(x,v-x) dvdx = \int_{-\infty}^{z}\int_{-\infty}^{\infty} f_{(X,Y)}(x,v-x) dvdx $$. Then, taking the derivative with respect to $x$, using the fundamental theorem of calculus, and assuming independence of $X$ and $Y$, we have that $f_{X+Y}(z) = \int_{-\infty}^{\infty} f_X(x)\cdot f_Y(z-x) dx$.

  

## Characteristic Function

  

The characteristic function of a PDF is the (inverse) Fourier transform of its density. The characteristic function of a Gaussian is a Gaussian, since the Gaussian is an eigenvector of the [Fourier transform](fourier.md).

  
## Central Limit Theorem

  

Various increasingly powerful versions, but simplest is that for a sequence $\{X_i\}$ of independent and identically distributed (iid) random variables with mean $\mu$ and variance $\sigma^2$, with $X_n = \left(\sum_i^nX_i\right)-n\mu$, the random variable $Z_n=\frac{X_n-n\mu}{\sqrt{n\sigma^2}}$ converges in distribution to $N(0,1)$, i.e. to a standard normal.

  
  
  

<!-- The proof uses the continuity theorem, which effectively says that it's sufficient to show that the moment generating function (MGF) converges to that of a normal MGF. Then we observe the following:

  

$$MGF_{X_n}(t) = [MGF_{X_i}(t)]^n $$

$$ MGF_{Z_n}(t) = [MGF_{X_i}(\frac{t}{\sqrt{n}\sigma})]^n$$

  

Further, we can Taylor expand the first MGF as follows:

  

$$ MGF_{X_n}(t) = MGF(0) + tMGF'(0) + \frac{t^2}{2}MGF''(0) + o(t^2) = 1 + \frac{t^2}{2}\sigma^2 + o(t^2) $$

  

(The last step happens by fact that the derivatives of the MGF at $0$ are the moments of the distribution in question.)

  

But then:

  

$$ MGF_{Z_n}(t) = [1 + \frac{(\frac{t}{\sqrt{n}\sigma})^2}{2}\sigma^2 + o(t^2)]^n = [1 + \frac{t^2}{2n} + o((\frac{t}{\sqrt{n}\sigma})^2)]^n$$

  

But this converges to $e^{\frac{t^2}{2}}$ as $n$ goes to infinity. That's the MGF of a standard normal, so we're done.

-->

  

The proof uses Fourier methods. The PDF of a sum of iid random variables $X_i$ is a convolution of $n$ PDFs of $X_i$, the Fourier transform of a convolution is a raising of the Fourier transform of those PDFs to the $n$th power, and Taylor expanding inside the Fourier integral gives us the result (see e.g. page 130 of [this](https://see.stanford.edu/materials/lsoftaee261/book-fall-07.pdf)).

## Inference

It is common to be in the situation that we know a PDF $p$ only up to proportionality, i.e. we know that $p(x) \propto \hat p(x)$ for some unnormalized probability function $\hat p$. Inference is the goal of recovering $p$, which amounts to finding the constant of proportionality $1/Z$, i.e. $p(x) = \frac{1}{Z}\hat p(x)$ for some constant $Z$.

### Variational Inference (VI)


In this approach, we specify a submanifold of distributions $q$ with coordinates $\lambda$ that we vary in order to move as close as possible to $p$ according to the metric.

That is, we optimize $\lambda$ in some $q_{\lambda}(\cdot)$ to minimize $KL(q || p) - \sum_x q(x) \log\frac{q(x)}{p(x)} = E_q[\log\frac{q(x)}{p(x)}]$. Once we have performed this optimization to find some $\lambda^\star$, $q_{\lambda^\star}$, is our approximation of $p$.

The challenge is to minimize $KL(q || p)$ without knowing $p$. Here's the idea: let $\hat{p}$ be the unnormalized version of $p$, and let's assume we have that. Then

  

$$L(q) := -\sum_x q(x)\log\frac{q(x)}{\hat{p}(x)} = -\sum_x q(x)\log\frac{q(x)}{p(x)} + \log Z = - KL(q || p) + \log Z$$

  KL divergence is always positive (a basic fact of information theory), so:

  

$$ \log Z = KL(q || p) + L(q) \geq L(q) $$

  
which means that $L(q)$ is a lower bound (in Bayesian inference contexts known as the evidence lower bound, or ELBO) on $Z$. So we maximize $L$ to minimize the KL.
  
#### Mean Field Variational inference

If the distribution you are trying to approximate is a joint distribution (e.g. [the Ising model](../physics/statisticsphysics.md)) then as your approximating family, you can use a product of marginals (each independently parametrized). This is a familiar idea in statistical physics.


### Monte Carlo Methods

Another method for inference is to find a good way to "draw samples" from a distribution, such that the empirical distribution you obtain converges to the true distribution. In a sense, this is also a variational method, since you are moving around a space of empirical distributions to get as close as possible to the true distribution.

Typically, the goal is not to obtain the PDF of the distribution of interest, but rather some expectation value.

!!! Notes

	https://ermongroup.github.io/cs228-notes/inference/sampling/

  

<!-- Often you find yourself in a situation where you have specified a distribution P, which you know up to a normalization constant. You might find yourself in this position in statistical physics (e.g. you don't know the partition function) or in Bayesian inference (you know the posterior distribution up to the denominator, which has a hard integral). A common thing you might want is the expectation of some function $f$ under P (i.e. $\int_{support(P)} f(x)P(x)dx)$, where I'm using $P$ to also mean the pdf of the distribution $P$). You can approximate this, and other such quantities, if you have a good means of taking representative samples from $P$.
-->
  



  

In general, you want samples from the typical set, i.e. the part of the space of the support of $P$ which has both large volume and high probability density (speaking informally - it isn't always a  region with sharp boundaries). It turns out that in high dimensions, almost all of the mass is concentrated in such a set.

#### Markov Chain Monte Carlo (MCMC)

This is a particular type of Monte Carlo method. The idea is that you choose a transition kernel $T(x|x')$ in such a way that $P$ is a fixed point of $T$, that is, $P(x) = (TP)(x) = \int T(x|x')P(x')dx'$. There are different ways to do this, and one common one described below is Metropolis-Hastings. Then you invoke some theorems (largely, I think, the Perron-Frobenius theorem) which tells you that given some assumptions (your $T$ should be ergodic), $T$ has a unit eigenvector (i.e. a distribution which is the fixed point of the kernel) which is maximal and unique. That means that $\lim_{n\to\infty}T^nA$ for any initial distribution $A$ converges to this fixed point, because the largest eigenvector eventually dominates. Because it's unique, this fixed point must be $P$. Taking a Markovian walk along the kernel, starting from any $A$, amounts to sampling from the fixed point, i.e. from $P$. 

##### Metropolis Hastings (MH)

  

$P(x)T(x'|x) = P(x')T(x|x')$ is the condition of *detailed balance* for a pair of a distribution and a kernel. As shown below, detailed balance is sufficient (but *not necessary*) to show that $P$ is a fixed point of $T$.

  

$$ P(x)T(x'|x) = P(x')T(x|x') \Rightarrow \sum_xP(x)T(x'|x) = \sum_xP(x')T(x|x') = P(x')\sum_xT(x|x') = P(x') $$

  

MH is one method to obtain a kernel which satisfies detailed balance. The idea is that you have another kernel $Q$ which you can choose pretty freely, and let $T = A(x'|x)Q(x'|x)$, where $A(x'|x)=min(1,\frac{P(x')Q(x|x')}{P(x)Q(x'|x)})$. Note that you don't have to know $P$, but rather $P$ only up to normalization, since it appears in a ratio. Clever. By design, some simple maths shows that with $T$ as defined, $(P,T)$ satisfies detailed balance, so you're in business. Caveat: you want to make sure that $T$ is ergodic.

  

<!-- In other words, the states in your Markov chain are assignments to all the variables of the distribution (it could be a joint distribution) and so the stationary distribution of the walk is a distribution over the relevant variable(s). If detailed balance is satisfied, then $P$ is the stationary distribution, and so you can sample from $P$ by taking a nice long walk along the chain, since $\lim_nT^n(x) = P $ for any starting value $x$. Magic! (Why does this work? It resembles the fix point operator: for $g = f(f(f(....(f(x)))))), $f(g(x)$ = g(x)$, which is familiar from set theory and computer science. But I think the more important point here is that the unit eigenvector is also the largest one, and so, on each iteration, it gains ground while the others diminish). -->

  

##### Hamiltonian Monte Carlo (HMC)

  
The idea is that we derive a better transition kernel by moving into a phase space and exploiting the nice volume preserving nature of Hamiltonian dynamics (hence the name).

  
We start with the canonical distribution (see [notes on statistical mechanics](/physics/statisticalphysics)).

  

$$ \pi(q,p) = e^{-H(p,q)} $$

  

where $\pi$ is our density. We assume that $\pi(q,p)=\pi(p|q)\pi(q)$ so that

  

$$ H(p,q) = -\log \pi(p,q) = -\log\pi(p|q) -\log \pi(q) = K(p,q) + V(q) $$

  

In other words, choosing $\pi(p|q)$ amounts to choosing a Kinetic energy, while the potential energy $V$ is determined by $\pi(q)$, which is known.

  

The transition kernel at a point $q$ is a three step procedure. First sample $p$ from $\pi(p|q)$. Then push $(p,q)$ forward using Hamiltonian dynamics, approximated with a Symplectic integrator. Finally marginalize out $p$ to get $\pi(q)$ (since we have $\sum_p \pi(p,q) = 1$).

  

What remains is a good choice of Hamiltonian, and a good choice of sympletic integrator.
  

<!-- "Generically, then, volume is largest out in the tails of the target distribution away

from the mode, and this disparity grows exponentially with the dimension of parameter

space. Consequently, the massive volume over which we integrate can compensate to give

a significant contribution to the target expectation despite the smaller density."

  

"The only significant contributions come

from the neighborhood between these two extremes known as the typical set (Figure 3).

Importantly, because probability densities and volumes transform oppositely under any

reparameterization, the typical set is an invariant object that does not depend on the

irrelevant details of any particular choice of parameters."

  

"Consequently, in

order to compute expectations efficiently, we have to be able to identify, and then focus

our computational resources into, the typical set"

  

"The guess-and-check strategy of Random Walk Metropolis is doomed to fail in highdimensional spaces where there are an exponential number of directions in which to guess

but only a singular number of directions that stay within the typical set and pass the check.

In order to make large jumps away from the initial point, and into new, unexplored regions

of the typical set, we need to exploit information about the geometry of the typical set"

  

"Hamiltonian Monte Carlo is the unique procedure for automatically generating this

coherent exploration for sufficiently well-behaved target distributions."

  

"To utilize the information in the gradient we need to complement it with additional geometric constraints, carefully removing the dependence on any particular parameterization

while twisting the directions to align with the typical set. Auspiciously, there is an elegant

procedure for doing exactly this in a field of mathematics known as differential geometry. "

  

"A defining feature of conservative dynamics is the preservation of volume in position-momentum

phase space. For example, although dynamics might compress volumes in position space, the corresponding

volume in momentum space expands to compensate and ensure that the total volume is invariant."

  

add momentum coordinates

obtain a phase space distribution p(q,p) = p(p|q)p(q)

p(q,p) = e^{-H(p,q)}

H(p,q) = -log \pi(p,q) = -log\pi(p|q) -log \pi(q) = K(p,q) + V(q)

  

"Following the Hamiltonian vector field for some time, t, generates trajectories,

φt(q, p), that rapidly move through phase space while being constrained to the typical set.

Projecting these trajectories back down onto the target parameter space finally yields the

efficient exploration of the target typical set for which we are searching." -->

  
## Entropy

  

Entropy $(H : DIST \to \mathbb{R_+})$ is a function that maps a distribution to a real number. It is best defined via the relative entropy, a.k.a. KL divergence:

  

$$ KL(p,q) = \int p(x)\log \frac{p(x)}{q(x)} dx $$

  

Conceptually, this is a measure of the information gained by moving from $q$ to $p$. It is (evidently) not symmetric.

  

When $q(x)\propto C$, i.e. when $q$ is uniform, and when the support of the distribution is discrete, we define $H$ as follows:

  

$$ H(p) = -KL(p, q) = - \sum p(x)\log p(x) dx $$

  

So, entropy is the measure of how much more information a distribution contains than the uniform one.

  

### Entropy in a continuous space

  

The obvious extension of entropy to a continuous variable, namely

  

$$ - \int (p(x)\log p(x))dx $$

  

does **not** represent the right definition. The most obvious way to see that it cannot be right is that it isn't invariant under a change of variables, which means that for $f : X \to Y$, and $y=f(x)$:

  

$$

- \int (p(x)\log p(x))dx

$$

$$

= - \int (p'(f(x)))|\frac{df}{dx}|\log(p'(f(x))|\frac{df}{dx}|) dx

$$

$$

= - \int (p'(f(x)))\log(p'(f(x))|\frac{df}{dx}|) df(x)

$$

$$

= - \int (p'(y))\log(p'(f(x))|\frac{dy}{dx}|) dy

$$

$$

\neq - \int p'(y)\log p'(y)dy

$$

  

(This uses $p(x)dx = p'(y)dy$ and $df(x) = |\frac{dy}{dx}|dx$ )

  

A similar derivation shows that relative entropy **is** reparametrization invariant, which is an indication that it is the more fundamental quantity.

  

### Entropy and Communication

  

Suppose you have a distribution over some set $A$, $p : D(A)$, from which you will be given a sample. Your goal is to come up with a bijection $f : A \to List(\{0,1\})$ (i.e. from $A$ to arbitrary length bitstrings) such that $E_{x\sim p}[len(f(x))]$ is minimized.

  

The intuition: you are trying to minimize the *expected* length of messages which losslessly communicate.

  

The upshot is that one can talk of the *information* contained in a distribution, measured in the *expected* number of bits (Booleans) needed to encode a draw from the distribution.

  

The source coding theorem states that the minimum expected length is $H(p)$, known as the entropy of $p$, which is, up to a factor, the KL distance from a uniform distribution.

  

$$ - \sum_ip_i\log(p_i)$$

  

Intuition: if the entropy is low, this means the distribution puts a lot of mass on certain elements of the support, and accordingly, these can be assigned short messages, minimizing the expected message length.

There is the foundation of a much larger relationship between information theory and communication, which tries to find efficient ways to send data over noisy or noiseless channels and has many applications to modern communication.

### Properties of entropy

  
As the source coding theorem makes clear, information, as measured by entropy, is an additive quantity, which is why a logarithm appears in the definition.

It has various intuitive properties, not least that your uncertainty on a distribution over the cells of a partition of the $p_i$, added to your uncertainty for each distribution over the cell weighted by the cell probability, is equal to the entropy of the unpartitioned set.

  
  

<!--

  
  

## Divergence

  

Rather than defining a metric directly, one can instead specify a divergence $D : M \times M \to \R$, for which $D(p,q)$ is $0$ for $p=q$ and positive otherwise, and for which $D(p,p+dp) = \frac{1}{2}g_{ij}(p)dp_idp_j + O(|dp|^3)$, for $g$ positive-definite.

  

### **Divergence from a convex function**

  

Looking at this definition, we see that for any convex function $\phi : \R^n \to \R$ that acts on the *parameters* of the manifold, we obtain a metric by:

  

$$

D_\phi(p,q) = \phi(x(p)) - \phi(x(q)) - \frac{d\phi(x(q))_i}{dx(q)}(x(p)-x(q))_i

$$

  

This is known as the Bregman divergence measures the distances between the tangent hyperplane of $\phi$ (the last two terms) and its value (the first term), which is always non-negative as desired, by convexity. Moreover, convexity means that the first two terms of the Taylor series are $0$ and that the Hessian, which is $g$, is positive-definite.

  

 make sure you understand the above

  

The Legendre transform $L : (X \to_c \R) \to (X^* \to_c \R$ (where $a \to_c b$ is a convex function) is involutive (i.e $f(f(x)) = x$)).

  

It is defined by $X^* = f(X)$, where $f(x) = \nabla\phi(x)$, and by

  

$$

\phi^*(x^*) = \langle f^{-1}(x^*), x^* \rangle - \phi(x)

$$

  

(We're assuming that both $X$ and $X^*$ are $\R^n$).

  

We can view $\phi$ as acting on $m \in M$ under the $x$ chart (ie. $\phi(m) := \phi(x(m))$), but then $\phi^*$ acts under the $x^*$ chart.

  

It happens that the Bregman divergence then takes a convenient form:

  

$$

D_\phi(p,q) = \phi(x(p)) + \phi^*(x^*(q)) - \langle x(p), x^*(q)\rangle

$$

  

## Geometry of the Exponential family maniofld

  

A particularly important manifold of probability distributions is the exponential family (see [these notes](/maths/probability)):

  
  

$$

P(x) = e^{\theta_is^i(x) -k(x) - \phi(\theta)}

$$

  

The familiar features of the exponential family all come into play here.

  

$\theta$ can be taken as coordinates of $P$, in which case a divergence is induced by $\phi$, the log normalizer, which is known to be convex for the exponential family.

  

Moreover, the dual coordinates are $\frac{\partial \phi(\theta)}{\partial \theta_i}$, which for the exponential family are $E[s(x)]$.

  

The dual of $\phi$ is:

  

$$\phi^*(\theta^*) = \langle \theta^*, \theta \rangle - \phi(\theta) = \langle E_\theta[s(x)], \theta \rangle - \phi(\theta)

$$

  

$$

= \langle \int s(x)p(x;\theta) dx, \theta \rangle - \phi(\theta) $$

$$

= \int \langle s(x), \theta \rangle p(x;\theta) dx - \phi(\theta)

$$

$$

= \int (\log(p(x;\theta))+\phi(\theta)) p(x;\theta) dx - \phi(\theta)

$$

$$

= \int (\log(p(x;\theta))) p(x;\theta) dx = -H(p(\cdot | \theta))

$$

-->

  
  

## Probability distributions

  

### Gaussian (a.k.a. Normal) Distribution

$$
p(x) \propto e^{-x^2/2}
$$
This is the Normal distribution with variance $1$ and mean $0$.

<!--
Its complicated looking PDF can be understood by first looking at the standard normal $N(0,1)$, with PDF $\frac{1}{\sqrt{2\pi)}}e^{-\frac{1}{2}x^2}$ and then doing change of variables, noting that if $f$ is the pdf of $X$, $\frac{1}{\sigma}f(\frac{x-\mu}{\sigma})$ is the pdf of $\mu + \sigma X$, by change of variables.
--> 

The more complicated looking form of a normal distribution with general mean and variance simply follows from change of variables. Similarly for the multivariate Gaussian, a change from $X$ to $\mu + \Sigma X$ justifies its form, where $\Sigma$ is a linear map.

  

The normalization constant can be computed analytically, by using the fact that $\int_{-\infty}^{\infty}e^{-x^2}=\sqrt{\pi}$.

??? Derivation

	Smoothing over a bunch of analytic difficulties, here's the basic idea:
	
	  
	
	$$\int_{-\infty}^{\infty}e^{-x^2}=\sqrt{(\int_{-\infty}^{\infty}e^{-x^2}dx)^2}$$
	
	$$ = \sqrt{\int_{-\infty}^{\infty}e^{-x^2}dx\int_{-\infty}^{\infty}e^{-y^2}dy}$$
	
	$$ = \sqrt{\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}e^{-(x^2+y^2)}dxdy}$$
	
	$$ = \sqrt{\int_{-\infty}^{0}e^{-r^2}2\pi rdr}$$
	
	$$ =\sqrt{\pi}$$
	
	  

### Exponential Distribution

  

$$p(x;\lambda) = \int \lambda e^{-\lambda x} $$

  

$$E[X;\lambda] = E[\int \lambda e^{-\lambda x}] = \int x \lambda e^{-\lambda x} = [x \cdot -e^{-\lambda x}]_0^{\inf} + \int e^{-\lambda x}$$

  

$$ = 0 + [-\frac{1}{\lambda}\cdot e^{-\lambda x}]_0^{inf} = \frac{1}{\lambda}$$

  

### Markov Random Field

  

$$P(x|\theta) = \frac{e^{\theta^T\cdot f(x)}}{\sum_{x'}e^{\theta^T\cdot f(x')}}$$

  

where $f(x)$ is an indicator function and $\theta$ is a vector of parameters. This parametrization shows that an MRF is an exponential family distribution (see below).

  

### Empirical Distribution

A distribution over any set $X$. Given a data set $D$ of points $d \in X$, 

$p(y) \propto \sum_{d \in D} I[d=y]$

  
### Exponential Family


Not to be confused with the exponential distribution. Really it's a family of families. For fixed functions $b$ and $T$ but with $\eta$ varying, we have a family:

  

$$P(x;\eta) = b(x)e^{\eta^TT(x)-a(\eta)}$$

  

$T(X)$: sufficient statistics, $\eta$ : natural parameter, $a(\eta)$: log-normalizer, $b$ : base measure.

  

Canonical Parameters: $\mu,\sigma...$ : $\Omega$ (the sample space)

  

Natural Parameters: $\eta : \R$

  

Link function: $L : \Omega \to \R$

  

Response function: $R : \R \to \Omega$

  

So $\eta$ parametrizes a family. For instance, we can choose $T$ and $b$ to make $\eta$ range over all Gaussians, or Bernoulli, Poisson, Exponential, Von-Mises, Gamma etc distributions. $a$ is determined by $T$ and $b$ and is the log of the normalizing constant.

  

The reason this is useful is that we can prove a bunch of super useful things about distributions in this form. In particular:

  

- $\frac{da(\eta)}{d\eta} = E[T(x);\eta]$

- $H_{\eta}a(\eta) = Cov[T(x);\eta]$

- $a$ is convex in $\theta$

- Each exponential family is conjugate to an exponential family

- Maximum Entropy: exponential families are the most entropic distributions given that the expectation is equal to some $\alpha$, for a fixed base measure

  

To find the maximum likelihood $\theta$ for an observation $D$, one wants to take the gradient of log $P(x|\theta)$, since log-likelihood in exponential families is convex. Taking the gradient of the log of the numerator is easy. But the gradient of the log of the denominator is as follows:

  

$$ \frac{d}{d\theta} log \sum_{x'}e^{\theta^T\cdot f(x')} = \frac{1}{\sum_{x'}e^{\theta^T\cdot f(x')}}

\cdot \sum_{x'} \frac{d}{d\theta} e^{\theta^T\cdot f(x')} $$

  

$$ = \frac{1}{Z(\theta)} \cdot \sum_{x'}e^{\theta^T\cdot f(x')} \cdot f(x') = \sum_{x'} P(x'|\theta) \cdot f(x') = E_{x\sim p(x|\theta)}[f(x)] $$

  

The Hessian wrt. $\theta$ is the covariance of f(x) wrt the MRF. Covariance matrices are positive semi-definite, proving that the log-likelihood is convex.

  

Example of how to put Bernoulli distribution in exponential family form:

  

$T=id$, $b(x)=1, \eta=\sigma^{-1}(\mu)$.

  

Crucial point: how do we convert from the mean parametrized form of the Bernoulli distribution, namely $P(x|\mu) = x^\mu\cdot x^{1-\mu}$ to the naturally parametrized form?

  

Easy: take the log odds: $\eta=log(\frac{\mu}{1-\mu})$. And the inverse is the sigmoid function.

  
  

### Distributions over functions of time (stochastic processes)

  

We can have distributions that live in $I(\R\to\R)$, i.e. where each element of the support is a function.



One can marginalize such a distribution $f : \mathcal{P}(\R\to\R)$ at a particular time, to obtain $\rho(t) : (\R \to \mathcal{P}(\R)) = map(g \mapsto g(t))(f)$, i.e. a time varying distribution.

  

A physical application is to model the time varying motion of a particle with unknown dynamics (see e.g. Brownian motion).

  

#### Stochastic integration

  

For a process P:

  

$$

\int_0^\tau g(t)dP(t) := \lim_{v\to\infty}\sum_{k=0}^{v-1}g(t_k)(P(k+1)(\tau/v))-P(k(\tau/v))

$$

  

where $t_k = k(\tau/v)$ in the **Ito formulation** of the integral, and $t_k = (k + \frac{1}{2})(\tau/v)$ in the **Stratonovich formulation**.

  

#### Wiener process

  

$$

W(t) = lim_{dt \to 0}\sqrt{dt}\sum_{k=0}^{t/dt}J_k

$$

  

So $W$ is the limit of a random walk in a high density of steps.

  

We have that $W(t) = N(0,t)$, and $W(t)-W(s) = N(0, ||t-s||)$.

  

Moreover, for $Y(t) = \int_0^t g(s)dW(s)$:

  

$$

E(Y(t)) = 0
$$
$$
E(Y^2(t)) = \int_0^t g(s)^2ds

$$

  

<!-- ## Chain rule for stochastic processes

  

In the Ito formulation, we have:

  

$$

d\phi(X) = \phi'(X)(a(X,t))

$$ -->

  
  
  

#### Processes via Stochastic Differential Equations (SDEs)

  

It is typical to use the Wiener process to create more complex processes, e.g. $dX = a(X(t),t)dt + b(X(t),t)dW$

  

#### Generators

  

For a given process $dX$, it has an associated generator $\mathcal{L} = a\frac{d}{dx} + \frac{1}{2}b^2\frac{d^2}{dx^2}$.

  
  

#### Ornstein-Uhlenbeck SDE

  

Let $dP = -\gamma Pdt + \sqrt{2\gamma T m} dW$. Then it isn't hard to show that for $t$ large:

  

$$

X(t) = \sqrt{Tm}N(0,1)

$$

  

Physically, this is a model of the approach the equilibrium distribution (of momenta) via an SDE.

  

#### Langevin SDE

  

This is basically Ornstein-Uhlenbeck coupled to Hamiltonian dynamics, in the following sense:

  

$$

d\begin{bmatrix}

q \\

p

\end{bmatrix}

=

\begin{bmatrix}

M^{-1}p \\

-(\nabla U(q) + \gamma p)

\end{bmatrix}dt

+

\begin{bmatrix}

0 \\

\sqrt{2\gamma T}M^{\frac{1}{2}}

\end{bmatrix}dW

$$

  

Physically, it is used as a model of a particle in a "bath" of smaller particles.

  
  

#### Fokker-Planck

  
Considering the definition of $\rho$ above, we may ask about its dynamics, in terms of the defining process $X$.

  
  
  

The answer is a *continuity equation* $\partial^\mu j_\mu=0$ for flux $j^0=\rho$ and $j^i := \frac{dx}{dt}\rho - D\frac{d}{dx^i}\rho$ (for $i$ ranging over space dimensions).

  

Equivalently:

  

$\frac{d}{dt}\rho = \mathcal{L}^\dagger \rho$

  

where (via integration by parts) we have that $\mathcal{L}^\dagger\rho = -\frac{d}{dx}(a\rho) + \frac{1}{2}\frac{d^2}{dx^2}(b^2\rho)$

  

Or more explicitly in 1D:

  

$$

\frac{\partial}{\partial t}\rho(x,t)

= \frac{1}{2}\frac{\partial^2}{\partial x^2}(b^2(x,t)\rho(x,t))-\frac{\partial}{\partial x}(a(x,t)\rho(x,t))

$$

  

**Example**

  

For $dX = 0a(X,t)dt + b^0(X,t)dW = dW$, $\mathcal{L}^\dagger = \frac{1}{2}\frac{d^2}{dx^2}$, so

  

$$

\dot \rho = \frac{1}{2}\frac{d}{dx^2}\rho

$$

  

This is known as the **diffusion equation**.


??? Derivation
	
	  
	
	We proceed in a recursive fashion, taking $P(f(t)=x | x_0, t_0)$ to be the marginal probability conditional on an initial condition, to obtain:
	
	  
	
	$$
	
	P(f(t+dt)=x | x_0, t_0) = \int dx' P(f(t)=x'|x_0,t_0)P(f(t+dt)=x|x',t')
	
	$$
	
	  
	
	$$
	
	= \int dx' P(f(t)=x'|x_0,t_0)E(\delta(x'-x(t+dt)))
	
	$$
	
	  
	
	$$
	
	\approx \int dx' P(f(t)=x'|x_0,t_0)E(\delta(x-x') + \frac{\partial}{\partial x'}(\delta(x-x')\Delta X) + \frac{1}{2}\frac{\partial^2}{\partial x^2}(\delta(x-x')(\Delta x)^2))
	
	$$
	
	  
	
	where we have expanded $g(a) := \delta(x-a)$ around $x'$, so that $\Delta X = x(t+dt)-x'$. Then to evaluate $E[\Delta X]$ and $E[(\Delta X)^2]$, we'll need to know the SDE for $f$.
	
	  
	
	To go further, let us suppose that we have
	
	  
	
	$$
	
	\frac{d}{dt}f(t) = v(f)(t) + \xi(t)
	
	$$
	
	  
	
	where $v$ is deterministic and $\xi$ stochastic with $E(\xi(t)\xi(t'))=2D\delta(t-t')$. We could do other cases, but this gives the general idea. Then $f_{|x_0=x'}(t+dt) = x' + v(x')dt + \int_t^{t+dt}\xi(t')dt'$, so $E[\Delta X] =v(x')dt$, and $E[(\Delta X)^2] = 2Ddt$
	
	  
	
	$$
	
	P(f(t+dt)=x | x_0, t_0) = \\
	
	\int dx' P(f(t)=x'|x_0,t_0)
	
	(1 - v(x')dt\frac{d}{dx} + Ddt\frac{d^2}{dx^2})\delta(x-x') \\
	
	$$
	
	  
	
	so that for
	
	  
	
	$$
	
	\frac{\partial}{\partial t}\rho(x,t) = \frac{P(f(t+dt)=x | x_0, t_0) - P(f(t)=x | x_0, t_0)}{dt} \\
	
	= D\frac{\partial^2}{\partial x^2}\rho(x,t)-\frac{\partial}{\partial x}(v(x)\rho(x,t))
	
	$$
	
	  
  


## Dynamical systems

!!! References

	Chapter 18 of [Machine Learning: A Probabilistic Perspective](https://doc.lagout.org/science/Artificial%20Intelligence/Machine%20learning/Machine%20Learning_%20A%20Probabilistic%20Perspective%20%5BMurphy%202012-08-24%5D.pdf) is great on this topic.

One can also have stochastic dynamical systems, in the sense of a distribution over functions of time, conditional on a function of time.

Discrete time cases of stochastic dynamical systems are known as state space models. For example, imagine a distribution over the position of a particle, that at each time $t$ is a function of the position at time $t-1$.  

The goal is to infer the current, or future states from previous states. Inference methods take advantage of this recurency inherent in the model.

A linear dynamical system is one where the temporal transitions and production of observations are linear, with additive Gaussian noise. They are solvable in closed form by a Kalman filter.


In the case where the transition and observation models are not linear, one option (the Extended Kalman Filter) is to take the Jacobian in order to obtain a linear approximation, and basically do a Kalman filter with that. The unscented Kalman filter is similar, but instead first passes the distribution (or sample points) through the non-linear function, and then fits a Gaussian. 

More generally, one can do Monte Carlo inference in the sense of approximating the state at time $t$ by an empirical distribution, and then update this empirical distribution at each time.

### Distributions over functions of space

  

This mathematics is crucial for field theories in physics (particularly statistical and quantum field theories), since they amount to distributions over fields, where "field" is the physics term for a [section of a fiber bundle](topology.md), which in the simplest case is a function $f : \R^n \to G$ for some space $G$.

  

[Recall](linearalgebra.md) that we can view functions $f: \R^n \to \R$ as vectors. In terms of coefficients, we can regard $f(x), x\in\R$ as the coefficients of the vector $|f\rangle$. $\langle f, g \rangle := \int dx f(x)g(x)$, and $(Af)(x) = \int dy A(x,y)f(y)$.

  

We are interested in distributions on the space, in particular the Boltzmann distribution $p(\phi) \propto e^{-\beta F(\phi)}$ for some $F : (\R^n \to \R) \to \R$.

  

Since the Boltzmann distribution is in the exponential family, the normalizing constant $Z = \int d\phi e^{-\beta F(\phi)}$ is a generating function for the expectations we want to calculate.

  

When $F$ only has quadratic terms, $Z$ is a Gaussian integral:

  

$$

F(\phi) := \int d^dx \partial_i\phi(x)\partial_i\phi(x) + \mu^2\phi^2(x) - B(x)\phi(x)

$$

  
  

$$

Z = \int d\phi e^{\langle\phi , A\phi\rangle - \langle B, \phi \rangle}

$$

  

for $A(x,y) := \delta(x-y)(-\partial^2_x + \mu^2)$ (where we have integrated by parts to obtain the $\partial^2_x$ term).

  

In finite dimensional vector spaces, we use the formula: $Z = \int y e^{-\frac{1}{2}xAx + Bx} = \sqrt{\det(2\pi A)}e^{\frac{1}{2}BA^{-1}B}$. This requires the inverse of $A$. In the infinite dimensional case, the same formula holds, but $A^{-1}$ is defined by the property:

  

$$

AA^{-1} = \delta

$$

  

and known as the *Green's function* of $A$. In the finite dimensional case, $A^{-1}$ is the covariance of the Gaussian, and generated by the second derivative of $\log Z$, as we can see explicitly above. Higher moments are functions of the covariance. Similarly in the infinite dimensional case, $A^{-1}(x,y) = \langle \phi(x), \phi(y)\rangle$ and Wick's theorem gives that higher order correlations are sums of products of the two-point correlation.

  

<!-- The prefactor is often unimportant, e.g. when using $Z$ as a generating function, and we are concerned with $Z \propto e^{\frac{\beta}{2}\langle B, A^{-1}B\rangle}$. -->

  

<!-- Translational invariance (a common *physical* assumption) gives that $A(x,y) = \tilde A(x-y)$, in other words, $A$ only depends on the difference between the points. -->

  

Then since:

  

$$

\delta^4(x) = \int d^4k \frac{1}{(2\pi)^4}e^{ikx}

$$

  

we find that $\langle \phi(x), \phi(y)\rangle = A^{-1}(x,y) = (\nabla^2_x + \mu^2)^{-1}(x,y) = \int d^4k \frac{1}{(2\pi)^4}\frac{e^{ik(x-y)}}{k^2+m^2 + i\epsilon}$

  
**Under construction**
  

<!-- todo:

- fix negation and constants

- understand the ie prescription!

- compute the residue

- find the correlation at high and low distance
-->
  
  
  

