**Consolidate Duplicate Conditional Fragments**

This technique is pretty straight forward.  
Same piece of code used in all branches of a conditional.  
Then move the code outside of conditional and make it used once.

**Example**

_Issue_

```csharp
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
```

_Refactoring_

```csharp
if(CanWrite())
{
  WriteToFile();
}
else
{
  LogError();
}
SendEmail();
```

