# Building Relationships in NoSQL

### Building a Relationship Between Two Schemas
Two entities:

1. User schema:
```jsx
const userSchema = new mongoose.Schema({
  name: { // the user only has a name
    type: String,
    minlength: 2,
    maxlength: 20,
    required: true,
  },
});

module.exports = mongoose.model('user', userSchema);
```

2. Ad schema
```jsx
const adSchema = new mongoose.Schema({
  title: {
    type: String,
    minlength: 2,
    maxlength: 20,
    required: true,
  },
  text: {
    type: String,
    minlength: 2,
    required: true,
  },
});

module.exports = mongoose.model('ad', adSchema);
```

Now we'll need a way to assign an author to each advertisement. Let's make another field titled 'creator'. This field will store a link to the ad author.

An identifier is the best way to set up a relationship between documents. MongoDB automatically creates the `_id` field, which provides a unique identifier for each document and allows documents to be linked to one another.

To do this with schemas, the `type` property should be set to `mongoose.Schema.Types.ObjectId`. It should also have a `ref` property, which will contain the name of the model we are linking:
```jsx
const adSchema = new mongoose.Schema({
  title: {
    type: String,
    minlength: 2,
    maxlength: 20,
    required: true,
  },
  text: {
    type: String,
    minlength: 2,
    required: true,
  },
  // add the creator field
  creator: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'user',
    required: true
  },
});
```

### Including the `_id` Field During Document Creation
Now we need to make sure this identifier is recorded in the `creator` field whenever a new ad is created:
```jsx
// controllers/ads.js

const Ad = require('../models/ad');

module.exports.createAd = (req, res) => {
  const { title, text, creatorId } = req.body;

  Ad.create({ title, text, creator: creatorId })
    .then(ad => res.send({ data: ad }));
};
```

### Acquiring Complete Information via the `populate()` Method

To get all information about the author of the ad, you'll need to use the `populate()` method by passing it the field name:

```jsx
// controllers/ads.js

const Ad = require('../models/ad');

module.exports.getAds = (req, res) => {
  Ad.find({})
    .populate('creator')
    .then(ad => res.send({ data: ad }));
};
```

In order to send a response containing the multiple fields resulting from the relationships, we need to pass an array to the `populate()` method:

```jsx
// controllers/ads.js

const Ad = require('../models/ad');

module.exports.getAds = (req, res) => {
  Ad.find({})
    .populate(['creator', 'followers'])
    .then(ad => res.send({ data: ad }));
};
```

[https://mongoosejs.com/docs/populate.html](https://mongoosejs.com/docs/populate.html)