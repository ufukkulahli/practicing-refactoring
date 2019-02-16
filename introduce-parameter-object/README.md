**Introduce Parameter Object**

When the numbers of method parameters increase then we can use this technique.
Simply, put method parameters into a new object and then use this object for method parameter.
 
 **Example**
 
 _Issue_
 ```csharp
 void Calculate(int number1, int number2, int number3)
 ```
 _Refactoring_
 ```csharp
 public class NumberArgs
 {
    public int number1 {get;set;}
    public int number2 {get;set;}
    public int number3 {get;set;}
 }
 
public class Calculator
{
    public void Calculate(NumberArgs args)
    {
        // Calculation as it is before
        var result = (args.number1 / args.number2) * args.number3;
    }
}
  ```

Notes

But on the other hand, a method with many parameters is a signal of loosing the "single responsibility".
This should be refactored with other techniques.

Use of this refactoring **may** lead us to use of:
* Parameterized strategy pattern,
* Abstract factory pattern,
* Facade service