**Split Temporary Variable**

We have a temp variable which is written over and over again.  
It is **not** used for `collecting` some results.  
Meaning that it is used literally instead of a genuinely new variable.  
Refactor it to have its own dedicated meaningful variable.

**Example**

_Issue_

```csharp
void CalculateArea(double height, double width)
{
  double temp = 2 * (height + width);
  Console.WriteLine(temp);
  temp = height * width;
  Console.WriteLine(temp);
}
```

_Refactoring_

```csharp
void CalculateArea(double height, double width)
{
  double perimeter = 2 * (height + width);
  Console.WriteLine(perimeter);
  double area = height * width;
  Console.WriteLine(area);
}
```
