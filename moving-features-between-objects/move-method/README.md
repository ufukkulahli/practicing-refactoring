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
public class Account
{
  private AccountType type;
  private int daysOverdrawn;

  public double bankCharge()
  {
    var result = 4.5;
    if (daysOverdrawn > 0)
    {
      result += type.OverdraftCharge(daysOverdrawn);
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

  public double OverdraftCharge(int daysOverdrawn)
  {
    if (isPremium())
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

  // ...
}
```

When the target class needs a feature from source class we can
* move this feature to the target class
* create or use a reference from the target class to the source
* pass the source object as a parameter to the method
* pass as a parameter if the feature is a variable
