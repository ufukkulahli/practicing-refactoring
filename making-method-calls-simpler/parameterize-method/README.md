**Parameterize method**

We can use this refactoring technique when multiple methods that perform similar operations  
but differs on some values, behaviours.  
Firstly, that similar methods could be combined into one method.  
And the necessary values are provided as method parameter.  
Then we let the method do its job on given parameters.

**Example**

_Issue_

```csharp
decimal multiplyPriceByTwo()
{
  return this.amount * 2;
}

decimal multiplyPriceByFive()
{
  return this.amount * 5;
}
```

_Refactoring_

```csharp
decimal multiplyPriceBy(int factor)
{
  return this.amount * factor;
}
```

We should be careful while applying this technique.  
Method could become a mud if much more put into it.  
We may swim in if statements.  

This refactoring:

Eliminates smell
* Duplicate code

Anti refactoring of
* Replace parameter with explicit methods

Similar to refactorings
* Extract method
* Form template method
