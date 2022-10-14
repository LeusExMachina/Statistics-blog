# Application 5 - Parse a CSV file given by a wireshark capture and print the univariate distribution of an attribute

[Click here](https://drive.google.com/uc?export=download&id=1Y37AibJSBtwltlxrXihCd6TILdeVxiSd) to download the application.

A video of the application can be watched down below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app5.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

This application has to be tought as an improvement of application 3&4. In fact, it parses a csv file and computes the univariate distribution of some variables, but it does it better and implements some new features.

First of all, the parsed file is shown in a DataGridView so that it can be analyzed by the user even before calculating the distributions. Then, we can see how the app gives the possibility to calculate the distribution of two variables, a continuous and a discrete one, and also those distributions are reported in a DataGridView.

The code used to parse the csv file and to compute the discrete univariate distribution of "Protocol" won't be shown, since it's very similar to the one reported for applications 3 & 4. The code used to calculate the continuous distribution of "Size", instead, is the following:

```C#
private void button3_Click(object sender, EventArgs e)
{

    richTextBox1.Clear();

    if (myParser == null || mySet == null || attributes == null)
    {
        richTextBox1.AppendText("Read the csv file first!\n");
        return;
    }

    Dictionary<Interval,int> dict = new Dictionary<Interval, int>();
    int max_value = 64;
    Interval i_0 = new Interval(0, max_value);

    dict[i_0] = 0;

    foreach(Packet p in mySet)
    {
        bool inserted = false;
        List<Interval> list = dict.Keys.ToList();

        int lunghezza = p.length;

        foreach(Interval i in list)
        {
            if (lunghezza >= i.down && lunghezza <= i.up)
            {
                dict[i]++;
                inserted = true;
                break;
            }

        }
        while (!inserted)
        {
            Interval i_x = new Interval(max_value+1, max_value * 2);
            max_value = max_value*2;

            dict[i_x] = 0;

            if (lunghezza >= i_x.down && lunghezza <= i_x.up)
            {
                dict[i_x]++;
                inserted = true;
            }
        }
    }

    dataGridView3.Columns.Add("Size", "Size");
    dataGridView3.Columns.Add("Absolute Frequency", "Absolute Frequency");
    dataGridView3.Columns.Add("Relative Frequency", "Relative Frequency");

    foreach(KeyValuePair<Interval,int> item in dict)
    {
        Interval inter = item.Key;
        int absfreq = item.Value;
        double relfreq = ((double)absfreq /(double)mySet.Count); 

        string s1 = inter.ToString();
        string s2 = absfreq.ToString();
        string s3 = relfreq.ToString();

        string[] row = new string[] {s1, s2, s3};

        dataGridView3.Rows.Add(row);
    }
}
```

To manage the intervals, a simple class Interval was created. This class only contains two fields "up" and "down", that are respectively the upper and the lower bound of the interval. To count the occurrencies, a dictionary was created. Initially the only interval avaliable is (0,64), but each time the software can't find in the dictionary the interval where the size of the current packet should be collocated, it creates new intervals until it reaches the correct one.

Notice that the dimension of intervals is not the same, but grows. This was done on purpose, because high-dimension packets are less frequent that low-medium dimension ones, and then a great precision at higher sizes is not necessary.