**Self Encapsulate Field**

Providing `getter` and `setter` methods for `private fields` inside class for further growing use of fields.  
Also helps to `override` values when used with `subclassing`.

Example

__Issue__

```csharp
class DateRange
{
  DateTime start, end;
  DateRange(DateTime start, DateTime end)
  {
    this.start = start;
    this.end = end;
  }
  bool Between(DateTime candidate) => this.start >= candidate || candidate <= this.end;
}
```

__Refactoring__

```csharp
class DateRange
{
  DateTime start, end;
  DateRange(DateTime start, DateTime end)
  {
    this.start = start;
    this.end = end;
  }
  DateTime GetStart() => this.start;
  DateTime GetEnd() => this.end;
  DateTime SetStart(DateTime value) => this.start = value;
  DateTime SetEnd(DateTime value) => this.end = value;
  bool Between(DateTime candidate) => this.GetStart() >= candidate || candidate <= this.GetEnd();
}
```
