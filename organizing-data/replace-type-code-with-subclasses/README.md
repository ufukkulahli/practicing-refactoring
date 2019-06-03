**Replace Type Code with Subclasses**

Primitive data type is being used to represent different types.  
Replace each type code with an object and build a inheritance hierarchy.

_Issue_

```csharp
class Employee
{
  static int Engineer = 0;
  static int Salesman = 1;
  static int Manager = 2;
  // ...
}

```

_Refactoring_

```csharp
static Employee Create(int type)
{
  if(type == 0)
    return new Engineer();
  if(type == 1)
    return new Salesman();
  if(type == 2)
    return new Manager();
}
```
