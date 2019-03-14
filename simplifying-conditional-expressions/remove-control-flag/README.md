**Remove Control Flag**

This technique is to eliminate old programming era habits.  
There is a flag variable to start process, use of inside process, use of terminate process.  
This variable acts as a control flag.   
Instead, modern programming languages have special keywords to control the flow of processes like `break, continue, return`.  
We use these keywords to get rid off that flag variables.

**Example**

_Issue_

```csharp
void ValidateEmails(IEnumerable<string> emails)
{
  var hasNotValidEmail = false;
  foreach(var email in emails)
  {
    if(!hasNotValidEmail)
    {
      if(notValid(email))
      {
	hasNotValidEmail = true;
	ShowWarning(email);
      }
    }
  }
}
```

_Refactoring_

```csharp
void ValidateEmails(IEnumerable<string> emails)
{
  foreach(var email in emails)
  {
    if(notValid(email))
    {
      ShowWarning(email);
      break;
    }
  }
}
```
