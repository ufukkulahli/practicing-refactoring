**Decompose conditional**

We have a place which is fulled with conditionals.  
Every time we go there ending up by interpreting the code to understand what it does.  
We are not interpreters/compilers and we do not have time always to fully understand what is going on.  
Conditions and actions tell us what happens but can not tell us "why" it happens.  
So that this technique says decompose conditionals to their very own methods.  
Extract them to methods, give them meaningful names even if they simple queries.  
By giving names (give names to show intent) to them we make things clear/official such as business rules.

**Example**

_Issue_

```csharp
if(date < summerStart || date > summerEnd)
{
  charge = quantity * winterRate * winterServiceCharge;
}
else
{
  charge = quantity * summerRate;
}
```

_Refactoring_

```csharp
if(NotSummer(date))
{
  charge = WinterCharge(quantity)
}
else
{
  charge = SummerCharge(quantity)
}

private bool NotSummer(DateTime date)
{
  return date < summerStart || date > summerEnd
}

private decimal WinterCharge(int quantity)
{
  return quantity * winterRate * winterServiceCharge;
}

private decimal SummerCharge(int quantity)
{
  return quantity * summerRate;
}
```

Conditions may be short so we may think that not worth extracting method.  
But reading `notSummer(date)` way better than reading conditions.  
Let the code reveal its intention.
