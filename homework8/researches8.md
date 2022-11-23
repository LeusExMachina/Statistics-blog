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

# Research 17 - possible derivations of the Normal distribution

The normal distribution has been introduced by french mathematician Abraham De Moivre. He noticed that the Binomial discrete distribution, for large values of $n$, could be approximated to a continuous distribution, that is the normal distribution. However, this result was obtained almost accidentally by De Moivre itself, and passed unnoticed. De Moivre called this distribution he found "bell-shaped exponential curve"

Later, however, the german mathematician Karl F. Gauss derived and used again this distribution in his work regarding some astronomical observations. Again, the distribution was found as a "collateral effect" of another work and could have passed unnoticed again if the french mathematician Pierre S. Laplace didn't noticed it.

Laplace published a series of studies proving various interesting properties of the normal distribution and providing a first, non-rigorous proof of the **central limit theorem**. This theorem was later formalized and proved himself to be one of the most important results in statistics.

Let's now take a look to the derivations mentioned above.

## De Moivre derivation

De Moivre managed to prove that, under specific conditions, a Binomial distribution $Y=Bi(n,p)$ can be approximated to a normal distribution with mean $np$ (the mean of the Binomial) and variance $npq$ (the variance of the binomial). Specifically, this is true for $n$ that grows very high.

More formally, as $n$ grows large, for $k$ close to $np$, it is true that:

$${n \choose k}\, p^k q^{n-k} \simeq \frac{1}{\sqrt{2 \pi npq}}\, e^{-\frac{(k-np)^2}{2npq}}, \qquad p+q=1,\ p, q > 0$$

Let's prove this result. First of all, we take into account the Stirling formula, that tells us that the factorial of a large number $n$ can be approximated as:

$$n! \simeq  n^n e^{-n}\sqrt{2 \pi n}\qquad \text{as } n \to \infty$$

Using this result, we can re-write the Binomial distribution as:

{% raw %}
$${\begin{aligned}{n \choose k}p^{k}q^{{n-k}}&={\frac{n!}{k!(n-k)!}}p^{k}q^{{n-k}} \simeq {\frac{n^{n}e^{{-n}}{\sqrt{2\pi n}}}{k^{k}e^{{-k}}{\sqrt{2\pi k}}(n-k)^{{n-k}}e^{{-(n-k)}}{\sqrt  {2\pi (n-k)}}}}p^{k}q^{{n-k}}\\&={\sqrt  {{\frac  {n}{2\pi k\left(n-k\right)}}}}{\frac{n^{n}}{k^{k}\left(n-k\right)^{{n-k}}}}p^{k}q^{{n-k}}\\&={\sqrt{{\frac{n}{2\pi k\left(n-k\right)}}}}\left({\frac  {np}{k}}\right)^{k}\left({\frac  {nq}{n-k}}\right)^{{n-k}}\end{aligned}}$$
{% endraw %}

Now, since we assumed $k$ close to $np$, we can approximate ${\tfrac{k}{n}}\to p$ and write:

{% raw %}
$${\begin{aligned}{n \choose k}p^{k}q^{{n-k}}&\simeq {\sqrt  {{\frac  {1}{2\pi n{\frac  {k}{n}}\left(1-{\frac  {k}{n}}\right)}}}}\left({\frac  {np}{k}}\right)^{{k}}\left({\frac  {nq}{n-k}}\right)^{{n-k}}\\&\simeq {\frac  {1}{{\sqrt  {2\pi npq}}}}\left({\frac  {np}{k}}\right)^{{k}}\left({\frac  {nq}{n-k}}\right)^{{n-k}}\qquad p+q=1\\\end{aligned}}$$
{% endraw %}

We can now rewrite the entire expression applying first a logarithm and then an exponential, thus obtaining:

{% raw %}
$${\displaystyle {\begin{aligned}{n \choose k}p^{k}q^{n-k}&\simeq {\frac {1}{\sqrt {2\pi npq}}}\exp \left\{\ln \left(\left({\frac {np}{k}}\right)^{k}\right)+\ln \left(\left({\frac {nq}{n-k}}\right)^{n-k}\right)\right\}\\&={\frac {1}{\sqrt {2\pi npq}}}\exp \left\{-k\ln \left({\frac {k}{np}}\right)+(k-n)\ln \left({\frac {n-k}{nq}}\right)\right\}\\\end{aligned}}}$$
{% endraw %}

Where we just used the properties of the logarithms. Now, let's consider

{% raw %}
$$x = \dfrac{(k-np)}{\sqrt{npq}}$$
{% endraw %}

Then,

{% raw %}
$${k=np+x{\sqrt {npq}}}$$
{% endraw %}

Thus we obtain:

