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

$$ 0 \leq f(A) \leq 1%$$

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

In mathematics **measure theory** is a theory that introduces the concept of measure. This concept is a generalization and formalization of geometrical measures like volume, area, length, but also of other kind of measures, like mass and, how we will see, probability. These seemingly distinct concepts have many similarities and can often be treated together in a single mathematical context.

The basic object of the measure theory is the **measure space**. A measure space is a triple $(X, A, \mu)$ where:

- $X$ is a set.

- $A$ is a $\sigma$-algebra on the set $X$. A $\sigma$-algebra on a set $X$ is a set of some possible subsets of $X$, closed under the operations of union, complement and intersection. Notice that in order to be a proper $\sigma$-algebra on $X$, $A$ must always contain the empty set $\emptyset$ and the whole set $X$.

- $\mu$ is a measure on the so called **measurable space** $(X, A)$.

The measure $\mu$ associates a value to each possible $E \in A$ and is a proper measure if it has the following properties:

1. **Non-negativity**: for all $E$ in $A$, we have $\mu(E) \geq 0$.

2. **Null empty set**: $\mu(\emptyset)=0$

3. **Countable additivity**: for all countable collections $\{E_{k}\}_{k=1}^{\infty}$ of pairwise disjoint sets in $A$, then:

$$\mu \left(\bigcup _{k=1}^{\infty }E_{k}\right)=\sum _{k=1}^{\infty }\mu (E_{k})$$

It's easy to see that those three properties are the same that, according to the Kolmogorov axioms, belong to the probability (the Null empty set property for probability is easily implied by the three axioms). The only big difference is the Unitarity property, that probability has while measure has not.

We can then say that probability is a measure bound to 1: in other words, probability is a measure that assigns the value 1 to the entire measure space.

Since we defined probability as a measure, we can apply to probability all the results of the measure theory: in this sense, measure theory provides the mathematical foundation of the probability theory.

In fact, while in measure theory we define a measure space, in probability theory we define a **probability space** that is a triple $(X, A, P)$ where:

- $X$ is a set.

- $A$ is a $\sigma$-algebra over $X$. An element $E \in A$ is called **event**.

- $P$ is a probability measure, that follows Kolmogorov axioms. As we said, the difference between a probability measure and the more general notion of measure is that a probability measure must assign value 1 to the entire probability space.

This definition manages to overcome all the problems that belonged to the other probability definitions (the classical definition, the frequentist interpretation, the subjective interpretation, ecc...) providing a strong mathematical base and allowing further developement of probability theory.

**References** \
[1] [https://en.wikipedia.org/wiki/Measure_(mathematics)](https://en.wikipedia.org/wiki/Measure_(mathematics)) \
[2] [https://en.wikipedia.org/wiki/Measure_space](https://en.wikipedia.org/wiki/Measure_space) \
[3] [https://en.wikipedia.org/wiki/Probability_measure](https://en.wikipedia.org/wiki/Probability_measure)

# Research 9 - Discuss some concrete examples of measure space

In the previous research we saw what measure theory is, defining the concepts of measure space and probability space. We now want to make some examples.

### Coin toss

Let's think about a coin toss: the result of this experiment can be either head ("H") or tail ("T"). We want to measure the probability of the possible events that can happen: in order to do so, we can build a probability space $(X,A,P)$ as follows:

- The set $X$ will be $X = \{H, T\}$. As we can see, $X$ contains all the possible outcomes of the experiment.

- The $\sigma$-algebra $A$ will be $A = \{\emptyset, \{H\}, \{T\}, \{H,T\}\}$. As we can see, A contains all the possible subsets of $X$, included the empty set and $X$ itself, and is closed under union, complement and intersection.

- The probability measure $P$ must respect the Kolmogorov axioms.

An example of $P$ that respects all tose axioms is the following:

$$P(\emptyset) = 0$$

$$P(\{H\}) = 0,5$$

$$P(\{T\}) = 0,5$$

$$P(\{H,T\}) = 1$$

We can notice how all the axioms are respected: 
- $P(E) \geq 0 \qquad \forall E\in A$ - **Non negativity**.
- $P(X) = 1$ - **Unitarity**
- $P(\{H\} \cup \{T\}) = P(\{H\}) + P(\{T\})$ - **Additivity**.

This probability measure is very simple, and assigns the same probability to both the outcomes of the toss. Neverthless, another possible probability measure $P$ is the following:

$$P(\emptyset) = 0$$

$$P(\{H\}) = 0,9$$

$$P(\{T\}) = 0,1$$

$$P(\{H,T\}) = 1$$

Also this probability measure is valid, since it respects Kolmogorov axioms, and may be realistic, for example, in case of a gimmicked coin.

Whatever valid $P$ we decide to choose, $(X,A,P)$ is a probability space and then, by definition, a measure space.

### Dice toss

Another possible example of measure space is given by a dice toss. In this case, the possible outcomes are all the possible faces of the dice, and then the numbers 1, 2, 3, 4, 5, 6. The probability space $(X,A,P)$ we associate to this experiment is built as follows:

- The set $X$ will be $X = \left \{1,2,3,4,5,6 \right \}$.

- The $\sigma$-algebra $A$ will be $A = \{\emptyset, \{1\}, \{2\}, \{3\}, \{4\}, \{5\}, \{6\}, \{1,1\}, \{1,2\}, ... , X\}$. Notice how A contains all the possible subsets of A, that are too many to be all reported.

- The probability measure $P$ will assign probability 0 to the empty set $\emptyset$, 1 to the whole set $X$ and $\dfrac{1}{6}$ to each unitary event. The probability of all the other events in $A$ follows by additivity.

So defined, the triple $(X,A,P)$ respects Kolmogorov axioms and is then a probability space. Then, by definition, it's also a measure space.