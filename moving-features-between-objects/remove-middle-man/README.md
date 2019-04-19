**Remove Middle Man**

Adding `delegating methods` to `server` object becomes painful to provide clients functionality.  
That is server turns just to a `middle man` to operate onto.  
`Delegations` are looking redundant now.  
We remove them and let the `client` call delegate directly.  
This technique is the reverse of `hide delegate`.  

**Example**

_Issue_

```csharp
public class Student
{
  private Class Class;
  public Teacher GetTeacher() => this.Class.GetTeacher();
}

public class Class
{
  private Teacher teacher;
  public Class(Teacher teacher) => this.teacher = teacher;
  public Teacher GetTeacher() => this.teacher;
}

public class Program
{
  public void Main()
  {
    // ...
    var teacher = joeTheStudent.GetTeacher();
    // ...
  }
}
```

_Refactoring_

```csharp
public class Student
{
  public Class Class{get;set;}
}

public class Class
{
  private Teacher teacher;
  public Class(Teacher teacher) => this.teacher = teacher;
  public Teacher GetTeacher() => this.teacher;
}

public class Program
{
  public void Main()
  {
    // ...
    var teacher = joeTheStudent.Class.GetTeacher();
    // ...
  }
}
```
