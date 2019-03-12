**Consolidate Conditional Expression**

Sometimes we write multiple conditionals that have same return values.  
So consolidate these conditionals in a single expression and  
apply extract method to expression.   
Give a clearer name to method to reflect intent.  

**Example**

_Issue_

```csharp
decimal CalculateDisabilityAmount()
{
  if(seniority < 2)
  {
    return 0;
  }
  if(monthsDisabled > 12)
  {
    return 0;
  }
  if(isPartTime)
  {
    return 0;
  }

  return amount * days;
}
```

_Refactoring_

```csharp
decimal CalculateDisabilityAmount()
{
  if(IsNotEligableForDisability())
  {
    return 0;
  }

  return amount * days;
}

bool IsNotEligableForDisability()
{
  return
    (seniority < 2) ||
    (monthsDisabled > 12) ||
    (isPartTime)
}
```
Extracting conditions into methods most useful way to clarify code blocks.  
Method calls represents **WHY** we are doing it instead of **WHAT/HOW** we are doing.  
We can replace if statements with other techniques but being clear on 'why' part is main goal.
