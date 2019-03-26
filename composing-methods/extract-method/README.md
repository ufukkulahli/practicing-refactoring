**Extract method**

This technique is the most common one and plays important role to make things clear in the most simple way.  
Abstractions, architectures have their own importance but this is where all begins.  
We can use this technique for long methods or code blocks need comments to understand their intent.  
Giving methods good names is a must.   
By taking out codes to their dedicated methods and giving clear method names we make things official.  
Method name and its body should overlap semantically. We can use this to decide method long.  
Names should tell 'what it does' not 'how it does'.  
If we see that given method name performs better then extract the code even if it is a single line.  
If otherwise then we can leave it alone.  

Example

_Issue_

```csharp
decimal CalculatePrice()
{
  var basePrice = amount * quantity;
  var discount = discountAmount + extraDiscountAmount;
  var finalPrice = basePrice - discount;
  return finalPrice;
}
```

_Refactoring_

```chsarp
decimal CalculatePrice()
{
  var basePrice = CalculateBasePrice();
  var discount = CalculateDiscount();
  var finalPrice = basePrice - discount;
  return finalPrice;
}

decimal CalculateBasePrice()
{
  return amount * quantity;
}

decimal CalculateDiscount()
{
  return discountAmount + extraDiscountAmount;
}
```

When extracted method needs a local variable from source code block then we need to pass in that.

Example

_Issue_

```csharp
decimal CalculatePrice()
{
  var basePrice = amount * quantity;
  var discount = discountAmount + extraDiscountAmount;
  var finalPrice = basePrice - discount;
  Console.WriteLine("Calculated price: {0}", finalPrice);
  return finalPrice;
}
```

_Refactoring_

```chsarp
decimal CalculatePrice()
{
  var basePrice = amount * quantity;
  var discount = discountAmount + extraDiscountAmount;
  var finalPrice = basePrice - discount;
  Log(finalPrice);
  return finalPrice;
}

void Log(decimal price)
{
  Console.WriteLine("Calculated price: {0}", price);
}
```

If some variables prevents or hardens extracting see:
* `split temporary variable`
* `replace temp with query`
* `replace method with method object`
* `remove assignments to parameters`
