**Push Down Method**

We have some performing methods in base class which is used by very few sub classes.  
We can move method into related sub class and delete it from base.

Example

_Issue_

```csharp
class Unit
{
  int GetFuel() => 50;
}

class Soldier : Unit
{
}

class Tank : Unit
{
}
```

_Refactoring_

```csharp
class Unit
{
}

class Soldier : Unit
{
}

class Tank : Unit
{
  int GetFuel() => 50;
}
```
