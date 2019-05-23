**Replace Magic Number with Symbolic Constant**

Turn hard-coded numbers into `const` declared variables, make them meaningfull in a more descriptive way.

**Example**

_Issue_

```csharp
class Pi
{
  public bool MultiplyBy(int factor) => 3.14159265359 * factor;
}
```

_Refactoring_

```csharp
class Pi
{
  const double pi = 3.14159265359;
  public bool MultiplyBy(int factor) => pi * factor;
}
```
