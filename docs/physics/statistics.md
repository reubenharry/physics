# Statistics

Statistics is the application of probability theory to problems in the world where your information is incomplete.

!!! Note

    There are two main schools of thought in statistics, known as *frequentist* and *Bayesian* statistics.
    
    While frequentist statistics is the more widely used, it is hard to motivate, mathematically painful to understand (though not always to use), and riddled with conceptual problems.

    Bayesian statistics is easy to motivate, straightforward to understand (though not always to apply), and beautifully consistent.

    In these notes, "statistics" refers to Bayesian statistics by default.

## Modeling uncertainty with probability

The fundamental idea of statistics is that we use a distribution as the mathematical object that describes our incomplete information of a system of interest. We call this distribution a *belief* or a belief distribution. For example, in [statistical mechanics](statisticalphysics.md), our incomplete knowledge of the configuration of the system is represented by a distribution over phase space.

The core questions of statistics are: (1) how do we determine our belief distribution to start with, and (2) how do we update it in light of new information.

(2) has an answer. If your current belief (aka your *prior* belief) is $q$, and you obtain information that constrains you to a family of distributions $P$, the best choice of distribution $p \in P$ (known as your *posterior* belief) is the one that **maximizes relative entropy $S[p,q]$ up to the constraints on $p$ you currently know**, where $q$ is your previous belief.

!!! Note

    This is known as the principle of maximum (relative) entropy. It isn't a particularly standard way of setting up Bayesian statistics, but as shown below, the much more famous Bayes rule follows from it.

## Bayes' rule

Bayes' rule arises when modeling an unknown quantity (e.g. how biased a coin is) given data (e.g. results of flipping the coin).

In this case, the relevant space is $\Theta \times X$, where the unknown quantity lives in $\Theta$ and the data lives in $X$. Then receiving data $x_0 : X$ amounts to the constraint that

$$
p(x) := \int p(\theta, x) dx = \delta(x-x_0) 
$$

We then need to determine our belief $p(\theta, x)$ which satisfies this constraint, and therefore proceed variationally with Lagrange multipliers, by maximizing:

$$
F(p,q) := S[p, q] + a(\int dx d\theta p(\theta,x)-1) \\ + \int dx \lambda(x)(\int d\theta p(\theta,x)-\delta(x-x_0)) 
$$

The condition $\delta F = 0$  yields the joint posterior $p(\theta,x) = \frac{1}{Z}q(\theta,x)e^{\lambda(x)}$ (if unclear, try with discrete distributions, and differentiate by $p_i$), with

$$
\int d\theta \frac{1}{Z}q(\theta,x)e^{\lambda(x)} = \frac{1}{Z}q(x)e^{\lambda(x)} = \delta(x-x_0)
$$

so that $p(\theta, x) = q(\theta | x)\delta(x-x_0)$, and $p(\theta) = q(\theta|x_0)$. 

This last equation is Bayes' rule. Since $q(\theta|x_0) = \frac{q(x_0|\theta)q(\theta)}{q(x_0)}$, we can derive our posterior distribution from $q(\theta)$, our (marginal) prior over $\theta$, $q(x_0)$, our marginal prior over $x_0$, and $q(x_0|\theta)$, which is known as the *likelihood* (when viewed as a function of $\theta$).

The advantage of the principle of maximum entropy is that also tells you what to do in other situations, e.g. if you receive uncertain data, or a different sort of constraint, like information about a moment of the distribution.

As for (1), with distributions over finite sets (aka discrete distributions), maximum entropy without constraints suggests that we should pick a uniform distribution, but for distributions over infinite sets (aka continuous distributions), the choice of a prior is undetermined. Often symmetry plays a role, but there's no general procedure and this forms a common criticism of Bayesian probability.

That's all there is to statistics. All that remains is to choose a prior by carefully considering your domain, and to calculate probabilities. Sometimes this is possible analytically, sometimes approximate methods are required (Monte Carlo methods, variational inference, etc.). Sometimes one makes restrictive modeling assumptions so that analytic solutions are possible (see e.g. Kalman filters).

## Why maximize entropy?

The idea is that we should choose the belief that has the most uncertainty (which is what entropy measures) that is possible under our present constraints. Otherwise we would be using information we don't have the right to assume. One can develop this idea more mathematically, see e.g. https://www.arielcaticha.com/my-book-entropic-physics.


### Independence

A joint distribution is independent if it takes the form $p(x,y) \propto p_1(x)p_2(y)$, where $p_{1,2}$ are distributions over the two respective variables. The statistical relevance of this concept is that if $p$ is such a distribution, adding a constraint to the left variable $x$ gives you no information on the marginal over $y$.

### Conditional independence

Suppose you have a distribution $p(x,y,z) \propto f(x,y)g(y,z)$. Then the marginal $p(x)$ is independent of the marginal $p(z)$ **conditional** on knowing the exact value of $y$. That is, if you know the value of $y$, then learning about $x$ does not change your belief about $z$. 