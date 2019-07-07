**Extract Interface**

Several clients use the same subset of a class' interface, or two classes have part of their interfaces in common.
So we extract the subset into an interface.

Example

_Issue_

```csharp
class TimeSheet
{
  public Employee Employee {get;}
  public TimeSheet(Employee employee) => this.Employee = employee;
  public double GetCharge(int days)
  {
    if(this.Employee.HasSpecialSkill)
    {
      return Employee.Rate * days * 1.05;
    }
    return Employee.Rate * days;
  }
}

class Employee
{
  public readonly double Rate;
  public readonly bool HasSpecialSkill;
  public Employee(double rate, bool hasSpecialSkill)
  {
    this.Rate = rate;
    this.HasSpecialSkill = hasSpecialSkill;
  }
  // ...
}
```

_Refactoring_

```csharp
class TimeSheet
{
  public IBillable Billable {get;}
  public TimeSheet(IBillable Billable) => this.Billable = Billable;
  public double GetCharge(int days)
  {
    if(this.Billable.HasSpecialSkill)
    {
      return Billable.Rate * days * 1.05;
    }
    return Billable.Rate * days;
  }
}

interface IBillable
{
  double Rate{get;}
  bool HasSpecialSkill{get;}
}

class Employee : IBillable
{
  // remains same...
}
```