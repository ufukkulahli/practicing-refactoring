**Replace Subclass with Fields**

There are subclasses with constant returning methods and no other differences.  
Move values to base class fields and get rid of the subclasses.

_Issue_

```csharp
abstract class Person
{
  abstract bool IsMale();
  abstract char GetCode();
}
class Male : Person
{
  bool IsMale() => true;
  char GetCode() => 'M';
}
class FeMale : Person
{
  bool IsMale() => false;
  char GetCode() => 'F';
}
```

_Refactoring_

```csharp
class Person
{
  readonly bool isMale;
  readonly char code;
  Person(bool isMale, char code)
  {
    this.isMale = isMale;
    this.code = code;
  }
  bool IsMale() => this.isMale;
  char GetCode() => this.code;
}
```
