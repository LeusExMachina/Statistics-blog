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

# Research 10 - Various derivations of the arithmetic mean and other common types of average

The word "Statistics" can assume various meanings, according to what we are referring about. Until now, we considered "Statistics" as a science that regards data and their collection and elaboration. Neverthless, more specifically, a "Statistic" is a function of the observed data: after collecting informations from a population, organizing them into a dataset and maybe creating distriubutions for various attributes, we may want to obtain more informations from those data applying a function on them: this funnction is a statistic.

Examples of statistics as functions over a set of data are, for example:

- Mean

- Median

- Standard Deviation

- Variance

- Mean quadratic error

Let's now focus on the **mean**, on its possible meanings, kinds, and derivations.

### Arithmetic mean

The arithmetic mean $\bar{x}$ of a set of values $x_1, x_2, ... , x_n$ is a single value that summarizes the entire set. The mean, in other words, is a single value that is representative of an entire set of values, and that allows us to represent that set with much more synthesis. Of course representing a set of values using their mean is an approximation, and an inevitable consequence is a loss of precision in our description. What we gain, otherwise, is a (more or less) representative synthesis of an entire set.

The reliability of the arithmetic mean as a representation of a set of values can be extimated with another statistic, that is the **mean quadratic error**.

The formula to obtain the arithmetic mean of a set of $n$ values is well known and is the following:

$$ \displaystyle{\bar{x}}={\frac {1}{n}}\left(\sum _{i=1}^{n}{x_{i}}\right)={\frac {x_{1}+x_{2}+\cdots +x_{n}}{n}} $$

This formula can be derived by the various definitions we assign to the concept of mean. **Let's now consider some of them.**

- (1) The **arithmetic mean** of $n$ values is that value that, if substituted to the values of the set, gives the same sum.

This first definition describes the arithmetic mean of a set of $n$ values $x_1, x_2, ... , x_n$ considering the sum of those values. The mean will be that number that, if substituted to each of the values in the sum, will give the same result:

$$\bar{x} + \bar{x} + ... + \bar{x} = x_1 + x_2 + ... + x_n$$

It's easy now to see that, given this definition, the well known formula of the mean follows:

$$ n\bar{x} =  \sum _{i=1}^{n}{x_{i}}$$

$$ {\bar{x}}={\frac {1}{n}}\left(\sum _{i=1}^{n}{x_{i}}\right) $$

Hence, we derived the mean from this concept of a value that represents the set in terms of equality of the sum. This is not the only possible derivation of the mean: we obtain the same value from other definitions.

- (2) The **arithmetic mean** of $n$ values is that value that equates all the positive and negative differences between the mean itself and the single values of the set.

This second definition does not consider the sum of our $n$ values $x_1, x_2, ... , x_n$, but instead refers to the difference between each of those values and a value $c$. $c$ is the mean $\bar{x}$ if the sum of all those differences (both positive and negative) is $0$, and then all positive and negative differences are equated. Translating this intuition into formulas, we will have that:

$$ \sum _{i=1}^{n}{(x_{i} - c)} $$

is the sum of all the differences (both positive and negative) between a value $c$ and each value $x_i$ of the set. As said, $c = \bar{x}$ will be the mean if:

$$ \sum _{i=1}^{n}{(x_{i} - \bar{x})} = 0$$

Again, it's easy to prove that from this definition we obtain the classical formula of the mean:

$$ \sum _{i=1}^{n}{(x_{i} - \bar{x})} = 0$$

$$ \sum _{i=1}^{n}{x_{i}} - \sum _{i=1}^{n}{\bar{x}} = \sum _{i=1}^{n}{x_{i}} - n\bar{x} = 0$$

$$ \sum _{i=1}^{n}{x_{i}} = n\bar{x}$$

$$\bar{x} = \frac{1}{n}\left(\sum _{i=1}^{n}{x_{i}}\right)$$

We can then see how we could derive the mean and its formula also from a different definition. This means that the same value $\bar{x}$, that is the arithmetic mean, can assume various meanings and represent the original set in various ways.

