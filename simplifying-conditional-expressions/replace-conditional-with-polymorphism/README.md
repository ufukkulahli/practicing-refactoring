**Replace Conditional with Polymorphism**

We have a conditional and it's each leg presents different behaviour based on a object.  
So create a new base class with the base behaviour defined in it.  
Then create sub classes for each behaviour and override base behaviour inside them.

Example

_Issue_

```csharp
string GetFamily()
{
  switch(animal)
  {
    case lizard:
      return "Reptile";
    case tiger:
      return "Felidae";
    case orangutan:
      return "Hominidae";
  }
}
```

_Refactoring_

```csharp
public abstract class Family
{
  public abstract string GetFamily();
}

public class Lizard : Family
{
  public override string GetFamily()
  {
    return "Reptile";
  }
}

public class Tiger : Family
{
  public override string GetFamily()
  {
    return "Felidae";
  }
}

public class Orangutan : Family
{
  public override string GetFamily()
  {
    return "Hominidae";
  }
}
```
