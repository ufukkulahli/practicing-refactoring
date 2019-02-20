**Separate query from modifier**

We have a method that _returns a value_ and also _modifies something_.
This refactoring technique says that we should split these two distinct behaviours into separate methods.
Ok.
But what is query and modifier?
Query term is used for methods that return value.
Modifier (or Command) term is used for methods that does not return value
but does a job such as writing to database or modifying a value.
We call this _Command and Query Responsibility Segregation_.
A method either should return value or modify something.

**Example**
 
 _Issue_
 
 ```csharp
var countries = GetCountriesAndFillUpCache();
 ```
 
 _Refactoring_
 
 ```csharp
 FillUpCache();
 var countries = GetCountries();
  ```