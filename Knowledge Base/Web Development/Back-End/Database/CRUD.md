# CRUD

Model which allows us to interact with our collection of documents.

-   Create: `create()`
-   Read: `findById()`, `findOne()`, `find()`
-   Update: `findByIdAndUpdate()`, `findOneAndUpdate()`, `updateOne()`, `updateMany()`
-   Delete: `findByIdAndRemove()`, `findOneAndRemove()`, `delete()`, `deleteMany()`


## Creating Documents

Documents can be created via the `create()` method. It accepts objects with data as input and records them to the database

```jsx
// routes/users.js

/*
    code for creating routers, etc.
*/

// import the model
const User = require('../models/user');

router.post('/', (req, res) => {
  const { name, about } = req.body; // get the name and description of the user

  User.create({ name, about }); // create a document based on the input data 
});
```

The `create()` method is like a promise in that you can add `then()` and `catch()` handlers to it. This is usually done to return the data or an error to the user:

```jsx
// routes/users.js

/*
    code for creating routers, etc.
*/

const User = require('../models/user');

router.post('/', (req, res) => {
  const { name, about } = req.body;

  User.create({ name, about })
    // returns the recorded data
    .then(user => res.send({ data: user }))
    // data not recorded, prompting an error
    .catch(err => res.status(500).send({ message: 'Error' }));
});
```

## Reading Documents
-   **Searching for a specific document:** The `findById()` method uses the identifier to do this, i.e. the `_id` property that is assigned to each document in MongoDB. To find a specific document, pass the `findById()` identifier to the method in the form of a string:
```jsx
// routes/users.js

/*
    code for creating routers, etc.
*/

const User = require('../models/user');

router.get('/:id', (req, res) => {
    User.findById(req.params.id)
        .then(user => res.send({ data: user }))
        .catch(err => res.status(500).send({ message: 'Error' }));
});
```

-   **Searching for one document by specific parameters:** The `findOne()` method returns the first document that matches the request parameters:
```jsx
// find the first match with a field that equals "Elise Taylor"
User.findOne({ name: 'Elise Taylor' });
```

-   **Searching all documents by specific parameters:** The `find()` method works the same way as the `findOne()` method, except that it returns all documents that match the request parameters:
```jsx
// find all 30-year-old users
User.find({ age: 30 });

// find all users
User.find({});
```

## Updating Documents
When we update documents, first we find an entry, then we change its properties.
- You can use the `findByIdAndUpdate()` method to update a specific document. It accepts an identifier in string form as the first argument. The second argument is an object with the properties that need to be updated:
```jsx
  // routes/users.js

  // ...

  const User = require('../models/user');

  router.patch('/:id', (req, res) => {
    // updating the name of the user found by _id
    User.findByIdAndUpdate(req.params.id, { name: 'Henry George' })
      .then(user => res.send({ data: user }))
      .catch(err => res.status(500).send({ message: 'Error' }));
  });
  
```

- You can also find the first match for the request and update it. This is done using the `findOneAndUpdate()` method, which accepts two objects as arguments. The first argument is the object we're looking for, and the second argument is the updated object:
```jsx
  // find the first match with the name field that equals to "Sam Taylor" and replace is with "Henry George"
  User.findOneAndUpdate({ name: 'Sam Taylor' }, { name: 'Henry George' }));
```

- You can also turn every 'Sam Taylor' into 'Henry George' using the `updateMany()` method:
```jsx
  // find all matches with the name field that equals to "Sam Taylor" and replace it with "Henry George"
  User.updateMany({ name: 'Sam Taylor' }, { name: 'Henry George' });
```

These update methods come with a caveat. By default, the parameter that the handler receives as input is the original document before the update.
Fortunately, there's a way to change this. All these methods can take a third argument, which is an options object.
Thanks to the options object, we can transfer an updated record to the `then()` handler. We can also set up validation or create a document if it was not found:
```jsx
User.findByIdAndUpdate(
    req.params.id,
    { name: 'Henry George' },
    // pass the options object:
    {
        new: true, // the then handler receives the updated entry as input
        runValidators: true, // the data will be validated before the update 
        upsert: true // if the user entry wasn't found, it will be created
    }
)
  .then(user => res.send({ data: user }))
  .catch(user => res.send({ 'Data validation failed or another error occured.' }));
```

## Deleting Documents
- **Deleting a specific document:**
```jsx
// routes/users.js

// ...

const User = require('../models/user');

router.delete('/:id', (req, res) => {
    User.findByIdAndRemove(req.params.id)
        .then(user => res.send({ data: user }))
        .catch(err => res.status(500).send({ message: 'Error' }));
});
```

-   **Deleting the first match:** Use `findOneAndRemove()`:
```jsx
// delete a user with a specific name
User.findOneAndRemove({ name: 'Sam Taylor' });
```

-   **Delete all matches:** To do this, call `deleteMany()`:
 ```jsx
// delete all 30-year-old users
User.deleteMany({ age: 30 });
```

We've listed the most popular methods in this lesson, but there are many others available for working with mongoose models. You can find them all in this guide:

[https://mongoosejs.com/docs/api/model.html](https://mongoosejs.com/docs/api/model.html)
