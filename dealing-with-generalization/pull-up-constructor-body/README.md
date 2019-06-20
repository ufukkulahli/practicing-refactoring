**Pull Up Constructor Body**

Sub classes have identical constructor code.  
Create suitable code with the constructor in the base class and then call it from sub classes.

Example

_Issue_

```csharp
class Student : BaseStudent
{
  Student(string name, string id, int grade)
  {
    // ...
  }
}
```

_Refactoring_

```csharp
class Student : BaseStudent
{
  Student(string name, string id, int grade) : base(name, id)
  {
    this.grade = grade;
  }
}
```
