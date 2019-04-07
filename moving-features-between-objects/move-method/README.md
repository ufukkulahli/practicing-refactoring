**Move Method**

A method is used more by another class than its own.  
Then move the method to 'other' class.

**Example**

_Issue_

```csharp
public class Account
{
  private AccountType type;
  private int daysOverdrawn;

  public double OverdraftCharge()
  {
    if (type.isPremium())
    {
      double result = 10;
      if (daysOverdrawn > 7)
      {
        result += (daysOverdrawn - 7) * 0.85;
      }

      return result;
    }

    return daysOverdrawn * 1.75;
  }

  public double bankCharge()
  {
    var result = 4.5;
    if (daysOverdrawn > 0)
    {
      result += OverdraftCharge();
    }

    return result;
  }

  // ...
}

public class AccountType
{
  private bool premium;

  public bool isPremium()
  {
    return premium;
  }

  // ...
}
```

_Refactoring_

```csharp
// TODO
```
