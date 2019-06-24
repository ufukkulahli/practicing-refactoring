**Extract Superclass**

There are two classes with identical structure.  
Create a superclass, move shared structure to it and let subclasses inherit it.

Example

_Issue_

```csharp
class Department
{
  int GetCost() => 100;
  string GetName() => "IT";
  string GetManager() => "Jen Barber";
}

class Employee
{
  int GetCost() => 10;
  string GetName() => "Maurice Moss";
  int GetId() => 1234;
}
```

_Refactoring_

```csharp
class Party
{
  int GetCost()
  {
    // ...
  }
  string GetName()
  {
    // ...
  }
}

class Department : Party
{
  string GetManager() => "Jen Barber";
}

class Employee : Party
{
  int GetId() => 1234;
}
```
