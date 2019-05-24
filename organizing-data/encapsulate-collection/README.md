**Encapsulate Collection**

Restrict operations on a collection variable.  
Allowing modifications on our collection would eventually have side effects.  
With a slightly big class, it is hard to tell who does what on it.  
To prevent these symptoms, return `unmodifiable collection` for clients and add required operational methods such as `Add`, `Remove`.

**Example**

_Issue_

```csharp
class Combination
{
  List<List<int>> values;
  public List<List<int>> GetValues() => this.values;
  public void SetValues(List<List<int>> values) => this.values = values;
  // ...
}
```

_Refactoring_

```csharp
class Combination
{
  private List<List<int>> values;
  public ReadOnlyCollection<ReadOnlyCollection<int>> GetValues() => this.values.AsReadOnly();
  public void Add(IEnumerable<int> val) => this.values.Add(val);
}
```
