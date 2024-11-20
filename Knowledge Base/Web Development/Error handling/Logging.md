# Logging

Logs contain information about events that occur on the server. In the simplest case, it is a record of requests to the server and its response to those requests. If we write down the requests and the responses, we can investigate what went wrong if anything unusual happens. Logs will help you to better understand what is happening on the server.

## Winston

There are many logging solutions available, the most popular and flexible of which is a logging library named Winston, so that's what we're going to use here. In addition, we'll need the `express-winston` middleware to make it convenient to work within Express. After installing the two packages (`winston` and `express-winston`), you'll be able to import them. We'll do all the work in the `middlewares/logger.js` file:

```jsx
// middlewares/logger.js

// importing the necessary modules
const winston = require('winston');
const expressWinston = require('express-winston');
```

After that, you need to create a logger. We will log two types of information — requests to the server and errors that occur on it. To create a request logger, use the `logger()` function of the `expressWinston` module:

```jsx
// middlewares/logger.js

const winston = require('winston');
const expressWinston = require('express-winston');

// create a request logger
const requestLogger = expressWinston.logger({
  transports: [
    new winston.transports.File({ filename: 'request.log' }),
  ],
  format: winston.format.json(),
});
```

Consider the options that we pass upon creation. The `transports` option is responsible for where the log should be written. In our case, this is the `request.log` file. Also, `transports` is an array in which you can write other destinations for your logs. For example, logs can be written to the console or to a third-party analytics service, but we are going to log data to a file for now. The second option is `format`, which is responsible for the format of logging. We have specified `json` because it is convenient to parse.

Now that the request logger is ready to use, let's make an error logger. We need to do this so that when an error occurs, information about it is written to the log, i.e. the name of the error, the message, and its stack trace. The error logger is created by the `errorLogger()` method of the `expressWinston` module:

```jsx
// middlewares/logger.js

const winston = require('winston');
const expressWinston = require('express-winston');

const requestLogger = expressWinston.logger({
  transports: [
    new winston.transports.File({ filename: 'request.log' }),
  ],
  format: winston.format.json(),
});

// error logger
const errorLogger = expressWinston.errorLogger({
  transports: [
    new winston.transports.File({ filename: 'error.log' }),
  ],
  format: winston.format.json(),
});
```

After creating loggers, you need to export them:

```jsx
module.exports = {
  requestLogger,
  errorLogger,
};
```

And then import them into `app.js`:

```jsx
const { requestLogger, errorLogger } = require('./middlewares/logger');
```

It's time to enable the loggers as middleware. The request logger must be enabled before all route handlers:

```jsx
app.use(requestLogger); // enabling the request logger

// followed by all route handlers
app.post('/signup', createUser);
app.post('/signin', login);
app.use('/users', usersRouter);
app.post('/posts', postsRouter);
```

The error logger needs to be enabled after the route handlers and before the error handlers:

```jsx
app.use(requestLogger);

app.post('/signup', createUser);
app.post('/signin', login);
app.use('/users', usersRouter);
app.post('/posts', postsRouter);

app.use(errorLogger); // enabling the error logger

app.use(errors()); // celebrate error handler

// centralized error handler
app.use((err, req, res, next) => {
  // ...
});
```

Loggers are enabled. Now, when making a request to the server, the `request.log` file will be created, and some of the data from the request and response will be written to it in JSON format. If an error occurs on the server, the `error.log` file will be created. Part of the request and response data and information about the error will be written there. This will only include part of the data since the request body won't be written to the log. It works this way by default because the body may contain sensitive information such as the user's password, which isn't safe to keep in plain text. It's possible to change this default behavior. If you want to know more, you can follow the links at the end of the lesson and read through the documentation.

## gitignore

The last point: don't forget to add the log files to `.gitignore` so they don't get added to the repository. You can do this by adding the following line to the `.gitignore` file:

```jsx
*.log 
```


Now all log files are invisible to git.

