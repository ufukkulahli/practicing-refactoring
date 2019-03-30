**Replace Temp with Query**

Extract temp variable's expression into its dedicated method.  
Use newly created method from necessary places by invoking it.  
Delete temp variable.  

Using temps causes methods to be longer since we can access them over and over again.  
This technique is not just to delete temps also for making extract method easier.  
Allows all methods inside class to use query method.


**Example**

_Issue_

```csharp
// TODO
```

_Refactoring_

```csharp
// TODO
```

We may need to use `Split Temporary Variable` or `Separate Query from Modifier` to be able to use this one.
