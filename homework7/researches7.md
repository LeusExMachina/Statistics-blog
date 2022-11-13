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

# Research 15 - Lebesgue-Stieltjes integration

In order to define the Lebesgue-Stieltjes integration, we first need to define the Lebesgue integration, of which the Lebesgue-Stieltjes is a generalization. To do that, we start from a generic definition of integral.

## Lebesgue integration

In mathematics, the integral of a non-negative function of a single variable can be regarded, in the simplest case, as the area between the graph of that function and the x-axis. This definition led to the mathematical formulation of the Riemann integrals, where a certain portion of the domain of a function is divided in to intervals, and we approximate the area under the function as the sum of the areas of the rectangles built on those intervals, whose heights are given by the graph of the function in those intervals. Reducing the length of the intervals into infinitesimals $dx$, we obtain the area under the function without approximation.

This definition suffices for simple functions, but not for more exotic functions. An example of a function that cannot be integrated under the Riemann definition is the Dirichlet function, defined as:

$${\mathbf {1} _{\mathbb {Q} }(x)={\begin{cases}1&x\in \mathbb {Q} \\0&x\notin \mathbb {Q} \end{cases}}}$$

This function is nowhere continuous and so cannot be integrated under the Riemann definition. Henri Lebesgue expanded the definition of integration in order to include also more complex functions: for example, the above Dirichlet function can be integrated with the Lebesgue integrals.

### Intuition behind Lebesgue integrals [1](https://en.wikipedia.org/wiki/Lebesgue_integration#Intuitive_interpretation)

Let's now examine the difference between Riemann integrals and Lebesgue integrals from an intuitive point of view.

For the Riemann integral, the domain is partitioned into intervals, and bars are constructed to meet the height of the graph. The areas of these bars are added together, and this approximates the integral, in effect by summing areas of the form ${f(x)dx}$ where ${f(x)}$ is the height of a rectangle and ${dx}$ is its width.

For the Lebesgue integral, the range is partitioned into intervals, and so the region under the graph is partitioned into horizontal "slabs" (which may not be connected sets). The area of a small horizontal "slab" under the graph of $f$, of height $dy$, is equal to the measure of the slab's width times $dy$:

$${\mu \left(\{x\mid f(x)>y\}\right)\,dy.}$$

The Lebesgue integral may then be defined by adding up the areas of these horizontal slabs.

### Formalization of Lebesgue integrals

In order to formalize the Lebesgue integration, we must identify some preliminary concepts: outer measure, Lebesgue measure, and Lebesgue-measurable functions.

#### Outer measure [2](https://en.wikipedia.org/wiki/Outer_measure#Outer_measures)

In the mathematical field of measure theory, an outer measure or exterior measure is a function defined on all subsets of a given set with values in the extended real numbers satisfying some additional technical conditions.

More formally, given a set $X$, let $2^X$ denote the collection of all subsets of $X$, including the empty set $\varnothing$ . An outer measure on $X$ is a set function

$${\mu :2^{X}\to [0,\infty ]}$$

such that:

- null empty set: ${\mu (\varnothing )=0}$

- monotone: if $A$ and $B$ are subsets of $X$ with ${A\subseteq B}$, then ${\mu (A)\leq \mu (B)}$

- for arbitrary subsets ${B_{1},B_{2},\ldots}$ of $X$,

$${\mu \left(\bigcup _{j=1}^{\infty }B_{j}\right)\leq \sum _{j=1}^{\infty }\mu (B_{j}).}$$

#### Lebesgue measure [3](https://en.wikipedia.org/wiki/Lebesgue_measure#Definition)

Now that we have defined what a generic outer measure is, we can define the Lebesgue measure, that is based upon the Lebesgue outer measure. The Lebesgue measure is the standard way of assigning a measure to subsets of $n$-dimensional Euclidean space. For n = 1, 2, or 3, it coincides with the standard measure of length, area, or volume.

Let's now define the Lebesgue measure for subsets of the set $\mathbb {R}$ of real numbers.

