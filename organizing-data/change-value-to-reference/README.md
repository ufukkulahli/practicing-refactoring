**Change Value to Reference**

We have many same instances of a class(they are some sort of copies) and we want exactly one instance to use everywhere.  
So with this technique we change object into a `reference object`.  
Reference objects are usually like `customer, user, product` since copy of a same user would be abnormal in system.

Example

__Issue__
```csharp
class Customer
{
  private readonly name;
  public Customer(string name) => this.name = name;
  public string Name() => this.name;
}

class Order
{
  private Customer customer;
  public Order(string customerName) => this.customer = new Customer(customerName);
  public string CustomerName() => this.customer.Name();
  public void SetCustomer(string customerName) => this.customer = new Customer(customerName);
}
```

__Refactoring__

```csharp
// TODO
```
