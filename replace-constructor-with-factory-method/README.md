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
    this.Id = Id;
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

This technique is better known for creating business object types / subtypes
depending on an argument and deciding upon it.

Here we use type parameter to decide the customer type.

```csharp
public class Customer
{
  private int _type;
  public static int Regular = 0;
  public static int Newcomer = 1;
  public static int Loyal = 2;
  public int Id;
  public DateTime Birthday;
  public string Name;
  public string Surname;

  public Customer
  (
    int type,
    int Id,
    DateTime Birthday,
    string Name,
    string Surname
  )
  {
    this._type = type;
    this.Id = Id;
    this.Birthday = Birthday;
    this.Name = Name;
    this.Surname = Surname;
  }
}
```

to:

```csharp
public class Customer
  {
    private int _type;
    public static int Regular;
    public static int Newcomer;
    public static int Loyal;
    public int Id;
    public DateTime Birthday;
    public string Name;
    public string Surname;

    private Customer()
    {
    }

    public static Customer Create
    (
      int type,
      int Id,
      DateTime Birthday,
      string Name,
      string Surname
    )
    {
      return new Customer
      {
        _type = type,
        Id = Id,
        Birthday = Birthday,
        Name = Name,
        Surname = Surname
      };
    }
```

and the client code:

```csharp
var customer = Customer.Create
(
  type: Customer.Newcomer,
  Id: 1234,
  Birthday: new DateTime(1980, 1, 1),
  Name: "Johny",
  Surname: "Begood"
);
```

It is up to us to make constructor private.
Since we are using static method to create object we might want to control creation.
Careless constructor use might lead to unwanted business errors.

Factory method
* Can return an already created object
* Can return subclasses of containing class

This technique helps other refactorings
* Change value to reference
* Replace type code with subclasses

This technique implements design pattern
* Factory method