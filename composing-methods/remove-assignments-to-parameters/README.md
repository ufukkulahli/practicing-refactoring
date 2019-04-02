**Remove Assignments to Parameters**

Method's argument is overridden(assigned) by another value inside of the method.  
Delete assignment and use temporary variable instead.  

**Example**

_Issue_

```csharp
int Discount(int inputVal, int quantity, int yearToDate)
{
  if (inputVal > 50) inputVal -= 2;
  if (quantity > 100) inputVal -= 1;
  if (yearToDate > 10000) inputVal -= 4;
  return inputVal;
}
```

_Refactoring_

```csharp
int Discount(int inputVal, int quantity, int yearToDate)
{
  int result = inputVal;
  if (inputVal > 50) result -= 2;
  if (quantity > 100) result -= 1;
  if (yearToDate > 1000) result -=4;
  return result;
}
```
