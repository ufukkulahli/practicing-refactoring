**Introduce Assertion**

This refactoring technique is making `assumption` explicit with an assertion.  
There are `assumptions` in codes which some of them explicit, some of them implicit.  
We write comments about the state of the program to make these assumptions explicit.  
Or we would look through the code to see them.  
So writing an `Assertion` makes all explicit.  

Example

_Issue_

```csharp
decimal CalculatePrice()
{
  // Either of them is alwasy there.
  if(winterFee || summerFee)
  {
    finalPrice = basePrice * piece;
  }
}
```

_Refactoring

```csharp
decimal CalculatePrice()
{
  Assert.IsTrue(winterFee || summerFee)
  finalPrice = basePrice * piece;
}
```

Assertion:
* Won't change any behaviour.
* Assumed to be always true.
* Failure indicates programmer error.
* Failure should result in unchecked exceptions.
* Usually removed for production code.
* Is helpful to reader.
* Should be used only to check things that `need` to true.
* Should be removed if the code works when fails.
