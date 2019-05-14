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
class Customer
{
  private readonly name;
  private static Dictionary<string, Customer> instances = new Dictionary<string, Customer>();
  private Customer(string name) => this.name = name;
  public static Customer GetNamed(string name) => instances[name];
  public string Name() => this.name;
  private void Store() => instances.Add(this.Name(), this);
  public static void LoadCustomers()
  {
    // Load customers from somewhere such as DB. Or for now;
    new Customer("Joe").Store();
    new Customer("Jack").Store();
  }
}

class Order
{
  private Customer customer;
  public Order(string customerName) => this.customer = Customer.GetNamed(customerName);
  public string CustomerName() => this.customer.Name();
  public void SetCustomer(string customerName) => this.customer = new Customer(customerName);
}

// A client to use 'Order' and 'Customer'.
class NumberOfOrders
{
  public int For(IEnumerable<orders> orders, string customer)
  {
    return orders.Where(o => o.CustomerName() == customer).Select(o=>o).Count();
  }
}
```
