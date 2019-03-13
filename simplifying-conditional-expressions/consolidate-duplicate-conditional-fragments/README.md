**Consolidate Duplicate Conditional Fragments**

This technique is pretty straight forward.  
Same piece of code used in all branches of a conditional.  
Then move the code outside of conditional and make it used once.

**Example**

_Issue_

```csharp
void WriteThenSendEmail()
{
  if(CanWrite())
  {
    WriteToFile();
    SendEmail();
  }
  else
  {
    LogError();
    SendEmail();
  }
}
```

_Refactoring_

```csharp
void WriteThenSendEmail()
{
  if(CanWrite())
  {
    WriteToFile();
  }
  else
  {
    LogError();
  }
  SendEmail();
}
```

This is easy. But we should be careful in quite long methods since if there happens  
an alternative branching `SendEmail()` method would be called anyways.  

Same approach could be used in try-catch statements.  
We can move the same codes from `catch` blocks to a `finally` block and make it call once.
