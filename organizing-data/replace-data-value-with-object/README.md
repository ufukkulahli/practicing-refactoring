**Replace Data Value with Object**

We are trying to `represent` a rather rich object with a `primitive` type.  
We need additional `behaviours` to attach that type.  
Since it is primitive that is not possible.  
So we introduce new class instead of it and use it in required places.

Example

__Issue__

```csharp
class Sale
{
  readonly string SaleItem;
  Sale(string SaleItem) => this.SaleItem = SaleItem;
  string GetSaleItem() => this.SaleItem;
}
```

__Refactoring__

```csharp
class Sale
{
  readonly SaleItem SaleItem;
  Sale(SaleItem SaleItem) => this.SaleItem = SaleItem;
  string GetSaleItem() => this.SaleItem.Name();
}

class SaleItem
{
  readonly int Id;
  readonly string name;
  SaleItem(int Id, string name)
  {
    this.Id = Id;
    this.name = name;
  }
  int Id() => this.Id;
  string Name() => this.name;
}
```
