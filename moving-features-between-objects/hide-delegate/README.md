**Hide Delegate**

`Hide delegate` by creating a `delegate method` in `server` object.

We apply this technique when there are several delegates to call each after.  

By providing a delegate method on the server object to `client codes`:
* We may protect clients from further changes when there is a change on delegates or on server (Changes do not propagate from server down to client).
* Strengthen the `Encapsulation`.

**Example**

_Issue_

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

_Refactoring_

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
Encapsulation means that `objects need to know less about other parts of the system` causes to be `told about the change to fewer objects`.  
`Method chanining` and the `train wreck` are the other definitions of these `delegates` that we may encounter.
