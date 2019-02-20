**Preserve Whole Object**

Instead of passing values _from same object_ to method one by one, just pass the whole object.

**Example**

_Issue_

```csharp
var number1 = numberArgs.GetNumber1();
var number2 = numberArgs.GetNumber2();
var number3 = numberArgs.GetNumber3();

calculator.Calculate(number1, number2, number3);
```

_Refactoring_

```csharp
calculator.Calculate(numberArgs);
```

This technique eliminates smells
* Primitive obsession
* Long parameter list
* Long method
* Data clumps

Similar refactorings
* Introduce parameter object
* Replace parameter with method call