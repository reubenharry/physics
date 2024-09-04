
$\newcommand{\pd}[2]{\frac{\partial #1}{\partial #2}}$
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Z}{\mathbb{Z}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$

!!! Note 

    These notes are strongly opinionated, following [Jaynes](https://www.amazon.com/Probability-Theory-Science-T-Jaynes/dp/0521592712), and present statistical physics as the application of the [maximum entropy principle](statistics.md) to physical systems. Furthermore, thermodynamics is presented in terms of the geometry of the information manifold, following [Caticha](https://www.arielcaticha.com/my-book-entropic-physics).
    
    This seems like the natural modern approach, since it demystifies entropy, temperature and so on, viewing them as information-theoretic concepts, and not intrinsically physical ones. On this view, statistical physics is not new physics, it is the application of probability theory to old physics.

    However, note that it isn't entirely uncontroversial, and a common criticism is that it makes temperature dependent on the information state of an observer, rather than being a property of the system. I take the view that this is indeed the case, but see Caticha for nuanced discussion.

## Statistical physics

**Statistical** physics examines systems up to incomplete information, using the standard apparatus of Bayesian probability theory. That is, we describe our (incomplete) knowledge of a system by a probability distribution over systems, $p : Dist(Time \to C)$, where $C$ is the configuration space of the system, classical or quantum.

While systems live on one manifold (the microspace), the space of interest to statistical physics (call it the "macrospace") is the manifold of distributions over the original space. Each macrostate is really a whole distribution over microstates. Quantities of interest, like energy, can be viewed as expectations over the distribution.

Often the macrospace is much lower dimensional than the microspace (when we only consider maximum-entropy distributions - see below). This is why statistical physics is so effective.


!!! Note

    It is important to note that statistical physics often involves very large systems (e.g. a system of $10^{23}$ particles), but doesn't need to. It makes total sense to consider a distribution over a single particle system. It is just that many common results do not hold in this situation, but all the ensembles are defined exactly the same.


## Equilibrium statistical physics (thermodynamics)

From our distribution, we can obtain a marginal distribution at a given time $t$, i.e. a distribution over $f(t) : C$. Equilibrium physics is concerned with such marginal distributions $\rho(t) : Dist(C)$ which are time-invariant under the dynamics of the system, i.e.

$$
\frac{\partial}{\partial t}\rho(t) = 0
$$

The principle of maximum entropy orders that we pick the maximum-entropy distribution over states consistent with our assumptions, namely: (1) the distribution is stationary, (2) the exact energy of the system is known. Note that energy is time-conserved in a closed system.

This gives a distribution often referred to as the microcanonical ensemble, namely $p(x) \propto \delta(E(x) - E^*)$, for some given energy $E^*$.

If we know the *expected* energy instead has a fixed value, the maximum entropy distribution is in the  [exponential family](../maths/probability.md), a distribution known as the *canonical ensemble*.

Concretely, suppose we have a classical system with Lagrangian $\mathcal{L}$, and we know the expected energy $\langle E \rangle$, where $E$ (i.e. the Hamiltonian, more commonly written $H$ in classical mechanics) is a function on phase space $E(p,q) \in \mathbb{R}$. Then the appropriate distribution is $P(p,q) = \frac{1}{Z}e^{-\beta E(p,q)}$, where $\beta$ is the coordinate on the information manifold (i.e. for each value of $\beta$ we can a different distribution).

We may have further constraints, like knowing the volume or number of particles. For example, the so-called *grand canonical ensemble* is the distribution $p(x, N) \propto e^{-\beta(E(x, N) - \mu N)}$ where $N$ is the number of particles.

??? Stationarity

    Being a function of an invariant quantity, the energy, the distribution is stationary as desired. More precisely, we have from classical mechanics that $\frac{d}{dt}\rho = \frac{\partial}{\partial t}\rho + \{H, \rho\}$, and by Louville's theorem, $\frac{d}{dt}\rho = 0$. Since $\rho$ is a function of $H$, we have $\{H, \rho\} = 0$ too, so $\frac{\partial}{\partial t}\rho = 0$.

### Terminology: physics vs. probability

The physics community uses a different terminology, reflecting the complicated history of the field. Here is a table of terminological correspondences between probability and physics:

| Physics    | Probability |
| -------- | ------- |
| ensemble | distribution |
| Boltzmann distribution | exponential family distribution |
|partition function $Z$ | normalization constant |
| Free energy $F$ | log of normalization constant |
| (micro)energy $E$ | sufficient statistic |
| (macro)energy $E$ or $\langle E\rangle$ | expectation of energy |
| inverse temperature $\beta$ | natural parameter |
| thermodynamic entropy | information theoretic entropy of equilibrium distribution |
| equilibrium system | stationary maximum entropy distribution |
| Legendre transform between ensembles | Legendre transform between mean and natural parameters |

### Classical vs quantum statistical mechanics

#### Quantum

Equilibrium statistical mechanics applies equally to classical and quantum systems.

For quantum systems, the density matrix is the object which fully describes a distribution over states of the system. Unitarity is the counterpart to Louville's theorem, i.e. that probability density is conserved over time. The entropy has exactly the same form, but can be written:

$$
-\sum_i p_i\log p_i = -Tr(\rho\log \rho)
$$

For instance in the canonical ensemble,

$$ Z = \sum_j e^{-\beta E_j} = \sum_n \langle n|e^{-\beta H}|n\rangle = Tr(e^{-\beta H})$$

and 

$$\rho = \frac{e^{-\beta H}}{Z}$$

Also recall that, since for an operator $O$ and an eigenvector $O_n$, $p(O_n)=\langle O_n|\rho | O_n\rangle$, we have for $O=H$:

$$p(E_n) = \langle E_n|\rho | E_n\rangle = \frac{e^{-\beta E_n}}{Z}$$

#### Classical

Classical statistical mechanics can be derived from quantum statistical mechanics. Recall that:

- $[T,U] = O(\hbar)$. That is, the commutator of potential and kinetic energy (these being quadratic in position and momentum respectively) is of the order of Planck's constant.
- $\langle x | p \rangle = \frac{1}{\sqrt{2 \pi\hbar}}e^{ixp/\hbar}$

Then note that $Z = e^{-\beta H} = e^{-\beta T}e^{-\beta U}$, *up to a correction term on the order of Planck's constant*. Working in a convenient basis, for a single particle system:

$$Z \approx Tr(e^{-\beta T}e^{-\beta U}) = \sum_{r,k} \langle x|e^{-\beta U} |x\rangle \langle x |p \rangle \langle p | e^{-\beta T} | p \rangle \langle p | x \rangle $$

$$ = \frac{1}{2\pi \hbar}\int dpdq e^{-\beta \left( U(r) + \frac{p^2}{2m}\right)}$$

which is an integral over phase space with a correction factor that makes dimensional sense.

For a multiparticle system, we need to also account for the symmetrization in quantum mechanics, and obtain:


$$Z = \frac{1}{h^{dN}N!}\int dp^Nq^N e^{-\beta \left( U(r^n) + \sum_i\frac{p_i^2}{2m}\right)}$$

What's happening here is that we're integrating over phase space, which at a very high resolution is really the discrete grid of position and momentum eigenvalues. 


<!-- This gives us a (sub)manifold of exponential family distributions, which we can parametrize either in primal or dual coordinates, related by a Lagrange transform. These are either:

- parametrized by mean energy
- parametrized by (inverse) temperature -->



!!! Note

    The language in which statistical physics is usually expressed is frequentist. That is, an ensemble is described as being "many copies of a system". The Bayesian way to think, followed here, is not to think of many systems, but just to think about uncertainty about a single system.

### Dimensions

For historical reasons, temperature is sometimes treated as having a new dimension, so that a dimensional constant is needed to convert between energy and temperature, i.e. so that $k_BT$ has dimensions of energy. It is much simpler to set temperature as having dimensions of energy.

### The thermodynamic limit

### Relationship between ensembles

In the thermodynamic limit, which means the limit of a system of very many particles, the canonical and microcanonical ensemble converge. To see this, write:

$$ Z = \sum_ie^{-\beta E_i} = \sum_{E_i}\Omega(E_i)e^{\beta E_i} \approx \Omega(E^{\\*})e^{\beta E^{\\*}}$$

where $E^{\\*}$ is the maximum value of $E_i$, and the approximation is justified since both terms in the sum scale exponentially with $E_i$ which scales linearly (energy is extensive) with $N$, which is enormous. So we can differentiate the negative of the log of both sides of the above equation by $\beta$, to obtain:

$$\langle E \rangle \approx -\pd{}{\beta}\log \Omega(E^{\\*})e^{\beta E^{\\*}} = -\pd{}{\beta}\log \Omega(E^{\\*}) + \pd{}{\beta}\beta E^{\\*} = E^{\\*}$$

In other words, the energy is effectively a constant, for $N\to\infty$ in the canonical ensemble, which is precisely the constraint of the microcanonical ensemble.

As for the variance, since $c_v$ is an intensive quantity, we now have that $Var(E)=(\Delta E)^2=k_BT^2NC_v \Rightarrow STD(H)=\Delta E\propto N$, and since $E$ is extensive with $E\propto \sqrt{N}$, it follows that $\frac{\Delta E}{E}\propto \frac{1}{\sqrt{N}}\to 0$ as $N\to \infty$.

Suppose we are in the canonical ensemble, but wish to parameterize our distribution not by a choice of $\beta$, but by a choice of $\langle E \rangle$. $\langle E \rangle$ is effectively $E$ in the thermodynamic limit, so our new coordinates will parametrize microcanonical distributions. 

Geometrically, this is a change of coordinates from primal to dual coordinates on our manifold (see e.g. https://www.amazon.com/Information-Geometry-Applications-Mathematical-Sciences/dp/4431559779), and corresponds to a Legendre transform. A similar story applies to parametrization in terms of pressure $p$ or volume $V$.

### Entropy

!!! Conventions
    
    It is conventional to write $E$ to mean the expected energy $\langle E \rangle$ in the context of thermodynamics. We define $T := \frac{1}{\beta}$.


Entropy is a map from a distribution (i.e. a point on the information manifold) to a real number. So it's a function on the information manifold.

For a microcanonical distribution, the entropy is:

$$
S[p] = -\sum p(x)\log p(x)dx = -\sum \frac{1}{\Omega} \log \frac{1}{\Omega} = \log \Omega
$$

where $\Omega$ is the number of states. For the canonical distribution, the entropy is:

$$
S[p] = -\sum_x p(x)\log\frac{1}{Z}e^{-\beta E(x)} = \log Z + \beta\langle E \rangle
$$

So we see that:

$$
\beta = \frac{\partial S}{\partial E}
$$

This in fact holds for all ensembles. Further, we can calculate the exterior derivative of $S$:

$$
dS = d(\log Z) = d(\beta 
langle E\rangle) = -\frac{1}{Z}\sum_a e^{-\beta E_a}(E_ad\beta + \beta dE_a) + \langle E\rangle d\beta + \beta d\langle E\rangle
$$

$$ = \beta(d\langle E\rangle - \langle dE \rangle)
$$

### Temperature


import: explanation of temperature physically


### Composing systems

Given two closed systems with respective energies $E_1$ and $E_2$, we can merge them into one system, which is to say we forget the individual energies and only keep knowledge of $E = E_1 + E_2$. Physically, the systems do not interact (i.e. the Hamiltonian is of the form $H(p_1, q_1, p_2, q_2) = H_1(p_1, q_1) + H_2(p_2, q_2)$).

A common scenario is where $E_1/E_2$ is huge, in which case we refer to system $1$ as a heat bath. 

It is natural to ask what the marginal distribution $p_2(x_2)$ over system $2$ then looks like, where $x_2$ is a phase space point. We can calculate it by marginalizing:

$$
p_2(x_2) \propto \sum_{x_1}(x_1)\delta(E_1(x_1) + E_2(x_2) - E) \propto \Omega_1(E - E_2(x_2))$$

$$ 
= e^{S_1(E - E_2(x_2))} \approx e^{S_1(E) - \frac{\partial S_1}{\partial E}E_2(x_2)} \propto e^{-\beta_1E_2(x_2)}
$$

This is the marginal distribution of system $2$ when open (i.e. when it is a small part of a much larger system), and we see that the constraint of a fixed $\langle E \rangle$ will give rise to this same distribution, the canonical ensemble. So we say that for an open system, the expected energy is the relevant constraint.

### Heat and work

Consider the function which maps each point on the information manifold to the expected energy of the distribution in question. Note that we can calculate it as $\sum_i E_i p(E_i)$, where we work in discrete levels for simplicity and $p$ is the distribution over energies, *not states*. This is a function on the manifold, which we'll also call $E : \mathcal{M} \to \R$, so that $dE$ is a differential form.

In particular:

$$
d\langle E \rangle = \sum_i dE_ip(E_i) + E_idp(E_i) := w + q
$$


!!! Note

    Conventionally, we write $dE = dQ + dW$ or similar, but this is a misleading notation since $dQ$ and $dW$ are **not exact forms**. That is, there is no function $Q$ or $W$.


Since $dE$ is exact, any integral of it over a path is path-independent. In particular, it is $0$ around any contractible loop. The same is *not* true of $q$ and $w$, and a loop may exchange heat and work, which is to say that $\int q \neq 0$ and $\int w \neq 0$ around a loop. We call $q$ the heat and $w$ the work of a system.

In particular $w = \langle dE \rangle$, and $q = d\langle E \rangle - \langle dE \rangle$. $q$ measures the change in expected energy from a change in probabilities, while $w$ measure the change in expected energy from a change in the energy levels.

If $E$ is a function of volume $V$, then $w = \frac{d\langle E \rangle}{dV}dV := -pdV$. And by our above calculation of $dS$, we have $q = TdS$. 

This means that $q/T$ is an exact form. When integrated over a path, it gives the different between the entropy at the beginning and end, by Stokes' theorem:

$$
\int_{\gamma} \frac{q}{T} = \int_{\gamma} dS = S(\gamma(1)) - S(\gamma(0))
$$

Summarizing, we have $dE = TdS - PdV$, which is a formulation of the first law of thermodynamics.


### The language of thermodynamics

A process in thermodynamics is a path on the information manifold, i.e. a curve $\gamma : [0, 1] \to \mathcal{M}$. If $\int_\gamma q > 0$, we say that heat is gained, and similarly for work.

A process $\gamma$ is adiabatic if $\int_\gamma q = 0$. This means that the probabilities don't change.

A process is quasistatic (and reversible) if it lies entirely on the maximum entropy submanifold.


<!-- by noting that if system $2$ is in a state $x_2$ (i.e. some tuple $x_2=(p_2,q_2)$) with energy $E_2(x_2)$, then its probability is proportional to the number of states of system $1$ with energy $E_1$ such that the total energy is $E_1 + E_2(x_2)$, i.e.  -->

### Second law of thermodynamics

As per the above table, entropy in statistical physics refers to the information entropy of the equilibrium distribution. This **is not the distribution you get by pushing an equilibrium distribution forward in time**. 

!!! Example

    Consider an ideal gas, and start in a distribution $d$ (not in equilibrium) at time $t$ where probability mass concentrates on states with all particles in a small area. The dynamics map, call it $U(t'-t)$, which maps the system's state to a new state at a later time $t'$, also induces a map on the distribution $d$ to a new distribution $d'$. Louville's theorem (incompressibility of phase space) states that the normalization constant will not change. This also means that the information entropy of the distribution at time $t'$ will be the same as at $t$. In this sense, systems **do not evolve towards a more entropic distribution over time**.

Instead, the idea of equilibrium statistical physics is that at time $t'$, we take as our macrostate the distribution $d^*$ with maximum-entropy for the parameters (temperature, volume, etc).

The second law of thermodynamics considers a situation where at time $t$ we have an equilibrium distribution $d$, and asks about the entropy at a later time, *given that parameters like volume and pressure are also being changed*. In general, $d'$ is still well defined, but by definition, it will have less entropy than $d^*$.

We can now consider time evolution while also changing one of these parameters. For example, suppose we vary the Hamiltonian. However, we ensure that the process is adiabatic. In this case, the entropy of the pushforward distribution under the dynamics, at time $t'$ is still well defined, and by Louville's theorem still the same as the initial entropy, but by definition, will be less than the equilibrium distribution at $t'$ (since that is a maximum entropy distribution). This is the second law of thermodynamics. 

More succinctly: $dS \geq 0$. It is only equal when the process from the initial distribution to the final one lies on the maximum entropy submanifold (i.e., the process is quasistatic).

#### Consequences of second law

Consider a process running on a system that has two separate parts, one hotter, one colder. Let $Q_H$ be the heat taken from the hot body by the process, and let $Q_C$ be the heat given to the cool body. Then the efficiency $\eta$ is:

$$\eta := \frac{W}{Q_H} = \frac{Q_H-Q_C}{Q_H} = 1 - \frac{Q_C}{Q_H} $$

By the second law, the heat given to the cool body and the heat taken from the hot body are positive, so $\eta < 1$. 

Another consequence is that a reversible engine has the best efficiency. To see this, suppose we have a process $\tau$ which takes heat from the hot to the cool body, and gives its work to a reversible engine $R(\pi)$ running in reverse. Let $Q_H$ and $Q_C$ be as before, for system $\tau$, and $Q'_H, Q'_C$ be the heat *given* to the hot bath and taken from the cold bath respectively by $R(\pi)$. 

By the second law, considering the two processes as a single process, $Q_H \gt Q'_H $, since otherwise heat would be flowing into the hot body at no work cost (all the work transfer is internal to the joint system, not to anywhere else). Also, we have that $Q_H-Q'_H = Q_C-Q'_C$. But then:

$$\eta(\tau) = 1 - \frac{Q_C}{Q_H} = 1 - \frac{Q_H-Q'_H+Q'_C}{Q_H} = \frac{Q'_H-Q'_C}{Q_H} \leq \frac{Q'_H-Q'_C}{Q'_H} = \eta(R(\pi))  $$

Further, any two reversible engines are equally efficient, *when both operating between the same pair of heat baths*, by the above argument applied in both directions. Note that efficiency is a function of the temperatures of the two heat baths, $\eta(T_1,T_2)$.


### Temperature

Consider a system of two parts with fixed volume, such that $S \approx S_1 + S+2$, is that $0 \leq dS = dS_1 + dS_2 = \frac{dS_1}{dE}dE_1 + \frac{dS_2}{dE}dE_2 = \frac{dS_1}{dE}dE_1 - \frac{dS_2}{dE}dE_1 = (\frac{1}{T_1} - \frac{1}{T_2})dE_1$.

This implies that if $T_1 > T_2$, then $dE_1 > 0$, and if $T_1 < T_2$, then $dE_1 < 0$. In other words, energy change (here heat change) is from the hotter system to the colder system. This confirms that $T$ corresponds to the intuitive notion of temperature.

One can make the same argument for pressure.

<!-- This is a straightforward consequence of the principle of maximum entropy: the Gibbs entropy $\rho$ remains constant over time, by Louiville's theorem, but the equilibrium distribution is the maximum entropy distribution with the relevant constraint (expected energy), so must have greater or equal entropy to the Gibbs entropy.  -->




### An effective theory: thermodynamics

We can imagine an effective theory in which macrostates are actually physical states, and temperature is a physical variable. In this scenario, heat is a fluid which flows from hot systems to cooler ones. 

!!! History

    This is how thermodynamics was first conceptualized, without an understanding that the theory was only an effective description.

### Free energy

$F \propto \log Z$. It satisfies $F = \langle H \rangle - TS$, so that at high temperature, it is maximized by maximizing entropy, and at low temperature, by minimizing energy. 



## Non-equilibrium statistical physics

Here, we want to consider also the evolution of the system towards equilibrium over time, so our belief distributions are over full paths of the system over time.

### Brownian motion

Suppose we have an SDE:

$$
\frac{d}{dt}
\begin{bmatrix}
x \\
v
\end{bmatrix} = \begin{bmatrix}
v \\
\frac{-v}{\tau} + \frac{\xi(t)}{m}
\end{bmatrix}
$$

The first term in the change in velocity is frictional (i.e. proportional to velocity), while the second is a random force $\xi$ drawn from some stationary distribution over functions $\R \to \R$, with $E[\xi](t) = 0$ and $c(t) := E[\xi(0)\xi(t)]$ decays to $0$ at a time scale $\tau_\alpha << \tau$.

!!! Note 

    Looking at dimensions, we see that $\tau$ is a timescale, i.e. has dimensions of time.

We may now ask about if and how this system approaches equilibrium, which mathematically means: what is the time-invariant fixed point of the flow of the marginal probability of $v(t)$.

This gives 

$$
v(t) = v_0e^{-t/\tau}+\frac{1}{m}\int_0^te^{-(t-t')/\tau}\xi(t')dt'
$$

so we see that $E[v](t) = v_0e^{-t/\tau}$ and that 

$$
E(v(t_1)v(t_2)) = v_0^2e^{-t_1/\tau}e^{-t_2/\tau}\\ + \frac{1}{m^2}\int_0^{t_1}dt'e^{-(t-t')/\tau}\int_0^{t_2}dt''e^{-(t_2-t'')/\tau}c(t''-t')
$$

and then using the fast decay of $c(t)$ to evaluate the inner integral, by taking $c$ a positive constant $\int c(s)ds$ only at $t''=t'$, we can obtain:

$$
E(v(t_1)v(t_2)) = (v^2_0 - D/\tau)e^{-(t_1+t_2)/\tau} + \frac{D}{\tau}e^{-(t_2-t_1)/\tau}
$$

for $D := \frac{\tau^2}{2m^2}\int c(s)ds$.

This form reveals several things:

- since at equilibrium the correlation function can only depend on time difference, we see the process equilibrates at large $t$
- but this analysis of the approach to equilibrium also holds if the initial velocity $v_0$ is draw from the equilibrium distribution itself, in which case $t_1$ and $t_2$ can be arbitrarily small. In that case, $v_0^2=D/\tau$.
- by equipartition, we also know that $mv^2_0/2 = k_bT/2$, so $mk_BT/\tau = \int_0^\infty E(\xi(0)\xi(t))dt$. This relates dissipation ($\tau$) and fluctuation ($\xi$).
- the *diffusion constant* D measures the rate of change of variance: it has dimensions $L^2T^{-1}$ accordingly

## Phase transitions

Thermodynamic states live on the information manifold, and observables (functions from the manifold to $\R$) can be measured experimentally.

For systems that have a size $N$, when $N$ tends to infinity, we often see non-analytic behavior of observables as we move on the manifold, and the points at which cusps or discontinuities appear are known as phase transitions.

### The Ising Model

This is the physicist's name for a Markov Random Field on a rectangular graph with Bernoulli variables. Solvable in 1D and 2D. It is important because it is a simple model which displays a phase transition.

In the language of physics, each Bernoulli variable is called a spin, and the graph is called a lattice. Spins take values $1$ and $-1$, instead of $0$ and $1$. The partition function is written:

$$
Z(\beta) = \sum_s e^{\beta \sum_{\langle i, j \rangle}s_is_j}
$$

where $\sum \langle i, j \rangle$ ranges over neighbouring spins, and $\sum_s$ ranges over all $2^N$ configurations (where $N$ is the number of variables). 

We can now consider the information manifold, parameterized by $\beta$. For each point on the manifold (i.e. each distribution), we calculate a quantity $E_\beta[m]$, for $m(s)=\frac{1}{N}|\sum_i s_i|$. Note the absolute value. 

For large $\beta$, the distribution is dominated by two states, where all spins are up, and where all spins are down. In either case, we have $m(s)=1$, so that $E_\beta[m]=1$. However, as we increase the temperature, states such as the "chessboard" (alternating up and down spins) gain non-zero probability, and since these have $m(s)=0$, we see $E_\beta[m]$ decrease.

At small $\beta$, all states have the same probability, and there are many more states with $m(s)=0$, so that $E_\beta[m] \to 0$. What is remarkable about the Ising model is that for large $N$, the value of $\beta$ for which $E_\beta[m]=0$ for the first time tends towards a finite value.

This implies a non-analyticity of the function $\beta \mapsto E_\beta[m]$ (it is always a fixed value, $0$, after a certain point $\beta^*$, but $>0$ before, and this is not possible for an analytic function - there's a kink in the graph), and this is the characterizing property of the Ising model phase transition.

$\beta^*$ is known as the critical point. As usual, we define $T:=\frac{1}{\beta}$ as the temperature. Near the critical temperature, we find power law behavior, so for $t := (T-T_c)/T_c$:

$$
C_v := \frac{\partial U}{\partial T} \sim |t|^{-\alpha} \\ \quad \\
m \sim |t|^\beta \quad\quad  (t \to 0^-) \\ \quad \\
\chi := \frac{\partial m}{\partial h} \sim |t|^{-\gamma} \\ \quad \\
$$

for $\alpha, \beta, \gamma$ irrational constants that appear in a wide variety of models said to be in the same *universality class* as the Ising model.

### Mean-field theories

(Mean-field) [variational inference]() on the Ising model works as follows. As normal, we consider the manifold of identical independent distributions on the space (so $q_H(s) = \Pi_iq_H(s_i)$), with $H$ the parameter, so that $q_H(s_i) \propto e^{-\beta Hs_i}$.

We then vary $H$ to maximize the lower bound on $L \leq \log Z$:

$$
L(H) := \sum_x q_H(x)\log\frac{q_H(x)}{\hat{p}(x)}
$$

We now exploit our mean field assumption:

$L(H) = E_{s\sim q_H}[\log q_H] - E_{s\sim q_H}[\log \hat p] = E_{s\sim q_H}[-\beta H \sum_is_i - \log Z_H] - E_{s\sim q_H}[-\beta J \sum_{\langle i,j\rangle}s_is_j] = -\beta H NE[s_1] - \log Z_H + \beta J N\frac{1}{2}zE[s_1]^2$

So that (at the minimum), now exploiting the properties of the derivative of the normalizing constant of the exponential family: $0 = \frac{d}{dH}L(H) = -\beta NE[s_1] -\beta H N\frac{d}{dH}E[s_1] - \frac{1}{Z_H}\frac{d}{dH}Z_H + \beta J NzE[s_1]\frac{d}{dH}E[s_1] = -\beta H N + \beta J NzE[s_1]$ 

$$
\Rightarrow H = JzE_{s\sim q_H}[s_1]
$$


This is sufficient to determine the *effective "mean" field* $H$, by finding a value of $m := E[s_1] = \tanh(\beta H) = \tanh(\beta JzE[s_1])$ that is self-consistent. Physicists often give a confusing justification for this choice of the $H$ to do with eliminating fluctuations, but the above is clearer: we are introducing a simplifying constraint (namely, independence) and choosing the best distribution under those circumstances.

#### Exact solution of 2D Ising model


The fact that there is an exact solution to the 2D Ising model is valuable because it proves that the model exhibits phase transitions, and allows the calculation of critical exponents (against which approximate techniques can be compared). 

Actually understanding the exact solution(s) is also valuable, since it involves fundamental ideas in statistical field theory. 

Let $N$ be the length of a side of the grid.

**The transfer matrix method**

This method is quite algebraic. We begin by expressing the normalization constant (aka partition function) $Z$ as the normalization constant of a *quantum* system, i.e. as $Tr(e^{-\beta H})$ where $A^n = e^{-\beta H}$ is known as the *transfer matrix* (with $n$ the length of the lattice). We then use standard techniques of many-body quantum physics.

To arrive at the desired form, we first consider a lattice of width $N$ and height $1$. We can view a configuration of this lattice as a basis element of a Hilbert space $\bigotimes_i^N \mathbb{C}^2$. Concretely, let $|s\rangle = |s_1\ldots s_n\rangle$ by an eigenvector of $\sigma_3(i) := I_1 \otimes \ldots \otimes I_{i-1} \otimes \sigma_3 \otimes \ldots I$, so that $\sigma_3(i)|s\rangle = s_i|s\rangle$. In other words, the state of the lattice at site $i$ is specified by the eigenvalue of $\sigma_3(i)$.

Then for a function $b(K)$ (to be determined below), define:

$$
V_1 := \frac{e^{\sum_i^N b(K)\sigma_1(i)}}{\cosh^N b(K)} \\
\quad \quad \quad \\
V_3 := e^{\sum_i K\sigma_3(i)\sigma_3(i+1)}
$$

so that we have:

$$
\langle s' | V_1V_3 | s \rangle \\
= \langle s' | V_1| s \rangle e^{\sum_i Ks_is_{i+1}} \\
= \prod_i^N\langle s_i' | \frac{e^{\sigma_1(i)}}{\cosh b(K)}| s_i \rangle e^{\sum_i Ks_is_{i+1}}
$$

$$
= \prod_i\langle s_i' | \frac{\cosh b(K) I + \sinh b(K)\sigma(i)}{\cosh b(K)}| s_i \rangle e^{\sum_i Ks_is_{i+1}}
$$

$$
= \prod_i\langle s_i' | I + \tanh b(K)\sigma(i)| s_i \rangle e^{\sum_i Ks_is_{i+1}}
$$

$$
= (\delta_{s_i, s'_i} + \delta_{s_i, -s'_i}\tanh b(K))e^{\sum_i Ks_is_{i+1}}
$$

so that with $b(K) = \tanh^{-1}(e^{-2K})$, we recover the energy of the Ising model.

!!! Note

    $b$ is an involution, and in fact represents the *Kramers–Wannier* duality : distributions parametrized by $K$ and by $b(K)$ on the manifold are (up to some factors) the same. 

That makes $V_3V_1$ function as a transfer matrix, in the sense that $Tr((V_3V_1)^2) = \sum_s \sum_s' \langle s | V_3V_1 |s'\rangle \langle s' | V_3V_1 | s \rangle$ is a sum over all states of the Ising model for height $3$ and so on for higher $n$.

Note that our partition function is then also a time evolution of a quantum system.

Calculating $Tr(V_3V_1)$ is difficult and requires us to rewrite the Pauli matrices as Majorana fermions (fermions following a Clifford algebra). After this, diagonalization is straightforward.

**Under construction**

### Critical exponents

For a function $f$, we write 

$$
f(x) \sim x^\alpha
$$

to mean 

$$
\alpha = \lim_{x\to 0} \frac{\log|f(x)|}{\log|x|}
$$

These are the conventions:

$$
c \sim t^{-\alpha}
$$

$$
m \sim t^{\beta} \sim B^{\frac{1}{\delta}}
$$

$$
\chi \sim t^{-\gamma}
$$

$$
\xi \sim t^{-\nu}
$$

<!-- 
$$
F[(T)\phi] = \int d^dx \frac{1}{2}\alpha_2(T)\phi^2 + \frac{1}{4}\alpha_4(T)\phi^4 + \frac{1}{2}\gamma(T)(\nabla\phi)^2
$$

First consider $\alpha_4=0$. Then when $\alpha_2 > 0$, taking functional derivative and solving the Helmholtz equation gives 

Define $\xi^2 = \gamma/\mu^2$. From this, we can calculate the normal facts like $\langle \phi(x)\phi(0)\rangle \sim \frac{e^{-r/\xi}}{r^{(d-1)/2}}$ in the $r >> \xi$ regime. Further, since $\mu^2 \sim t$, we have $\xi \sim t^{-\nu}=t^{-\frac{1}{2}}$ -->


## Renormalization

Suppose you have some field, for instance the discrete field $s : \Z \to C$ for some $C$. This is a (1D) lattice with a value at each site. There is a natural projection map $\pi$ which drops the even sites, to obtain a new lattice which can be expressed as a new field $s' : \Z \to C$. It is as if we have zoomed out by a factor of 2.

This projection map $\pi$ induces a map on distributions over configurations of the field, so a map $f : I(M) \to I(M)$, where $I(M)$ is the space of distributions over functions $\Z \to C$.

A key insight is that fixed points of $f$ are critical points of phase transitions. Methods for discrete fields and continuous fields, in real and Fourier space exist.

<!-- The simplest example would be the Central Limit Theorem, where $M$ is $\R$ (for example), and we have the function $\lambda x \mapsto x+x$, which one can think of as a scale transformation where we squash the real line to half its size. The operation on PDFs is $f \mapsto (f * f) / 2$, that is, by the sum (or in fact, the mean) of a distribution with itself, and the fixed point is the Gaussian distribution. Note that this endomorphism can be seen as a scale transformation of discrete random (which are nothing but sums of variables), and so works on absolutely any distribution over a given space. -->

### Real space, discrete (Migdal-Kadanoff)

The simplest example of renormalization is illustrated with the 1D Ising model. Recall that the Ising model (aka Markov Random Field) has the form $p({s}) = e^{\sum_{\langle i,j\rangle}Ks_is_j}$. Call $I_{MRF}$ the space of distributions on the 1D lattice, parametrized by the choice of $K$, so that $Z(K)$ denotes a particular such distribution.

We are interested in some expectation, e.g. $G(k, K) := \langle x_0x_k\rangle_K$. We then make three key observations:

- marginalization shouldn't affect the result, in the sense that $G(32)$ could be calculate directly, or calculated after marginalizing out the odd sites
- the model we obtain after marginalizing out the odd sites lives on the same manifold $I_{MRF}$ (if we assume the lattice is infinitely large), so is $Z(f(K))$, for some $f$. (Intuitively, the conditional independence structure of the model makes this clear: once we marginalize out sites $1$ and $3$, sites $0$ and $2$ will be dependent, but $0$ and $4$ will be conditionally independent given $2$.)
- this act of marginalization therefore gives us a flow $f$ on the manifold, and it will turn out that the fixed points are the critical points, i.e. where phase transitions happen.

Here are the details. The new model is given by:

$$
\sum_{s_{even}}\sum_{s_1}e^{Ks_1(s_0+s_2)}\sum_{s_3}e^{Ks_3(s_2+s_4)}\ldots
$$

We observe that $\sum_{s_1 \in \{1,-1\}}e^{Ks_1(s_0+s_2)}$ is a function of $s_0$ and $s_2$ which is invariant under $s_0 \mapsto -s_0, \quad s_2 \mapsto -s_2$, and since $s_i^2=1$, we obtain: $\sum_{s_1 \in \{1,-1\}}e^{Ks_1(s_0+s_2)} = e^{f(K)s_0s_2 + C}$

We then get an equation for each choice of values for $s_0$ and $s_2$. In particular:

$$
2\cosh(K(1 + 1)) = e^{f(K) + C}
$$

$$
2\cosh(K(1 - 1)) = e^{-f(K) + C}
$$

These can jointly be solved by $e^{f(K)} = \sqrt{\cosh(2K)}$ and $e^{C}=2\sqrt{\cosh(2K)}$, so $\tanh f(K) = \tanh^2 K$.

As regards $G$, note that then $G(2n, K)= G(n, f(K))$, so that for $G(n, K) = e^{-n/\xi(K)}$, we get:

$$
e^{-2n/\xi(K)} = e^{-n/\xi(f(K))} \Rightarrow \xi(K) = 2\xi(f(K))
$$

This real-space approach to renormalization isn't particularly general; in the 2D Ising model for example, decimation introduces more complex relationships between variables, so the information manifold is no longer 1D, and instead we have terms $K_1s_is_j, K_2s_is_js_ks_l$, and others.

### Real space, continuous

!!! Note

    Most references aren't very clear on the fact that the space of distributions is a function of $\Lambda$, and don't mention that we are performing a change of variables in the infinite-dimensional measure $D\phi$, but without making these points explicit, the logic of renormalization is difficult to follow.

Our setting here is distributions over fields, i.e distributions over functions of space. Without (much) loss of generality, we consider distributions of the form:

$$
p(\phi) \propto e^{-F(\phi)}
$$

where $F$ is local. For example, we could have $F=\int dx \phi(x)^2$ or $\int dx a_1\phi^n + a_2\nabla^n\phi^m\ldots$. The coefficients $a_i$ fully determine $F$, so we can write a distribution as $\rho(a)$. 

We also want to specify the support of the distribution, in particular the band of frequencies allowed for a field in the support of the distribution. Call the maximum frequency $\Lambda$ and write $\rho(a, \Lambda)$ for a given distribution. Write $Z(a, \Lambda) := Z(\rho(a, \Lambda)) := \int (D\phi) \rho(a, \Lambda)(\phi)$.

Note that fixing $\Lambda$ specifies an information manifold of distributions $\rho(\_, \Lambda)$ for which $a$ are coordinates.


Our interest is in marginalizing out high frequencies (i.e. low length scales), to obtain a distribution $Z(a'_i, \Lambda/b)$, and then rescaling back to the original support, to get  a distribution $Z(T(b)(a)_i, \Lambda)$, where the goal is to find $T(b)$.

More concretely, let $f_{\Lambda}(\phi)$ be a function which filters out frequencies above some $\Lambda$, so that the pushforward $Z(a'_i, \Lambda) = f_{\Lambda/b}\rho(a, \Lambda)$ is a distribution over fields with frequencies below $\Lambda$. We then marginalize (i.e. pushforward by this map), to obtain a distribution $(f_{\Lambda/b}^*\rho(a, \Lambda)) \propto \int_{[\Lambda/b, \Lambda]}\rho(a, \Lambda)$.

<!-- 
Working in Fourier space, with $\Lambda$ the reciprocal of the minimum grid spacing, $\Lambda' = \Lambda/b$ for some $\zeta \in [1, \infty)$, and $F[\phi] = F_0[\phi^-]+F_0[\phi^+] + F_I[\phi^-,\phi^+]$, where $\phi^\pm$ are the parts of $\phi$ composed of frequencies above/below $\Lambda'$, we define: -->
<!-- 
To this end:

$$
% e^{-F'[\phi^-]} := e^{F_0[\phi^-_k]}\int\prod_{\Lambda' < k < \Lambda}d\phi_k^+e^{F_0[\phi^+_k]}e^{F_I[\phi^-_k, \phi^+_k]}
e^{-F'[\phi^-]} := e^{F_0[\phi^-]}\int D\phi^+e^{F_0[\phi^+]}e^{F_I[\phi^-, \phi^+]}
$$

so that

$$Z = \int D\phi^- e^{F_0[\phi^-]}\int D\phi^+e^{F_0[\phi^+]}e^{F_I[\phi^-, \phi^+]} \\ \quad \\
:= \int D\phi^-e^{-F'[\phi^-]}
$$
-->

This procedure is parametrized by $b \in [1,\infty)$, and each $a$ describes a point on the information manifold over fields, so what we have is a flow on the manifold. Certain fixed points of the flow correspond to critical points (i.e. points of phase transition), therefore our interest is in these points and their stability (i.e. the local linearization of the flow around these points).

#### Gaussian example

$$
Z(m, \Lambda) = \int_\Lambda D\phi \quad e^{-F_m(\phi)}
$$

$$
F_m(\phi) = \int \nabla_x\phi(x)\cdot \nabla_x\phi(x) + m\phi(x)^2dx
$$

where the maximum frequency for functions $\phi$ ranged over by the measure $D\phi$ is $\Lambda$.

<!-- We then write:

$$
Z(m, \Lambda/b) = \int_{\Lambda/b}D\phi e^{-F_m(\phi)} = \int_{\Lambda}D\phi e^{-F_m'(\phi)}
$$

The challenge is to solve for $F'$, i.e. to find a relationship $F'_m(\phi) = F_{m(b)}(f \circ \phi \circ g)$, where $f$ and $g$ are scaling functions of the form $x \mapsto cx$ (different $c$ for $f$ and $g$). -->

In this case, we begin by marginalizing out frequencies above $\Lambda/b$, to obtain a distribution $Z(m', \Lambda)$.

<!-- $Z(m, \Lambda) = \int_{\Lambda/b}D\phi e^{-F_m(\phi)} = \int_{\Lambda}D\phi e^{-F_{m(b)}(f \circ \phi \circ g)} = K\int_{\Lambda/b}D\phi e^{-F_{m(b)}(\phi)} = K Z(m(b), \Lambda/b)$, where $K$ comes from the change of measure $D(f \circ \phi \circ g) = K D\phi$. -->


<!-- In the Gaussian case, we see that -->

<!-- $$
\int_{\Lambda}D\phi e^{-F_m'(\phi)} 
= Z(m, \Lambda/b) 
$$ -->


$$ 
Z(f_{\Lambda/b}^*(\rho(m,\Lambda))) = \int_{\Lambda/b} D\phi^- e^{F_m[\phi^-]}\int_{[\Lambda/b, \Lambda]} D\phi^+e^{F_m[\phi^+]}$$

$$
= \mathcal{N}\int_{\Lambda/b} D\phi e^{F_m[\phi]} = \mathcal{N}Z(m, \Lambda/b)
$$

for a constant $\mathcal{N}$. This shows that in this case, $m'=m$. We now need to pushforward the distribution by a map $g_w(\phi) = (x \mapsto xb^w) \circ \phi \circ (x \mapsto xb)$, for $w$ to be determined shortly, which scales the fields in the support. Note that the initial multiplication by $b$ in real space amounts to a division by $b$ in Fourier space, so that the support will contain functions that take frequencies up to $\Lambda$.

<!-- $$\phi(x) = b^{(2-d)/2}\phi'(x/b)$$ -->

To determine $w$, observe that:

$$
F_m(\phi) = \int \nabla_{x'b}\cdot \nabla_{x'b}\phi(x'b) + m\phi(x'b)^2d(x'b)$$ 

$$
= \int \nabla_{x'}f(\phi)(x')\cdot \nabla_{x'}f(\phi)(x') + mb^{2}f(\phi)(x')^2dx' = F_{m'}(f(\phi))
$$

where $\phi(x'b) = \phi(x) = b^{(2-d)/2}f(\phi)(x/b)$ and $m' = mb^2$, so that $w = \frac{d-2}{2}$.

This means that $Z(g_w^*(f^*_{\Lambda/b}(\rho(m, \Lambda)))) \propto \int_\Lambda D(f(\phi))e^{-F_{m'}(\phi)} = Z(\rho(m', \Lambda))$,

so that

$$
Z(m, \Lambda/b) = K Z(m(b), \Lambda)
$$

Note here that in changing variables from $D\phi$ to $D(g_w(\phi))$, we move from $\Lambda/b$ to $\Lambda$, as desired. Note also that the change of measure from $D\phi$ should incur a Jacobian determinant, and without going into the theory of functional determinants, let us assume that this is a constant $K$.

Since we are eventually concerned with derivatives of $\log Z$ (which are the expectations of interest), the constant $K$ is irrelevant. In this case, we find a fixed point for $m = 0$ or $m = \infty$.

In the more general case, things are much harder. This is because we can no longer trivially marginalize out the high frequencies, and instead have to resort to peturbative methods, e.g. via Feynman diagrams. However, calculations of this sort have been extremely important both in statistical physics and quantum field theory.

<!-- 
$$
e^{-F'[\phi^-]} = e^{F_0[\phi^-]}\int D\phi^+e^{F_0[\phi^+]} = \mathcal{N}e^{-F[\phi^-]}
$$

We then rescale, with $x' = x/ b$ or $k' = kb$:

$$
F'(\phi^-) \propto F_m(\phi^-) = \frac{1}{2}\int (\nabla_x\phi^-(x))^2 + m^2\phi^-(x)^2d^dx \\ \quad \\ 
$$

$$
= \frac{1}{2(2\pi)^d}\int^{\Lambda/ b} (k^2 + m^2)\phi_k^-\phi_{-k}^- d^dk \\ \quad \\
$$

$$
= \frac{1}{2(2\pi)^d}\int^{\Lambda} ((\frac{k'}{ b})^2 + m^2) b^{2w}\phi_{k'}'\phi_{-k'}' d^dk' \frac{1}{ b^d} \\ \quad \\
$$

with $w = \frac{2+d}{2}$ and $\phi'_{k'} = b^{-w}\phi^-_k$, so that:

$$
F'(\phi^-) \propto \frac{1}{2(2\pi)^d}\int^{\Lambda} (k^2 +  b^2m^2)\phi_k\phi_{-k} d^dk \\ \quad \\
$$

which means that renormalization has induced a change of $m^2 \mapsto  b^2m^2$, which gives us a fixed point at $\mu^2 = 0$ or $\mu^2=\infty$. The first is the Gaussian fixed point. This is more or less the central limit theorem.

Note that $F_I = 0$ in this case, so all we have to do is rescale to $x' = x/b$.



We first note 

We then do a change of variable of the *outer* integral $D\phi$ to $D\phi'$, which incurs a factor of the determinant of the transformation. This is constant in $m$, so $\log Z$ only changes by a constant term. -->




## Landau theory

!!! References

    [David Tong's notes](https://www.damtp.cam.ac.uk/user/tong/sft/one.pdf) are good as usual. Other resources often poorly motivate why the free energy can be viewed as a function of $m$, which is both subtle and necessary to understand.

!!! Note

    It is expedient to use the Ising model as a running example, although Landau theory is a general technique.

The idea is to obtain the bifurcation diagram of a phase transition qualitatively (i.e. topologically correct) without computing the partition function explicitly.

Concretely, what we want to obtain is:

![](../img/ising.png)


First, a definition: $F(m, T) := -T\log \sum_{s|m}e^{-\frac{1}{T} H(s)}$, where $\sum_{s|m}$ means the sum ranging over all configurations $s$ with $\frac{1}{N}\sum_i s_i = m$.  Then:

$$
Z(T) = \sum_m\sum_{s | m} e^{-\beta H(s)} := \sum_m e^{-\beta F(m, T)} \approx \int dm e^{-\beta F(m, T)}
$$

In the case that the final integral is dominated by the minimum $m^*$, we get $Z(T) \approx e^{-\beta F(m^*, T)}$, so that $F$ is, as suggested by the name, the equilibrium free energy.

Actually calculating $F$ as defined here is usually intractable, but we can still make progress. 

We first observe from the definition above that $F$ has to respect certain symmetries. For the Ising model, $F(m, T)=F(-m, T)$, as seen from the definition and the symmetry of the Hamiltonian. Further, we expect it to be analytic in $m$, at least for a finite sum, so that in an expansion around the minimum (dropping the constant term):

$$
F(m,T)  \approx r_0(T)m^2 + r_1(T)m^4
$$

The key fact is then that **we know $m^*$ must be $0$ above the critical temperature**. 

But observe that the bifurcation diagram of the above polynomial (i.e. plotting the minimum $m^*$ of $F(m, T)$ as a function of $T$) shows two non-zero minima appearing precisely when $r_0(T) \geq 0$. So we can deduce $r_0(T) = a(T-T_c)$, at least close to $T_c$.

<!-- 

In the Ising model, position is discrete, and the value at each position is boolean. So the state is a function $m_d : \Z \times Z \to \{-1,1\}$. If we generalize to $m_c : \R \times \R \to \R$, we can use more interesting methods. We can obtain $m_c$ as the average of $m_d$ in a ball around any point.

First write $Z(T) = \int Dm e^{-\frac{1}{T}\int g(m(x))dx} := \int Dm e^{-G(m,T)}$, where $Dm$ indicates an integral over all functions $m$. -->


<!-- Assume the exponent is dominated by constant functions, then in particular the constant function  $\lambda x : m^*$ will dominate, where $m^*$ is the minimum of $g$, so that $Z(T) = e^{-Vf(T)} = e^{-G(m^*)}$, so that $f(T) = G(m^*,T)$. -->

<!-- We now observe that $G$ is analytic (finite sum of exponentials) and even. So, neglecting constant terms, and in the vicinity of $m^*$: -->


Since $m^*$ is minimal: $0 = 2r_0(T)m^* + 4r_1(T)m^{*3} \Rightarrow m^*(T) = \pm \sqrt{\frac{2|r_0(T)|}{4u_0(T)}}$.

### Landau-Ginzburg

We can generalize the above to a field. Let $m : \R\times\R \to \R$, and write as above:

$$
Z(T) = \sum_m\sum_{s | m} e^{-\beta H(s)} := \sum_m e^{-\beta F(m, T)} \approx \int dm e^{-\beta F(m, T)}
$$

However now $m$ is a function, so the final integral ranges over functions.

The simplest case is 

$$
F(m) = \int d^nx (\nabla m)^2(x) + \mu^2m^2(x)
$$

For which $p(m)\propto e^{-F(m)}$ is a (infinite dimensional) Gaussian. At and above criticality, we observe that for all $x$, the marginal distribution $m(x)$ must be $0$, so at $T=T_c$, $\mu=0$. 
<!-- Note that if $F$ were interpreted as the Lagrangian of a QFT, excitations would be massless. -->


## Linear Response Theory

The following assumes the basics of statistical mechanics (see notes). Suppose we have a system whose Hamiltonian is $H$ and we perturb it to $H_T = H - K(t)A(p,q)$. We then want to calculate the resulting change in expectation $\Delta B(t) = E_{H_T}[B(t)] - E_{H}[B(t)]$.

Ostensibly, this would require knowing the (time varying) distribution of the system resulting from the perturbation, but we can get what we want by exploiting the a quite general form of the fluctuation-dissipation theorem. The critical assumption is that this applies in the limit of $K$ small:

$$ \Delta B(t) = \beta E_H[\dot{A}(0)B(t)] * K(t) $$

The expected perturbation is the output of a linear system with input $K$ and a kernel representing the correlation of the change of input variable and the output variable, under the original system. So you can predict the response to a small perturbation of the system just by seeing the behavior of the system without the perturbation.

## Magnetic field and chemical potential

There is a relationship between magnetic fields and chemical potentials.

For example, $H(n) = -J\sum_{\langle i,j \rangle}n_in_j$ would be a reasonable Hamiltonian for a lattice gas with no double occupation. If we assume that particles and energy can be exchanged with the bath (grand canonical ensemble) so that only mean energy and particle number is known, our distribution is:

$$
p(n) \propto e^{-\beta(J\sum_{\langle i,j \rangle}n_in_j + \mu \sum_in_i)}
$$

But with the Ising model, we instead have $H(s) = -J\sum_{\langle i,j \rangle}s_is_j - B\sum_is_i$. Only energy is exchanged (nothing moves), so our distribution is:

$$
p(s) \propto e^{-\beta (J\sum_{\langle i,j \rangle}s_is_j + B\sum_is_i)}
$$

This is the same distribution, with a different interpretation. It suggests that to model a sort of thing with fixed number in a field (e.g. spins) is the same as modeling things with no fixed number without a field. 

## Spontaneous symmetry breaking


To say that the Ising model has a spontaneously broken symmetry is to say that in the limit

$$
\lim_{b\to 0}\lim_{N \to \infty} m(b,N, T=0) \neq 0
$$

That is, in the limit of an infinitely large system ($N \to \infty$) and $0$ temperature, an arbitrarily small magnetic field $b$ will make the system choose either the all-spins-up or the all-spins-down state.

More generally, spontaneous symmetry breaking involves a system with a symmetry of the Hamiltonian that exhibits this kind of arbitrary sensitivity to perturbation, expressed by a non-commuting limit.

## Examples of systems

There are a few systems which are ubiquitous in statistical physics, often because their thermodynamic properties can be calculated exactly, or because they exhibit interesting phenomena, like phase transitions.

Some principles these experiments demonstrate:

- it is usually possible to work in either the microcanonical or canonical ensemble, and derive the same results from either
- the equation of state (relationship between energy, entropy and volume) is often analytically derivable, and leads to experimentally testable predictions

### Classical ideal gas

Let $m$ be the mass of a single particle, and assume we have $N$ non-interacting particles trapped in a volume $V$. Let $U$ be the potential function, so that $U(q_i)=0$ if the particle is in the box, and $\infty$ otherwise.

#### Fixed energy (microcanonical)

First choose some value of $E$. Then:

$$N!h^{3N}\rho(p,q) = \frac{1}{\Omega(E)}$$

where 

$$\Omega(E) = \int_{E \leq H(p,q) \leq E + \Delta E}  dp_i\ldots dp_n,dq_i\ldots dq_n = \int_{E \leq \sum_i^{3N}\frac{p_i^2}{2m} + U(q_i) \leq E + \Delta E} dp_i\ldots dp_n,dq_i\ldots dq_n 
$$

$$ = \int_{\sum_i^{3N}\frac{p_i^2}{2m} + U(q_i) \leq E + \Delta E} dp_i\ldots dp_n,dq_i\ldots dq_n - \int_{\sum_i^{3N}\frac{p_i^2}{2m} + U(q_i) \leq E} dp_i\ldots dp_n,dq_i\ldots dq_n = \tilde{\Omega}(E+\Delta E) - \tilde{\Omega}(E)   
$$

where 

$$\tilde{\Omega}(J) = \int_{\sum_i^{3N}\frac{p_i^2}{2m} + U(q_i) \leq J} \frac{1}{\Omega(E)} dp_i\ldots dp_n,dq_i\ldots dq_n
$$ 

Note that 

$$\tilde{\Omega}(J) = V^N\cdot Vol(S_{3N,\sqrt{J}})$$

where the volume of the d-sphere with radius $R$ is
$Vol(S_{d,R})=\frac{\pi^{\frac{d}{2}}\sqrt{2mE}^{d}}{\Gamma(\frac{d}{2}+1)}$

Since $\Delta E$ is differentially small, we have:

$$ \frac{1}{\Delta E}N!h^{3N}\rho(p,q) =  \frac{\tilde{\Omega}(E+\Delta E) - \tilde{\Omega}(E) }{\Delta E} \to \tilde{\Omega}'(E)  $$

Then:

$$\tilde{\Omega}'(E) = \frac{d}{dE}V^N\frac{\pi^{\frac{3N}{2}}\sqrt{2mE}^{3N}}{\Gamma(\frac{3N}{2}+1)} = \frac{3N}{2}\cdot 2m\cdot V^N\frac{\pi^{\frac{3N}{2}}(2mE)^{\frac{3N}{2}-1}}{\Gamma(\frac{3N}{2}+1)}
$$

$$ 
= \frac{3N}{2E} \cdot V^N\frac{(2\pi mE)^{\frac{3N}{2}}}{\Gamma(\frac{3N}{2}+1)} = \frac{1}{E} \cdot V^N\frac{(2\pi mE)^{\frac{3N}{2}}}{\Gamma(\frac{3N}{2})} $$

And putting it all together:

$$ \rho(p,q) = \Delta E\frac{1}{EN!h^{3N}} \cdot V^N\frac{(2\pi mE)^{\frac{3N}{2}}}{\Gamma(\frac{3N}{2})} $$

#### Fixed temperature (canonical)

Since particles are independent, $Z=\frac{Z_i^N}{N!}$

$$Z_1(\beta) = \frac{1}{h^{3}} \int e^{-\beta H(p,q)} dp_i\ldots dp_n,dq_i\ldots dq_n = V^N\cdot \left(\int_{-\infty}^{\infty} e^{\frac{-\beta p_i^2}{2m}}\right)^{3}
$$

$$ 
= V\cdot\left(\frac{\sqrt{2\pi mT}}{h}\right)^3 = V\cdot\left(\frac{\sqrt{mT}}{\sqrt{2\pi}\hbar}\right)^3 = V\cdot\left(\frac{mT}{2\pi\hbar^2}\right)^{\frac{3}{2}} $$

Defining the thermal de-Broglie wavelength as:

$$\lambda = \left(\frac{2\pi\hbar^2}{mT}\right)^{\frac{1}{2}}$$

with dimensions, where $E=ML^2T^{−2}$, of $\left(E^2T^2M^{-1}E^{-1}\right)^{\frac{1}{2}} = \left(ML^2T^{−2}T^2M^{-1}\right)^{\frac{1}{2}}=L$ 


we then have:

$$ Z_i(\beta) = \frac{V}{\lambda^3}$$


$$ p = -\pd{A}{V} = -\pd{-T\log Z}{V} = NT\pd{}{V}\log V = \frac{NT}{V}$$

(This is the usually seen as $pV = Nk_BT$.)

$$ E = -\pd{\log Z}{\beta} = \frac{3}{2}NT$$

Then note that energy per particle is then $\frac{3}{2}T=\frac{\dot{q}^2}{2m}$, where $\dot{q}$ is the momentum of a single particle, so that $\sqrt{3Tm}=\dot{q}$

But recalling that $\lambda_{dB}=\frac{h}{p}$ is the de Broglie wavelength, we see why $\lambda$ is called the thermal de Broglie wavelength, since it is, up to a constant, the wavelength of the average particle.


#### Equation of state

The equation of state for the ideal gas is known as the Sackur-Tetrode formula. We can derive it as follows:

$$ S = -\pd{A}{T} = \pd{}{T} T\left(\log \left(\frac{V}{\lambda^3}\right)^N - \log N!\right) = \pd{}{T} T\left(\log \left(\frac{V}{\lambda^3}\right)^N - N\log N + N \right) = \pd{}{T} TN\left(\log \left(\frac{V}{\lambda^3}\right) - \log N + 1 \right)   $$

$$ = \pd{}{T} TN\left(\log \left(\frac{V}{N\lambda^3}\right) + 1 \right) $$

Now note that $\pd{}{T} N\left(\log \left(\frac{V}{N\lambda^3}\right) + 1 \right) = -N\pd{}{T}\log(\lambda^3)=-N\pd{}{T}\log\left(\frac{2\pi\hbar^2}{mT}\right)^{\frac{3}{2}}=\frac{3}{2}N$

so 

$$ S = \pd{}{T} TN\left(\log \left(\frac{V}{N\lambda^3}\right) + 1 \right) = N\left(\log \left(\frac{V}{N\lambda^3}\right) + \frac{5}{2} \right)  $$

### Quantum Harmonic Oscillator

The state space is $\mathbb{N}$, the natural numbers, with $E(n)=(n+\frac{1}{2})\hbar\omega$. Then:

$$Z = \sum_{n=0}^{\infty} e^{-\beta(n+\frac{1}{2})\hbar\omega} = e^{-\beta\frac{1}{2}\hbar\omega}\sum_{n=0}^{\infty} \left(e^{-\beta \hbar\omega}\right)^n =  e^{-\beta\frac{1}{2}\hbar\omega} \frac{1}{1- e^{-\beta \hbar\omega}} = \frac{1}{e^{\frac{\beta\hbar\omega}{2}}- e^{-\frac{\beta \hbar\omega}{2}}} $$

Proceeding in the normal fashion, we obtain as energy and heat capacity:

$$ E = \hbar\omega\left( \frac{1}{2} + \frac{1}{e^{\beta\hbar\omega}-1}  \right) $$

$$
C_v = \frac{\omega ^2 \hbar ^2
   e^{\frac{\omega  \hbar }{T}}}{T^2
   \left(e^{\frac{\omega  \hbar
   }{T}}-1\right)^2}
$$

At low $T$, we can see that $E$ becomes increasingly constant (in $T$), but at high $T$, becomes linear in $T$ (you need to consider the locally linear region near $\beta=0$, since otherwise we get division by $0$. This is the  thermodynamic behaviour predicted by the corresponding classical model.

Further note that $\omega = \sqrt{\frac{k}{m}}$, so similar remarks hold for oscillators with a strong spring constant, for example.  


**Note**: one example of a physically useful consequence of this: a gas of diatomic molecules should have vibrational energy from the molecules (which are harmonic oscillators), but if their spring constant is high enough relative to the temperature of the system, we can treat them as frozen. More generally, we get locking of certain degrees of freedom. This explains why macroscopic systems have lower energy than classical statistical mechanics predicts, and similarly the heat capacity of solids (lattices of harmonic oscillators) was overestimated classically. Another example is a vibrating string. If each complex exponential (harmonic oscillator) in its Fourier series had energy equal to the temperature, the total energy would be unbounded. We need instead to say that the high frequency oscillators have exponentially small temperature.

### A crystal

For simplicity, assume we have a 1D lattice (same ideas apply in 3D). The configuration of the lattice can be represented by a vector $\textbf{q}$, giving the displacement from equilibrium of each atom. Moreover assume periodic boundary conditions so that $q_{N+1}=q_N$. Kinetic energy is then straightforward, namely $\sum_i^N \frac{p_i^2}{2m}$. 

The problem is the potential, which could be enormously complex. What we can do is to consider the low temperature case, where displacements are small, and so a Taylor expansion is justified, with:

$$ U(q) \approx U(q_0) +\left(q-q_0\right)\left(\nabla U|_{q_0}\right) + \left(q-q_0\right)^T\left(\nabla^2U|_{q_0} \right)\left(q-q_0\right) $$

We can then diagonalize $H=\left(\nabla^2U|_{q_0} \right)$ to obtain a new formula for $N$ independent oscillators, which allows us to express the partition function as a sum of independent harmonic oscillators (either quantum or classical).

The next step is to approximate the sum by an integral, which requires us to provide a density $\sigma(\omega)d\omega$ over frequencies for our harmonic oscillators. Notice that this is a continuum approximation of the solid.

The Debye model provides one choice of $\sigma$.

The much simpler Einstein model of a solid, which qualitatively captures the fact that the heat capacity drops with temperature, is to treat a solid as a set of $3N$ harmonic oscillators, all sharing the same $\omega$. 


### Gas with quantized energy levels

([These lecture notes](https://ps.uci.edu/~cyu/p115A/LectureNotes/Lecture13/lecture13.pdf) were helpful here)

Suppose that we have $N$ particles, energy levels denoted $e(i)$, and number of particles per level denoted $R(n_i)$ (in a full state of the system $R$). Then $N=\sum_ie(i)R_n(i)$ in that state. Assume that temperature (and chemical potential) are fixed.

$$ \langle n_j \rangle = \frac{1}{\sum_R e^{-\beta\sum_ie(i)R(n_i)}}\sum_R R(n_j) e^{-\beta\sum_ie(i)R(n_i)} = -\frac{1}{\beta}\pd{}{e(j)}\log Z $$

Then under different assumptions we obtain different values of $Z$, and can proceed from there.

### With distinguishable particles (Maxwell-Boltzmann statistics)

If the particles are distinguishable, we have:

$$ \log Z = \log \xi^N = N \log \xi $$

where $\xi = \sum_ie^{-\beta e(i)}$

Then 

$$ \langle n_j \rangle = -\frac{1}{\beta}\pd{}{e(j)}\log Z = -\frac{1}{\beta}\pd{}{e(j)}N\log \sum_ie^{-\beta e(i)} = N \frac{e^{-\beta e(j)}}{\sum_ie^{-\beta e(i)}}   $$

### With indistinguishable bosons with no fixed number (Bose-Einstein statistics)

Here we have to use the Grand Canonical Ensemble, namely:

with $R(E) = \sum_ie(i)R(n_i)$ and $R(N) = \sum_i R(n_i)$:

$$\mathcal{Z} = \sum_R e^{-\beta (R(e) - \mu R(N) )} = \sum_R e^{-\beta (\sum_i e(i)R(n_i) - \mu R(n_i) )} = \sum_{n_1=0}^{\infty} e^{-\beta(e(1)-\mu)n_1}\cdot\sum_{n_2=0}^{\infty} e^{-\beta(e(2)-\mu)n_2}\ldots  $$

$$ = \frac{1}{1- e^{-\beta(e(1)-\mu)}}\cdot \frac{1}{1- e^{-\beta(e(2)-\mu)}}\ldots $$

So 

$$ \log \mathcal{Z} = -\sum_{r=1}^{\infty} \log(1 - e^{-\beta(e(1)-\mu)}) $$

and 

$$  \langle N \rangle = \frac{1}{\beta}\pd{}{\mu}\log \mathcal{Z} = \sum_{r=1}^{\infty} \frac{e^{-\beta(e(r)-\mu)}}{(1 - e^{-\beta(e(r)-\mu)})} = \sum_{r=1}^{\infty} \frac{1}{e^{\beta(e(r)-\mu)} - 1}   $$

Similarly: $\langle n_j \rangle = \frac{1}{e^{\beta(e(j)-\mu)} - 1}$


Note that since $\forall j: \langle n_j \rangle \gt 0$, we have $\forall j: E_j\gt \mu$. In particular, as $\mu$ approaches the lowest energy $E_0$, $\langle n_0 \rangle \to \infty$ and so almost all of the particles reside in the ground state. This is Bose-Einstein condensation, and leads to weird macroscopic effects of quantum behaviour.

### With indistinguishable fermions with no fixed number (Fermi-Dirac statistics)

Now assume the particles are Fermions. Proceeding in the same fashion, but summing $n_i$ up to $1$, not to infinity, in order to respect the Pauli exclusion principle for Fermions, we obtain:

$$ \langle n_j \rangle = \frac{1}{e^{\beta(e(j)-\mu)} + 1}  $$

This is a useful model of electron and hole density in semiconductors. Note that $\langle n_j \rangle \leq 1$, as we would want. 



### Two spin system

A state $s$ is an array of $N$ Booleans, and the energy is $E=\epsilon\cdot N_T(s)$, where $N_T(s)$ is the number that are true (or spin-up, if you prefer). 

Note that in this system, we have fixed number and volume, so don't have to worry about those.

#### Two Spin System: Microcanonical Ensemble

The microcanonical ensemble is binomial, and so the entropy is $0$ at $E(s)=N_T(s)\epsilon=0$.

Using [Stirling's approximation](/maths/probability), entropy at $E=\epsilon N_T$: 

$${N \choose N_T} = \log N! - \log N_T - \log (N-N_T)$$ 

$$
\approx N\log N - N - N_T\log N_T + N_T - (N-N_T)\log(N-N_T) + N - N_T
$$

Symbolically solving, to save effort, and working in units where $k_B=1$, we calculate $S(E)$ and $E$ in terms of $T$:

$$S = -\frac{E}{\epsilon}\log\frac{E}{\epsilon} + N\log N - (-\frac{E}{\epsilon} + N)\log(-\frac{E}{\epsilon} + N)$$

which forms roughly a semicircle when graphed ($S$ on y-axis, $E$ on x-axis). From this, we see that temperature is negative when $E \gt \frac{N_T}{2}$. Further, negative temperatures are hotter than positive ones, in the sense that heat flows from a system with negative temperature to a system with positive temperature. To see this, suppose we place system $1$ with positive temperature next to system $2$ with negative temperature. $dS \gt 0$, so 

$\frac{dS_1}{dE_1} = \frac{1}{T_1} \gt 0$ and $\frac{dS_2}{dE_2} = \frac{1}{T_2} \lt 0$

Then energy must be added to system $1$ to increase energy, and removed from system $2$.


#### Schottky anomaly

Inverting the equation for $S(E)$ to obtain $E(S)$, we see that:

$$E = \frac{N \epsilon}{e^{\frac{\epsilon}{T}} + 1}$$

Heat capacity is defined as:

$$C = \frac{dE}{dT}$$

Graphing this shows a non-monotonic curve. This non-monotonicity is known as the Schottky anomaly, anomalous relative to the monotonic heat capacity for many types of systems.

#### Two Spin System: Canonical Ensemble

We calculate:

$$Z = \frac{N\epsilon}{e^{\frac{\epsilon}{T}} + 1}$$

$$\langle E \rangle = \frac{N \epsilon}{e^{\frac{\epsilon}{T}} + 1}$$

Note that this agrees with the same result obtained from the microcanonical ensemble after a Legendre transform.


### Classical Harmonic Oscillator

#### Microcanonical ensemble

$1 = \int d^{6N}\mu \rho = C'\cdot A$, for $A=\int_{E \leq \sum_{i}^{3N}\frac{p_i^2}{2m}+\frac{kq_i^2}{2}\leq E+\delta E} dq_1...q_n,p_1...p_n$

To evaluate this integral, we can note that for $\tilde{\Omega}(E)=\int_{\sum_{i}^{3N}\frac{p_i^2}{2m}+\frac{kq_i^2}{2}\leq E} dq_1...q_n,p_1...p_n$, we have that $A=\tilde{\Omega}(E+\delta E)-\tilde{\Omega}(E)$.

$\tilde{\Omega}(E)$ is can be obtained by the formula for the volume of a sphere, and a change of variables to $(\frac{p_1}{\sqrt{m}}...\frac{p_n}{\sqrt{m}},\sqrt{k}q_1...\sqrt{k}q_n)$, which incurs a Jacobian determinant of $(\frac{m}{k})^{\frac{3N}{2}}$. In particular:

$$\tilde{\Omega}(E) = \int_{\sum_{i}^{3N}(\frac{p_i}{\sqrt{m}})^2+(\sqrt{k}q_i)^2\leq 2E} dq_1...dq_n,dp_1...dp_n = (\frac{m}{k})^{\frac{3N}{2}} \int_{\sum_{i}^{3N}(\frac{p_i}{\sqrt{m}})^2+(\sqrt{k}q_i)^2\leq 2E} d\frac{p_1}{\sqrt{m}}...d\frac{p_n}{\sqrt{m}},d\sqrt{k}q_1...d\sqrt{k}q_n = (\frac{m}{k})^{\frac{3N}{2}} Sph(6N,\sqrt{2E})$$

$$=\sqrt{\frac{m}{k}}^{3N}\frac{\pi^{3N}(2E)^{3N}}{\Gamma(3N+1)}$$

So in the limit of small $\Delta E$, we have that $\frac{A}{\Delta E}=\frac{\partial A}{\partial E} = \sqrt{\frac{m}{k}}^{3N}\frac{\pi^{3N}(2E)^{3N}}{\Gamma(3N+1)}=\frac{6N\sqrt{\frac{m}{k}}^{3N}\pi^{3N}(2E)^{3N-1}}{\Gamma(3N+1)}$

Then, again in the limit of small $\Delta E$, $C'=\frac{1}{\Delta E}\frac{\Gamma(3N+1)}{6N\sqrt{\frac{m}{k}}^{3N}\pi^{3N}(2E)^{3N-1}}$

#### Canonical ensemble

Let's consider a single, 1D classical harmonic oscillator. I use $\mu$ to denote a point in phase space, with coordinates $(p,q)$. Assume units where $k_B$ is $1$.

$$H(q,p)=\frac{p^2}{2m}+\frac{kq^2}{2}$$

$$Z = \int e^{-\beta H(\mu)}d\mu = \left(\int_{\RR} dp e^{-\beta T(p)}\right)\cdot\left( \int_{\RR} e^{-\beta V(q)} \right) = \sqrt{\frac{2m\pi}{\beta}}\cdot \sqrt{\frac{2\pi}{\beta k}} = \frac{2\pi}{\omega\beta}$$

where $\omega$ is $\sqrt{\frac{k}{m}}$, which is the frequency of the oscillator.

So $E = -\frac{\partial \log Z(\beta)}{\partial\beta} = \frac{1}{\beta} \Rightarrow E = T$

This means that for *any spring constant*, the oscillator is equal to the temperature. This turns out not to be the correct model for nature: it turns out that at low temperatures and high spring constants, heat capacity decreases. Explaining this requires quantum mechanics.







## Kinetics

Kinetics is the application of actual mechanics to obtain physical behaviors of large systems. So for example, you could take the Maxwell speed distribution of particles in an ideal gas, and look at their collisions with the sides of a box, for example, to work out how much force they should impart, and thus what the pressure is. 


<!-- ### Conserved current

A closely connected relation between discrete and continuum systems is as follows: let $\rho(x)\Delta x$ be the density of the quantity of interest, and $J(x)$ the rate of this quantity moving through $x$. Then 

$$\frac{d \rho(x)\Delta x}{dt} = J(x)-J(x+\Delta x) \Rightarrow \frac{d \rho(x)}{dt} = -\frac{J(x+\Delta x)-J(x)}{\Delta x} \to -\frac{dJ}{dx}  $$

Given conserved current and a further assumption that $J=-a\frac{\partial \rho}{\partial t}$, we recover the diffusion equation. This second assumption is, Sethna notes, sensible in the context of perturbations of equilibrium systems, which can be studied more formally.
 -->



