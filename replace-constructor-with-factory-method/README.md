**Replace Constructor with Factory Method**

When we have many constructor arguments to initialize a object things get easily messy.
Instead of depending constructor we can use a factory method.

**Example**
 
_Issue_
 
```csharp
public class Customer
{
  public readonly int Id;
  public readonly DateTime Birthday;
  public readonly string Name;
  public readonly string Surname;
  
  public Customer
  (
    int Id,
    DateTime Birthday,
    string Name,
    string Surname
  )
  {
    this.Id
    this.Birthday = Birthday;
    this.Name = Name;
    this.Surname = Surname;
  }
}
```
 
_Refactoring_
 
```csharp
public class Customer
{
  public int Id;
  public DateTime Birthday;
  public string Name;
  public string Surname;
  
  public static Customer Create
  (
    int Id,
    DateTime Birthday,
    string Name,
    string Surname
  )
  {
    return new Customer
  {
      Id = Id,
      Birthday = Birthday,
      Name = Name,
      Surname = Surname
  };
  }
}
```