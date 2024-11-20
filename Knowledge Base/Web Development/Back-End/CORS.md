# CORS


### Allowing Request by Origin
```jsx
Access-Control-Allow-Origin: https://my-site.com
```

### Allowing Request Methods
```jsx
Access-Control-Allow-Methods: GET,HEAD,PUT,PATCH,POST,DELETE
Access-Control-Allow-Headers: Origin, X-Requested-With, Content-Type, Accept
```

### Setting Headers in Express
To allow cross-domain requests, we'll add a middleware function to our application:
1. cross-domain requests
```jsx
app.use(function(req, res, next) {
  res.header('Access-Control-Allow-Origin', 'https://around.nomoreparties.co');
  next();
});
```
2. allowed headers and methods
```jsx
app.use(function(req, res, next) {
  res.header('Access-Control-Allow-Origin', 'https://around.nomoreparties.co');
  res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept');
  res.header('Access-Control-Allow-Methods', 'GET,HEAD,PUT,PATCH,POST,DELETE');
  res.header("Access-Control-Allow-Credentials", true);

  next();
});
```
3. handle OPTIONS request
```jsx
app.use(function(req, res, next) {
  res.header('Access-Control-Allow-Origin', 'https://around.nomoreparties.co');
  res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept');
  res.header('Access-Control-Allow-Methods', 'GET,HEAD,PUT,PATCH,POST,DELETE');

    // Respond to preflight OPTIONS requests
    if (req.method === 'OPTIONS') {
        res.send()
    } else {
      next();
    }
});
```

### Allowing Requests from Multiple Resources

```jsx
// an array of allowed domains
const allowedOrigins = [
  'https://around.nomoreparties.co',
  'http://around.nomoreparties.co',
  'http://localhost:3000'
];

app.use(function(req, res, next) {
  const { origin } = req.headers; // assign the corresponding header to the origin variable

  res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept');
  res.header('Access-Control-Allow-Methods', 'GET,HEAD,PUT,PATCH,POST,DELETE');

  if (allowedOrigins.includes(origin)) { // check that the origin value is among the allowed domains
    res.header('Access-Control-Allow-Origin', origin);
  }

    // Respond to preflight OPTIONS requests
    if (req.method === 'OPTIONS') {
        res.send()
    } else {
      next();
    }
});
```

## The `cors` Package
For convenience, we can also use the npm `cors` package to set the headers for you. The configuration is simple:
```jsx
const cors = require("cors");

// Place this before any routes
const allowedOrigins = [
  "https://around.nomoreparties.co",
  "http://around.nomoreparties.co",
  "http://localhost:3000", // Use the port your frontend is served on
];
app.use(cors({ origin: allowedOrigins }));
```

Using this at the top level, `app.use()` also handles adding the preflight OPTIONS endpoints for us automatically.

For security, make sure not to simply use `app.use(cors())`, as this enables requests from all domains, not just your own, which can be a [major security risk](https://portswigger.net/research/exploiting-cors-misconfigurations-for-bitcoins-and-bounties) for your users.