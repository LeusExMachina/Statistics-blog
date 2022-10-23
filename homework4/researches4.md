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

# Research 7 - Illustrate the parallelism between the properties of the relative frequency and the axioms for probability measure

In the previous researches, we defined in a detailed way what is the relative frequency of a value of a certain attribute. We described also how it can be calculated given a univariate or multivariate distribution and we introduced also the concepts of marginal and conditional relative frequency.

Doing this, we intuitively described and used some properties that any relative frequency has, and that we now want to formalize. Let's define $A$ and $B$ as "events": for example $A$ can be "Attribute $X$ has value $X_1$", while $B$ can be "Attribute $X$ has value $X_2$". Those properties are the following:

1. Relative frequency is non negative and included between 0 and 1:

$$ 0 <= f(A) <= 1%$$

2. If $A$ and $B$ are **disjoint events**, meaning that one can't happen if the other one happened, then the relative frequency of $A$ or $B$ is given by the sum of the two single relative frequencies:

$$ f(A \cup B) = f(A) + f(B) $$

3. The relative frequency of the empty set is 0, where for empty set we consider an event that never happens in the given population. The relative frequency of the "Population" is 1, where for "Population" we mean an event, or union of events, that happen for each unit in the given population:

$$ f(\emptyset) = 0 $$

$$ f(Population) = 1 $$

We can now notice how those three properties are almost identical to the three axioms of probability, or Kolmogorov axioms, given by the mathematician Andrey Kolmogorov in 1933. In fact, Kolmogorov defined probability $P$ as a Measure on the Measure Space $(\Omega, F, P)$ (further details about this in the next research) with the following properties:

1. **Non negativity**  - The probability of an event is a non-negative real number:

$$ P(E)\in \mathbb {R} ,P(E)\geq 0\qquad \forall E\in F $$

2. **Unitarity** - The maximum possible probability is the probability of the whole set (union of all possible events) that is 1:

$$ P(\Omega) = 1 $$

3. **Additivity** - The probability of the union of two disjoint events is the sum of the probabilities of those events:

$$ P\left(\bigcup _{i=1}^{\infty }E_{i}\right)=\sum _{i=1}^{\infty }P(E_{i}) $$

It's easy to see how those axioms can be directly mapped on the properties of the relative frequency.

A possible explanation of this parallelism is given by the so called "frequentist definition" of probability, that is one of the possible definitions that try to describe what probability is. The definition says that, given a repeatable experiment and a set of events that are all the possible outcomes of that experiment, we can measure the frequency of the various events after a certain number of repetitions. We then define the probability of a certain event as the limit of the frequency of the same event, meaning that probability is the frequency we would obtain if we could do infinite repetitions of the same experiment.

Of course this definition has many problems: for example it uses in a not proper way the concept of mathematical limit, and is suitable only for repeatable experiments. Neverthless, the definition links probability to frequency. It's then obvious, if probability is a frequency, that it must have all the properties that also frequency has.

**References** \
[1] [https://en.wikipedia.org/wiki/Probability_axioms](https://en.wikipedia.org/wiki/Probability_axioms)

# Research 8 - Illustrate how measure theory provides the mathematical foundation for the probability theory



**References** \
[1] [https://en.wikipedia.org/wiki/Measure_(mathematics)](https://en.wikipedia.org/wiki/Measure_(mathematics)) \
[2] [https://en.wikipedia.org/wiki/Measure_space](https://en.wikipedia.org/wiki/Measure_space) \
[3] [https://en.wikipedia.org/wiki/Probability_measure](https://en.wikipedia.org/wiki/Probability_measure)