$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$
$\newcommand{\pd}[2]{\frac{\partial #1}{\partial #2}}$
$\newcommand{\inner}[2]{\langle #1 | #2 \rangle}$
$\newcommand{\ket}[1]{| #1 \rangle}$
$\newcommand{\bra}[1]{\langle #1 |}$



The fundamental idea of quantum physics is that physical quantities that you measure in experiments are eigenvalues of some linear operator. For example, when you measure the spin of an electron, if there are two possible values you can measure (say, $\frac{1}{2}$ and $-\frac{1}{2}$), then there must be some operator $S$ on some space complex inner product space $\mathcal{H}$ which has those eigenvalues.

Since physical quantities are real numbers, the operator must be self-adjoint (since the spectral theorem then implies that the eigenvalues are real).

If the quantity in question varies continuously, like the position of a particle, then the operator must be on an infinite-dimensional space, so that it has a continuous range of eigenvalues.

It then makes sense to think of the state of the system as a vector in this space, so that if the state is an eigenvector of the operator, you measure the corresponding eigenvalue. 

If your vector is a weighted sum of eigenvectors, e.g. $v = c_1v_1 + c_2v_2$, for $c_1,c_2 \in \mathbb{C}$ and $||v||=1$, and $v_1, v_2$ eigenvectors with eigenvalues $e_1, e_2$ respectively, then the probability of measuring the eigenvalue corresponding to $v_i$ is $|c_i|^2$, or equivalently $|\langle v, v_i \rangle|^2$.

In fact, the state is really a vector in the vector space quotiented by scalar multiplication (by a complex number - the vector space is over a complex fiend), since this operation does not affect eigenvalues.

!!! Note

    For an infinite-dimensional space, the state is then a function (up to scalar multiplication), known as the wavefunction, but all the principles of quantum physics make perfect sense in finite dimensions, where there is no wavefunction.

A natural consequence is that a general state induces a distribution over eigenvalues, with probabilities proportional to the square of the inner product of the state with the eigenvector.

Measurement has a strange property, which is that it causes the state to change instantaneously to the eigenvector corresponding to the measured value. While this is very suggestive of the idea that what is really happening is that a state represents the observer's uncertainty, and the change is an information update, this sort of interpretation, if it works at all, requires a lot of care and extra work (see e.g. [Caticha](https://www.arielcaticha.com/my-book-entropic-physics))

Here are the rules more explicitly:

- A state is a vector in some (dimension could be finite or infinite, depending on what's being modeled) vector space over the complex field whose Euclidean norm is 1.
- A measurable is a self-adjoint (i.e. Hermitian) operator over that vector space.
- A measurement of a measurable results in a distribution over the spectrum, i.e. the eigenvalues of that measurable (all real because of the spectral theorem), each with probability proportional to the square norm of the projection of the state onto the corresponding eigenspace (this last part is the Born rule).
- importantly, the measurement causes the state to change to the projection of the previous state onto the eigenvector corresponding to the observed eigenvalue. Or if you prefer, a measurement induces a distribution over states which you can then propagate onwards to the next measurement
- measurement is idempotent: if you measure, it collapses the state, and measuring again gives the same result
- The new state after time $t$ is given by a unitary matrix $U(t)=e^{iHt/\hbar}$. This unitarity means the past is determinable from the present (if you know the present).
- A mixed state is a probability distribution over pure states, and can be represented by an operator with a corresponding matrix called the density matrix.


## Path integral

Here is an important fact:

$$
\langle q_F | U(T) | q_I \rangle = \int D\phi e^{(i/\hbar)S(\phi)}
$$

where $S$ is the [action](classical.md) of the theory, and the integral ranges over all functions $\phi$ with $\phi(T)=q_F, \phi(0)=q_I$.

This has a simple derivation, by splitting $U(T)$ into a series of smaller units of time evolution, and then performing a Gaussian integral on each (once in an appropriate basis). 

Physically, the formula is very important. It says: **the probability of being in state $\ket{q_F}$ after starting in $\ket{q_I}$ can be calculated by summing over all possible functions $\phi$, each weighted by its action.

!!! Remarks

	The action itself is an integral, and a change of variables (here known as Wick rotation) yields $\int D\phi e^{-\hbar \int \ldots}$, which is an (infinite dimensional) Boltzmann distribution. This is the source of a ubiquitous relationship between quantum mechanics and statistical mechanics.

	The path integral generalizes easily to a field theory, and so is prevalent in quantum field theory, where many calculations amount to expectations of distributions over fields. 

<!-- !!! Derivation

	First, a mathematical observation. Suppose we have a linear map $U : \R^n \to \R^n$. Note that we could decomposed it into $\sum \frac{U}{2}|x\rangle\langle x|\frac{U}{2}$ for any (orthonormal) basis $\{x\}$. In fact, we could continue decomposing it arbitrarily, each time adding another sum.

Now the physical consequence: suppose $U$ is a propagator, in the sense of a unitary linear map that evolves the system through time (or in the case of a field in general, through spacetime). Then the above decomposition above becomes roughly:

$$
\Pi_i^{n-1}(\int dx_i) \frac{H}{n}
$$
 



The nature of composition in the category of vector spaces (or any profunctor category) involves summing out the intermediate space. That is:

$$
(f \circ g)(x) = 
$$
ERM...

This implies a relationship between a measure over paths and

Derivable via a Gaussian integral, the propagator:

$$
U(q_2, q_1, t) = \langle q_2 | e^{-it \frac{p^2}{2m}} | q_1 \rangle = (\frac{-im}{2\pi t})^{\frac{1}{2}}e^{itm/2[(q_2 - q_1)/t]^2}
$$

We obtain the path integral by composing small increments of time $\delta t$ together:

Shape:
$$
\int Dq = \lim_{N\to\infty, \delta t \to 0} \Pi_k \int dqk e^{i\delta t\sum_j (q_{j+1}-q_j)^2}
$$
finish
The classical world emerges with $\hbar$ small, so that the mimimal $\phi$ dominates, yielding the principle of least action.
-->





## Expectation

Since a state $a$ implies a distribution over eigenvalues of a given operator $L$, we can consider the expectation of that operator's eigenvalues:

$$ \langle a | L | a \rangle = \sum_i a^{*}_i (La)_i = \sum_i a^{*}_i a_i \lambda_i = \langle S(L) \rangle_{a} $$

Where $\langle S(L) \rangle_{a}$ is the expectation of the spectrum of $L$ under the probability distribution induced by $a$.

### Phase factor

Multiplying any ket by $e^{i\theta}$, for $\theta\in \RR$ won't change any of its measurable properties.

### Time Evolution

An infinitesimal time change $(I - i\epsilon H)$ must also be unitary, so $I = (I - i\epsilon H)(I - i\epsilon H)^* = (I - i\epsilon H)(I + i\epsilon H^*) = I - i\epsilon H + i\epsilon H^* \Rightarrow H^* = H$. This means $H$ is self-adjoint, so is measurable. We call it the Hamiltonian, as it acts analogously to the classical Hamiltonian. Most notably, using the definition of a derivation and taking a limit of small $\epsilon$, $\hbar\frac{d\phi(t)}{dt}=-iH\phi$. $\hbar$, the reduced Planck's constant, is for the dimensions. So to summarize, Schrödinger's equation is:

$$ \hbar\frac{d}{dt}\ket{\Phi(t)} = -iH\ket{\Phi} $$

A more direct way to understand this is to recall that if $\frac{d\phi(t)}{dt}=X\phi$, then $\ket{\Phi(t)}=e^{tX}\ket{\Phi(0)}$ (by solving the linear differential equation with a matrix exponential) and if $X=iH$ with $H$ Hermitian, that $X$ is skew-self-adjoint and as a consequence, $e^{tX}$ is unitary (see the section on unitary flow in [ODE notes](/maths/odes)).

As the name suggests, $H$ is the measurable corresponding to the energy of the system.

Time evolution is particularly easy to solve in the basis of eigenvectors of the Hamiltonian, since if we express $\ket{\Phi(t)}=\sum_ia_i(t)\ket{E_i}$, then:


$$ -\frac{i}{\hbar}\sum_ia_i(t)E_i\ket{E_i} = -\frac{i}{\hbar}H\sum_ia_i(t)\ket{E_i} = -\frac{i}{\hbar}H\ket{\Phi(t)}$$


$$\frac{d}{dt}\ket{\Phi(t)}=\frac{d}{dt}\sum_ia_i(t)\ket{E_i} = \sum_i\frac{d}{dt}a_i(t)\ket{E_i}  $$

Consequently, $-\frac{iE_i}{\hbar}a_i(t) = \frac{d}{dt}a_i(t)$, which means that $a_i(t)=e^{-\frac{i}{\hbar}E_it}a_i(0)$

(note that $i$ is both the complex unit and an index above)

### The Commutator

$$ [A, B] = AB-BA $$

The commutator is antisymmetric and linear in the first argument. If $A$ and $B$ commute, it is $0$ (i.e. the linear map which maps all inputs to the $0$ vector.


### Time Evolution of Expectation

$$ \frac{d}{dt}\langle L \rangle_{\Psi(t)} = \frac{d}{dt} \inner{\Psi(t)}{L|\Psi(t)} =  \inner{\frac{d}{dt}\Psi(t)}{L|\Psi(t)} + \inner{\Psi(t)}{L|\frac{d}{dt}\Psi(t)}$$

$$ = \inner{\frac{i}{\hbar} H\Psi(t)}{L|\Psi(t)} + \inner{\Psi(t)}{L|\frac{i}{\hbar} H\Psi(t)} = \frac{i}{\hbar} \inner{ H\Psi(t)}{L|\Psi(t)} - \frac{i}{\hbar} \inner{\Psi(t)}{L|H\Psi(t)} $$

$$ = \frac{i}{\hbar} \inner{\Psi(t)}{HL|\Psi(t)} - \frac{i}{\hbar} \inner{\Psi(t)}{LH|\Psi(t)} = \frac{i}{\hbar}\langle[H,L]\rangle\_{\Psi(t)} = -\frac{i}{\hbar}\langle[L,H]\rangle\_{\Psi(t)}   $$

Therefore, if $A$ is an observable, and $[A,H]=0$, then the expectation of $A$ is constant in time. A special case is $[H,H]=0$: so the Hamiltonian, which measures the energy, is conserved.

Also note that then the Poisson bracket (as in classical mechanics) can be interpreted as $[L,H] = i\hbar\\{L,H\\}$, so that we recover the classical rule for change over time of a quantity.

### Projection operator and density matrix

Note that for $\ket{\Phi}$, $\pi=\ket{\Phi}\bra{\Phi}$ is a linear operator. In fact, $\pi$ is a projection operator, which is to say that $\pi^2=\pi$ and that $\pi$ is Hermitian:

$$ \left(\ket{\psi}\bra{\psi}\right)\left(\ket{\psi}\bra{\psi}\right) = \ket{\psi}\left(\bra{\psi}\ket{\psi}\right)\bra{\psi} = \ket{\psi}\bra{\psi} $$

For the above, recall that a ket is normalized, by assumption. Being Hermitian, it is a measurable, and in fact it will have one 1D eigenspace with eigenvalue 1, namely the span of $\ket{\Phi}$ and all other eigenvectors with eigenvalue $0$. This means that the trace, being the sum of the eigenvalues, is $1$.

Also, if we have an orthonormal basis $\ket{i}$ (with $i$ ranging over the basis vectors), then

$$ \sum_i \ket{i}\bra{i} = I$$

This should be understood as the statement: if you take a vector, decompose it into its components along a basis, and then add those components back together, you get back what you started with.

We can also use the trace trick to see that

$$ \langle \Phi | L | \Phi \rangle = Tr(\langle \Phi | L | \Phi \rangle) = Tr( \ket{\Phi}\bra{\Phi} L) $$

### Density matrix

If we have uncertainty about what state we're in, there's a very convenient way to express that. Suppose, for example, that $p$ is a distribution over state vectors, so that the probability of a state $\ket{\Phi_i}$ is $p(\ket{\Phi_i})$. Then $\rho = \sum_ip\left(\ket{\Phi_i}\right)\ket{\Phi_i}\bra{\Phi_i}$ is called the density matrix (or operator) and by the linearity of the trace:

$$ \langle L \rangle = Tr(\rho L)$$


### General uncertainty principle

Uses the following form of the Cauchy-Schwartz inequality:

$$ |X||Y| \geq \frac{1}{2}| \langle X|Y \rangle + \langle Y|X \rangle | $$

Let $X=A\ket{\Psi}$ and $Y=iB\ket{\Psi}$

$$Var_{\Psi}(A)\cdot Var_{\Psi}(B) \geq \frac{1}{2} |\langle[A,B] \rangle_{\Psi} | = \frac{1}{2} |E_{\Psi}([A,B])| $$

The consequence is that if two measurables don't commute, then as your uncertainty about one goes to $0$, your uncertainty about the other goes to infinity.

## Composing systems

If you want states with multiple things, e.g. two spins (qubits), you need a tensor product of vector spaces. The key feature of the monoidal product in a category of vector spaces is that it is *not the categorical product*. You can't get the parts out of the whole. So if you have a fully specified state in the tensor product space, that need not give you any information about the subspace corresponding to one of your qubits.

<!-- Alternatively, using the trace trick, we can form from a state $\phi$ the projection operator $|\phi\rangle\langle\phi|$ (remember that $\phi$ is normalized), and note that $Tr(|\phi\rangle\langle\phi|M)=Tr(\langle\phi|M|\phi\rangle)$ is the expectation of $M$ in state $\phi$. More generally, an operator $\rho=\sum_ia_i|\phi_i\rangle\langle\phi_i|$ gives you a *mixed* state, and the corresponding matrix is the density matrix. -->

<!-- Probability flow

The flow of $\psi$ under time evolution implies a flow for the probability distribution $\rho = \psi^*\psi$, from which a continuity equation follows, by using the Schrödinger equation:

$$
\frac{d}{dt}\int_V \rho = \ldots = \int_{\partial V}\nabla\cdot j
$$

for $j = -\frac{i\hbar}{2m}(\psi^*\nabla\psi - \psi\nabla\psi^*)$

: explain/finish ^

-->

### Qubits

The simplest non-trivial system is a 2D state space called a qubit or spin. It's called a spin cause of its use in the physical interpretation for electromagnetism, and more directly because the measurables themselves form a vector space isomorphic to real 3-space. It's called a qubit in the context of quantum computing, because it has two eigenvalues, and these correspond to the values the qubit can take. The eigenvalues are always $1$ and $-1$.

Any measurable on a qubit is composed of the three *Pauli* matrices (and the identity, but it doesn't do much):

$$ \sigma_x = \begin{bmatrix} 0 & 1\\\\ 1 & 0 \end{bmatrix} $$

$$ \sigma_y = \begin{bmatrix} 0 & -i \\\\ i & 0 \end{bmatrix} $$

$$ \sigma_z = \begin{bmatrix} 1 & 0 \\\\ 0 & -1 \end{bmatrix} $$

In fact we can interpret e.g. $\sigma\_x$ as the the x component of the vector representing the orientation of a measurement device.

The Pauli matrices are also closed under commutation (i..e they form a commutator algebra):

$$ [\sigma_x, \sigma_y] = 2i\sigma_z $$

$$ [\sigma_y, \sigma_z] = 2i\sigma_x $$

$$ [\sigma_z, \sigma_x] = 2i\sigma_y $$

Note that the commutators aren't $0$ and so the three Pauli operators are not simultaneously measurable.

### Magnetic field

We can model a magnetic field as a vector $B$ in physical space and the Hamiltonian as:

$$ H = \overrightarrow{\sigma}\cdot \overrightarrow{B} = \sigma_xB_x + \sigma_yB_y + \sigma_zB_z $$

For simplicity, let's choose a simpler example: $H = \frac{\hbar\omega}{2}\sigma_z$

Then, using the commutator algebra above and the equation for time-evolution of the Hamiltonian:

$$ \frac{d}{dx}\langle \sigma_x \rangle = -\frac{i}{\hbar}\langle [\sigma_x, H] \rangle = -\frac{\hbar\omega}{2}\frac{i}{\hbar}\langle [\sigma_x, \sigma_z] \rangle = -\omega\langle\sigma_y\rangle  $$

Similarly:

$$ \frac{d}{dx}\langle \sigma_y \rangle = \omega\langle\sigma_x\rangle $$

$$ \frac{d}{dx}\langle \sigma_z \rangle = 0 $$

Note the very close relation to the analogous classical situation (e.g. Classical Mechanics: The Theoretical Minimum, p183 onwards).

## Particles in continuous (1D) space

Quantization is the act of taking a classical system and designing a quantum system that behaves like the classical system in the limit of $h\to 0$ (roughly). To quantize the motion of a classical particle, we need to upgrade to infinite dimensional Hilbert spaces.

In particular, take the space of functions which are normalizable (when you integrate them multiplied by their complex conjugate from $-\infty$ to $\infty$, you get a finite number). Actually, we'll even allow some non-normalizable things - see [Fourier analysis notes](../maths/fourier.md) to get an intuition of why *distributions* are also allowed.


Fixing a basis, a function can be defined by its coefficients. So the element $|\Phi\rangle$ of the Hilbert space is expressed in a basis (the position basis) as $\phi(x)$, where $\phi$ refers to the coefficient function.

An obvious operator $X$ on this space can then be defined such that $X|\Phi\rangle$ in the position basis is $x\phi(x)$. $X$ is self-adjoint. To see this, first note that for any kets $\Phi$ and $\Psi$ and operator $L$: $\langle\Phi|L|\Psi\rangle=\langle\Psi|L|\Phi\rangle^{*} \to \langle\Phi|L|\Psi\rangle = \langle L\Phi|\Psi\rangle$ which implies that $L$ is Hermitian. Then:

$$ \bra{\Phi}X\ket{\Psi}$$

$$ = \int_{-\infty}^{\infty} \phi(x)^{*}x\psi(x)dx$$

$$ = \left(\int_{-\infty}^{\infty} \psi(x)^{*}x\phi(x)dx\right)^{*}  $$

$$ = \bra{\Psi}X\ket{\Phi}^{*}$$

The eigenvectors of $X$ are the delta functions and its spectrum (space of eigenvalues) are $\RR$. The eigenbasis is called the *position* basis.

$$X\phi(x) = x\phi(x) = x\_0\phi(x) \Rightarrow (x-x\_0)\phi(x) = 0 \Rightarrow \phi(x)=\delta(x-x\_0)$$

Viewed as a matrix, we have $\bra{x}X\ket{x'} = \delta(x-x')$.

Another obvious operator $Y$ can be defined such that $Y|\phi\rangle$ in the position basis is $\pd{}{x}\phi(x)$. This is skew-self-adjoint and as a consequence, the momentum operator $P$, defined as $P=-i\hbar Y$ is self-adjoint (see [Fourier notes](../maths/fourier.md)). See to this, first note that for any ket $\ket{\Phi}$, we have $\phi(\infty)=\phi(-\infty)=0$ (since otherwise $\phi$ would not be normalizable). This explains why the first term on the third line below drops out:

$$ \bra{\Phi}D\ket{\Psi}$$

$$ = \int_{-\infty}^{\infty} \phi(x)^{*}\frac{d}{dx}\psi(x)dx$$

$$ = [\phi(x)^{*}\psi(x)]_{-\infty}^{\infty} - \left(\int_{-\infty}^{\infty} \frac{d}{dx}\psi(x)^{*}\phi(x)dx\right)^{*}  $$

$$ = \bra{\Psi}D\ket{\Phi}^{*}$$

The eigenvector with eigenvalue $p\in \RR$ is $\frac{1}{\sqrt{2\pi}}e^{\frac{ixp}{\hbar}}$, so the eigenbasis, known as the momentum basis, consists of the complex exponentials.

Note that in the momentum domain, we have to use a definition of integration in which complex exponentials integrate to $0$. Roughly, we'll say that their average over increasingly long times goes to $0$.

Also note that $\lambda = \frac{2\pi\hbar}{p}$ is the wavelength (spatial periodicity) of the wave corresponding to  $\frac{1}{\sqrt{2\pi}}e^{\frac{ixp}{\hbar}}$.

A common notation has that $\ket{x}$ and $\ket{p}$ are respectively eigenvectors of $X$ and $P$. The following derivation gives an example of the kind of thing that bra-ket notation allows for (it's not formally justified here, but turns out to work):


First recall that for $\ket{i}$ ranging over a set of *orthogonal* basis vectors, $I = \int dx \ket{i}\bra{i} $. Also note that the following two equation hold because the eigenvectors of $X$ (i.e. $\ket{x}$) are delta functions:

$$ \inner{x}{\Phi} = \int dx' \delta(x-x')\phi(x') = \phi(x)$$

<!-- $$\inner{x}{p} = \frac{1}{\sqrt{2\pi}}e^{\frac{ixp}{\hbar}} = $$ -->


Then:

$$ \inner{p}{\Phi}$$

$$ = \bra{p}I\ket{\Phi}$$

$$ = \bra{p}\left( \int dx \ket{x}\bra{x} \right)\ket{\Phi}$$

$$ = \int dx \inner{p}{x}\inner{x}{\Phi}$$

$$ = \frac{1}{\sqrt{2\pi}}\int dx e^{-\frac{ixp}{\hbar}}\phi(x) $$

$$ = \mathcal{F}(\phi)(p)$$

where $\mathcal{F}$ is the Fourier transform.

### Heisenberg uncertainty principle

Note that (working in the position basis):

$$ [X,P]\phi(x) = (XP - PX)\phi(x) = -xi\hbar\frac{d}{dx}\phi(x) + i\hbar\frac{d}{dx}(x\phi(x)) $$

$$ = -xi\hbar\frac{d}{dx}\phi(x) + i\hbar\phi(x) + ix\hbar\frac{d}{dx}\phi(x) = i\hbar\phi(x)$$

$$ \Rightarrow [X,P] = i\hbar $$

As a consequence, we can apply the general uncertainty principle to $X$ and $P$ to obtain:

$$ Var(X)\cdot Var(P) \geq \frac{1}{2} |\langle i\hbar \rangle | = \frac{1}{2\hbar} $$

### Schrödinger Equation

Suppose $H = \frac{P^2}{2m}$. Then we get the follow time evolution:

$$ ih\frac{d}{dt} \ket{\Phi} = \frac{-\hbar^2}{2m}\frac{d^2}{dx^2}\ket{\Phi} $$

Eigenvalues and eigenvectors of this Hamiltonian take the form of $\frac{p^2}{2m}$ and $\phi(x)=e^{\frac{ipx}{\hbar}}$ respectively. What this means is that we can simplify the calculation of the time evolution by diagonalizing (i.e. taking the Fourier transform, i.e. moving into the eigenbasis of $P$).

<!-- $$\phi(x,t) = \int dp \mathcal{F}(\phi)(p)e^{-\frac{ipx}{\hbar}}e^{-\frac{p^2t}{2m\hbar}} $$

One important consequence is that $\mathcal{F}(\phi)(p,t)$ only changes in time by a phase factor, which has no measurable consequence. In other words, momentum is preserved over time. -->

### Velocity

In a classical setting, momentum and velocity are things of the same type. In the (1D) quantum setting, velocity is a scalar $v = \frac{d}{dt}\langle X \rangle_{\Psi(t)}$. But by the formula for change of expectations above, we have:

$$ v =  \frac{d}{dt}\langle X \rangle_{\Psi(t)}$$

$$ = \frac{i}{2m\hbar} \langle [P^2,X]\rangle_{\Psi(t)}$$

$$ = \frac{i}{2m\hbar} \langle P[P,X] + [P,X]P\rangle\_{\Psi(t)}  $$

$$ = \frac{i}{2m\hbar} \langle -2i\hbar P \rangle_{\Psi(t)}$$

$$ = \frac{\langle P \rangle_{\Psi(t)}}{m}  $$

So $\langle P \rangle_{\Psi(t)} = mv$: the *expected* momentum is mass times velocity, as in the classical case.

### Forces

An operator $V(x)$, such that $V\ket{\Phi}$ in the position basis is $V(x)\phi(x)$ represents a potential, with $F(x)=-\frac{\partial V}{\partial x}$. But note that then $V(x)$ commutes with $X$, so that $[X,V(x)]=0$.

A consequence is that, by linearity of the commutator, $[X,H]=[X,P]$, for $H=\frac{P^2}{2m}+V(x)$. This means that as above, $\langle P \rangle_{\Psi(t)} = mv$.

A similar calculation gives change in momentum (suppressing the dependence on state and noting that $[V(x),P]\psi(x) = V(x)(-i\hbar\frac{d}{dx})\psi(x) - -i\hbar\frac{d}{dx}\left(V(x)\psi(x)\right) = -i\hbar\frac{d}{dx}V(x)\psi(x)$)

$$\frac{d}{dt}\langle P \rangle = \frac{i}{2m\hbar} \langle [P^2,P]\rangle + \frac{i}{\hbar}\langle[V,P]\rangle $$

$$ = \frac{i}{\hbar}\langle i\hbar \frac{dV(x)}{dx}\rangle = -\langle \frac{dV(x)}{x}\rangle = \langle F(x) \rangle  $$


This is the same as the classical equation of motion, but now for expectations. But *note*: the equation is *not* $\frac{d}{dt}\langle P \rangle = -\frac{dV(\langle X \rangle)}{d\langle X \rangle}$. If it were, then the expectations would follow Newton's law of motion. This equation, however, is approximate when $\langle \frac{dV(x)}{x}\rangle \approx \frac{dV(\langle X \rangle)}{d\langle X \rangle}$ which in turn holds when $\frac{dV}{dx}$ is small and the wave packet (i.e. the ket) is big. This is the case (approximately) described by classical mechanics.

### Quantum harmonic oscillator

Harmonic oscillators are both analytically solvable and approximate any system perturbed slightly from equilibrium.

The QHO Hamiltonian is the natural quantum analog to the classical oscillator, namely (setting $m=1$):

$$
H = \frac{P^2+\omega^2 X^2}{2}
$$

We can actually find the spectrum (set of eigenvalues) of the Hamiltonian without doing almost any calculus, by using an Heisenberg style approach, as follows.

First, the completion of the square to rewrite $H$:

$$H =  \frac{1}{2}\left(P^2+\omega^2X^2\right) = \frac{1}{2}(P+i\omega X)(P-i\omega X) - \frac{1}{2}\left(i\omega XP - i\omega PX \right) $$

$$ = \frac{1}{2}(P+i\omega X)(P-i\omega X) - \frac{1}{2}i\omega[X,P] $$

$$ =  \frac{1}{2}(P+i\omega X)(P-i\omega X) + \frac{\omega\hbar}{2} $$

$$ =  \omega\hbar \frac{-i}{\sqrt{2\omega\hbar}}(P+i\omega X)\frac{i}{\sqrt{2\omega\hbar}}(P-i\omega X) + \frac{\omega\hbar}{2} $$

This suggests some operators:

$$ a_+ := \frac{-i}{\sqrt{2\omega\hbar}}(P + i\omega X) $$

$$ a_- := \frac{i}{\sqrt{2\omega\hbar}}(P - i\omega X)  $$

These two are adjoint. We also define:

$$ N := a_+a_- $$


Then, using these definitions in the above:

$$ H = \omega\hbar(a_+a_- -\frac{1}{2}) = \omega\hbar(N + \frac{1}{2}) $$


Next, a simple Lie algebra (set of operators closed under commutation), easily verified by brute calculation:

$$ [a_-,a_+] = 1 $$

$$ [a_-, N] = a_- $$

$$ [a_+, N] = -a_+ $$

Then, the punchline:

$$ N(a_+\ket{n}) = (a_+N + (Na_+ - a_+N))\ket{n} $$

  

$$= (a_+N+[N,a_+])\ket{n} = (a_+N+a_+)\ket{n} = a_+(N+1)\ket{n} = (n+1)a_+\ket{n} $$

  
  

In other words, if $\ket{n}$ is an eigenvector (of $H$) with eigenvalue $n$, then $a_+\ket{n}=K\ket{n+1}$, i.e. $a_+\ket{n}$ is an eigenvector with eigenvalue $n+1$. $K$ is there as a normalization factor, not yet determined. Similarly for $a_-$. $a_+$ and $a_-$ are respectively called the creation and annihilation operators.

  

A second punchline:

  

Because of the squares in the operators constituting $H$ (and the fact that eigenvectors multiply under composition) we know already that the eigenvalues are non-negative. Since the eigenvalues are non-negative, there must be an eigenvector $\ket{0}$ such that $a_-\ket{0}=\overrightarrow{0}$. This is because the annihilation operator keeps reducing the eigenvalue. So eventually we would hit an eigenvector $\ket{0}$ which $a_-$ annihilates. But then:

  

$$\overrightarrow{0}=a_-\ket{0}=\frac{i}{\sqrt{2\omega\hbar}}(P - i\omega X)\ket{0}$$

  

$$ \Rightarrow -i\hbar\frac{d}{dx}\phi_0(x) = i\omega x\phi_0(x)$$

  

$$ \Rightarrow \phi_0(x) = e^{-\frac{\omega x^2}{2\hbar}} $$

  

So the position projection of $\ket{0}$ is a Gaussian function. We even know that $H\ket{0}=\omega\hbar(N+\frac{1}{2})\ket{0} = \frac{\omega\hbar}{2}$, and that each successive $\ket{n}$ gains $\omega\hbar$ energy.

  

Finally:

  

Now that we know the ground state, we can generate the eigenvectors using the creation operator, which is great. What we get are functions which are a polynomial times the ground state. These polynomials are called the Hermite polynomials, and are alternatively odd and even.

  

We can see that they're orthogonal, because $\ket{n}=K(a_+)^n\ket{0}$, for a normalizing constant $K$, so $\inner{n}{m} = \bra{0}(a_-)^n(a_+)^m\ket{0}$. WLOG, suppose $n > m$. Then we raise more than we lower, so we annihilate the ket.

  
Given orthonormality (which I have not shown - I've only shown orthogonality), we can find the appropriate value of the normalizing constant $K$ as follows:

  

$$ a_-\ket{n} = K\ket{n+1} \Rightarrow \bra{n}a_+a_-\ket{n} = K^2 \inner{n+1}{n+1} = \bra{n}N\ket{n} = n\inner{n}{n} $$

  

$$ \Rightarrow n = K^2 \Rightarrow K = \sqrt{n} $$

## Interaction picture

Given a Hamiltonian $H_0 + H_1$, we have states $|\psi_S(t)\rangle$ in the Schrödinger picture, and observables $O_S$. We then define:

$$
|\psi_I(t)\rangle := e^{iH_0t/\hbar}|\psi_S(t)\rangle
$$

and 

$$
O_I(t) = e^{iH_0t/\hbar}O_Se^{-iH_0t/\hbar}
$$

The important result is:

$$
i\hbar \frac{d}{dt}|\psi_I(t)\rangle = H_{I,1}(t)|\psi_I(t)\rangle \\
$$
and 

$$
i\hbar \frac{d}{dt}O_I(t) = [O_I(t), H_{0,S}]
$$

so states evolve with the interaction Hamiltonian $H_{I,1}$, and operators with the Schroedinger Hamiltonian $H_{S,0}$. Convenient.


## Representations in quantum physics

Representations have an immediate application in quantum physics, since they describe how a symmetry acts on a space. This is important in classical physics (a representation of the Galilean group on spacetime preserves rest frames), relativistic physics (the representation of the Poincare group on spacetime preserves rest frames), but also in quantum mechanics.

As an important example, a physical statement about a quantum mechanical system like "The Hamiltonian is rotationally symmetric" translates to the mathematical statement that $[H,R]=0$ for all $R \in SO(3)$.
<!-- The groups of interest to physics are often continuous groups, like $SO(3)$.  -->

Once we have this mathematical statement, we know from the corollaries of Schur's lemma above that the eigenspaces of $H$, which of course are all important for the physics of the system, are precisely the irreducible representations of $SO(3)$, which are extremely well studied mathematically.

Physically speaking, the elements of the Lie algebra of the group correspond to generators of the symmetry, so for example $L_i$ lives in $so(3)$ and generates rotations of space. This is where angular momentum and its strange behavior comes from.

<!-- As a second example, we showed above that the representations of $S(1)$ are eigendecomposable, so energy takes integer eigenvalues in systems where the Hamiltonian has this symmetry. This is a simple case of quantization. -->


<!-- xAn relevant example of a Lie group for physics is the collection of rotations of 3D space (this group is called SO(3) ), or the set of all inertial frame preserving transformations in classical or relativistic physics.  -->

### Spherical harmonics

There is also a representation of $SO(3)$ onto $L^2(S^2)$ (the space of functions from the circle to itself that are normalizable). This is the direct sum of all the irreducible representations. That means that we can write

$$
f(\theta, \phi) = \sum_l\sum_m \alpha^m_lY^m_l
$$

where we have decomposed an arbitrary $f \in L^2(S^2)$ into a  sum of functions on the subspaces corresponding to the irreducible representations. These are the spherical harmonics.

<!-- ### Vector operators

!!! Note 

	(I have pieced the following together, and think it's roughly correct, but doesn't come directly from any source I could find).

The adjoint representation is what we're invoking when we talk about vector operators, in the following sense. Given the Lie algebra $so(3)$, which can be regarded as the real vector space $V^3$, we get the adjoint representation of $SO(3)$ on $so(3)$ being $R^T(\delta)V_iR(\delta)$. Now since we have classified the representations of $SO(3)$, we know that this must be the spin $n$ representation for $n$ half integer. For $n=0$, $V_i$ is a scalar, for $n=1$, a vector (note the correspondence with the indexing in the Wigner Eckart theorem).

If $[L_i, V_j] = ie^{ijk}V_k$, then $R^T(\delta)V_iR(\delta) = i\delta n_j[L_j, V_i] = V_i + \delta(n \times V)^i$, for small $\delta$, which indicates this is the spin 1 representation. -->


### Spin

Physically, there is a reason, to do with symmetry, why qubits arise in nature.

It is reasonable to expect that a quantum system should not have a preferred orientation with respect to measurement. Taking this as a postulate and thinking physically, that means that for any rotation of the observation apparatus in 3D space, there should be a corresponding action on the Hilbert space of the system which cancels out the change. That is to say that there must be a representation of $SO(3)$ on the system.

We can define a representation $\pi$ of $SU(2)$ given a representation of $\phi$ of $SO(3)$, given the standard map $f : SU(2) \to SO(3)$, namely by $\pi = \phi \circ f$. But recall that $f$ is not injective, so its inverse isn't a representation, and so we can't automatically get a representation of $SO(3)$ from one of $SU(2)$. *However*, we only care about a representation up to a phase change since as far as measurement is concerned, quantum states are rays, not vectors. In this case, we can invert $f$ (choosing one of the two points) and then construct $\xi \circ f^{-1}$, where $\xi$ is a representation of $SU(2)$. $\xi \circ f^{-1}$ is a representation up to phase. In summary, we get all the representations spin(n) of $SU(2)$, for $n$ half-integer. That's the origin of spin, which is the spin 1/2 representation (up to phase) of $SO(3)$: a spin 1/2 representation *can* exist, and indeed it appears in nature: it is a qubit.


## Spectroscopy

Turns out that waves roughly behave in a way where if you have a plane wave hit a wall with a hole, it will *diffract*, causing the *Fourier transform of the hole* to be the resulting field on a wall further on (at least, this is how *far-field* diffraction works). Actually this is pretty intuitive. Any situation where each of a wave's frequencies respond differently is going to result in Fourier type transformation. Just think of a prism splitting light into different angles based on frequency.

This generalizes a lot, and is the principle that allows you to "see" the structure of a crystal by looking at the pattern it makes (the diffraction pattern), which is the Fourier transform (and then 2D projection) of an appropriate Dirac comb representing the lattice in question (the given model of the atomic structure of the material of interest).

