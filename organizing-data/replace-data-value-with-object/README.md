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
  // For existing constructor calls
  Sale(string SaleItem) => this.SaleItem = new SaleItem(SaleItem);
  // For new constructor calls
  Sale(SaleItem SaleItem) => this.SaleItem = SaleItem;
  string GetSaleItem() => this.SaleItem.Name();
}

class SaleItem
{
  readonly string name;
  SaleItem(string name) => this.name = name;
  string Name() => this.name;
}
```

Currently SaleItem is `value object` (so as old string SaleItem) meaning that each Sale has its own SaleItem.  
Value objects should be immutable.  
We may turn SaleItem into a `reference object` with the `Change Value to Reference` refactoring.
