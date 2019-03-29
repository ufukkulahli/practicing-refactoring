**Inline Temp**

This refactoring technique is for temp variables inside methods.  

We can apply this when;
* The temp is used only once and does nothing more, meaning that it is unnecessary
* The temp is getting the way of further refactorings such as `extract method`, `replace temp with query`

Leave it when;
* The temp is being used for caching result of some method

Example

_Issue_

```csharp
bool HasMiddleName()
{
  var middleName = person.GetMiddleName();
  return String.IsNullOrEmpty(middleName);
}
```

_Refactoring_

```csharp
bool HasMiddleName()
{
  return String.IsNullOrEmpty(person.GetMiddleName());
}
```
