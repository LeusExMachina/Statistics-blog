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