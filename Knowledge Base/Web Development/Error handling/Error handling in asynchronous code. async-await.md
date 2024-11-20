# Error handling in asynchronous code: 

## async/await

The purpose of the async/await syntax is to enable the developer to write asynchronous code in a synchronous style. Simply put, it tells the JS engine where to "wait" for the result of a promise before proceeding any further in the code.

```jsx
// Moved the code returning the promise with an error to an external function
function returnPromiseError() { 
  return Promise.reject(new Error("Something went wrong...")); 
}

(async function testAsyncAwaitError() {
  try {
    console.log("Function execution started");
    await returnPromiseError(); // wait till returnPromiseError() is executed
  } catch (err) {
    console.log(`${err.name} with the message ${err.message} has occured, but we've handled it`);
  }
  console.log("Function execution completed successfully");
})();
```

![[Pasted image 20211130183721.png]]

## the `.catch` handler
If an error occurs when executing code in a promise, the error goes to the nearest `.catch` block described after it.

```jsx
function returnPromiseError() { 
  return Promise.reject(new Error("Error. Something went wrong..."));
}

(function testPromiseRejectHandler() {
  returnPromiseError();
  .catch((err) => {
    console.log(`Error ${err.name} with the message ${err.message} has occurred while executing the code, but we've handled it`);
  });
})();

```

## Error handling in callbacks

JavaScript developers have a convention where the result of function execution is returned to the callback as two arguments:

-   The error object (if it occurs)
-   The result of the operation

```jsx
const fs = require('fs');
function writeTextToFile(filename, text) {
  fs.writeFile(filename, text, function (err, res) {
    // check that the error object is not empty
    if (err) {
      console.error(`An error has occurred while writing the file: ${err.message}`);
      // end the function execution if an error occurs
      return;
    }
    console.log(`fs.writeFile has ended with the following result: ${res}`);
  })
}

writeTextToFile('', 'sometext');
```

## Error handling and Mongoose: the `orFail()` helper

When attempting to find a record with Mongoose, such as with `findOne` or `findById`, if the record is not found, instead of throwing an error, it will simply pass `null` into your `.then` handler.

```jsx
Card.find({ _id: "507f1f77bcf86cd799439011" }) // some nonexistent ID
  .then((cardData) => {
    // incorrectly sends `null` back to the client with a 200 status!
    res.send(cardData);
  })
  .catch((error) => {
    // does not run because no error was thrown
  });
```

You could handle this by checking `if (cardData == null)` in `.then` and throwing an error there, but the `orFail` helper can streamline your code by running when no record is found:
```jsx
Card.find({ title: "nonexistant card" })
  .orFail() // throws a DocumentNotFoundError
  .then((cardData) => {
    res.send(cardData); // skipped, because an error was thrown
  })
  .catch((error) => {
    // now this does run, so we can handle the error and return an appropriate message
  });
```

pass in custom function to the orFrail method:

```jsx
.orFail(() => {
  const error = new Error("No card found with that id");
  error.statusCode = 404;
  throw error; // Remember to throw an error so .catch handles it instead of .then
})
```