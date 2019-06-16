**Pull Up Field**

A field in base class is used by very few of sub classes.  
We can move the field to these which uses.

Example

_Issue_

```csharp
class Unit
{
  int fuel;
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
  int fuel;
}
```
