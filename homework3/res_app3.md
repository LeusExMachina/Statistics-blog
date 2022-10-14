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

# Research on Application 3 - On-Line algorithms: an overview

By definition, an **online algorithm** is an algorithm that processes some input even if the entire input is not immediately available, but it consists in a sequence of data that the algorithm recieves over time. In particular, while an offline algorithm is a classical algorithm that needs the entire input to solve the problem related to it, an online algorithm's input consists of a stream of data. For each element of the stream, the algorithm must take a decision or produce some result. When the next element will be recieved, the algorithm will use this new element and the old result to compute a new output, and so on.

Many problems can have both offline and online solutions, although not every offline algorithm has an efficient online counterpart. A simple problem that can be resolved with both an offline and an online algorithm is the sorting problem. Let's think, for example, to the following two algorithms, both suitable to sort a list:

1. Selection Sort

2. Insertion Sort

**Selection sort** works considering the list as initially unsorted. It then extracts the minimum value from this unsorted list and puts it at the top of a new sorted list. Iterating this procedure $n$ times, we will manage to sort our numbers. It's easy to see how the algorithm can work only if the input (the unsorted list) is immediately available.

**Insertion sort** is similar to selection sort, since it creates a sorted list out of an unsorted one. However, instead of searching for the minimum in the unsorted list, insertion sort considers the unsorted list as a flow of data: for each element in this list, it will move it to the sorted list collocating it in the right place to obtain an appropriate result. It's immediate to see that this algorithm is an online algorithm: instead of having an initial unsorted list, in fact, we could have a stream of data, and insertion sort would work as well for it.

In Statistics, online algorithms are very important: it's actually not so common to have all the input immediately available, while it's much more common that the data to analyze arrive in a continuous stream and that the result produced must be updated at any iteration.

Some examples of Statistics' related online algorithms are **Knuth's recursion for mean** and **Welford's algorithm for variance**. They both work expressing the result for input $n$ as a function of the result for input $n-1$ and of the new input. Another advantage of online algorithms is that they can avoid problems with floating point numbers, like catastrophic cancellation.

Notice that, even if online algorithms are good if the input is a stream and also can mitigate problems due to floating point representation, they tend to be less computationally efficient than their offline counterparts: this because, not having the entire input, they may take inefficient decisions.


**References - Q3** \
[1] [https://en.wikipedia.org/wiki/Online_algorithm](https://en.wikipedia.org/wiki/Online_algorithm) \
[2] [https://en.wikipedia.org/wiki/Algorithms_for_calculating_variance](https://en.wikipedia.org/wiki/Algorithms_for_calculating_variance)

# Research on Application 4 - Knuth's online algorithm for the arithmetic mean

Given a sequence of $n$ numbers, their arithmetic mean is defined as the sum of all those $n$ numbers divided by the cardinality of the sequence:

$$\dfrac{1}{n}\sum_{i=1}^{n} x_{i}$$

If I want to compute the arithmetic mean in a software, an immediate "naive" implementation comes directly from the definition: I can sum all the numbers I have and then divide by the cardinality. Although apparently easy, this solution can lead to two major problems:

1. offline solution

2. floating point errors

The first point is related to the fact that this implementation, as it was presented before, needs all the input numbers to be available immediately: the algorithm is not suitable to compute the average of a stream of numbers.

This first problem can be actually easily solved by memorizing an intermediate variable "sum" that contains the sum of all the numbers and is updated every time a new input arrives, to be then divided by the number of inputs recieved. This solution, however, leads to problem two.

In fact, the second problem is related to the floating point representation of decimal numbers in computers. Since decimal numbers are represented with an exponent and a mantissa, a too big number can loose precision since the exponent grows and significant digits can be lost. This can lead to big approximations and also to catastrophic cancellations. For this reason, calculating the sum of each value to then divide by $n$ can cause severe problems.

The solution to both those critical points is using an online algorithm that expresses the value of the mean of $n$ numbers as a function of the mean of $n-1$ numbers and a new input. Applying this to a stream of inputs allows us to calculate the mean at every new input without loss of precision. The Knuth's algorithm derives from the following mathematical equivalence:

$$\dfrac{1}{n}\sum_{i=1}^{n} x_{i} = \dfrac{1}{n}(\dfrac{1}{n-1}\sum_{i=1}^{n-1} x_{i}(n-1) + x_{n})$$

If now i denote $\overline{x}_n$ the average of $n$ numbers and $\overline{x}_{n-1}$ the average of $n-1$ numbers i can rewrite:

$$\dfrac{1}{n}(\dfrac{1}{n-1}\sum_{i=1}^{n-1} x_{i}(n-1) + x_{n}) = \dfrac{1}{n}(\overline{x}_{n-1}(n-1) + x_n)$$

**References - Q4** \
[1] [https://nullbuffer.com/articles/welford_algorithm.html#references](https://nullbuffer.com/articles/welford_algorithm.html#references)