{% raw %}
$${\begin{aligned}{n \choose k}p^{k}q^{n-k}&\simeq {\frac {1}{\sqrt {2\pi npq}}}\exp \left\{-k\ln \left({\frac {np+x{\sqrt {npq}}}{np}}\right)+(k-n)\ln \left({\frac {n-np-x{\sqrt {npq}}}{nq}}\right)\right\}\\&={\frac {1}{\sqrt {2\pi npq}}}\exp \left\{-k\ln \left({1+x{\sqrt {\frac {q}{np}}}}\right)+(k-n)\ln \left({1-x{\sqrt {\frac {p}{nq}}}}\right)\right\}\qquad p+q=1\\\end{aligned}}$$
{% endraw %}

Now we can apply the taylor approximation, for which:

{% raw %}
$${\ln \left(1+x\right)\simeq x-{\frac {x^{2}}{2}}+{\frac {x^{3}}{3}}-\cdots }$$
{% endraw %}

Obtaining:

{% raw %}
$${\displaystyle {\begin{aligned}{n \choose k}p^{k}q^{n-k}&\simeq {\frac {1}{\sqrt {2\pi npq}}}\exp \left\{-k\left({x{\sqrt {\frac {q}{np}}}}-{\frac {x^{2}q}{2np}}+\cdots \right)+(k-n)\left({-x{\sqrt {\frac {p}{nq}}}-{\frac {x^{2}p}{2nq}}}-\cdots \right)\right\}\\&={\frac {1}{\sqrt {2\pi npq}}}\exp \left\{\left(-np-x{\sqrt {npq}}\right)\left({x{\sqrt {\frac {q}{np}}}}-{\frac {x^{2}q}{2np}}+\cdots \right)+\left(np+x{\sqrt {npq}}-n\right)\left(-x{\sqrt {\frac {p}{nq}}}-{\frac {x^{2}p}{2nq}}-\cdots \right)\right\}\\&={\frac {1}{\sqrt {2\pi npq}}}\exp \left\{\left(-np-x{\sqrt {npq}}\right)\left(x{\sqrt {\frac {q}{np}}}-{\frac {x^{2}q}{2np}}+\cdots \right)-\left(nq-x{\sqrt {npq}}\right)\left(-x{\sqrt {\frac {p}{nq}}}-{\frac {x^{2}p}{2nq}}-\cdots \right)\right\}\\&={\frac {1}{\sqrt {2\pi npq}}}\exp \left\{\left(-x{\sqrt {npq}}+{\frac {1}{2}}x^{2}q-x^{2}q+\cdots \right)+\left(x{\sqrt {npq}}+{\frac {1}{2}}x^{2}p-x^{2}p-\cdots \right)\right\}\\&={\frac {1}{\sqrt {2\pi npq}}}\exp \left\{-{\frac {1}{2}}x^{2}q-{\frac {1}{2}}x^{2}p-\cdots \right\}\\&={\frac {1}{\sqrt {2\pi npq}}}\exp \left\{-{\frac {1}{2}}x^{2}(p+q)-\cdots \right\}\\&\simeq {\frac {1}{\sqrt {2\pi npq}}}\exp \left\{-{\frac {1}{2}}x^{2}\right\}\\&={\frac {1}{\sqrt {2\pi npq}}}e^{\frac {-(k-np)^{2}}{2npq}}\\\end{aligned}}}$$
{% endraw %}

We then finally obtain the approximation:

{% raw %}
$${n \choose k}p^{k}q^{n-k} \simeq {\frac {1}{\sqrt {2\pi npq}}}e^{\frac {-(k-np)^{2}}{2npq}}$$
{% endraw %}

## Gauss derivation

The previous derivation proved that, under some assumptions, a Binomial random variable can be approximated to a Normal random variable $N(\mu, \sigma^2)$, where $\mu = np$ and $\sigma^2 = npq$. As previously mentioned, this result went unnoticed and, a few years later, Gauss ended up deriving the same distribution with a totally different process.

The formal derivation of the normal distribution made by Gauss will not be reported, since it needs the knowledge of complex topics that were not covered during the lectures. Intuitively, Gauss managed to derive the distribution by studying the inference of the mean of an unknown random variable.

In particular, while studying some astronomical phenomena, Gauss calculated a specific random variable for which a certain extimation (specifically, the maximum likelihood estimation) of the mean of that random variable, given some samples of it, coincided with the sample mean. It can be proven that the only random variable with such a property has the following density function:

{% raw %}
$$f(x) = \frac {\alpha}{\sqrt {2\pi}}e^{-\frac{1}{2}\alpha(x-\mu)^2}$$
{% endraw %}

This density, for $\alpha = \frac{1}{\sigma}$, is exactly the normal density function.

## Central limit theorem

The final derivation of the normal probability distribution is the so called **central limit theorem**, that is also one of the most important results of statistics and of probability theory. The theorem states that given any sequence of $n$ independent random variables, their sum will converge to a normal random variable for $n$ large enough.

The theorem was first proved by Laplace, that understood the potential of the normal distribution and published many studies about it. However, this first proof was not very rigorous, and worked only under some strong assumptions. 

A better enunciation (and proof) of the theorem was given by **Lindeberg** and **Levy**, that however still assumed that the sequence of random variables was composed by not only independent, but also identically distributed random variables. Finally, the russian mathematician **Aleksandr Lyapunov** gave an enunciation and a proof of the theorem only assuming a sequence of independent random variables.

