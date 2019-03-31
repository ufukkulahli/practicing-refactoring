**Add parameter**

Use this refactoring technique when a method needs additional parameter to perform its job.

**Example**

_Issue_

```csharp
decimal CalculatePrice()
{
  // we want this calculation
  // to be dynamic
  return this.amount * 2
}

```

_Refactoring_

```csharp
decimal CalculatePrice(int factor)
{
  return this.amount * factor
}
```

We should be careful when adding parameters to methods.  
This could easily lead to chaos.  

This refactoring:

Could cause to smell
* Long parameter list

Anti refactoring of
* Remove parameter

Similar to
* Rename method

Helps to
* Introduce parameter object
