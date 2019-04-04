**Replace Method with Method Object**

We have a complicated method that we can not apply `extract method` because of tangled local variables.  
So move the method into its dedicated class(method object) and turn the local variables to instance fields of newly created class.
By that freely operate on these variables and begin splitting the complicated method into smaller and understandable parts.

**Example**

_Issue_

```csharp
public class Accounting
{
  private decimal dailyDiscount = 10;

  public decimal CalculatePrice(decimal amount, decimal discount, int quantity, DateTime discountValidDate)
  {
    var basePrice = amount * quantity;
    if(discountValidDate >= DateTime.Now)
    {
      return netPrice = basePrice - discount;
    }
    return basePrice - this.dailyDiscount;
  }
}
```

_Refactoring_

```csharp
public class Accounting
{
  internal decimal dailyDiscount = 10;

  public decimal CalculatePrice(decimal amount, decimal discount, int quantity, DateTime discountValidDate)
  {
    return new CalculatePrice(this, amount, discount, quantity, discountValidDate).Calculate();
  }
}

public class CalculatePrice
{
  private readonly Accounting accounting;
  private decimal amount;
  private decimal discount;
  private int quantity;
  private DateTime discountValidDate;

  public CalculatePrice(Accounting accounting, decimal amount, decimal discount, int quantity, DateTime discountValidDate)
  {
    this.accounting = accounting;
    this.amount = amount;
    this.discount = discount;
    this.quantity = quantity;
    this.discountValidDate = discountValidDate;
  }

  public decimal Calculate()
  {
    var basePrice = this.amount * this.quantity;
    if(this.discountValidDate >= DateTime.Now)
    {
      return netPrice = basePrice - this.discount;
    }
    return basePrice - this.accounting.dailyDiscount;
  }
}
```
