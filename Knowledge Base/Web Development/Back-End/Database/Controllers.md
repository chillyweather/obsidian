# Controllers

A **controller** is a collection of **request handler functions** responsible for interacting with a particular model (in this case, the User model). These handler functions can read, create, update, and delete documents, and send a response back to the client.

```jsx
// controllers/users.js
// this file is the user controller

const User = require('../models/user');

// the getUser request handler
module.exports.getUser = (req, res) => {
  User.findById(req.params.id)
    .then(user => res.send({ data: user }))
    .catch(err => res.status(500).send({ message: 'Error' }));
};

// the createUser request handler
module.exports.createUser = (req, res) => {
  const { name, about } = req.body;

  User.create({ name, about })
    .then(user => res.send({ data: user }))
    .catch(err => res.status(500).send({ message: 'Error' }));
};
```

```jsx
// routes/users.js
// this is the routes file
    
const { getUser, createUser } = require('../controllers/users');

// route definitions
router.get('/:id', getUser)
router.post('/', createUser);
```