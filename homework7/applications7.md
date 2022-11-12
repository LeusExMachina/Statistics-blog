# Application 11 - Binomial and interarrivals

[Click here](https://drive.google.com/uc?export=download&id=19xyXoxje391WMWFPlJiUbddhZgo7_nj-) to download the application.

A video of the application can be watched down below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app11.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

The application is very similar to the one created for [homework 4](https://leusexmachina.github.io/StatisticsHomework/homework4/applications4), but there are many different things due to the fact that this time the charts are represented in a resizeable rectangle.

First of all, instead of computing the distribution of the arriving pixels of the chart, we compute the real distribution of the real arriving points. The function that does that is the following:

```C#
private void compute_lastpoints_distribution()
{
    lastpoints_distribution = new Dictionary<Interval, int>();

    int current = (int)Math.Floor(minY);
    int max = (int)Math.Ceiling(maxY);

    int size = (int)Math.Min(maxY/6, 3);

    while (current < max)
    {
        Interval i = new Interval(current, current + size);
        current = current + size;

        lastpoints_distribution[i] = 0;
    }

    foreach (RealPoint p in lastpoints)
    {
        List<Interval> keys = lastpoints_distribution.Keys.ToList();
        bool p_inserted = false;
        foreach (Interval v in keys)
        {
            if (p.Y >= v.down && p.Y <= v.up && !p_inserted)
            {
                p_inserted = true;
                lastpoints_distribution[v]++;
            }
        }
    }
}
```

The class "RealPoints" stores the real points obtained through the tosses. Real world trajectories and the last point for each trajectories are stored in lists. The linear transformation needed to draw them is computed at each trigger of a timer, that draws again the charts with all the modifications.

Another important difference is in the way the histogram on the side of the trajectories is drawn, since the rectangle and the trajectories can be resized. The following function draws it adapting it to the size of the chart, and is called by the timer event handler:

```C#
private void drawHistogram()
{
  int maxvalue = lastpoints_distribution.Values.Max();
  int space_height = (r1.r.Right - r1.r.Left)/3;

  foreach (KeyValuePair<Interval, int> kv in lastpoints_distribution)
  {

      Interval i = kv.Key;
      int alt = kv.Value;

      int rect_height = (int)(((double)kv.Value / (double)maxvalue) * ((double)space_height));

      int down_mod = linearTransformY(i.down, minY, maxY, r1.r.Top, r1.r.Height);
      int up_mod = linearTransformY(i.up, minY, maxY, r1.r.Top, r1.r.Height);

      int size = Math.Abs(down_mod - up_mod);

      Rectangle histrect = new Rectangle(r1.r.Right, up_mod, rect_height, size);
      g.FillRectangle(Brushes.Green, histrect);
      g.DrawRectangle(Pens.Red, histrect);
  }
}
```

Finally, in this application the interarrival distribution is drawn in a histogram. The code to do that is very similar to the one of the previous applications and won't be shown again.