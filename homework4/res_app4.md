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

# Research on applications 5 - Graphics in .NET environement

In order to create some simple graphics in the .NET framework, we need the following objects:

1. A PictureBox

2. A Bitmap

3. A Graphics object

A PictureBox is, as its name says, a picture box needed to display an image in a window. This image can be a  simple image from the device's hard drive, but it also can be a picture created by the programmer in order to display some graphics. We are interested to this second option.

After instantiating the picturebox where our graphic will be displayed, we need to instantiate also a Bitmap object. This object basically encapsulates an image, composed by pixels: we can open in a Bitmap object an already existing image, to modify it operating on pixels, or we can create an entirely new Bitmap just specifying its size, basically creating a blank image to modify.

Finally, the bitmap we created must be encapsulated in a Graphics object. This object is needed to modify the image itself: applying methods on the Graphics object we will be able to perform various operations on the image and, doing so, draw our graphics.

In the end, in order to display the so created image, we will have to assign it to the picturebox object.

What I described is performed in the following code (that assumes the existance of a PictureBox object pictureBox1 created in the designer panel):

```C#
Bitmap b;
Graphics g;

b =  new Bitmap(pictureBox1.Width, pictureBox1.Height);
g = Graphics.FromImage(b);

pictureBox1.Image = b;
```

Of course the code presented will display a blank image, since we did not operate any method on g. Neverthless, we have many methods we can apply to g to design our graphics, for example the one in the following code:

```C#
Bitmap b;
Graphics g;

b =  new Bitmap(pictureBox1.Width, pictureBox1.Height);
g = Graphics.FromImage(b);

Rectangle r = new Rectangle(20,20, b.Width - 40, b.Height - 40);
g.DrawRectangle(Pens.Black, r);

pictureBox1.Image = b;
```

The method DrawRectangle will created in the bitmap b opened in g a rectangle: the position of the rectangle $(x,y)$ is specified in the first two inputs, while the other two inputs specify the rectangle size.

If we want, for example, to create a chart, we can use the method "DrawLines(Pen, Point[])": this method will design a chart connecting the points contained in an array specified in the input.

**References** \
[1] [https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.picturebox?view=windowsdesktop-7.0](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.picturebox?view=windowsdesktop-7.0) \
[2] [https://learn.microsoft.com/en-us/dotnet/api/system.drawing.bitmap?view=dotnet-plat-ext-6.0](https://learn.microsoft.com/en-us/dotnet/api/system.drawing.bitmap?view=dotnet-plat-ext-6.0) \
[3] [https://learn.microsoft.com/en-us/dotnet/api/system.drawing.graphics?view=windowsdesktop-7.0](https://learn.microsoft.com/en-us/dotnet/api/system.drawing.graphics?view=windowsdesktop-7.0)

# Research on Applications 6 - Get device coordinates from world coordinates

When we draw a chart on a bitmap, using the methods provided by a Graphics object, we need to keep into account the fact that the real world coordinates of the points that compose our chart can't be reported in the image as they are: there are in fact a lot of differences between the "real world" where we think our chart and the "virtual world" where we want to draw it. The two most important are the following:

- In the real world, a chart is displayed in a Cartesian plane, and each point of the chart is a couple of Real numbers. In the virtual world, the chart must be represented in an image composed by pixels: each point will be a pixel, and a pixel can be indexed in the bitmap with a couple of Integers.

- In a Cartesian plane, if we consider just the first quadrant, the origin of the plane $(0,0)$ will be placed down on the left. In the virtual world, a bitmap is a matrix of pixels: then, the coordinates $(0,0)$ will refer to the pixel up on the left.

In order to overcome the representation problems given by those differences, we need to operate a coordinate transformation, in order to obtain "virtual coordinates" from real world ones. The conversion to operate is the following:

$$X_v = \dfrac{X_r - X_{min}}{X_{max} - X_{min}} W$$

Where $X_r$ is the "real" $X$, $X_{max}$ is the maximum value for $X_r$, $X_{min}$ is the minimum value for $X_r$ and $W$ is the width of the image.

$$Y_v = H - H\dfrac{Y_r - Y_{min}}{Y_{max} - Y_{min}}$$

Where $Y_r$ is the "real" $Y$, $Y_{max}$ is the maximum value for $Y_r$, $Y_{min}$ is the minimum value for $Y_r$ and $H$ is the height of the image.

The difference between the two conversions (for $X$ and for $Y$) is due to the fact that while the origin of the plane corresponds for the $X$, it changes for the $Y$ and so we need to manage this difference.
