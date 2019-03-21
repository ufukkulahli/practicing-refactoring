**Introduce Null Object**

Trying to be safe with null checks before invoking a method is exhausting many times.  
To get rid off of null checks and invoke methods without fear is possible with this technique.  
Simply, create new sub class and override those methods which cause to null reference exception.  
And now, to represent absent object, instead of returning null return that sub class called null object.  
By that, null checks could be deleted and invocation to those methods will not cause exception.

Example

_Issue_

```csharp
class Program
{
  void Main()
  {
    // ...
    string customerName;
    if (customer == null)
    {
      customerName = "AbsentCustomer";
    }
    else
    {
      customerName = customer.GetName();
    }
  }
}
```

_Refactoring_

```csharp
class Site
{
  Customer customer;
  // Return null object when does not exist
  Customer GetCustomer() => customer ?? Customer.NewNull();
}

class Customer
{
  string name;
  string GetName() => name;
  static Customer NewNull() => new NullCustomer();
  // Now, should use `IsNull()` methods for null checks
  bool IsNull() => false;
}

class NullCustomer : Customer
{
  string GetName() => "AbsentCustomer";
  bool IsNull() => true;
}

class Program
{
  void Main()
  {
    // ...
    string customerName = customer.GetName();
  }
}
```
