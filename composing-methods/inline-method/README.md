**Inline Method**

We use this one when;  
A method body clear as its name.

Badly refactored methods exist. Some code blocks extracted but did worst. So we inline these methods back.  
Then we can try to do a better extracting. Inlining helps work better `Replace Method with Method Object`.

Too much delegation between methods exist then the actual work. We follow the methods and just see another calls.  
After inlining these methods we may get rid off redundant ones.

Example

_Issue_

```csharp
decimal CalculatePrice()
{
  if(DiscountEqualToZero())
  {
    return basePrice * quantity;
  }
  return (basePrice - 10) * quantity;
}

bool DiscountEqualToZero()
{
  return discount == 0;
}
```

_Refactoring_

```csharp
decimal CalculatePrice()
{
  if(discount == 0)
  {
    return basePrice * quantity;
  }
  return (basePrice - 10) * quantity;
}
```
