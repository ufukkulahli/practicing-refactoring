**Hide method**

We can make modifier of a method private or protected  
when a method is not used by other class or is used only inside its own class hierarchy.

**Example**

_Issue_

```csharp
public int GetAge()
{
  return this.age;
}
```

_Refactoring_

```csharp
private int GetAge()
{
  return this.age;
}
```

If method is used by a subclass then we can make it protected

```csharp
protected int GetAge()
{
  return this.age;
}
```

By hiding methods as much as possible we move toward more consistent code base.  
We can track down the places where modifications are done to a object's state.  
We reduce the side effects of application.  

This technique eliminates smell
* Data class
