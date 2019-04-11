**Move Field**

A field is used more by another class than its own.  
Then move the field to 'other' class.

**Example**

_Issue_

```csharp
public class Account
{
  private AccountType type;
  private double interestRate;

  double InterestForAmountDays(double amount, int days)
  {
    return this.interestRate * amount * days / 365;
  }
}
```

_Refactoring_

```csharp
public class Account
{
  private AccountType type;

  double InterestForAmountDays(double amount, int days)
  {
    return this.type.InterestRate * amount * days / 365;
  }
}

public class AccountType
{
  private double interestRate;
  public double InterestRate
  {
    get {return this.interestRate;}
    set {this.interestRate = value;}
  }
}
```

When a lot of methods use the interest rate field, we can use `Self Encapsulate Field`.  
To apply for this example, create getter and setter methods for `interestRate` field in `Account` class.  
Then call the relevant getter and setter methods of `InterestRate` property in `AccountType` class from `Account` class.
