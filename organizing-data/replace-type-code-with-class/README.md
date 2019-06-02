**Replace Type Code with Class**

There are `primitive` data types that are being used to represent different types.  
Instead of taking advantage of OOP, such an integer is taking place.  
For example; 0, 1, 2, 3 are moving around to specify a person’s blood group.  
Using primitives allow bugs to born.  
Strict compiler and IDE type checking could easily be skipped.  
Turn these ones to full build classes and take advantage of type checking.  
Do not use this refactoring if these types are being used more than dummy representatives.

**Example**

_Issue_

```csharp
class Person
{
  public static int O = 0;
  public static int A = 1;
  public static int B = 2;
  public static int AB = 3;
  // ...
}
```

_Refactoring_

```csharp
class BloodGroup
{
  public static BloodGroup O = new BloodGroup(0);
  public static BloodGroup A = new BloodGroup(1);
  public static BloodGroup B = new BloodGroup(2);
  public static BloodGroup AB = new BloodGroup(3);
  // ...
}
```
