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

Laplace published a series of studies proving various interesting properties of the normal distribution and providing a first, non-rigorous proof of the **central limit theorem**. This theorem was latter formalized and proved himself to be one of the most important results in statistics.

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

Where we just used the properties of the logarithms. Now, let's consider $x=\dfrac{k-np}{{\sqrt{npq}}}$. Then, ${k=np+x{\sqrt {npq}}}$.

Thus:

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