For any interval ${I = [a,b]}$, or ${I=(a,b)}$, in the set $\mathbb {R}$ of real numbers, let ${\ell (I)=b-a}$ denote its length. For any subset $E\subseteq {\mathbb  {R}}$, the Lebesgue outer measure ${\lambda ^{*}(E)}$ is defined as an infimum:

$${\lambda ^{\!*\!}(E)=\inf \left\{\sum _{k=1}^{\infty }\ell (I_{k}):{(I_{k})_{k\in \mathbb {N} }}{\text{ is a sequence of open intervals with }}E\subset \bigcup _{k=1}^{\infty }I_{k}\right\}}$$

Some sets $E$ satisfy the Carathéodory criterion, which requires that for every ${A\subseteq \mathbb {R}}$,

$${\lambda ^{\!*\!}(A)=\lambda ^{\!*\!}(A\cap E)+\lambda ^{\!*\!}(A\cap E^{c}).}$$

The set of all such $E$ forms a $\sigma$-algebra. For any such $E$, its Lebesgue measure is defined to be its Lebesgue outer measure: ${\lambda (E)=\lambda ^{*}(E)}$.

A set $E$ that does not satisfy the Carathéodory criterion is not Lebesgue-measurable. Non-measurable sets do exist; an example is the Vitali sets.

Then, the Lebesgue measure of a set $E$ coincides with its Lebesgue outer measure when $E$ respects the Carathéodory criterion, while it's not defined if $E$ does not respect it.

#### Lebesgue-measurable functions [1](https://en.wikipedia.org/wiki/Lebesgue_integration#Measurable_functions)

We start with a measure space $(E, X, \mu)$ where $E$ is a set, $X$ is a $\sigma$-algebra of subsets of $E$, and $\mu$ is a (non-negative) measure on $E$ defined on the sets of $X$.

For example, $E$ can be Euclidean $n$-space $\mathbb{R}^n$ or some Lebesgue measurable subset of it, $X$ is the $\sigma$-algebra of all Lebesgue measurable subsets of $E$, and $\mu$ is the Lebesgue measure. In the mathematical theory of probability, we confine our study to a probability measure $\mu$, which satisfies $\mu(E) = 1$.

Lebesgue's theory defines integrals for a class of functions called measurable functions. A real-valued function $f$ on $E$ is measurable if the pre-image of every interval of the form $(t, \infty)$ is in $X$:

$${\{x\,\mid \,f(x)>t\}\in X\quad \forall t\in \mathbb {R}}$$

We can show that this is equivalent to requiring that the pre-image of any Borel subset of $\mathbb{R}$ be in $X$. Note that the Borel set on $\mathbb{R}$ is the smallest $\sigma$-algebra containing all the intervals of $\mathbb{R}$. This means that if we compute the pre-image of any measurable set of the co-domain through $f^{-1}$, we obtain a measurable set in the domain:

$$\forall b \in B\quad f^{-1}(b) \in X$$

The set of measurable functions is closed under algebraic operations, but more importantly it is closed under various kinds of point-wise sequential limits:

$${\sup _{k\in \mathbb {N} }f_{k},\quad \liminf _{k\in \mathbb {N} }f_{k},\quad \limsup _{k\in \mathbb {N} }f_{k}}$$

are measurable if the original sequence $(f_k)_k$, where $k \in \mathbb{N}$, consists of measurable functions.

### Lebesgue integral definition [1](https://en.wikipedia.org/wiki/Lebesgue_integration#Via_simple_functions), [4](https://it.wikipedia.org/wiki/Integrale_di_Lebesgue#Funzioni_semplici)

Now that we have formalized these concepts, we can proceed with the definition of the Lebesgue integration. The following that is reported is the definition via simple functions. A simple function is a finite linear combination of indicator functions of measurable sets.

An indicator function of a measurable set $A$ is denoted as ${\mathbf {1}}_{A}:X\to \lbrace 0,1\rbrace$ and is defined as:

$${\mathbf{1} _{A}(x)={\begin{cases}1&x\in A \\0&x\notin A \end{cases}}}$$

The Lebesgue integral of an indicator function will be:

$${\displaystyle \int 1_{A}\,d\mu =\mu (A)}$$

