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

In this application, we want to generate random cartesian coordinates (x,y) on the plane. In order to do that, we are using two Random objects in order to produce two Uniform independent random variables $U_1$ and $U_2$ in the interval $(0,1)$. We then use $U_1$ and $U_2$ to obtain the polar coordinates $(R, \theta)$, using the following operations:

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

From the video, we can easily notice that the distributions obtained don't follow anymore a uniform density function, but instead resemble two normal distributions. This is true because we are using something that is very similar to the **Box-Muller transform**.

The Box-Muller transform is a way to generate two independent normal random variables $X$ and $Y$, using two independent random variables $U_1$ and $U_2$ uniform over (0,1). The way $X$ and $Y$ are computed is the following:

$${X=R\cos(\Theta )={\sqrt {-2\ln U_{1}}}\cos(2\pi U_{2})}$$

$${Y=R\sin(\Theta )={\sqrt {-2\ln U_{1}}}\sin(2\pi U_{2})}$$

Notice then that the only difference between the actual Box-Muller transform and our coordinate generation is that for us $R = rU_1$, while for Box-Muller $R = \sqrt{-2\ln U_{1}}$. We will then generate coordinates where both $x$ and $y$ are bounded between $-r$ and $r$, and their distribution is not actually uniform (although near to uniform).

In **application 13**, we will implement the correct Box-Muller method and use it to generate normal random variables.

**References** \
[1] [https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller](https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller)


# Application 13 - Various other distributions

[Click Here](placeholder) to download the application

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

**References** \
[1] [https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller](https://it.wikipedia.org/wiki/Trasformazione_di_Box-Muller) \
[2] [https://en.wikipedia.org/wiki/Normal_distribution](https://en.wikipedia.org/wiki/Normal_distribution) \
[3] [https://it.wikipedia.org/wiki/Distribuzione_chi_quadrato](https://it.wikipedia.org/wiki/Distribuzione_chi_quadrato) \
[4] [https://it.wikipedia.org/wiki/Distribuzione_di_Cauchy](https://it.wikipedia.org/wiki/Distribuzione_di_Cauchy) \
[5] [https://it.wikipedia.org/wiki/Distribuzione_di_Fisher-Snedecor](https://it.wikipedia.org/wiki/Distribuzione_di_Fisher-Snedecor) \
[6] [https://it.wikipedia.org/wiki/Distribuzione_t_di_Student](https://it.wikipedia.org/wiki/Distribuzione_t_di_Student)