"Signal" is an electrical engineering term for "function". Filtering is the idea of taking a signal $f$, diagonalizing it (i.e. Fourier transforming), doing some function on $\mathcal{F}f$ like zeroing out some of it, and then inverting the transform. That's (at least one of) the foundational ideas of signal processing.

As an example, consider the process of denoising. We model a noisy signal as $n=v+p$, where $p$ is the noise, and we want to design an LTI that denoises. To wit, let $h$ be the impulse response of $L$, and $q=h*p$, so that $Ln=Lv+q$.

Note that (using capital letters for Fourier transforms of functions):

$$||q||^2 = ||\mathcal{F}q||^2 = \int_{-\infty}^{\infty}|\mathcal{F}q(s)|^2ds = \int_{-\infty}^{\infty}|H(s)|^2|P(s)|^2ds $$

Now suppose that the noise $p$ is white, which here means that $\exists C. \forall s. P(s)=C$. That means that $||q||^2 = C^2||H||^2$. We now apply Cauchy-Schwartz to great effect, by noting that:

$$ ||w(t)||^2 = ||\mathcal{F}^{-1}w(t)||^2 = ||\int_{-\infty}^{\infty}(H\cdot V)(s)e^{2\pi i st}ds||^2$$

$$ \leq ||\int_{-\infty}^{\infty}H(s)ds||^2 ||\int_{-\infty}^{\infty}V(s)e^{2\pi i st}ds||^2 $$

$$ \leq \int_{-\infty}^{\infty}|H(s)|^2ds \int_{-\infty}^{\infty}|V(s)|^2ds $$

Adding a definition, we have the signal to noise ratio:

$$ SNR := \frac{|w(t)|^2}{||q||^2} \leq \frac{1}{C^2}\int_{-\infty}^{\infty}|V(s)|^2ds$$

We maximize the SNR by attaining equality in Cauchy-Schwartz. Recall that this happens when the two vectors lie in the same span, which here means that $H$ is proportional to $\mathcal{F}ve^{2\pi ist}$. (This is the matched filter theorem, and $H$ in the span is the matched filter).