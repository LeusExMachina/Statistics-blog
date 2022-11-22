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

# Application 12 - cartesian coordinates Distribution

[Click here](https://drive.google.com/uc?export=download&id=1uApk8c5zW7Q1q-2IMuGvgfh1wK47uJMK) to download the application.

A video of the application can be watched down below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app12.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

In this application, we want to generate random cartesian coordinates (x,y) on the plane. In order to do that, we are using two Random objects in order to produce two uniform independent random variables $U_1$ and $U_2$ in the interval $(0,1)$. We then use $U_1$ and $U_2$ to obtain the polar coordinates $(R, \theta)$, using the following operations:

$$R = rU_1$$

$$ \theta = 2\pi U_2$$

Where $r$ is a certain pre-fixed maximum radius. By the simple transformations:

$$ x = R\cos(\theta)$$

$$ y = R\sin(\theta)$$

we obtain two cartesian coordinates (x, y).

In the application, what is described abovbe is obtained through a class "CoordinatesGenerator", which is the following:

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace App_PolarCoordinates_C
{


    internal class CoordinatesGenerator
    {

        Random r_module;
        Random r_angle;

        int radius;
        
        public CoordinatesGenerator(int r)
        {
            r_module = new Random();
            r_angle = new Random();

            radius = r;
        }

        public (double, double) getNewPair()
        {
            double r = r_module.NextDouble()*radius;
            double angle = r_angle.NextDouble()*2*Math.PI;

            double x = r * Math.Cos(angle);
            double y = r * Math.Sin(angle);

            return (x, y);
        }
    }
}
```

Instantiating an object of this class, we can call the method "getNewPair()", that will give us a pair $(x, y)$ of random cartesian coordinates, operating the operations described above. Notice that, though random, all the points generated are inside the circumference of centre $(0,0)$ and radius "radius", which is specified when creating the object.

The application uses the above class to generate a certain number of coordinates, which can be specified by the user, and then represents them in a plane. It then computes and show the empirical distribution of both the $x$-es and the $y$-s obtained.

From the video, we can easily notice that the distributions obtained don't follow anymore a uniform density function, but instead resemble two normal distributions. This is true because we are using something that is very similar to the **Box-Muller transform**, that was explained in research 18.

Notice then that the only difference between the actual Box-Muller transform and our coordinate generation is that for us $R = rU_1$, while for Box-Muller $R = \sqrt{-2\ln U_{1}}$. We will then generate coordinates where both $x$ and $y$ are bounded between $-r$ and $r$, and their distribution is not actually normal (although near to normal).

In **application 13**, we will implement the correct Box-Muller method and use it to generate normal random variables.

**References** \
[1] [https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller](https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller)


# Application 13 + Research on Application 7 - Various other distributions

[Click Here](https://drive.google.com/uc?export=download&id=1vbqVrHYQu6ONdIyyPpn21Ad9XuvBPaoS) to download the application

A video of the application can be watched down below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app13.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

The purpose of this application is to generate some distributions and to show them. Since those distributions are all coming from the normal distribution, first of all we need to generate a normal random variable. This is obtained using the **Box-Muller transform** that was already described for the previous application. This time, though, we implement it correctly to obtain an exact normal random variable.

The following class implements a normal random variable generator using the Box-Muller transform:

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace App_NormalDistributions_C
{
    internal class NormalRVGenerator
    {
        Random r_module;
        Random r_angle;

        double mean;
        double variance;

        double mse;

        public NormalRVGenerator(double m, double v)
        {
            r_module = new Random();
            r_angle = new Random();

            if (m >= 0) mean = m;
            else mean = 0;

            if (v > 0) variance = v;
            else variance = 1;

            mse = Math.Sqrt(variance);
        }

        public NormalRVGenerator()
        {
            r_module = new Random();
            r_angle = new Random();

            mean = 0;
            variance = 1;

            mse = Math.Sqrt(variance);
        }

        public (double, double) getNewPair()
        {
            double r = Math.Sqrt(-2*Math.Log(r_module.NextDouble()));
            double angle = r_angle.NextDouble() * 2 * Math.PI;

            double x = r * Math.Cos(angle) * mse + mean;
            double y = r * Math.Sin(angle) * mse + mean;

            return (x, y);
        }
    }
}
```

Notice that the standard Box-Muller transform generates two normal random variables $X$ and $Y$ with expected value $0$ and variance $1$. In order to have two random variables with a given mean and a given variance we multiply for a chosen mean square error $\sigma$ and sum for a chosen mean $\mu$.

After generating the random variables instantiating an object of this class, the application takes many samples and uses them to plot the empirical distribution of some random variables, coming from those two normals. Those distributions are the following:

### Normal distribution

First of all, we simply plot the distribution of one of our normal random variables by representing all the samples taken in a histogram. From the video, we can see how the plot resembles the density function of the normal distribution.

### Chi-squared distribution

The $\chi^2$ random variable is defined as a sum of $k$ normal random variables $x_k$ with mean $0$ and variance 1, each squared:

$${\chi _{k}^{2}=\sum _{i=1}^{k}x_{i}^{2}=x_{1}^{2}+\ldots +x_{k}^{2}}$$

The parameter $k$ is the degree of freedom of the random variable so defined. In the application, it is shown the distribution of a $\chi^2$ random variable with one degree of freedom, obtained computing the distribution of the elements sampled from the normal random variable, squared.

### Cauchy distribution

The Cauchy random variable has a distribution with density function:

$$f(x)={\frac  {1}{\pi }}{\frac  {y_{0}}{(x-x_{0})^{2}+y_{0}^{2}}}$$

Where $x_0$ and $y_0$ are the parameters of the function. In the particular case where $x_0 = 0$ and $y_0 = 1$, the Cauchy random variable distribution is the same distribution of a random variable $\dfrac{X}{Y}$, where $X$ and $Y$ are normal random variables with mean $0$ and variance $1$. This is the case represented in the application: the distribution shown is obtained by the division of each sample of the normal $X$ with the corresponding sample of the normal $Y$.

### Fisher-Snedecor distribution

The Fisher-Snedecor random variable is defined as:

$${F={\frac {M/m}{N/n}}}$$

where $M$ and $N$ are $\chi^2$ random variables respectively with $m$ and $n$ degrees of freedom. In the application, the distribution shown is obtained by dividing two $\chi^2$ with one degree of freedom.

### Student-T distribution

Finally, the last distribution shown is the distribution of a Student-T random variable, defined as:

$${T_{n}={\frac {Z}{\sqrt {K/n}}}}$$

where $Z$ is a normal random variable and $K$ is a $\chi^2$ random variable with $n$ degrees of freedom. In the application, the the distribution shown is obtained by dividing a normal random variable $X$ with a $\chi^2$ random variable with one degree of freedom.

**References** \
[1] [https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller](https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller) \
[2] [https://en.wikipedia.org/wiki/Normal_distribution](https://en.wikipedia.org/wiki/Normal_distribution) \
[3] [https://it.wikipedia.org/wiki/Distribuzione_chi_quadrato](https://it.wikipedia.org/wiki/Distribuzione_chi_quadrato) \
[4] [https://it.wikipedia.org/wiki/Distribuzione_di_Cauchy](https://it.wikipedia.org/wiki/Distribuzione_di_Cauchy) \
[5] [https://it.wikipedia.org/wiki/Distribuzione_di_Fisher-Snedecor](https://it.wikipedia.org/wiki/Distribuzione_di_Fisher-Snedecor) \
[6] [https://it.wikipedia.org/wiki/Distribuzione_t_di_Student](https://it.wikipedia.org/wiki/Distribuzione_t_di_Student)