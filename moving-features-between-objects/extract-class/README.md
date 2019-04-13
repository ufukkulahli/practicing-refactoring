**Extract Class**

When we see that a new class should be created from an existing one.  
So we move the relevant fields and methods to the new class.

**Example**

_Issue_

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

_Refactoring_

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

To extract a class a rule of thumb could be the  
* If a subset of the data and a subset of the methods look consistent together
* If subsets of data that usually change together
* Subsets of data that particularly dependent on each other

After creating the new class we decide how much `expose` of it to clients  
* Completely hide by providing delegating methods for its interface
* Expose it completely
* Expose it to some clients such as in the same package

Another important decision is how to `expose` of new class
* As a `reference object`
* As an `immutable value object`
