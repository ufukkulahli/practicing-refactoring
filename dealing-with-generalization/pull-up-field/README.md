**Pull Up Field**

We have same fields in sub classes.  
We can move them into base class.

Example

_Issue_

```csharp
class Unit
{
}

class Soldier : Unit
{
  int healt;
}

class Tank : Unit
{
  int healt;
}
```

_Refactoring_

```csharp
class Unit
{
  int healt;
}

class Soldier : Unit
{
}

class Tank : Unit
{
}
```
