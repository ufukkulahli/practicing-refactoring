**Rename method**

When a method name does not reflect its intent or poorly written we simply rename it.  
Also, using abbreviations for method names makes it hard to read.

**Example**

_Issue_

```csharp
decimal ClcPrice(int factor)
{
  return this.amount * factor
}
```

_Refactoring_

```csharp
decimal CalculatePrice(int factor)
{
  return this.amount * factor
}
```

This technique should be applied to wherever possible  
such as fields, properties, classes even its name suggests renaming methods.
