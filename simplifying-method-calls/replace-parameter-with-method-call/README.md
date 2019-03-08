**Replace Parameter with Method Call**

Obtaining values from query methods and
passing these values to another method
while this method could query these methods itself.
So we remove the parameters from method and
call methods to obtain values inside method.

**Example**

_Issue_

```csharp
var basePrice = quantity * itemPrice;
var discount = this.GetDiscount();
var fees = this.GetFees();
var finalPrice = Calculate(basePrice, discount, fees);
```

_Refactoring_

```csharp
var basePrice = quantity * itemPrice;
var finalPrice = Calculate(basePrice);

decimal Calculate(decimal basePrice)
{
  var discount = this.GetDiscount();
  var fees = this.GetFees();
  return (basePrice + fees) - discount;
}
```