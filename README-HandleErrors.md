# Handle Errors

Errors meant something which accidentially happens or could happen beside the planned program flow, not the Jave Error class.

There many ways to handle errors. Below some of them are sorted from worse to acceptable:


## Do Nothing

This is the worst way to handle an error. In the worst case the error will crash your
application. So: NEVER IGNORE A THROWN EXCEPTION OR A POTENTIAL ERROR SITUATION !!!


## Send an Error Message to Console or Log

Which work for warning (meant situation, which will not harm the program flow), will not work for errors. In worst nobody will notice the error and the user is wondering about
unexpected application behavior.


## Throw an Exception

This is good way to handle program errors, but should be used for unexpected or 	
unpredictable error situations such network problems or missing file pathes.
Keep in mind: Catching and throwing exceptions cause some overhead in the JVM's program flow.


## Return an Error State

Whenever possible, integrate found errors in the program flow by using an appropriate error status.
This may collide with return values of method. If there is no space for such a return value, use the second best solution and throw an exception.

Example:

```
    public ErrorState doSomething(Long parameter) {
        ...
        if (parameter < 0) {
            return ErrorState.VALUE_IS_NEGATIVE;
        }
        ...
        return ErrorState.ANTHING_ALLRIGHT_CLYDE;
    }
```

Don't break the semantics of the method to only have an error state. If your method `doSomething` computes a value which should be returned, then prefer to throw an exception.


## Summary

Lacking a flexible return values, in Java the most used method to handle error situations is to throw an exception. If you see a way to return a kind of error state, prefer this, other wise throw an exception.

Take care while choosing the right exception and take a look to the packages, where possible by name matching exceptions come from. If it is no standard package like `java.util` or `java.lang`, prefer to create your own exception.

Creating your own exception, prefer inheriting from `RuntimeException` instead of `Exception`. Customer of the method will like this ...