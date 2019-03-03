**Replace exception with test**

There are times that we write blindly try-catch statements even for simple jobs.  
We try to invoke a method inside try block then immediately we catch exception and return some value.  
This practice says us that if we can avoid of try-catch by a conditional statement then we should do so.  

**Example**

_Issue_

```csharp
string GetDepartmentByName(string name)
{
  try
  {
    return namesAndDepartmens[name];
  }
  catch(Exception e)
  {
    return string.Empty;
  }
}
```

_Refactoring_

```csharp
string GetDepartmentByName(string name)
{
  if(namesAndDepartments.Contains(name))
  {
    return namesAndDepartmens[name];
  }
  return string.Empty;
}
```

Exceptions are for real errors.  
And use of them may be expensive for application.  
So should be used properly.  
