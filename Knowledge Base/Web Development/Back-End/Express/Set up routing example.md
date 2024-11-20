# Set up routing example

```jsx
// index.js

// here, is the entry point setup
const express = require('express');

const { PORT = 3000 } = process.env;
const app = express();

// here we have data
const users = [
  { name: 'Jane', age: 22 },
  { name: 'Hugo', age: 30 },
  { name: 'Juliana', age: 48 },
  { name: 'Vincent', age: 51 }
];

// here's where we'll do our routing
app.get('/users/:id', (req, res) => {
  if (!users[req.params.id]) {
    res.send(`This user doesn't exist`);

    // it's important we don't forget to exit from the function
    return;
  }

  const { name, age } = users[req.params.id];
  
  res.send(`User ${name}, ${age} years old`);
});

app.listen(PORT, () => {
    console.log(`App listening on port ${PORT}`);
});
```

## Let's split it!

First things first, let's move our data into an individual file called `db.js`:
```jsx
// db.js

module.exports = {
  users: [
    { name: 'Jane', age: 22 },
    { name: 'Hugo', age: 30 },
    { name: 'Juliana', age: 48 },
    { name: 'Vincent', age: 51 }
  ]
};
```

Now, let's set up routing. Our routing logic should also be moved into an individual file.

In this case, we'll need to write some more code. The response logic is described in the `get()` method's handler functions. In the code above, we were calling `get()` as a method of `app`. But there's no `app` variable in our new routing file. Further, since we can have only one app, we can't recreate this variable here.

To take care of this, Express provides us with the `Router()` method, which creates a new router object. Once we create this object, we can attach our handlers to it, like so:

```jsx
// routes.js

const router = require('express').Router(); // creating a router
const { users } = require('./db.js'); // since this data is necessary for routing,
                                      // we need to import it

router.get('/users/:id', (req, res) => { 
  if (!users[req.params.id]) {
    res.send(`This user doesn't exist`);
    return;
  }

  const { name, age } = users[req.params.id];
  
  res.send(`User ${name}, ${age} years old`);
});

module.exports = router; // exporting the router
```

Finally, let's set up our entry point inside the `index.js` file.

To be able to use our routing, we should import the `route` file we just created into the `index.js` file. To execute the router, we need to call the `use()` method of the app. This method takes two parameters:

-   The first part of the URL. The router will only start if a request begins with this line.
-   The router itself, in our case, we've saved it as a const called `router`.

```jsx
// index.js 

const express = require('express');
const router = require('./routes.js');
const api = require('./api.js');
const backoffice = require('./backoffice.js');

const { PORT = 3000 } = process.env;
const app = express();

// different routers for different requests
// looks awesome!

app.use('/', router);
app.use('/api', api);
app.use('/admin', backoffice);

app.listen(PORT, () => {
    console.log(`App listening on port ${PORT}`);
});
```