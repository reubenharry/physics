$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\RR}{\mathbb{R}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\Z}{\mathbb{Z}}$
  

$\newcommand{\R}{\mathbb{R}}$

$\newcommand{\C}{\mathbb{C}}$

$\newcommand{\N}{\mathbb{N}}$

$\newcommand{\Z}{\mathbb{Z}}$

$\newcommand{\pd}[2]{\frac{\partial #1}{\partial #2}}$


First order ordinary differential equations look as follows, where $\phi : \R \to (\R \to \R)$, and $x_0$ and $F$ are fixed:
  
$$
\frac{d\phi(x_0)(t)}{dt} = F(\phi(x_0)(t),t)
$$

The goal is to find a function $\phi(x_0)$ which satisfies the equation and also satisfies $\phi(x_0)(0)=x_0$. 

This formulation makes explicit that the solution depends on the initial condition $x_0$, so we can think of the solution as a function of *two* arguments $\phi(x=x_0,t=t)$. 

All $n$th order differential equations (featuring higher derivatives) can be reduced to first order equations of multiple variables, so that's why we focus on equations of the first order. In general

  

$$
\phi \in (\R^n\to(\R\to\R^n)),\quad t \in \R,\quad F \in ((\R^n, \R)\to\R^n)
$$

  

Often we consider the subset of *autonomous* cases:

  

$$
\frac{d\phi(x_0)(t)}{dt} = F(\phi(x_0)(t))
$$

  

Often we write the above as:

  

$$
\phi(x_0)' (t) = F(\phi(x_0)(t))
$$

  

or even, confusingly:

  

$$
\phi(x_0)' = F(\phi(x_0))
$$

  

Note that we are assuming that the initial time $t$ is $0$ without loss of generality.
  
I'll write $\phi_F$ to refer to the solution to the ODE defined in terms of some $F$, i.e. the unique maximal solution (when it exists). We can also uncurry $\phi$, and write an ODE as:

  

$$
D_2\phi_F(x_0,t) = F(\phi_F(x_0,t),t)
$$

  
## Existence and uniqueness theorems:

  

**Peano existence theorem**: If $F$ is continuous, a solution exists. We can prove this by constructing it from a series of linear interpolations, and using the Arzela-Ascoli theorem to show that this series of functions converges, and moreover converges to a solution.

  

**Picard existence theorem**: If $F$ is continuous in both arguments and locally Lipschitz in $t$, $\phi_F(x,t)$ exists in an interval around $0$ and is continuously differentiable in $t$. 

??? Proof

	We prove this by considering the
	
	  
	
	$$
	\phi(x_0)'(t)=F(\phi(x_0)(t),t)\Rightarrow \phi(x_0)(t) = x_0 + \int_0^t F(\phi(x_0)(t),t)dt
	$$
	
	  
	
	Let $A : C_1\to C_1$ be an operator mapping defined as $A[y] = \int_0^t F(y(t),t)dt$
	
	  
	If $A$ has a fix point, then that fix point is a solution to the ODE defined by $F$. If $A$ is a contraction map on the metric space of $C_1$ then it has a fix point. So we need only show it is a contraction map. This can be done with some careful analytic argumentation which is omitted here.
	
	  
	
	Note that this also gives a method (called Picard iteration) for constructing the solutions to particular differential equations, by analysing the sequence produced by repeated applications of $A$.

  

Now consider a solution like:

  

$$
\phi_{F}(x)(t)
$$

  

Think of this as a path through the space, with the first input representing the initial condition and the second representing the time. Note that $\phi_F$ is a semigroup in $t$ (and if $F$ is uniformly Lipschitz, then it's even a group):

  

$$
\phi_F(t+s,x)=\phi_F(t,x)\circ\phi_F(s,x);\quad \phi_F(0,x)=x
$$

  

**Note**: this path cannot intersect any other path representing a solution with a different initial condition. The proof of this follows from a more specialized case: if $x_0=y_0$, then for $F:U\to\R^n$ then $\forall t: \phi_F(x_0)(t)=\phi_F(y_0)(t)$ at least where the domains of definition agree. The proof illustrates some useful tools.

??? Proof

	First suppose that $\phi_F(x_0):I\to \R^n$ and $\phi_F(y_0)(t):J\to \R^n$ for open intervals $I$ and $J$ both containing $0$. Then suppose that $\phi_F(x_0):I\cap J$ and $\phi_F(y_0)(t):I\cap J$ are not equal Then for $\tau = \inf\{t \in I\cap J : \phi_F(x_0)(t)\neq \phi_F(y_0)(t) \}$, $\phi_F(x_0)(\tau)=\phi_F(y_0)(\tau)$. Let $\bar{x}=\phi_F(x_0)(\tau)$. Then for a ball $B_r(\bar{x})\subset U$, we can find $\delta>0$ such that for $t$, $\phi_F(x_0)(t)\in B_r(\bar{x})$ and $\phi_F(y_0)(t)\in B_r(\bar{x})$ .
	
	  
	
	We then set $L$ as $\sup_{x\in B_r(\bar{x})}||DF(x)||$, which gives us that $\forall t\in [\tau,\tau+\delta]: ||F(\phi_F(x_0)(t))-F(\phi_F(y_0)(t))||\leq L ||\phi_F(x_0)(t)-\phi_F(y_0)(t)||$
	
	  
	
	We now note that if $||F(z(t))||\leq L||z(t)||$ then:
	
	  
	
	$$ \frac{d}{dt}||z(t)||^2 = \frac{d}{dt}z(t)^Tz(t) $$
	
	
	
	
	$$ = 2z(t)^T\frac{d}{dt}z(t) $$
	
	
	
	
	$$ = \langle 2z(t),F(z(t)) \rangle \leq 2||z(t)||\cdot ||F(z(t))||$$
	
	  
	
	
	$$ \leq 2||z(t)||\cdot L ||z(t)|| = 2L||z(t)||^2$$
	
	  
	
	We can now be rather clever, and note that $\frac{d}{dt}(e^{-2Lt}||z(t)||^2)\leq 2Le^{-2Lt}||z(t)||^2-2Le^{-2Lt}||z(t)||^2=0$, so $e^{-2Lt}||z(t)||^2$ is monotone decreasing.
	
	  
	
	With $z(t)=\phi_F(x_0)(t)-\phi_F(y_0)(t)$, we have that $e^{-2Lt}||z(t)||^2$ is montone decreasing, which means that, since $e^{-2L\tau}||\phi_F(x_0)(\tau)-\phi_F(y_0)(\tau)||^2=0$, $\phi_F(x_0)(t)=\phi_F(y_0)(t)$ for $t\in[\tau,\tau+\delta]$, since otherwise the expression would be positive (norms are positive).
	
	  
	
	The fact that paths can never intersect is useful because it means we can often constrain the movement of a path. For example:
	
	  
	
	**Problem**: Show that for $x\in\R$, $F(x(t),t)=a(t)x(t)$, and $x_0>0$, $\forall t: \phi_F(x_0,t) >0$.
	
	  
	
	**Solution**: By assumption, $\phi(x_0,0)=x_0>0$. If there exists a $t$ such that $\phi(x_0,t)<0$, then by the intermediate value theorem, $\exists t': \phi(x_0,t')=0$. But $\phi(0,0)=0$, so $\forall t: \phi(0,t)=0$. This would be a contradiction. **Intuition**: to get to a negative value, you'd have to cross $0$, but then you'd cross another solution, namely the $0$ solution.

  

We can now introduce a powerful result about the domain of solutions of ODEs. For continuously differentiable (hence locally Lipschitz) $F : U\to \R^n$, solutions $\phi_F(x,t)$ where $F$ is autonomous which are defined for $t\in (\alpha,\beta)$ for $\beta$ finite, $||\phi_F(x,t)||$ either goes to infinity in finite time $t$, or $d(U,\phi_F(x,t))$ converges to $0$, i.e. the path converges to the boundary of $U$. Note that we assume $U$ is open, and that $d(U,y)$ for a set $U$ and a point $y$ is $\inf_{z\in U}d(y,z)$.

  The idea is that if the path doesn't continue for infinite time, the solution must either converge onto the boundary of the (finite) open domain, or go to infinity in finite time.

The contrapositive is equally useful: if $\phi_F(x,t)$ stays within a closed set, or equivalently $||\phi_F(x,t)||$ stays within a closed interval, then the solution exists for all $t >0$.

  

## Some simple ODEs and their solutions

  

For some simple forms of $F$, we can derive a general solution. For example, suppose:

  

$$
F(x,t) = ax,\quad a\in \R
$$

  

Then, to find a general solution, first note

$$
\frac{d}{dt}(e^{-at}\phi(x_0,t)) = -ae^{-at}\phi(x_0,t) + e^{-at}\frac{d}{dt}\phi(x_0,t)$$

  

$$ = e^{-at}(\frac{d}{dt}\phi(x_0,t) - a\phi(x_0,t)) = 0
$$

  

This means that $e^{-at}\phi(x_0,t)=c$ for some constant $c$, so $\phi(x_0,t) = ce^{at}$. Then $x_0 = \phi(x_0,0) = c$.

  

Now consider a more general case:

  

$$
F(x,t) = a(t)x(t)+f(t)
$$

  

for $a$ and $f$ continuous. We can apply a similar approach to before:

  

$$ \frac{d}{dt}(e^{-\int_{0}^ta(s)ds}\phi(x_0,t)) = -a(t)e^{-\int_{0}^ta(s)ds}\phi(x_0,t) + e^{-\int_{0}^ta(s)ds}\cdot (a(t)\phi(x,t)+f(t)) $$

  

$$ = e^{-\int_{0}^ta(s)ds} = (a(t)\phi (x,t)+f(t) = - a(t)\phi(x_0,t)) = e^{-\int_{0}^ta(s)ds}f(t) $$

  

$$\Leftrightarrow e^{-\int_{0}^ta(s)ds}\phi(x_0,t) = \int_{0}^t e^{-\int_{0}^ta(s)ds}f(t) + c $$

  

$$\Leftrightarrow \phi(x_0,t) = e^{\int_{0}^ta(s)ds}(\int_{0}^t e^{-\int_{0}^ta(s)ds}f(t) + c)$$

  

Further:

  

$$
x_0 = \phi(x_0,0) = c
$$

  

Another class of differential equations:

  

$$
F(x(t),t) = f(x(t))\cdot g(t)
$$

  

where both $g$ and $f$ are continuous, and $f$ has an open domain without $0$. Then suppose there exists a $\tau$ such that $\tau'(k)=\frac{1}{f(k)}$. What $\tau$ is may depend on the $F$, of course - that is, I don't think there's a general expression for it. Then:

  

$$
\frac{d}{dt}\tau(\phi(x_0,t)) = \frac{1}{f(\phi(x_0,t))}D_2\phi(x_0,t) = g(t)$$



  

$$\Rightarrow \tau(\phi(x_0,t)) = \int g(t)dt + c $$



  

$$\Rightarrow \phi(x_0,t) = \tau^{-1}(\int g(t)dt + c) $$

  

This approach is known as separation of variables. As an example, suppose you see $\frac{\partial}{\partial t}\phi(x_0,t)=t(1+\phi(x_0,t)^2)$. Then you can identify $f(x)=1+x^2,g(t)=t$. Further, you can remember from your trigonometry that $\int tan^{-1}(x)dx = \frac{1}{1+x^2}$. Using the above, $\frac{d}{dt}\tan^{-1}x(t)=\frac{1}{1+x(t)^2}x'(t) = t \Rightarrow x(t)=\tan(\frac{t^2}{2}+c)$

  
## Linear Differential Equations

We now consider $x(t) : \R^n$, for $n > 1$. Linear differential equations have an $F$ of the following form, where $\psi(t)$ is a linear operator, and $f$ is continuous:

  

$$
F(x(t),t) = \psi(t)(x(t))+f(t);\quad x(0)=x_0
$$

  

The approach to solving these is to use matrix exponentials. For a simple example, suppose $F(x(t),t)=\psi(x(t))$. Then, with some more analysis, we can show that $\phi_F(x,t)=xe^{t\psi}$ is the unique solution as we'd expect.

  

For a harder example, consider an ODE deriving from $F(x,t)=\psi(x)+f(t)$. We can derive a solution by:

  

$$
\frac{d}{dt}(e^{-t\psi}\phi(x_0,t)) = e^{-t\psi}(D_2\phi(x_0,t)-\psi(\phi(x_0,t)))=e^{-t\psi}f(t) $$

  

$$\Rightarrow \phi(x_0,t) = e^{t\psi} (\int_{0}^te^{-s\psi}f(s)ds + x_0)$$

  

  

### Unitary Flow

  
Suppose that $\psi$ is skew-self-adjoint, i.e. $\psi^*=-\psi$. This might arise, for instance, if $\psi=i\tau$ and $\tau$ is self-adjoint. Then suppose $F(x)=\psi x$. Then $||\phi_F(x,t)||$ is constant in $t$. This is because $\phi_F(x,t)=e^{t\psi}x$ and $e^{t\psi}$ is unitary. It is unitary because $(e^{t\psi})^*=e^{-t\psi}$, so $e^{t\psi}e^{-t\psi}=I$.

  
## Influence of initial conditions :

  
Now consider:

  



  

$$
D_1\phi_F(x,t) = F(\phi(x,t))
$$

  
  
  

with $D_1\phi_F(x,t) := \frac{\partial \phi_F(x,t)}{\partial x}$.  Intuitively, this is asking: how does the whole path change if I vary the initial condition by just a tiny bit. 

What can we say about this derivative? Well:

  

$$
D_2D_1\phi_F(x,t)_{ij} = \frac{\partial}{\partial t}\frac{\partial \phi_F(x_i,t)}{\partial x_j} =$$

  

$$ \frac{\partial}{\partial x_j}\frac{\partial \phi_F(x_i,t)}{\partial t} = \frac{\partial}{\partial x_j}F_i(\phi(x,t)) = DF(\phi(x,t))_{ik} \cdot D_1\phi_F(x,t)_{kj}
$$

  

This itself is a differential equation. To make this clear, write $H(t)=D_1\phi_F(x,t)_{ij}$ and $A(t)=DF(\phi(x,t))$. Then:

  

$$
H'(t) = A(t)H(t)
$$

The solution, analogous to the scalar case, is $e^{\int_0^t A(s)ds}$, which means that $D_1\phi_F(x,t)= e^{\int_0^t DF(\phi(x,s))ds}$


We can view $\phi$ as defining a flow in $\R^n$, and ask questions like: does the image of a set of some volume in $\R^n$ under $\phi$ have the same volume? In fluid dynamics, this is the question of compressibility. So we are asking: what are the conditions for an incompressible flow? More formally, given a set $X$ and abusing notation so that $\phi(X,t)$ is the image of $X$ under $\lambda x \to \phi(x,t)$:

  

$$
Vol(\phi(X,t)) = \int_{\phi(X,t)} 1 dx = \int_{X} |\det D_1\phi(x,t) | dx
$$

  
  

So what we want to know is the rate of change of the Jacobian $J(x,t)$=$\det D_1\phi(x,t)$ that is, $\frac{d}{dt}\det D_1\phi(x,t)$. If this is $0$, then the volume never changes.

  

Once again, let's define $H_x(t)=D_1\phi(x,t)$. Then:

  

$$
H_x'(t)_{ij} = DF(\phi(x,t))_{ik} \cdot H_x(t)_{kj}
$$

First, $H_x(0)_{ij} = D_1\phi(x,0)_{ij}=\frac{dx_i}{dx_j}=\delta_{i=j}$. This means that the initial value of $H$ is the identity matrix $I$. So know we know that if $\frac{\partial}{\partial t}J(x,t)$ is $0$, then the phase flow is incompressible and thus a volume of the space never changes under the flow.

  

OK, so now we would like to analyze $\frac{\partial}{\partial t}J(x,t)$ further.

  

Jacobi's formula is: $\frac{d}{dt}\det \phi = tr(\det(\phi)\phi^{-1}\frac{d\phi}{dt})$

??? Derivation

	First note (e.g. by working on a diagonal basis) that $\det A = \prod_i A_{ii} = e^{tr(\log A)}$. The rest follows from the chain rule.

  

This means that $\frac{d}{dt}\det H_x(t) = tr(\det(H_x(t))H_x(t)^{-1}DF(x,t)\cdot H_x(t))=tr(DF(x,t))\cdot det(H_x(t))$. Or:

$$
\det H_x(t) = \det H_x(0)e^{\int_0^ttr(DF(x(s)))ds}
$$

In other words, if the differential of $F$ is traceless, or in physics terminology, the divergence (trace of differential of $F$) is $0$, then the phase flow is incompressible.

  

Note for example that in a Hamiltonian system, divergence is $0$. To see this:

Let $F(x)=(DH(x)_1,-DH(x)_2)$. Then $\nabla\cdot F = D_1D_2H(x)-D_2D_1H(x)=D_1D_2H(x)-D_1D_2H(x)=0$.
	


### Separation of variables

  

You have some PDE, and are solving for some function $V$. Say it's a function of two arguments, although the approach generalizes. The idea is to try to find a *separable* solution of the form V(x,y)=X(x)Y(y). This turns out to be much easier, but of course, there's no reason why a solution of this form should necessarily be able to satisfy your boundary conditions. What you can do, however, in some circumstances, is to consider a solution consisting of an infinite sum of separable solutions. If you're lucky, the separable solutions will form an orthogonal and complete set

Solving the wave equation is a typical example, as below.

  

### Wave Equation Solutions

  

$$\frac{\partial^2 f(x,t)}{\partial x^2} = \frac{1}{v^2} \frac{\partial^2 f(x,t)}{\partial t^2}$$

  

Note that any function of the form $f(x)=g(x+vt)$, for an arbitrary $g$, is a solution. This fact explains the choice of the term $\frac{1}{v^2}$, because then $v$ is the velocity of the solution, in the sense that a shift in time is multiplied by the velocity $v$ to yield a shift in space. (Typically, solutions to this PDE are thought of as waves, e.g. sound waves, light waves, etc).

  

We can consider separable solutions, of the form $f(x,t)=g(x)\cdot h(t)$. Then:

  

$$ \frac{\partial^2 g(x)h(t)}{\partial x^2} = h(t)\frac{\partial^2 g(x)}{\partial x^2} = \frac{1}{v^2} \frac{\partial^2 g(x)h(t)}{\partial t^2} = g(x) \frac{1}{v^2} \frac{\partial^2 h(t)}{\partial t^2} $$

  

$$ \Rightarrow \frac{\partial^2 g(x)}{\partial x^2}\frac{1}{g(x)} = \frac{1}{h(t)v^2} \frac{\partial^2 h(t)}{\partial t^2} $$

  

Since $x$ and $t$ are independent, both sides must be constant, in order to satisfy this equality. Accordingly:

  

$$ \frac{\partial^2 g(x)}{\partial x^2} = Kg(x) $$

  

$$ \frac{\partial^2 h(t)}{\partial t^2} = Kv^2h(t) $$

  

These eigenequations have solutions:

  

$$ g(x) = ae^{\sqrt{K}t} + be^{-\sqrt{K}t} $$

  

$$ h(t) = ce^{\sqrt{K}vt} + de^{-\sqrt{K}vt} $$

  

We might have some further constraints that help us solve the problem. For instance, a common boundary condition is that $\forall t: f(0,t)=0=f(L,t)$, where $L$ is some designated point, for instance the end of a string might be one physical interpretation.

  

Then we can solve exactly, as follows:

  

$$ 0 = g(0) = a+b \Rightarrow a = -b $$

  

$$ 0 = g(L) = ae^{\sqrt{K}L} + be^{-\sqrt{L}L} \Rightarrow (a=-b=b=0) \vee (e^{\sqrt{K}L}=0=e^{-\sqrt{K}L}) $$

  

Assuming the latter disjunct, since the former leads to a trivial solution, we consider the latter. In general, if $e^{x}=e^{-x}$, then $x=ni\pi$, for $n\in \Z$ (convince yourself this is true by thinking about complex exponentials as rotations in the complex plane). So $\sqrt{K}=i\frac{n\pi}{L}$.

  
  
  

### Spherical Laplacian

  

For problems involving spheres and Laplace's equation, you often end up with a separation of variables which leads to solutions consisting of sums of Legendre polynomials. For reasons probably to do with Sturm-Liouville theory (which I understand to be the study of certain Hermitian operators on function spaces), these are complete and orthogonal, just like the corresponding sine functions you get from separation of variables in Cartesian coordinates, so can satisfy fairly arbitrary boundary conditions. More concretely, assume (just for simplicity) that $V$ is only a function of $r,\theta$. Then, taking the Laplacian in spherical coordinates:

  

$$ \frac{1}{r^2}\pd{}{r}(r^2\pd{V}{r}) + \frac{1}{\sin\theta}\pd{}{\theta}(\sin\theta\pd{V}{\theta}) = 0 $$

  

Assuming a separation of variables, we get:

  

$$ \frac{1}{r^2}\pd{}{r}(r^2\pd{R}{r}) + \frac{1}{\sin\theta}\pd{}{\theta}(\sin\theta\pd{\Theta}{\theta}) = 0 $$

  

Then both terms must be constant. If the constant takes the form $l(l+1)$, then $R( r)= Ar^l+\frac{B}{r^{l+1}}$ and $\Theta(\theta) = P_l(\cos\theta)$, where $P_l$ are the Legendre polynomials.

  

Since the Legendre polynomials are a "basis", we can write a fairly arbitrary solution as:

  

$$ V(r,\theta) = \sum_{l=0}^{\infty} (A_lr^l+\frac{B_l}{r^{l+1}})P_l(\cos\theta) $$

  
  

### Diffusion Equation

**Under construction** (duplication of material below from probability.md)

#### Derivation


For a simple random walk, we can describe not only the macroscopic equilibrium state, but also the approach to equilibrium, which is diffusion.

For a density $\rho(x,t)$, the following equation describes diffusion:

$$ \frac{\partial \rho}{\partial t} = a\frac{\partial^2 \rho}{\partial x^2} $$

This can be seen to be the continuum limit of random walks. The following derivation is from Sethna's excellent *Statistical Mechanics: Entropy, Order Parameters, and Complexity*.

Let $X(t)$ be the random variable (with density $\rho(x, t)$) for a particle's position at time $t$, and assume a discrete time step $\Delta t$, so that $X(t+\Delta t)=X(t)+L$, where $L$ is a random variable representing a step, with $E[L]=0$ and density $\chi$.

The density $\rho(x, t+\Delta t)$ is then the sum of the random variables $X(t)$ and $L$, which is the convolution of their densities:

$$\rho(x, t+\Delta t) = \int_{-\infty}^{\infty}\rho(x-z,t)\cdot \chi(z)dz$$

If we assume that the step size is very small compared to the varying of $\rho$ with $x$ then we can Taylor expand:

$$\rho(x, t+\Delta t) = \int_{-\infty}^{\infty}\left( \rho(x,t)-\frac{\partial \rho}{\partial x}z + \frac{\partial^2\rho}{\partial x^2}\frac{z^2}{2} \right)\cdot \chi(z)dz$$

$$ = \rho(x,t)\int_{-\infty}^{\infty}\chi(z)dz - \frac{\partial \rho}{\partial x}\int_{-\infty}^{\infty}\left(z \right)\cdot \chi(z)dz + \frac{1}{2}\frac{\partial^2\rho}{\partial x^2}\int_{-\infty}^{\infty}\left(z^2 \right)\cdot \chi(z)dz $$

$$ = \rho + \frac{1}{2}\frac{\partial^2\rho}{\partial x^2}\cdot Var[L] $$

Now suppose that we also assume that $\rho$ changes very little in each time step. Then, in the limit we can equate $\rho(x,t+\Delta t)-\rho(x,t)$ with $\frac{\partial\rho}{\partial t}\Delta t$

Putting together these two interpretations for $\rho(x,t+\Delta t)$ gives:

$$\frac{\partial\rho}{\partial t}= \frac{Var[L]}{2\Delta t} \frac{\partial^2\rho}{\partial x^2} $$

which not only derives the diffusion equation, but gives us the form of $a$.

#### Solution

For any choice of $t$, we first express $x\mapsto \rho(x,t)$ in the basis of complex exponentials (i.e. we express it as the inverse Fourier transform of its Fourier transform):

  

$$\rho_t(x) = \int_{\R} \mathcal{F}\rho_t(k)e^{i2\pi xk}dk$$

  

Then $\frac{\partial \rho}{\partial t} = \int_{\R} \frac{d}{dt}(\mathcal{F}\rho_t)(k)e^{i2\pi xk}dk$

  

And $\frac{\partial^2 \rho}{\partial x^2} = \int_{\R} \mathcal{F}\rho_t(k)e^{i2\pi xk}\cdot(-4\pi^2k^2)dk$

  

So, since $\frac{\partial \rho}{\partial t} = a\frac{\partial^2 \rho}{\partial x^2}$, it follows that

  

$$\int_{\R} \frac{d}{dt}(\mathcal{F}\rho_t)(k)e^{i2\pi xk}dk = \int_{\R} \mathcal{F}\rho_t(k)e^{i2\pi xk}\cdot(-a4\pi^2k^2)dk$$

  

Comparing terms, we have that:

  

$$ \frac{d}{dt}(\mathcal{F}\rho_t)(k) = -a4\pi^2k^2\mathcal{F}\rho_t(k) $$

  

which implies that $(\mathcal{F}\rho_t)(k)=(\mathcal{F}\rho_0)(k)e^{-a4\pi^2k^2t}$

  

That gives us:

  

$$\rho_t(x) = \int_{\R} (\mathcal{F}\rho_0)(k)e^{-a4\pi^2k^2t}e^{i2\pi xk}dk$$

  

This tells us that as $t$ increases, only values of $k$ close to $0$ will matter, which means that $\rho_t(x)$ will be increasingly uniform. As you'd expect for diffusion.

  

### Helmholtz theorem

  

Any vector field $F$ which is differentiable and goes to $0$ quicker than $\frac{1}{r}$ admits a decomposition:

  

$$ F(r ) = \frac{1}{4\pi} \left(\nabla\times\left( \int \frac{\nabla_{r'}\times F(r')}{||r-r'||} \right) - \nabla\left( \int\frac{\nabla_{r'}\cdot F(r')}{||r-r'||} \right) \right)$$

## Continuity equation

A continuity equation states that the change in a volume is fully determined by flux across its boundary (assuming there are no sources or sinks). For example in 3 dimensions:

$$
\frac{d}{dt}\int_V\rho  = \int_{\partial V} \dot x \rho 
$$

Observe how the dimensions work out correctly if $x : L$ and $t : T$.

Stokes' theorem now tells us:

$$
\int_V\frac{d}{dt}\rho = \frac{d}{dt}\int_V\rho = \int_{\partial V} \dot x \rho =_{Stokes} \int_{V} \nabla\cdot \dot x \rho 
$$

so 

$$
\frac{d}{dt}\rho = \nabla\cdot \dot x \rho
$$

Or for a 4-vector $j = (\rho, (\frac{d}{dt}\overrightarrow x) \rho)$, $\partial_\mu j^\mu = 0$.

