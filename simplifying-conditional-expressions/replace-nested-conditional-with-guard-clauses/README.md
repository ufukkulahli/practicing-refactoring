 **Replace Nested Conditional with Guard Classes**
 
 Sometimes we find a conditional nest with no clearer execution path.  
 There would be a temp variable at the very beginning to hold value from each conditional branch.  
 Then at the last exit point this temp variable would be returned.  
 So instead of letting this complicated execution path live we can quickly terminate execution within  
 each condition and make the result return immediately.  
 This kind of fail-fast test expressions are also called `guard clauses`.  
 
 Example
 
 _Issue_
 
```csharp
decimal GetAmountToPay()
{
  decimal amount = 0;
  if (isDead)
  {
    amount = CalculateDeadAmount();
  }
  else 
  {
    if (isSeparated)
    {
      amount = CalculateSeparatedAmount();
    }
    else 
    {
      if (isRetired)
      {
        amount = CalculateRetiredAmount();
      }
      else
      {
        amount = CalculateNormalPayAmount();
      }
    }
  }
  
  return amount;
}
```
 
_Refactoring_
 
```csharp
decimal GetAmountToPay() 
{
  if (isDead)
  {
    return CalculateDeadAmount();
  }
  if (isSeparated)
  {
    return CalculateSeparatedAmount();
  }
  if (isRetired)
  {
    return CalculateRetiredAmount();
  }
  return CalculateNormalPayAmount();
}
```
