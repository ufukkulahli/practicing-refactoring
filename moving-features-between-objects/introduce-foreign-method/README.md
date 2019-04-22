**Introduce Foreign Method**

We need a method on the `server` object (may be a third party class) but we can not `modify` the class.  
Introduce a `foreign method` on the client class, pass the server object as argument, do the desired work (which suppose to be in the server object).

Example

_Issue_

```csharp
class Report
{
  readonly DateTime previousEnd;
  public Report(DateTime previousEnd)=>this.previousEnd=previousEnd;
  void SendReport()
  {
    // We want something like `NextWeek` functionality
    DateTime nextWeek = previousEnd.AddDays(7);
    //...
  }
}
```

_Refactoring_

```csharp
class Report
{
  readonly DateTime previousEnd;
  public Report(DateTime previousEnd)=>this.previousEnd=previousEnd;
  void SendReport()
  {
    DateTime nextWeek = NextWeek(previousEnd);
    //...
  }
  // Foreign method
  private static DateTime NextWeek(DateTime date)=>date.AddDays(7);
}
```

Commenting as `foreign method` is useful for future lookups.  
When we have the chance of adding this method onto desired object we can quickly find it with the help of comment.