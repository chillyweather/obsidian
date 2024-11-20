# Approaches to Determine the Error Type

There are two primary approaches to determining error types in JS:

-   Using the name of an error (stored in the `name` field)
-   Using the error class with the `instanceof` operator

## The main rules for error handling

In the error handling block, make sure to add a condition for checking the error type using an `if` statement and describe the handling in the body of the `if` statement.

```jsx
...
} catch (err) {
  if (check_condition_for_error_1) {
    // Logic for handling error 1    ...
    return;
  }

  if (check_condition_for_error_2) {
    // Logic for handling error 2
    ...
    return;
  }

  // Logic for handling unknown errors
  // In this example we only log them
  console.log(`An unknown error ${err.name} has occurred: ${err.message}`);
}
```

When coding error handlers, regardless of the approach you're using to determine the error type (check condition), adhere to these two rules:

1.  At the end of the `catch` block, you must describe the logic for handling unknown errors or, as often referred to, you'll need to implement "default error handling". You'll need to do this for the error to be handled in any situation, even if it doesn't meet any of the listed conditions. If there is no "default" branch and the error doesn't fall under any of the conditions (an unknown error), it will be ignored, which is unacceptable.
2.  At the end of each block that handles a specific error, add an execution stop with `return` to exit `try...catch`. We do this to avoid repeated checks in subsequent if blocks when the error has already been handled. Moreover, `return` doesn't allow execution to reach the "default branch". If the error has already been handled, the code execution will simply terminate earlier.

### Determining the error type using its name

```jsx

...
} catch (err) {
  // Check the name of the error
  if (err.name === "ErrorName") { 
    // Describe the logic for handling the error
    ...
    return;
  }
  ...
} 
```


### Hierarchy of errors: the `instanceof` operator

Error classes can be inherited like any other classes in JavaScript. This allows us to describe a hierarchy of errors, group them, and describe the common handling logic.

In this case, the `instanceof` operator is used. It allows us to determine whether the specified object (error) is an instance of a certain class, taking into account the inheritance hierarchy.

For example, to check whether `err` is a `SomeErrorName` error or its special case (an inheritor class), we'd write the following: `err instanceof SomeErrorName`. If it is, the expression evaluates to `true`. Otherwise, it evaluates to `false`.

To better understand how the `instanceof` operator works, let's look at an example. We'll describe three error classes: `SomeErrorName`,`AnotherErrorName`, and `ChildOfAnotherErrorName`. We'll also indicate that `ChildOfAnotherErrorName` is the inheritor (that is, a special case) of `AnotherErrorName`.

Next, we'll check the result returned by `instanceof` for each of them:

```jsx
class SomeError extends Error {};
class AnotherError extends Error {};
class ChildOfAnotherError extends AnotherError;

let someError = new SomeError("SomeError")
let anotherError = new AnotherError("AnotherError")
let childOfAnotherError = new ChildOfAnotherError("Child error of AnotherError")

// This will return true because someError is an instance of SomeError
console.log(someError instanceof SomeError)

// This will return false because anotherError is an instance of AnotherError, not SomeError
console.log(anotherError instanceof SomeError)

// This will return true, childOfAnotherError is an instance of ChildOfAnotherError
// and ChildOfAnotherError is inherited from AnotherError
console.log(childOfAnotherError instanceof AnotherError)

// This will return true, childOfAnotherError is an instance of ChildOfAnotherError
console.log(childOfAnotherError instanceof ChildOfAnotherError)
```

```jsx
class ErrorGroup extends Error {};
class FirstChildOfErrorGroup extends ErrorGroup;
class SecondChildOfErrorGroup extends ErrorGroup;

try {
....
} catch( err) {
  // Separate handler for FirstChildOfAnotherError
  if (err instanceof FirstChildOfErrorGroup) { ... }

  // Handler for a group of errors
  if (err instanceof ErrorGroup) { ... }
}
```