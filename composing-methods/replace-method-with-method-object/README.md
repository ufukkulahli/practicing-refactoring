**Replace Method with Method Object**

We have a complicated method that we can not apply `extract method` because of tangled local variables.  
So move the method into its dedicated class(method object) and turn the local variables to instance fields of newly created class.
By that freely operate on these variables and begin splitting the complicated method into smaller and understandable parts.

**Example**

_Issue_

```csharp
// TODO:
```

_Refactoring_

```csharp
// TODO:
```
