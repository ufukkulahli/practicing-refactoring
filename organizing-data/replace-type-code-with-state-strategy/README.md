**Replace Type Code with State/Strategy**

A primitive type code is being used to represent types instead of objects.  
Replace type code with State/Strategy object.

_Issue_

```csharp
class Employee
{
  private int type;
  static int Engineer = 0;
  static int Salesman = 1;
  static int Manager = 2;
  Employee(int type) => this.type = type;
  int PayAmount()
  {
    if(this.type==Engineer)
      return salary;
    if(this.type==Salesman)
      return salary+commision;
    if(this.type==Manager)
      return salary+bonus;
  }
}
```

_Refactoring_

```csharp
class EmployeeType
{
  abstract int TypeCode();
}
class Engineer : EmployeeType
{
  int TypeCode() => Employee.Engineer;
}
class Salesman : EmployeeType
{
  int TypeCode() => Employee.Salesman;
}
class Manager : EmployeeType
{
  int TypeCode() => Employee.Manager;
}
class Employee
{
  private EmployeeType employeeType;
}
```