- (3) The **arithmetic mean** of $n$ values is that value that, globally, minimizes the distance between itself and the values of the set

The final definition of mean we consider refers to the intuitive notion of the average as that value that is in the "middle" of all the values that compose the set and that is closest to those values that appear more frequently in the sequence.

If we formalize this concept, we can say that the mean is that value that minimizes the overall distance between itself and each value of the set. The overall distance is the following:

$$\sum_{i=1}^{n}{(x_i - c)^2}$$

Where $(x_i - c)^2$ is the distance $d(x_i, c)$ between $x_i$ and $c$. We have that $c = \bar{x}$ will be the mean if and only if it's the value that minimizes this expression:

$$min(\sum_{i=1}^{n}{(x_i - c)^2})$$

In order to prove this, we can show that the value $c$ that minimizes this expression is obtained through the classical formula of the mean. In fact:

$$ s(c) = \sum_{i=1}^{n}{(x_i - c)^2} = $$

$$= \sum_{i=1}^{n}{(x_i^2 - 2cx_i + c^2)} = $$

$$= \sum_{i=1}^{n}{x_i^2} -\sum_{i=1}^{n}{2cx_i} + \sum_{i=1}^{n}{c^2} = $$

$$= \sum_{i=1}^{n}{x_i^2} -2c\sum_{i=1}^{n}{x_i} + nc^2$$

If we differentiate this function on $c$ and then equate the derivative to $0$ in order to get the minimum we obtain:

$$ s'(c) =-2\sum_{i=1}^{n}{x_i} + 2nc = 0$$

$$ \sum_{i=1}^{n}{x_i} = nc $$

$$ c = \bar{x} = \frac{1}{n}\left(\sum _{i=1}^{n}{x_{i}}\right)$$

That is the formula of the arithmetic mean.

We then showed many of the various derivations of the arithmetic mean. Each derivation obtains the same formula given a different definition: for this reason, the arithmetic mean is a value that includes all the properties described by those definitions, and includes, in its synthesis of the starting set, all the informations we described.

### Generalization of the concept of mean

Until now, we described the arithmetic mean, that is the most common and widely used average and the one we commonly refer to with the word "mean". Although that, the concept of average as we described it until now can be generalized in order to define not only other types of mean, but also other statistics.

#### Center of order r

First of all, let's consider the third definition of mean we gave, as the value that minimizes the overall distance $\sum_{i=1}^{n}{(x_i - c)^2}$, where $d(x_i, c) = (x_i - c)^2$ is the distance between $x_i$ and $c$. However, we can generalize this concept of distance and say that:

$$d(x_i, c) = |x_i - c|^r$$

We can now search for the value $c$ that minimizes the formula:

$$min(\sum_{i=1}^{n}{d(x_i, c)}) = min(\sum_{i=1}^{n}{|x_i - c|^r})$$

This value will be the mean $\bar{x}$ if $r = 2$. In general, $c$ will be the so called **center of order r** of our set of values. We can easily notice that, if $r = 1$, this center matches with the median of our set of values.

#### Geometric and Harmonic mean

Let's now consider the first definition of the arithmetic mean we gave, as the value that, if substituted to the values of the set, gives the same sum. What if instead of the value that gives the same sum we are interested in the value that gives the same product? We will then have:

$$\bar{x} * \bar{x} * ... * \bar{x} = x_1 * x_2 * ... * x_n$$

Then if we formalize this:

$$\bar{x}^n = \prod_{i=1}^{n}{x_i} => \bar{x} = \sqrt[n]{\prod_{i=1}^{n}{x_i}}$$

We have that, so defined, $\bar{x}$ is the **geometric mean** of our numbers.

If instead we want the value for which the sum of its reciprocal for $n$ times is identical to the sum of the reciprocals of the values of the set, we obtain the **harmonic mean**, defined as:

$${\bar{x}} = n\left(\sum _{i=1}^{n}{\frac {1}{x_{i}}}\right)^{-1}$$

#### Power mean

Arithmetic, geometric and harmonic mean are all generalized under the concept of **power mean**, defined as follows:

