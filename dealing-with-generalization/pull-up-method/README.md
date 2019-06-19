**Pull Up Method**

We have identical performing methods in sub classes.  
We can move method into base class and let sub classes use it.

Example

_Issue_

```csharp
class Unit
{
}

class Soldier : Unit
{
  int GetHealt() => 5;
}

class Tank : Unit
{
  int GetHealt() => 100;
}
```

_Refactoring_

```csharp
class Unit
{
  int GetHealt() => health;
}

class Soldier : Unit
{
}

class Tank : Unit
{
}
```
