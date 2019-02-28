**Replace Error Code with Exception**

We want to let the know client code what happened in our method so for that we use some special values like integers.
Each integer has a meaning such as "-1" for error, "0" for success.
Instead of depending some codes to tell clients that something went wrong,
we can use exceptions.
Something goes wrong, we throw exceptions, who has the responsibility to handle error that place catches exception.

**Example**

_Issue_

```csharp
int SendEmail(string address, string email)
{
  if(string.IsNullOrEmpty(address)
  {
    return -1;
  }
  else
  {
    send(address, email);
    return 0;
  }
}

// use of mail send
int code = SendEmail("a@b.com, "hello");
if(code == -1)
{
  // error actions
}
else
{
  // success actions
}
```

_Refactoring_

```csharp
void SendEmail(string address, string email)
{
  if(string.IsNullOrEmpty(address)
  {
    throw new EmailNotFoundException();
  }
  send(address, email);
}

// use of mail send
SendEmail("a@b.com, "hello");
// no more if-else!
// obviously an exception handler will catch error in a previous chain
```

The problem with error code approach is we push our clients to handle different return actions.
We cause to branching in the client code.
They will have to write if-else statements.
And we can guess what happens to our code base then.
This is from procedural era.
In OOP paradigm we have to build objects.
**Also, do not use exceptions to manage code execution.**
This is no different than forcing clients to write if-else statements.
After this refactoring technique we can delete if-else wrappers in client codes.
They do not have to check anything anymore.
Because if something goes wrong an exception handler will take care of the error situation.