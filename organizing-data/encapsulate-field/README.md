**Encapsulate Field**

Provide getter and setter methods for public variable and in the mean time make it private.

**Example**

_Issue_

```csharp
class Employee
{
  public decimal Salary;
  // ...
}
```

_Refactoring_

```csharp
class Employee
{
  private decimal salary;
  public decimal GetSalary() => this.salary;
  public void SetSalary(decimal salary) => this.salary = salary;
  // ...
}
```
