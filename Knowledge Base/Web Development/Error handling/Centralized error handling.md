# Centralized error handling

1. We'll need to add the following middleware to our app:

```jsx
app.use((err, req, res, next) => {
  // this is the error handler
});
```

2. This error handler should be added after all other `app.use()` statements. This is usually done somewhere at the end of `app.js`:

```jsx
// app.js

// all the app.js code

// we handle all errors here
app.use((err, req, res, next) => {
  res.status(500).send({ message: 'An error occurred on the server' });
});

app.listen(PORT);
```

## Calling `next()` with an Argument

If we pass an argument to `next()`, it will have a completely different effect and the request will go to the error handler instead:

```jsx
// calling next() with any argument
// will pass the request to the error handler

next('Argument');
```

Although you can technically pass any argument to `next()`, it's good practice to pass an error instance, like so:

```jsx
// call next() with an error argument

next(new Error('Authorization error'));
```

In the handler, we can use the message that was passed to the `Error` instance when it was created:

```jsx
app.use((err, req, res, next) => {
  res.send({ message: err.message });
});

// { "message": "Authorization error" }
```

## Custom Error Constructors

The simplest `404` constructor looks like this:

```jsx
// errors/not-found-err.js

class NotFoundError extends Error {
  constructor(message) {
    super(message);
    this.statusCode = 404;
  }
}

module.exports = NotFoundError;
```

All this constructor does is inherit and set the `statusCode` property from the standard `Error` class. After the `NotFoundError` constructor has been created, it can be imported elsewhere in your code and used in conjunction with the `throw` statement:

```jsx
const NotFoundError = require('./errors/not-found-err');

module.exports.getProfile = (req, res, next) => User
  .findOne({ _id: req.params.userId })
  .then((user) => {
    if (!user) {
      // if there is no such user,
      // throw an exception
      throw new NotFoundError('No user with matching ID found');
    }

    res.send(user);
  })
  // ...
```

The `throw` statement throws an exception, and code handling continues to the next `catch()` block, so don't forget to add it. We can do it elegantly:

```jsx
const NotFoundError = require('./errors/not-found-err');

module.exports.getProfile = (req, res, next) => User
  .findOne({ _id: req.params.userId })
  .then((user) => {
    if (!user) {
      throw new NotFoundError('No user with matching ID found');
    }

    res.send(user);
  })
  .catch(next); // catch added
```

This `catch()` entry is equivalent to the following one:

```jsx
.catch(err => next(err));
```

So `next()` will be called with an error argument and the request will go to the error handler, but now with the added status and message:

```jsx
app.use((err, req, res, next) => {
  res.status(err.statusCode).send({ message: err.message });
});
```

## Three Important Rules for Centralized Error Handling

**1. Always terminate promise chains with a `catch()` block.**

Pass the `next()` function to the `catch()` block and add an error handler somewhere at the end of `app.js`. If a promise chain is not terminated with a `catch()`, it will result in an unhandled promise rejection. In future versions of Node.js, the application will crash.

**2. Don't use `throw` in terminating `catch()` blocks.**

`throw` redirects the code handling to the next `catch()` block. If you use `throw` in the last `catch()` block, it will have nowhere to go and this will lead to an unhandled promise rejection.

**3. If the handler receives an error without a status, return a server error.**

We have created our own error constructors. Now, when we need to return an error to the client, we create an instance of the corresponding error and throw an exception using the `throw` statement. `throw` transfers code handling to the `catch()` block where `next()` waits for it. One thing to bear in mind is that it's possible for handling to go to the `catch()` block for some other reason, not only when we've used `throw`. For example, an exception may be thrown when trying to access the database, or our code might simply crash. If an error is not generated by us, it won't have the `statusCode` property:

```jsx
app.use((err, req, res, next) => {
  console.log(err.statusCode); // undefined
});
```

In this case, we'll consider it a server error. We'll return a status code of `500` and a standard message:

```jsx
app.use((err, req, res, next) => {
  // if an error has no status, display 500
  const { statusCode = 500, message } = err;
  res
    .status(statusCode)
    .send({
      // check the status and display a message based on it
      message: statusCode === 500
        ? 'An error occurred on the server'
        : message
    });
});
```