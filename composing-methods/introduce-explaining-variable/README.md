**Introduce Explaining Variable(Extract Variable)**

We use this one to make complicated expressions more clear by assigning them to temp variables.  
We would choose `extract method` if possible.  
But if it is hard to use `extract method` in the first place  
then we can use this technique to start making things clear for further refactorings.

**Example**

_Issue_

```csharp
bool IsChromeOnMacOS()
{
  if (platform.ToUpper().IndexOf("MAC") > -1 &&
    browser.ToUpper().IndexOf("Chrome") > -1 &&
    resize > 0)
  {
    return true;
  }
  return false;
}
```

_Refactoring_

```csharp
bool IsChromeOnMacOS()
{
  var isMacOS = platform.ToUpper().IndexOf("MAC") > -1;
  var isChrome = browser.ToUpper().IndexOf("Chrome") > -1;
  var wasResized = resize > 0;
  var chromeOnMacOS = isMacOS && isChrome && wasResized;
  if (chromeOnMacOS)
  {
    return true;
  }
  return false;
}
```
