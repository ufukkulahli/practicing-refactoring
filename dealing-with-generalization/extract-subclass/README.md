**Extract Subclass**

Class' features are used in some instances.  
Create a subclass for these features and used it where necessary.

Example

_Issue_

```csharp
class JobItem
{
  private int unitPrice, quantity;
  private Employee employee;
  private bool isLabor;
  public JobItem(int unitPrice, quantity, Employee employee, bool isLabor)
  {
    // ...
  }
  public int GetUnitPrice()
  {
    return isLabor ? employee.GetRate() : unitPrice;
  }
}

class Employee
{
  public int rate {get;}
  public Employee(int rate) => this.rate = rate;
}
```

_Refactoring_

```csharp
class LaborItem : JobItem
{
  public LaborItem(quantity, Employee employee) :
  base(0, quantity, true)
  {
    this.employee = employee;
  }
  protected bool IsLabor() => true;
  public int GetUnitPrice() => employee.GetRate();
}

class JobItem
{
  protected JobItem(int unitPrice, quantity, bool isLabor)
  {
  }
  protected bool IsLabor() => false;
  public int GetUnitPrice() => this.unitPrice;
}
```