$$\bar{x}(m)=\left({\frac {1}{n}}\sum _{i=1}^{n}x_{i}^{m}\right)^{\frac {1}{m}}$$

This is the power mean of order m. We can notice that if $m = 1$ we have the **arithmetic mean**, if $m = -1$ we have the **power mean**, while for $\lim{m \to 0}$ we have the **geometric mean**.

**References** \
[1] [https://en.wikipedia.org/wiki/Mean](https://en.wikipedia.org/wiki/Mean) \
[2] [https://math.stackexchange.com/questions/2554243/understanding-the-mean-minimizes-the-mean-squared-error](https://math.stackexchange.com/questions/2554243/understanding-the-mean-minimizes-the-mean-squared-error)

# Research 11 - Mathematical convergence and convergence in probability

In progress...

**References**

# Research 12 -  Descriptive Statistics and Inferential Statistics. The role of probability and probability distributions.

As I mentioned in [research 1](https://leusexmachina.github.io/StatisticsHomework/homework1/researches), the discipline of Statistics can be divided in 2 major branches, that are:

1. Descriptive statistics

2. Inferential statistics

Descriptive statistics defines methods and processes to describe or summarize data and features. In descriptive statistics we have a certain **known** population, that is a set of statistical units. Through a process of survey we get informations on those statistical units about those attributes we decide to analyze: we often mentioned that the structure used by descriprive statistics to collect and store those informations is the *dataset*.

Then in our dataset we will have all the informations about a population (of course only those informations we decide to collect): given this dataset, we can analyze the informations collected through the various methods and instruments descriptive statistics defines.

For example, given a certain dataset, we can choose one or more attributes and compute the univariate or multivariate distribution of those attributes. These distributions report the real frequencies (absolute or relative) of the values (or combination of values) of the attributes we chose. We can also compute some statistics (as functions on the data) of the collected informations: some examples are the mean, the median, ecc...

To summarize, descriptive statistics cares about entire sets of known entities, and describes the tendencies of those sets.

Inferential statistics is very different from descriptive statistics. In fact, the target of inferential statistics is not to describe a given known population, but to inference informations on an **unknown** population, having only a sample of it.

In other words, while in descriptive statistics the population is known and the purpose of the discipline is to describe it, in inferential statistics only a sample of the population can be analyzed, and the goal is to determine with more or less precision the general tendencies of the whole population given the analysis of the sample.

Inferential statistics is very important, for example, in scientific medical research: in medical trials a medicine is tested only on a representative sample of the entire world population, and the collected data are used to infernce the effectiveness of the medicine on the entire population.

When we pass from descriptive to inferential statistics, the concept of probability starts to have a role. In fact, when we are in descriptive statistics, we don't need probability: we analyze the *frequency* of events and attribute values, since the entire population is known and measurable. Otherwise, in inferential statistics, we cannot determine the frequency of a certain event or attribute value, since the great majority of the population is unknown and can't be measured. What we try to infer, instead, is the **probability** of a certain event or of a certain attribute value on the entire population, given its frequency in the sample set.

The same thing happens for distributions. In descriptive statistics, all the distributions we saw were frequency distributions, that summarize the frequency of the values that one or more attributes can assume in a certain known set of statistical units. If we pass to inferential statistics we can't determine a frequency distribution for the unknown population. What we can try to do is to assign to the unknown population some **probability distributions**, that are mathematical models that we can't really observe, but that we inference on the empirical frequency distribution calculated on the sample set with a certain error.

There are various possible probability distributions, both continuous and discrete: all of them are just models associated to an unknown population according to the data obtained by the sample set.

What we can say is that probability and probability distributions are generalizations of the concepts of frequency and frequency distributions that work also for unknown populations we inference on.

**References** \
[1] [https://en.wikipedia.org/wiki/Descriptive_statistics](https://en.wikipedia.org/wiki/Descriptive_statistics) \
[2] [https://en.wikipedia.org/wiki/Statistical_inference](https://en.wikipedia.org/wiki/Statistical_inference)