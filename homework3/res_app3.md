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

