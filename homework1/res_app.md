# Research on Application 1 - Main differences between C# and VB.NET

We want to list some of the main differences between C# and VB.NET.

### Accessibility

Both C# and Visual Studio.NET are programming languages developed by Microsoft. Although that, while VB.NET is strictly related to the Visual Studio IDE and then to Microsoft, C# can be used also on other platforms.

### Case Sensitivity

While C# is a case sensitive language, VB.NET is not case sensitive. For instance, the two variables:

- person

- Person

are different variables if declared in C#, but instead are considered the same in VB.NET

### Event Handling

Although the event handling happens in a similar way both in C# and in VB.NET, the syntax used by the two languages is totally different. In VB.NET, we can directly declare a sub as a handler of some event, with the following syntax:

```VB
Private Sub Button_Click(sender As Object, e As EventArgs) Handles MyButton.Click
 ...
End Sub
```
Otherwise, we can add or remove handlers at run-time using the following syntax:

```VB
AddHandler MyButton.Click, AddressOf Button_Click
RemoveHandler MyButton.Click, AddressOf Button_AnotherClick
```

In C# there is just one possible syntax to add or remove an event handler, that is the following:

```C#
MyButton.Click += new EventHandler(Button_Click);
MyButton.Click -= Button_Click;
```

### Delimiters

While each C# code row must be delimited with a semicolon (;), there is no need to do the same in VB.NET. This fact can be noticed analizing the 2 previous examples

### Variable initialization and Arrays

The syntax used to initialize variables is deeply different between the 2 languages. Let's do some example to understand this better.

To initalize a simple integer variable in C#, the code we can use is the following:

```C#
Int myInt = 3;
```

Doing the same in VB.NET needs a totally different and more verbose syntax:

```VB
Dim myinteger As Integer = 3
```
Also arrays are created and addressed differently. In C#, to create and then index an integer array, we use the syntax:

```C#
Int[] arr = new int[4]{1,2,3,4};
Int element = arr[1];
```

To do the same in VB.NET, the syntax used is the following:

```VB
Dim intdata() As Integer = {1,2,3,4}
Dim myinteger As Integer = intdata(1)
```

Notice then how in C# arrays are addressed with "[]", while in VB they are addressed with "()".

### Explicit pointers

A very important difference between C# and VB.NET is that, deriving from C, the first allows the programmer to handle explicit pointers. The same is not permitted by VB.NET

### Other generic syntax differences

In general, although running on the same framework, VB.NET and C# have a very different syntax. The first has a syntax that comes from C and Java, while the second tends to have a more verbose sintax, more similar to the natural language.

**References** \
[1] [https://www.grectech.it/blog/meglio-il-visual-basic-net-o-il-visual-c/#:~:text=Che%20VB.NET%20%C3%A8%20la,altri%20ambienti%2C%20come%20il%20MonoDevelop.](https://www.grectech.it/blog/meglio-il-visual-basic-net-o-il-visual-c/#:~:text=Che%20VB.NET%20%C3%A8%20la,altri%20ambienti%2C%20come%20il%20MonoDevelop.) \
[2] [https://www.html.it/pag/15441/c-e-vb-net-a-confronto/](https://www.html.it/pag/15441/c-e-vb-net-a-confronto/)