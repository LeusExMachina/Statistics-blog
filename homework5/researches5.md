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

The arithmetic mean $\bar{x}$ of a set of values $x_1, x_2, ... , x_n$ is a single value that summarizes the entire set. The mean, in other words, is a single value that is representative of an entire set of values, and that allows us to represent that set with much more synthesis. Of course representing a set of values using their mean is an approximation, and an inevitable consequence is a loss of precision in our description. What we gain, otherwise, is a (more or less) representative synthesis of an entire set.

The reliability of the arithmetic mean as a representation of a set of value can be extimated with another statistic, that is the **mean quadratic error**.

The formula to obtain the arithmetic mean of a set of $n$ values is well known and is the following:

$$ \displaystyle{\bar{x}}={\frac {1}{n}}\left(\sum _{i=1}^{n}{x_{i}}\right)={\frac {x_{1}+x_{2}+\cdots +x_{n}}{n}} $$

This formula can be derived by the various definitions we assign to the concept of mean. **Let's now consider some of them.**

1. The **arithmetic mean** of $n$ values is that value that, if substituted to the values of the set, gives the same sum.

This first definition describes the arithmetic mean of a set of $n$ values $x_1, x_2, ... , x_n$ considering the sum of those values. The mean will be that number that, if substituted to each of the values in the sum, will give the same result:

$$\bar{x} + \bar{x} + ... + \bar{x} = x_1 + x_2 + ... + x_n$$

It's easy now to see that, given this definition, the well known formula of the mean follows:

$$ n\bar{x} =  \sum _{i=1}^{n}{x_{i}}$$

$$ {\bar{x}}={\frac {1}{n}}\left(\sum _{i=1}^{n}{x_{i}}\right) $$

Hence, we derived the mean from this concept of a value that represents the set in terms of equality of the sum. This is not the only possible derivation of the mean: we obtain the same value from other definitions.

2.  The **arithmetic mean** of $n$ values is that value that equates all the positive and negative differences between the mean itself and the single values of the set.

This second definition does not consider the sum of our $n$ values $x_1, x_2, ... , x_n$, but instead refers to the difference between each of those values and a value $c$. $c$ is the mean $\bar{x}$ if the sum of all those differences (both positive and negative) is $0$, and since all positive and negative differences are equated. Translating this intuition into formulas, we will have that:

$$ \sum _{i=1}^{n}{(x_{i} - c)} $$

is the sum of all the differences (both positive and negative) between a value $c$ and each value $x_i$ of the set. As said, $c = \bar{x}$ will be the mean if:

$$ \sum _{i=1}^{n}{(x_{i} - \bar{x})} = 0$$

Again, it's easy to prove that from this definition we obtain the classical formula of the mean:

$$ \sum _{i=1}^{n}{(x_{i} - \bar{x})} = 0$$

$$ \sum _{i=1}^{n}{x_{i}} - \sum _{i=1}^{n}{\bar{x}} = \sum _{i=1}^{n}{x_{i}} - n\bar{x} = 0$$

$$ \sum _{i=1}^{n}{x_{i}} = n\bar{x}$$

$$\bar{x} = \frac{1}{n}\left(\sum _{i=1}^{n}{x_{i}}\right)$$

**References** \
[1] [https://en.wikipedia.org/wiki/Mean](https://en.wikipedia.org/wiki/Mean)