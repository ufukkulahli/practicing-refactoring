**Inline Class**

When we see that a class does almost nothing and no responsibility will be added in the future.  
So we can move its members to a most relevant class and delete it.  
This technique is the reverse of `extract class`.

**Example**

_Issue_

```csharp
public class Person
{
  private string name;
  private CellPhoneNumber cellPhoneNumber  = new CellPhoneNumber();

  public string GetCellPhoneNumber() => this.cellPhoneNumber.GetCellPhoneNumber();
  public CellPhoneNumber GetCellPhoneNumberObj() => this.cellPhoneNumber;
}

public class CellPhoneNumber
{
  private string cellPhoneNumber;
  private string countryCode;

  public string GetCellPhoneNumber() => countryCode + cellPhoneNumber;

  public void SetCellPhoneNumber(string countryCode, string cellPhoneNumber)
  {
    this.countryCode = countryCode;
    this.cellPhoneNumber = cellPhoneNumber;
  }
}
```

_Refactoring_

```csharp
public class Person
{
  private string name;
  private string cellPhoneNumber;
  private string countryCode;

  public string GetCellPhoneNumber() => $"{countryCode}{cellPhoneNumber}";

  public void SetCellPhoneNumber(string countryCode, string cellPhoneNumber)
  {
    this.countryCode = countryCode;
    this.cellPhoneNumber = cellPhoneNumber;
  }
}
```
