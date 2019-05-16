**Change Reference to Value*

This refactoring technique is the reverse of `Change Value to Reference`.  

**Example**

_Issue_

```csharp
class Currency
{
  public Currency New(string code) => new Currency(code);
  private Currency(string code) => this.code = code;
  private string code;
  public string Code() => this.code;
}
```

_Refactoring_

```csharp
class Currency
{
  public Currency(string code) => this.Code = code;
  public string Code { get; private set; }
  public override bool Equals(object obj) => this.Code.Equals(((Currency)obj).Code);
  public override int GetHashCode() => this.Code.GetHashCode();
}
class Client
{
  public bool Same()
  {
    return
      new Currency("USD").Equals(new Currency("USD"));
  }
}
```

Since Currency is a value object now 'Same' method returns true.
