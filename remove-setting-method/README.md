**Remove Setting Method**

The value of a field should be set only when it is created.
It should not change any time after that.
To prevent this change we simply remove the methods that set the field's value.
If there is no constructor to set the field then we add one, add constructor argument.
By this action, we get to the immutability one more step.
Because objects should defend themselves to random changes.

**Example**
 
 _Issue_
 
 ```csharp
 customer.SetId(1234);
 ```
 
 _Refactoring_
 
 ```csharp
public class Customer
{
    private readonly int Id;
    
    public Customer(int Id)
    {
      this.Id = Id;
    }
    
    ~~public void SetId(int Id) { this.Id=Id; }~~
}
  ```