**Remove parameter**

This refactoring technique is pretty straight forward.  
A parameter of method is not used anywhere.  
So simply delete it.

**Example**

_Issue_

```csharp
decimal CalculatePrice(int factor)
{
  return this.amount * 2
}
```

_Refactoring_

```csharp
decimal CalculatePrice()
{
  return this.amount * 2
}
```

We should be careful that if method has different implementations elsewhere,  
removing parameter breaks the method signature or one of implementation might be using it.

This refactoring is:

Anti refactoring of
* Add parameter

Similar to
* Rename method

Helps to
* Replace parameter with method call

Eliminates smell
* Speculative generality