We want now to enunciate the classical form of the central limit theorem.

#### Classical CLT (Lindeberg–Levy)

Let's take a sequence of i.i.d. random variables $X_1, \cdots, X_n$, with $\mathbb{E}(X_i) = \mu$ and $\operatorname{Var}(X_i) = \sigma$. Let now $\bar{X} = \dfrac{X_1, \cdots, X_n}{n}$ be the sample mean of the sequence. Then, as $n$ approaches to infinity, we will have that:

$${\sqrt{n}}({\bar {X}}_{n}-\mu ) \to \mathcal {N}\left(0,\sigma ^{2}\right)$$

Meaning that the random variable so defined converges in distribution to a normal random variable with variance $\sigma^2$ and mean $0$.

**References** \
[1][http://www.science.unitn.it/probab/Mathmodels/lecture-gaussiana.pdf](http://www.science.unitn.it/probab/Mathmodels/lecture-gaussiana.pdf) \
[2][https://en.wikipedia.org/wiki/De_Moivre%E2%80%93Laplace_theorem](https://en.wikipedia.org/wiki/De_Moivre%E2%80%93Laplace_theorem) \
[3][https://en.wikipedia.org/wiki/De_Moivre%E2%80%93Laplace_theorem](https://en.wikipedia.org/wiki/De_Moivre%E2%80%93Laplace_theorem) \
[4][https://en.wikipedia.org/wiki/Central_limit_theorem](https://en.wikipedia.org/wiki/Central_limit_theorem)

# Research 18 - generation of a normal random variable

Some methods that are used to generate random values that follow a normal distribution, thus creating a normal random variable, are for example the **Box-Muller** transform and the **Marsaglia polar method**. Let's describe both of them.

## Box-Muller transform

The Box-Muller transform is a way to generate two independent normal random variables $X$ and $Y$, using two independent random variables $U_1$ and $U_2$ uniform over (0,1). The way $X$ and $Y$ are computed is the following:

$${X=R\cos(\Theta )={\sqrt {-2\ln U_{1}}}\cos(2\pi U_{2})}$$

$${Y=R\sin(\Theta )={\sqrt {-2\ln U_{1}}}\sin(2\pi U_{2})}$$

Both $X$ and $Y$ are computed considering $U_1$ as a radius and $U_2$ as an angle, and operating a transformation from polar to linear coordinates. Notice how multiplying $U_2$ by $2\pi$ is necessary to generate values between $0$ and $2\pi$, while applying the logarithm to $U_1$ guarantees both the generation of values between $0$ and $+\infty$, so that the computed pair $(X,Y)$ can be any point on the cartesian plane.

Notice also that the generated variables follow a normal distribution with mean $0$ and variance $1$. By the way, it's easy to modify the transform to generate a pair normal distributions with chosen mean and variance:

$${X=R\cos(\Theta )\sigma + \mu={\sqrt {-2\ln U_{1}}}\cos(2\pi U_{2})\sigma + \mu}$$

$${Y=R\sin(\Theta )\sigma + \mu={\sqrt {-2\ln U_{1}}}\sin(2\pi U_{2})\sigma + \mu}$$

where $\sigma$ is the chosen mean square error and $\mu$ is the chosen mean.

## Marsaglia polar method

Another method that can be used to generate a pair of independent normal random variables is the so called **Marsaglia polar method**. This method uses the same theoretical basis of the Box-Muller method, of which it represents the polar form.

This method uses again two uniform random variables $U_1$ and $U_2$ to generate two normal random variables $X$ and $Y$. Each time we want to sample a couple $(x,y)$ from the couple of normal random variables $(X,Y)$, we sample two values $(u,v)$ respectively from $U_1$ and $U_2$ such that:

$$0 < s = u + v < 1$$

We will then have:

$$x = \sqrt{-2 \ln s} \left(\frac{u}{\sqrt{s}}\right) = u \cdot \sqrt{\frac{-2 \ln s}{s}}$$

$$y = \sqrt{-2 \ln s}\left( \frac{v}{\sqrt{s}}\right) = v \cdot \sqrt{\frac{-2 \ln s}{s}}$$

Again, if we want to choose the mean $\mu$ and the variance $\sigma^2$ of the generated variables:

$$x = \sqrt{-2 \ln s} \left(\frac{u}{\sqrt{s}}\right)\cdot \sigma + \mu = u \cdot \sqrt{\frac{-2 \ln s}{s}}\cdot \sigma + \mu$$

$$y = \sqrt{-2 \ln s}\left( \frac{v}{\sqrt{s}}\right)\cdot \sigma + \mu = v \cdot \sqrt{\frac{-2 \ln s}{s}}\cdot \sigma + \mu$$

**References** \
[1] [https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller](https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller)\
[2] [https://en.wikipedia.org/wiki/Marsaglia_polar_method](https://en.wikipedia.org/wiki/Marsaglia_polar_method)