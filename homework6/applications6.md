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
# Application 10 - sample mean and sample variance

[Click here](https://drive.google.com/uc?export=download&id=1asQfDrQQj5iYj13H1Ve_e_MEtgS2iMHM) to download the application.

A video of the application can be watched down below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app10.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

Since the code used to compute the distributions and print the histograms is very similar to the code shown for previous homework, it won't be repeated. Notice that the mean and the variance are computed using the on-line algorithms to avoid catastrophic cancellations with floating point values:

#### Mean computed with Knuth's algorithm:

```C#
public double compute_mean(double[] numbers)
{
    int count = 1;
    double mean = 0;
    int size = numbers.Length;
    for (int i = 0; i < size; i++)
    {
        mean = mean + ((numbers[i] - mean)/(double)count);
        count++;
    }
    return mean;
}
```

#### Variance computed with Welford's algorithm:
```C#
public double compute_variance(double[] numbers)
{
    double mean = 0;
    double oldM;
    double variance = 0;
    int count = 1;
    int size = numbers.Length;

    for(int j = 0; j < size; j++)
    {
        double val = numbers[j];
        oldM = mean;
        mean = mean + (val - mean) / count;
        variance = variance + (val - mean) * (val - oldM);
        count++;
    }

    variance = variance / (numbers.Length);

    return (variance);
}
```

From the video, it's possible to see that the values obtained as the mean (expected value) of the sample mean, variance of the sample mean, mean (expected value) of the sample variance and variance of the sample variance match the values we expect with a certain error, that reduces is we increase the sample size and the number of samples considered.

In particular the mean of the sample mean is very close to the mean of the entire population, the variance of the sample mean instead is very close to the variance of the entire population divided for the sample size $n$. Finally, the mean of the sample variance is very close to the variance of the entire population, multiplied for $\dfrac{n-1}{n}$.