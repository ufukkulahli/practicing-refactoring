**Replace Temp with Query**

Extract temp variable's expression into its dedicated method.  
Use newly created method from necessary places by invoking it.  
Delete temp variable.  

Using temps causes methods to be longer since we can access them over and over again.  
This technique is not just to delete temps also for making extract method easier.  
Allows all methods inside class to use query method.


**Example**

_Issue_

```csharp
decimal CalculatePrice()
{
  var price = quantity * itemPrice;
  decimal discountRate = 0;
  if (price > 1000)
  {
    discountRate = 0.95;
  }
  else
  {
    discountRate = 0.98;
  }
  return price * discountRate;
}
```

_Refactoring_

```csharp
decimal CalculatePrice()
{
  return CalculateBasePrice() * CalculateDiscountRate();
}

decimal CalculateBasePrice()
{
  return quantity * itemPrice;
}

decimal CalculateDiscountRate()
{
  if (CalculateBasePrice() > 1000)
  {
    return 0.95;
  }
  return 0.98;
}
```

We may need to use `Split Temporary Variable` or `Separate Query from Modifier` to be able to use this one.
