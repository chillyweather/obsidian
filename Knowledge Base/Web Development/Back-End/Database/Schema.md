# Schema

A schema is a set of rules for your data. It sets the number of fields a record has, the length of each field value, which characters are allowed in it, etc.

Schemas impose restrictions on the data recorded in the database, which is convenient for some tasks but unnecessary for others. With modern NoSQL databases, you can use schemas when necessary.

Let's have a go at setting up a schema for a user via Mongoose. We do this using the `mongoose.Schema()` constructor to create a new instance of the schema:
```jsx
// models/user.js
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  name: { // every user has a name field, the requirements for which are described below:
    type: String, // the name is a string
    required: true, // every user has a name, so it's a required field
    minlength: 2, // the minimum length of the name is 2 characters
    maxlength: 30, // the maximum length is 30 characters
  },
  pronouns: {
    type: String, // the pronouns are a string
    enum: ['they/them', 'she/her', 'he/him', 'other pronouns'] // every user can choose their pronouns
  },
  about: String, // type: String
});
```

Additional validation
```jsx
// models/user.js
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  name: { // every user has a name field, the requirements for which are described below:
    type: String, // the name type is a string
    required: true, // every user has a name, so it's a required field
    minlength: 2, // the minimum length of the name is 2 characters
    maxlength: 30, // the maximum length is 30 characters
  },
  pronouns: {
    type: String, // the pronouns are a string
    enum: ['they/them', 'she/her', 'he/him', 'other pronouns'] // every user can choose their pronouns
  },
    age: { // every user has an age field
        type: Number, // the age type is a number
        required: true, // the user has to specify their age
        validate: { // describe the validate feature
            validator(v) { // validator is a data validation feature. v is the age value
                return v >= 18; // if the age is less than 18, it will return false
            },
            message: 'Sorry. You have to be at least 18 years old', // when the validator returns false, this message will be displayed
        }
    },
  about: String, // type: String
});
```

### Subdocuments

If you use another schema as a property of your schema, you'll have to use the `Schema` method twice:

-   the first call is needed to create a schema that will describe the property's structure
-   the second call will pass the schema to the property. It should have the following structure:

```jsx
// models/user.js

const mongoose = require('mongoose');

// create a schema for the "Pet" document 
const petSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
    minlength: 2,
    maxlength: 30,
  },
  age: Number
});
// once the schema is ready, pass it to the property which should correspond to this template:
const userSchema = new mongoose.Schema({
  ...
  pet: petSchema // describe the pet property with this schema
});
```

### Array Properties

Arrays are used to store multiple data items of the same type. This is why the schema of an array is a schema for a single array element inside square brackets:

```jsx
// models/user.js

const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  ...
  hobbies: [{ // describe the schema for a single element and put it in square brackets
    type: String,
    minlength: 2,
    maxlength: 30,
  }]
});
```

This schema defines the hobbies property. It must contain an array of strings, each one from 2 to 30 characters in length.

### Creating a Model Based on a Schema
A model is basically a wrapper around the schema. It enables us to read, add, delete, and update documents. The `mongoose.model()` method is used to create models in Mongoose:

```jsx
// models/user.js

const mongoose = require('mongoose');
// Describe the schema:
const userSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
    minlength: 2,
    maxlength: 30,
  },
  about: String,
});

// create the model and export it
module.exports = mongoose.model('user', userSchema);
```

We passed two arguments to the `mongoose.model` method: the name of the model and the schema which will describe future documents.