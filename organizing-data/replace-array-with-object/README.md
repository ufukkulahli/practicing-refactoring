**Replace Array with Object**

An array is being used to represent a object instead of an actual one.  

**Example**

_Issue_

```csharp
class Program
{
  void Main()
  {
    var record = new string[2];
    record[0] = "Liverpool";
    record[1] = "15";
  }
}
```

_Refactoring_

```csharp
class Performance
{
  public string Name {get;set;}
  public int Wins {get;set;}
}

class Program
{
  void Main()
  {
    var performance = new Performance();
    performance.Name = "Liverpool";
    performance.Wins = 15;
  }
}
```

Obviously using an array instead of a real object should be avoided.
