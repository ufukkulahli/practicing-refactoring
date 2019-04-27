**Introduce Local Extension**

We need several methods on the server object (may be a third party class) but we can not modify the class.  
Introduce a new class containing these methods. Make new class `subclass` or `wrapper` of server class.

Example

Using subclass:

_Issue_

```csharp
// We want something like `NextWeek` functionality but it does not exist.
CustomDateTime nextWeek = previousEnd.NextWeek();
```

_Refactoring_

```csharp
class ExtensionDate : CustomDateTime
{
  public ExtensionDate(string dateTime) : base(dateTime){}
  public ExtensionDate(CustomDateTime dateTime) : base (dateTime.GetTime()){}
  public CustomDateTime NextWeek()
  {
    return new CustomDateTime(dateTime.GetYear(), dateTime.GetMonth(), dateTime.GetDay() + 7);
  }
}
```
