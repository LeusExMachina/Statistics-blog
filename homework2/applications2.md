# Application 2 - Make a simple demo program which uses the objects RANDOM and TIMER

[Click Here](https://drive.google.com/uc?export=download&id=19sSGEV65gdjIFecwziquKcvlF83WHmuL) to download the application.

A video of the application can be watched below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app2.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

The application I decided to create consists in a picture box and of a rich text box. Pressing the button "Start!", a timer starts to tick every 0.5 seconds; for each tick, the picturebox shows a new random colour and the rich text box appends a new string. Both the lenght and the content of the string are randomic.

The C# code is the following:

```C#
using System.Text;

namespace App_RandTim_C
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        Random random = new Random();

        private void button1_Click(object sender, EventArgs e)
        {
            timer1.Start();
            button1.Text = "Stop!";
            button1.Click -= button1_Click;
            button1.Click += button1_Stop;
        }

        private void button1_Stop(object sender, EventArgs e)
        {
            timer1.Stop();
            button1.Text = "Start!";
            button1.Click -= button1_Stop;
            button1.Click += button1_Click;
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            pictureBox1.BackColor = Color.FromArgb(random.Next(0, 256), random.Next(0, 256), random.Next(0, 256));

            int size = random.Next(0, 12);
            string s = RandomString(size);

            richTextBox1.AppendText(s + "\n");
        }

        private string RandomString(int Size)
        {
            StringBuilder builder = new StringBuilder();
            char ch;
            for (int i = 0; i < Size; i++)
            {
                ch = Convert.ToChar(Convert.ToInt32(Math.Floor(26 * random.NextDouble() + 65)));
                builder.Append(ch);
            }
            return builder.ToString();
        }
    }
}
```

It's interesting to see how the random strings are created via the RandomString function, that takes a size and generates a randomic string of length "size" using the objects StringBuilder and Random. Also the size is random, being generated randomically before calling RandomString, but can't be higher than 12.

The VB.NET code is similar and follows:

```VB
Imports System.Text

Public Class Form1

    Dim random As New Random
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        Timer1.Start()
        Button1.Text = "Stop!"
        RemoveHandler Button1.Click, AddressOf Button1_Click
        AddHandler Button1.Click, AddressOf button1_Stop
    End Sub

    Private Sub Button1_Stop(ByVal sender As Object, ByVal e As EventArgs)
        Timer1.Stop()
        Button1.Text = "Start!"
        RemoveHandler Button1.Click, AddressOf Button1_Stop
        AddHandler Button1.Click, AddressOf Button1_Click
    End Sub

    Private Sub Timer1_Tick(sender As Object, e As EventArgs) Handles Timer1.Tick
        PictureBox1.BackColor = Color.FromArgb(random.Next(0, 256), random.Next(0, 256), random.Next(0, 256))
        Dim size As Integer = random.Next(0, 12)
        Dim s As String = RandomString(size)
        RichTextBox1.AppendText(s & vbLf)
    End Sub

    Private Function RandomString(ByVal Size As Integer) As String
        Dim builder As StringBuilder = New StringBuilder()
        Dim ch As Char

        For i As Integer = 0 To Size - 1
            ch = Convert.ToChar(Convert.ToInt32(Math.Floor(26 * random.NextDouble() + 65)))
            builder.Append(ch)
        Next

        Return builder.ToString()
    End Function
End Class
```

# Applications 3 and 4 - CSV parser and univariate computing

[Click Here]() to download the application.

A video of the application can be watched below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app3&4.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

I decided to implement applications 3 and 4 in a unique single application, that parses a CSV file and then calculates the univariate distribution of an attribute i chose. In particular, the csv file i selected contains info about some videogames, and the attribute on which the distribution is calculated is "Console", that represents the particular device for which the videogame was created.

The code used to implement the parsing is the following:

```C#
private void button1_Click(object sender, EventArgs e)
{
    if (myParser != null)
    {
        myParser.Close();
    }

    richTextBox1.Clear();

    myParser = new TextFieldParser(Path.Combine(Directory.GetCurrentDirectory(), Directory.GetParent(Environment.CurrentDirectory).Parent.Parent.FullName + "\\videogames.csv"));
    myParser.Delimiters = new string[] { "," };

    attributes = myParser.ReadFields(); // reading the first line

    mySet = new List<Videogame>();

    while (!myParser.EndOfData)
    {
        string[] currentrow = myParser.ReadFields();

        string title = currentrow[0];
        int players = Convert.ToInt32(currentrow[1]);
        string publisher = currentrow[2];
        int review = Convert.ToInt32(currentrow[3]);
        int sales = Convert.ToInt32(currentrow[4]);
        int price = Convert.ToInt32(currentrow[5]);
        string console = currentrow[6];
        char rating = Convert.ToChar(currentrow[7]);
        int year = Convert.ToInt32(currentrow[8]);

        Videogame v = new Videogame(title, players, publisher, review, sales, price, console, rating, year);

        mySet.Add(v);

                
    }

    int size = mySet.Count;
            
    richTextBox1.AppendText("DataSet created! Size: " + size.ToString() + " elements\n\n" + "Attributes:\n\n");
    for(int i = 0; i < attributes.Length; i++)
    {
        richTextBox1.AppendText(attributes[i].ToString() + "\n");
    }
            
}
```

To parse the csv file, we use a TextFieldParser object, that allows us to specify a delimiter (the comma, in this case) and read a file separating the fields for each row. For each row, the fields are then stored in an object Videogame i created, and this object is put in a list. In this way, we manage to parse the entire file creating a list of Videogame objects, each of which contains all the info about one row.

We now have to calculate the univariate distribution for "Console". The code is the following:

```C#
private void button2_Click(object sender, EventArgs e)
{
    richTextBox1.Clear();

    if (myParser == null || mySet == null || attributes == null)
    {
        richTextBox1.AppendText("Read the csv file first!\n");
        return;
    }

    List<string> allvalues = new List<string>();

    foreach(Videogame v in mySet)
    {
        string console = v.Console;

        if (!allvalues.Contains(console))
        {
            allvalues.Add(console);
        } 
    }

    string[] allvaluesArr = allvalues.ToArray();
    int[] times = new int[allvaluesArr.Length];

    foreach(Videogame v in mySet)
    {
        string console = v.Console;
        for (int i = 0; i < times.Length; i++)
        {
            if (allvaluesArr[i] == console)
            {
                times[i]++;
            }
        }
    }

    richTextBox1.AppendText("Console".PadRight(50-"Console".Length) + "Absolute Frequency".PadRight(50- "Absolute Frequency".Length) + "Percentage".PadRight(50-"Percentage".Length) + "\n");

    for (int i = 0; i < times.Length; i++)
    {
        double percentage = ((double)times[i]/(double)mySet.Count)*100d;
        string perc = percentage.ToString() + "%";
        richTextBox1.AppendText(allvaluesArr[i].ToString().PadRight(50 - allvaluesArr[i].Length) + times[i].ToString().PadRight(50 - times[i].ToString().Length) + perc.PadRight(50 - perc.Length)+ "\n");
    }
}
```

First, we create a list that contains all the possible values assumed by "Console". Then we create a list with the same size, that will store the frequency of each value. We can now iterate on the set of videogames and count the frequency of each value, that is then printed on screen.

The VB code to do the same is the following.

Parsing:

```VB
Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    If myParser IsNot Nothing Then
        myParser.Close()
    End If

    RichTextBox1.Clear()

    myParser = New TextFieldParser(Path.Combine(Directory.GetCurrentDirectory(), Directory.GetParent(Environment.CurrentDirectory).Parent.Parent.FullName & "\videogames.csv"))
    myParser.Delimiters = New String() {","}

    attributes = myParser.ReadFields()

    mySet = New List(Of Videogame)()

    While Not myParser.EndOfData
        Dim currentrow As String() = myParser.ReadFields()
        Dim title As String = currentrow(0)
        Dim players As Integer = Convert.ToInt32(currentrow(1))
        Dim publisher As String = currentrow(2)
        Dim review As Integer = Convert.ToInt32(currentrow(3))
        Dim sales As Integer = Convert.ToInt32(currentrow(4))
        Dim price As Integer = Convert.ToInt32(currentrow(5))
        Dim console As String = currentrow(6)
        Dim rating As Char = Convert.ToChar(currentrow(7))
        Dim year As Integer = Convert.ToInt32(currentrow(8))
        Dim v As Videogame = New Videogame(title, players, publisher, review, sales, price, console, rating, year)
        mySet.Add(v)
    End While

    Dim size As Integer = mySet.Count

    RichTextBox1.AppendText("Dataset Created! Size: " & size.ToString & " elements" & vbLf & vbLf & "Attributes:" & vbLf & vbLf)
    For i As Integer = 0 To attributes.Length - 1
        RichTextBox1.AppendText(attributes(i).ToString() & vbLf)
    Next


End Sub
```

Univariate computing:

```VB
Private Sub Button2_Click(sender As Object, e As EventArgs) Handles Button2.Click

    RichTextBox1.Clear()

    If myParser Is Nothing OrElse mySet Is Nothing OrElse attributes Is Nothing Then
        RichTextBox1.AppendText("Read the csv file first!" & vbLf)
        Return
    End If

    Dim allvalues As List(Of String) = New List(Of String)()

    For Each v As Videogame In mySet
        Dim console As String = v.Console

        If Not allvalues.Contains(console) Then
            allvalues.Add(console)
        End If
    Next

    Dim allvaluesArr As String() = allvalues.ToArray()
    Dim times = New Integer(allvaluesArr.Length - 1) {}

    For Each v As Videogame In mySet
        Dim console As String = v.Console
        For i = 0 To times.Length - 1
            If Equals(allvaluesArr(i), console) Then
                times(i) += 1
            End If
        Next
    Next

    RichTextBox1.AppendText("Console".PadRight(50 - "Console".Length) & "Absolute Frequency".PadRight(50 - "Absolute Frequency".Length) & "Percentage".PadRight(50 - "Percentage".Length) & vbLf)

    For i = 0 To times.Length - 1
        Dim percentage = times(i) / CDbl(mySet.Count) * 100.0R
        Dim perc As String = percentage.ToString() & "%"
        RichTextBox1.AppendText(allvaluesArr(i).ToString().PadRight(50 - allvaluesArr(i).Length) & times(i).ToString().PadRight(50 - times(i).ToString().Length) & perc.PadRight(50 - perc.Length) & vbLf)
    Next
End Sub
```