# Middleware

Middleware functions execute during the lifecycle of a server request. These functions allow us to write our request processing code inside a separate module, which in turn allows for shorter code in the router itself.
Additionally, middleware is a great place to move code that will be repeatedly executed.

```jsx
// adding a middleware function globally
app.use(bodyParser.urlencoded({ extended: true }));

// adding a middleware to specific paths
app.use('/users/:id', checkRequest);
router.get('/users/:id', doesUserExist);
```

Middleware functions are perfect for organizing our code, so that it's easy to maintain. Here's some code that checks whether the user exists or not and returns a user object if the user is found
```jsx
router.get('/users/:id', doesUserExist);
router.get('/users/:id', sendUser);
```
If we want to add some new functionality later, we can just add one more middleware without touching the rest of the code:
```jsx
router.get('/users/:id', doesUserExist);

// new middleware function
router.get('/users/:id', doesUserHasPermission);

router.get('/users/:id', sendUser);
```


### body parser
```jsx
const postForm = (req, res) => {
  const { body } = req;
  // here, we can simply refer to the body object
};
```
```bash
npm i body-parser
```

```jsx
// app.js

const bodyParser = require('body-parser');
```
```jsx
app.use(bodyParser.json()); // parses data in JSON format
app.use(bodyParser.urlencoded({ extended: true })); // parses webpages inside POST requests
```


