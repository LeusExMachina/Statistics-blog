<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$']]
    }
  };
</script>

# Research 15 - Labesgue-Stieltjes integration

In progress...

**References**

# Research 16 - Law of large numbers

In order to prove the so called law of large numbers, we first need two results: the **Markov (Ма́рков) Inequality** and the **Chebyshev (Чебышёв) Inequality**. After proving them, we will see how they lead to the Law of large numbers.

### Markov Inequality

The Markov inequality states that given any non-negative random variable $X$ and a generic $a > 0$, then:

$$\operatorname {P} (X\geq a)\leq {\frac {\operatorname {E} (X)}{a}}$$

Let's prove the inequality. Given a non-negative random variable $X$, the espected value $E(X)$ is defined as:

$${\operatorname {E} (X)=\int _{-\infty }^{+\infty }xf(x)\,dx}$$

But since $X$ is non-negative, we can write:

$${\operatorname {E} (X)=\int _{0 }^{+\infty }xf(x)\,dx}$$

Now, by the properties of Riemann integrals, for any $a >0$, we can write:

$${\operatorname {E} (X)=\int _{0 }^{+\infty }xf(x)\,dx = \int _{0 }^{a}xf(x)\,dx + \int _{a}^{+\infty }xf(x)\,dx}$$

This leads to a simple first inequality:

$${\operatorname {E} (X) \geq \int _{a}^{+\infty }xf(x)\,dx}$$

In fact, we just removed one of the two terms of the sum that composed the expected value in the previous formula. If we now replace the $x$ in the integral with $a$, we can write that:

$${\operatorname {E} (X) \geq \int _{a}^{+\infty }xf(x)\,dx \geq \int _{a}^{+\infty }af(x)\,dx}$$

In fact, since $x$ is monotonous and growing from $a > 0$ to $+\infty$, replacing $x$ with the constant $a$ can only lead to a smaller or at most equal result. Finally then we have obtained that:

$${\operatorname {E} (X) \geq \int _{a}^{+\infty }af(x)\,dx = a\int _{a}^{+\infty }f(x)\,dx}$$

But then the proof easily follows: in fact, the cumulative distribution function associated to $X$, defined as $\operatorname {F} (x) = \operatorname {P} (X < x)$, can be computed as:

$${\operatorname {F} (x) = \int _{-\infty}^{x}f(t)\,dt}$$

If $X$ is non-negative:

$${\operatorname {F} (x) = \int _{0}^{x}f(t)\,dt}$$

But then:

$${\int _{a}^{+\infty }f(x)\,dx = 1 - \int _{0}^{a}f(x)\,dx = 1 - \operatorname {F} (a) = 1 - \operatorname {P} (X < a) = \operatorname {P} (X \geq a)}$$

Hence we obtain:

$${\operatorname {E} (X) \geq a\operatorname {P} (X \geq a)}$$

$$\operatorname {P} (X\geq a)\leq {\frac {\operatorname {E} (X)}{a}}$$

That is the Markov inequality.

### Chebyshev Inequality

The Chebyshev inequality is a result that immediately follows from the Markov inequality. In fact, it states that given any random variable $X$, then:

$${\operatorname {P} (|X-\operatorname {E} (X)|\geq a)\leq {\frac {\operatorname {Var} (X)}{a^{2}}}}$$

The proof easily follows from the Markov inequality. In fact, if $X$ is a random variable, then $\|X-\operatorname {E} (X)\|^2$ is a non-negative random variable. Hence, for this new random variable the Markov inequality is valid and then $\forall A > 0$:

$${\operatorname {P} (|X-\operatorname {E} (X)|^2\geq A)\leq \frac{\operatorname {E} (|X-\operatorname {E} (X)|^2)}{A}}$$

But $\operatorname {E} (\|X-\operatorname {E} (X)\|^2)$ is the definition of variance for $X$. Then, if we put $a = \sqrt{A}$, we obtain:

$${\operatorname {P} (|X-\operatorname {E} (X)|\geq a)\leq {\frac {\operatorname {Var} (X)}{a^{2}}}}$$

That is the Chebyshev inequality.

### Law of large numbers

Let's consider now any random variable $X$. In [research 13](https://leusexmachina.github.io/StatisticsHomework/homework6/researches6), we have seen the concept of sample mean $\bar{X}$ from the random variable $X$. We have also seen that the expected value $\operatorname {E}(\bar{X})$ is equal to the expected value $\operatorname {E}(X) = \mu$, while the variance $\operatorname{Var} (\bar{X}) = \dfrac{\sigma^2}{n}$, where $\sigma^2 = \operatorname{Var} (X)$. By the Chebyshev inequality:

$${\operatorname {P} (|\bar{X}-\operatorname {E} (\bar{X})|\geq a)\leq {\frac {\operatorname {Var} (\bar{X})}{a^{2}}}}$$

But knowing expected value and variance of the sample mean, we can rewrite:

$${\operatorname {P} (|\bar{X}-\mu|\geq a)\leq {\frac {\sigma^2}{na^{2}}}}$$

But then, if the number of samples we take for the sample mean is arbitrarily large, meaning that $n \rightarrow +\infty$, we will have that:

$${\operatorname {P} (|\bar{X}-\mu|\geq a) \rightarrow 0}$$

But this is exactly the definition of convergence in probability: we have that for $n \rightarrow +\infty$, the sample mean $\bar{X}$ converges in probability to the expected value $\mu$.

$${{\bar{X}}_{n}\ \rightarrow\ \mu \qquad {\textrm {when}}\ n\to \infty}$$

This result is called **weak law of large numbers**.

**References** \
[1] [https://en.wikipedia.org/wiki/Markov%27s_inequality](https://en.wikipedia.org/wiki/Markov%27s_inequality) \
[2] [https://en.wikipedia.org/wiki/Chebyshev%27s_inequality](https://en.wikipedia.org/wiki/Chebyshev%27s_inequality) \
[3] [https://en.wikipedia.org/wiki/Law_of_large_numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers)