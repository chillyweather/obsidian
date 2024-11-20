# Global Error Handlers and Custom Errors

## Global error handlers

To add a global error handler, we'll subscribe to the `uncaughtException` event of the built-in `process` module.

```jsx
const process = require('process');

process.on('uncaughtException', (err, origin) => {
  console.log(`${origin} ${err.name} with the message ${err.message} was not handled. Pay attention to it!`);
});

// Throw a synchronous error
throw new Error(`The missed error`);
```

We can determine where the error occurred by referring to the value stored in the `origin` parameter of the handler function. If its value is `unhandledRejection`, this means an error occurred in the promise. Otherwise, it means it was thrown using `throw`.

## Defining custom errors in JavaScript

Developers often need to extend the `Error` object to include additional information necessary for handling errors. For example, we may have a situation where we need to set our own error name or indicate the response status code we want to be sent to the user.

Since errors are normal objects, we can do this manually. All we need to do is specify the desired information as a property of a specific error instance.

However, in practice, developers usually define custom error classes by extending the standard `Error` class. By reusing code, developers prevent code duplication.

Data validation error:
```jsx
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = "ValidationError";
    this.statusCode = 400;
  }
}
```

We simply extended the standard `Error` class by setting the values of the `name` and `statusCode` fields in the constructor. In the future, we'll need the `name` field to determine the type of error.

You can use your own error in the same way you'd use a standard one, for example: `throw new ValidationError("A validation error occurred")`.