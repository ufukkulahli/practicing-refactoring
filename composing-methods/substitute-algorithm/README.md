**Substitute Algorithm**

After of some refactoring we may reach to a point that we see things more clearly and understand the problem better.  
In this case we may realize that there is an easier way of solving the problem.  
Write down the new algorithm, run the existing tests against it.  
If tests are OK then replace the old solution with the new one.
If otherwise, compare the old and new solution's test results and adjust the algorithm to pass tests.

**Example**

_Issue_

```csharp
bool AnyDaltonExist(string[] people)
{
  for (var person in people)
  {
    if (people.Equals("Joe"))
    {
      return true;
    }
    if (people.Equals("Jack"))
    {
      return true;
    }
    if (people.Equals("William"))
    {
      return true;
    }
    if (people.Equals("Averell"))
    {
      return true;
    }
  }
  return false;
}
```

_Refactoring_

```csharp
bool AnyDaltonExist(string[] people)
{
  List<string> daltons = new List<string>() {"Joe", "Jack", "William", "Averell"};

  for (var person in people)
  {
    if (daltons.Contains(person))
    {
      return true;
    }
  }
  return false;
}
```