Where $A$ is a Lebesgue-measurable set and $\mu$ is the Lebesgue measure.

A simple function is, as we said, a finite linear combination of indicator functions of measurable sets:

$${s(x)=\sum _{i=1}^{n}a_{i}{\mathbf {1} }_{A_{i}}(x)}$$

Where ${\mathbf {1}}_{A_i}(x)$ is the indicator function for each $A_i,\quad i = {1,...,n}$. For such a function, the Lebesgue integral on a set $F \in X$ is defined as:

$${\int _{F}s\,d\mu =\sum _{i=1}^{n}a_{i}\mu (A_{i}\cap F),\quad F\in X}$$

Finally we can define the Lebesgue integral for generic functions $f$. In particular, if $f:E \to \mathbb{R}^{*}$ is a non-negative function, the Lebesgue integral of $f$ over a certain measurable set $F$ is defined as:

$${\int _{F}f\,d\mu :=\sup \int _{F}s\,d\mu ,}$$

where the supremum is evaluated considering all the simple functions $s$ such that $0\leq s\leq f$. The value of the integral is a number in the interval ${[0,+\infty ]}$.

Note that $\mathbb{R}^{*}$ is the extended real set, defined as $\mathbb{R} \cup (-\infty; +\infty)$.

The set of the functions such that:

$$\int _{E}|f|d\mu <\infty$$

is said set of the functions integrable over $E$ according to Lebesgue with respect to the the measure $\mu$ (that, for what we said, is the Lebesgue measure), or also set of summable functions, and is denoted as $L^{1}(\mu )$.

If $f$ is not a non-negative function, in order to define the Lebesgue integral we have to pass through a little workaround. In fact, if $f$ can include negative values, we can write it like ${f=f^{+}-f^{-}}$, where:

$${f^{+}(x)={\begin{cases}f(x)&{\text{if }}f(x)>0\\0&{\text{otherwise}}\end{cases}}}$$

$${f^{-}(x)={\begin{cases}-f(x)&{\text{if }}f(x)<0\\0&{\text{otherwise}}\end{cases}}}$$

Note that both $f^{+}$ and $f^{-}$ are non-negative measurable functions. Also note that:$\|f\|=f^{+}+f^{-}$.

We say that the Lebesgue integral of the measurable function $f$ exists, or is defined, if at least one of ${\int f^{+}\,d\mu }$ and ${\int f^{-}\,d\mu }$ is finite:

$$\min \left(\int f^{+}\,d\mu ,\int f^{-}\,d\mu \right)<\infty$$

In this case we define:

$${\displaystyle \int f\,d\mu =\int f^{+}\,d\mu -\int f^{-}\,d\mu}$$

Finally, we have that if

$$\int |f|\,d\mu <\infty$$

we say that $f$ is Lebesgue integrable.

## Lebesgue-Stieltjes integration [5](https://en.wikipedia.org/wiki/Lebesgue%E2%80%93Stieltjes_integration#Definition)

Now that we have defined the Lebesgue integration, we can define the Lebesgue-Stieltjes integration.

In defining the Lebesgue integration we saw that the measure used to compute the integral is the Lebesgue measure $\mu$. The Lebesgue-Stieltjes integration is the Lebesgue integration that uses the Lebesgue-Stjeltes measure $\mu_g$ instead of the Lebesgue measure $\mu$. We want now to define what the Lebesgue-Stjeltes measure is.

Given a function ${g:\left[a,b\right]\rightarrow \mathbb {R}}$ that is monotone, non-decreasing and right-continuous, we can define $w((s,t]) = g(t)-g(s)$ and $w({a}) = 0$. Alternatively, if $g$ is left continuous, we define $w([s,t)) = g(t)-g(s)$ and $w({b}) = 0$.

By Carathéodory's extension theorem, there is a unique Borel measure $\mu_g$ on $[a, b]$ which agrees with $w$ on every interval $I$. The measure $\mu_g$ arises from an outer measure given by:

$$\mu _{g}(E)=\inf \left\{\sum _{i}\mu _{g}(I_{i})\ :\ E\subset \bigcup _{i}I_{i}\right\}$$

