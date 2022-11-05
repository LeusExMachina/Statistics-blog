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

# Research 13 - concepts of population and sampling distribution

Very often, in past researches, we have used the concept of statistical population, that is a set of so called statistical units. Each statistical unit is an object or an event similar to the others and, all together, statistical units are what we are interested to study.

A population can be either a finite set of well known objects (e.g. the set of all the students in a school) or a potentially infinite set of events (e.g. all the possible hands in poker).

In descriptive and inferential Statistics, while the concept of population stays the same, the way the population is considered changes a lot.

In **descriptive Statistics**, the population that we are interested to study is well known. So the purpose of descriptive Statistics, as the name itself says, is to produce informations that describe and summarize the features of this known population.

In **statistical inference**, instead, the population is unknown. We have instead access to one (or more than one) sample of the population, and the purpose of the discipline is to infer informations about the larger population starting from the sample.

One of the most important instruments used by inferential Statistics is the concept of **sampling distribution**.

Formally, a sampling distribution is the probability distribution of a given random-sample-based statistic. If an arbitrarily large number of samples, each involving multiple observations, were separately used in order to compute one value of a statistic for each sample, then the sampling distribution is the probability distribution of the values that the statistic takes on.[2]

Let's try to explain this concept better with an example. 

Given a certain unknown population, we can represent it with a random variable $X$. A random variable, in fact, is a variable that can assume certain values each with a certain probability and, since the population is unknown, we can only rely on the probabilities (and not on the frequencies).

A generic **random sample** of a population of size $n$ can be represented as a set of $n$ random variables:

$$\{X_i\}_n = \{X_1, X_2, ... , X_n\}$$

Each random variable $X_i$ is basically a copy of the random variable $X$, since each element of the sample belongs to the population, and then each $X_i$ and $X$ are identically distributed.

Informally, we could think to each $X_i$ as an observation on the population "immediately before" that the observation actually happens, and so $X_i$ can assume all the values that $X$ can assume. Hence, the set of random variables $\\{X_i\\}_n$ represents any possible random sample, and then any possible subset of size $n$ of the population (with repetitions, meaning that an element can appear more that once in a subset).

Given the $n$ random variables from a random sample, we can draw a statistic out of them: for example we could be interested in computing the mean of the random sample. Doing so, we will produce another random variable, called **sample mean**, defined as:

$$\bar{X} = \dfrac{X_1 + X_2 + ... + X_n}{n}$$

This new random variable "sample mean" will assume different values according to the values assumed by the random variables $X_1, X_2, ... , X_n$ that compose it. This means that the values that the sample mean $\bar{X}$ can assume are all the possible means of all the possible samples of size $n$ of the population.

As a random variable, $\bar{X}$ will have a probability distribution that assigns a probability to each value that $\bar{X}$ can assume: in fact, given an arbitrarily large number of samples, we will have that the mean of each sample will match some values more often than others, and therefore we can draw a probability distribution. This distribution will be a **sampling distribution**, since it's the probability distribution of all the values that the statistic "mean" can assume given an arbitrarily large number os samples of size $n$, and tells us the probability of the mean to assume a certain value for a generic random sample of the population.

Another example can be the **sample variance**: given our set $\\{X_i\\}_n$, we can define the sample variance as:

$$S^2 = \dfrac{1}{n}(\sum_{i=1}^{n}(X_i - \bar{X}))$$

Again, $S^2$ is a random variable that will assume as values all the possible variances of all the possible samples of size $n$. The probability distribution of $S^2$, that tells us with how much probability $S^2$ will assume one of those values, will be another **sampling distribution**.

Very often, it's impossible to calculate the sampling probability distribution of a statistic, that is the probability distribution of all the possible values assumed for an arbitrarily large number of random samples. What it's more common is to assume a certain sample size $n$ and a certain (large but fixed) number of random samples $m$. We can then draw with an Histogram the sampling frequency distribution of the statistics for the $m$ samples of size $n$, and then infer the mathematical model that is the probability distribution.

**References** \
[1] [https://en.wikipedia.org/wiki/Statistical_population](https://en.wikipedia.org/wiki/Statistical_population) \
[2] [https://en.wikipedia.org/wiki/Sampling_distribution](https://en.wikipedia.org/wiki/Sampling_distribution)


# Research 14 - Expected value and Variance of the Sample Mean and of the Sample Variance

in progress...

**References**