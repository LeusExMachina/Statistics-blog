# Applications 8 and 9 - Editable Rectangles and Charts

I decided to "merge" the two applications, first creating an editable rectangle (asked as application 9) and then designing the charts (asked for application 8) inside this editable rectangle I created. Since, i will first show how editable rectangles work (application 9) and then the charts created inside them (application 8).

## Editable rectangles

[Click here](https://drive.google.com/uc?export=download&id=1RyJUm4KoM_unX1ftbpST7oXqZWgv7C_5) to download the application.

A video of the application can be watched down below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app9.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

In order to create a resizeable rectangle, I decided to create an EditableRectangle class. This class encapsulates a simple Rectangle, a PictureBox and a Form. The PictureBox and the Form are needed to handle the events necessary to resize the rectangle. The code of the class is the following:

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace App_MovResRect_C
{
    class EditableRectangle
    {
        public Rectangle r;
        PictureBox p;
        Form f;

        public EditableRectangle(int X, int Y, int Width, int Heigth, PictureBox pb, Form fo)
        {
            r = new Rectangle(X, Y, Width, Heigth);
            p = pb;
            f = fo;

            pb.MouseUp += new MouseEventHandler(editableRect_Up);
            pb.MouseDown += new MouseEventHandler(editableRect_Down);
            pb.MouseMove += new MouseEventHandler(editableRect_Move);

            f.MouseWheel += new MouseEventHandler(editableRect_Zoom);
        }

        int x_down;
        int y_down;

        int x_mouse;
        int y_mouse;

        int r_width;
        int r_height;

        bool drag = false;
        bool resizing = false;

        double ScaleFact = 0.1d;

        int hoverX;
        int hoverY;

        private void editableRect_Down(object sender, MouseEventArgs e)
        {
            if (r.Contains(e.X, e.Y))
            {
                x_mouse = e.X;
                y_mouse = e.Y;

                x_down = r.X;
                y_down = r.Y;

                r_width = r.Width;
                r_height = r.Height;

                if (e.Button == MouseButtons.Left)
                {
                    drag = true;
                }
                else if (e.Button == MouseButtons.Right)
                {
                    resizing = true;
                }
            }
        }

        private void editableRect_Up(object sender, MouseEventArgs e)
        {
            drag = false;
            resizing = false;
        }

        private void editableRect_Move(object sender, MouseEventArgs e)
        {
            hoverX = e.X;
            hoverY = e.Y;

            int delta_x = e.X - x_mouse;
            int delta_y = e.Y - y_mouse;

            if (drag)
            {
                r.X = x_down + delta_x;
                r.Y = y_down + delta_y;
            }
            else if (resizing)
            {
                r.Width = r_width + delta_x;
                r.Height = r_height + delta_y;
            }
        }

        private void editableRect_Zoom(object sender, MouseEventArgs e)
        {

            int pictx = hoverX;
            int picty = hoverY;

            if (r.Contains(pictx, picty))
            {
                x_down = r.X;
                y_down = r.Y;

                r.Width = r.Width + (int)(e.Delta*ScaleFact);
                r.Height = r.Height + (int)(e.Delta*ScaleFact);

                r.X = x_down - (int)((e.Delta * ScaleFact)/2);
                r.Y = y_down - (int)((e.Delta * ScaleFact)/2);
            }
        }
    }
}
```

As we can see from the code, to move and resize the rectangle we used the events "MouseUp", "MouseDown" and "MouseMove" from the PictureBox. When a button of the mouse is pressed, the method "editableRect_Down" is called. If and only if the cursor is over the rectangle area this method will set "true" a bolean variable: "drag", if we clicked with the left mouse button, or "resizing", if we clicked with the right mouse button.

When the mouse moves over the PictureBox, the method "editableRect_Move" is called. This method will actually do something only if one of the variables "drag" or "resizing" is set to "true": in this case, the method allows to move or resize the rectangle acting respectively on the position or on its height and width. The method also keeps constant track of the position of the mouse over the picturebox, through the variables "hoverX" and "hoverY".

If we stop pressing the mouse button, the method "editableRect_Up" will be called, and thus both resizing and dragging will be disable.

Finally, in order to obtain the zoom of the rectangle, I used the event "MouseWheel" from the Form. This event is generated when when we scroll with the mouse wheel, and will call up the handler "editableRect_Zoom". This handler acts only if the mouse cursor (which position is given by the variables "hoverX" and "hoverY") is over the rectangle's area and will increment both the height and the width of the mouse of a factor "Delta". This "Delta" quantifies the wheel turns from the mouse, and is a positive or a negative value according to the sense of rotation. To keep fixed the centre of the rectangle, and not his upper left angle, we also move it of half the quantity added in both the directions.

Notice that to enable the moving animation, rectangles must be periodically deleted and re-drawn with the modifications. To do so I used a timer:

```C#
private void timer1_Tick(object sender, EventArgs e)
{
    g.Clear(pictureBox1.BackColor);
    g.DrawRectangle(Pens.Red, r1.r);
    g.DrawRectangle(Pens.Blue, r2.r);

    pictureBox1.Image = b;
}
```

## Charts

[Click here](https://drive.google.com/uc?export=download&id=1e3lPHUrm5fGnYn7m1YWd8pk444DJZ24E) to download the application.

A video of the application can be watched down below:

<div class="embed-container">
  <iframe
      src="/StatisticsHomework/docs/assets/images/app8.mp4"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

As I said, I decided to design the charts inside the EditableRectangles I designed: thus also the charts are resizeable (as we can see from the video). The distribution represented in the charts is obtained by the same file used in [Homework 3](https://leusexmachina.github.io/StatisticsHomework/homework3/applications3), with the same code.

The application uses a timer that ticks every 10 ms in order to draw again the charts. The code is the following:

```C#
private void timer1_Tick(object sender, EventArgs e)
{
    g.Clear(pictureBox1.BackColor);
    drawHistogram_horizontal();
    drawHistogram_vertical();
}
```

The two functions "drawHistogram_horizontal" and "drawHistogram_vertical" respectively draw the horizontal histogram and the vertical histogram. Let's see the first one (the second one is very similar with minimal changes):

```C#
private void drawHistogram_horizontal()
{

    g.FillRectangle(Brushes.Black, r.r);
    g.DrawRectangle(Pens.Red, r.r);

    int maxvalue = protocolDistribution.Values.Max();

    int space_height = r.r.Bottom - r.r.Top - 20;
    int space_width = r.r.Right - r.r.Left - 20;

    int num_intervals = protocolDistribution.Keys.Count;
    int histrect_width = space_width/num_intervals;

    int start = r.r.X;

    foreach(KeyValuePair<String, int> k in protocolDistribution)
    {
        int rect_height = (int)(((double)k.Value/(double)maxvalue)*((double)space_height));
        Rectangle hist_rect = new Rectangle(start, r.r.Bottom - rect_height, histrect_width, rect_height);

        g.FillRectangle(Brushes.Green, hist_rect);
        g.DrawRectangle(Pens.White, hist_rect);

        //scrittura chiavi

        string text = k.Key;
        Rectangle stringPos = new Rectangle(start, r.r.Bottom + 20, histrect_width, histrect_width + 20);
        Font font1 = new Font("Arial", 12, FontStyle.Regular, GraphicsUnit.Pixel);

        StringFormat stringFormat = new StringFormat();
        stringFormat.Alignment = StringAlignment.Center;
        stringFormat.LineAlignment = StringAlignment.Center;
        g.TextRenderingHint = System.Drawing.Text.TextRenderingHint.ClearTypeGridFit;
        Font goodFont = findFont(g, text, stringPos.Size, font1);

        g.DrawString(text, goodFont, Brushes.Black, stringPos, stringFormat);

        //fine scrittura chiavi

        start += histrect_width;
    }

    pictureBox1.Image = b;
}
```

As we can see, the function initially draws the resizeable rectangle, then it calculates the width of the rectangles in the chart given the room offered by the editable rectangle and the number of values to represent. Then, for each value in the distribution, a rectangle is created: its height will be proportioned to the absolute frequency of the attribute, in order to have a proper chart.

The code among the two comments is used to draw the names of the attributes under each rectangle of the chart.