**Introduce Null Object**

Trying to be safe with null checks before invoking a method is exhausting many times.  
To get rid off of null checks and invoke methods without fear is possible with this technique.  
Simply, create new sub class and override those methods which cause to null reference exception.  
And now, to represent absent object, instead of returning null return that sub class called null object.  
By that, null checks could be deleted and invocation to those methods will not cause exception.
