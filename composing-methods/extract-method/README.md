**Extract method**

This technique is the most common one and plays important role to make things clear in the most simple way.  
Abstractions, architectures have their own importance but this is where all begins.  
We can use this technique for long methods or code blocks need comments to understand their intent.  
Giving methods good names is a must.   
By taking out codes to their dedicated methods and giving clear method names we make things official.  
Method name and its body should overlap semantically. We can use this to decide method long.  
Names should tell 'what it does' not 'how it does'.  
If a better method name performs better then extract the code even if it is a single line.  
If otherwise then we can leave it alone.  

Example

_Issue_

```csharp
//TODO
```

_Refactoring_

```chsarp
//TODO
```

If some variables prevents or hardens extracting see:
* `split temporary variable`,
* `replace temp with query`,
* `replace method with method object`
* `remove assignments to parameters`