This measure $\mu_g$ is the Lebesgue–Stieltjes measure associated with $g$. Notice how the definition is similar to the definition of the Lebesgue measure: it is in fact almost the same, but instead of $\ell (I) = b - a$ be the length of an interval $I = (a, b)$, we will define this length as $g(b) - g(a)$. If $g$ is the identity function, the Lebesgue–Stieltjes measure corresponds with the Lebesgue measure.

Now that we defined the Lebesgue-Stieltjes measure, we can simply say that the Lebesgue–Stieltjes integral:

$${\int _{a}^{b}f(x)\,dg(x)}\int _{a}^{b}f(x)\,dg(x)$$

is defined as the Lebesgue integral of $f$ with respect to the measure $\mu_g$.

**References** \
[1] [https://en.wikipedia.org/wiki/Lebesgue_integration](https://en.wikipedia.org/wiki/Lebesgue_integration) \
[2] [https://en.wikipedia.org/wiki/Outer_measure](https://en.wikipedia.org/wiki/Outer_measure) \
[3] [https://en.wikipedia.org/wiki/Lebesgue_measure](https://en.wikipedia.org/wiki/Lebesgue_measure) \
[4] [https://it.wikipedia.org/wiki/Integrale_di_Lebesgue](https://it.wikipedia.org/wiki/Integrale_di_Lebesgue) \
[5] [https://en.wikipedia.org/wiki/Lebesgue%E2%80%93Stieltjes_integration](https://en.wikipedia.org/wiki/Lebesgue%E2%80%93Stieltjes_integration)

# Research 16 - Law of large numbers

In order to prove the so-called law of large numbers, we first need two results: the **Markov (Ма́рков) Inequality** and the **Chebyshev (Чебышёв) Inequality**. After proving them, we will see how they lead to the law of large numbers.

### Markov Inequality

The Markov inequality states that given any non-negative random variable $X$ and a generic $a > 0$, then:

$$\operatorname {P} (X\geq a)\leq {\frac {\operatorname {E} (X)}{a}}$$

Let's prove the inequality. Given a non-negative random variable $X$, the espected value $\operatorname{E}(X)$ is defined as:

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

Now, consider a random variable $X$. In [research 13](https://leusexmachina.github.io/StatisticsHomework/homework6/researches6), we have seen the concept of sample mean $\bar{X}$ from the random variable $X$. We have also seen that the expected value $\operatorname {E}(\bar{X})$ is equal to the expected value $\operatorname {E}(X) = \mu$, while the variance $\operatorname{Var} (\bar{X}) = \dfrac{\sigma^2}{n}$, where $\sigma^2 = \operatorname{Var} (X)$. By the Chebyshev inequality:

$${\operatorname {P} (|\bar{X}-\operatorname {E} (\bar{X})|\geq a)\leq {\frac {\operatorname {Var} (\bar{X})}{a^{2}}}}$$

But knowing the expected value and variance of the sample mean, we can rewrite:

$${\operatorname {P} (|\bar{X}-\mu|\geq a)\leq {\frac {\sigma^2}{na^{2}}}}$$

Then, if the number of samples we take for the sample mean is arbitrarily large, meaning that $n \rightarrow +\infty$, we will have that:

$${\operatorname {P} (|\bar{X}-\mu|\geq a) \rightarrow 0}$$

But this is exactly the definition of convergence in probability: we have that for $n \rightarrow +\infty$, the sample mean $\bar{X}$ converges in probability to the expected value $\mu$.

$$\bar{X}_n \rightarrow 0 \text{  when  } n \rightarrow +\infty$$

This result is called **weak law of large numbers**.

**References** \
[1] [https://en.wikipedia.org/wiki/Markov%27s_inequality](https://en.wikipedia.org/wiki/Markov%27s_inequality) \
[2] [https://en.wikipedia.org/wiki/Chebyshev%27s_inequality](https://en.wikipedia.org/wiki/Chebyshev%27s_inequality) \
[3] [https://en.wikipedia.org/wiki/Law_of_large_numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers)
