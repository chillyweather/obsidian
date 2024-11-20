# Node.js modules

We can only use lowercase letters when naming a module. Node.js has its own cache algorithm that treats uppercase and lowercase letters differently. Because of this, using uppercase letters in your module's name can interfere with the caching process and break your code.

```jsx
const http = require('http');
```

```jsx
const md5 = require('md5');
```

```jsx
const utils = require('../utils'); 
const helpers = require('../../helpers');
```

## Exporting modules

```jsx
// utils.js

module.exports.someFunction = () => {
  console.log('I was exported!');
};

module.exports.someValue = 42;
```

```jsx
// utils.js

const someFunction = () => {
  console.log('I was exported!');
};

const someValue = 42;

module.exports = {
  someFunction,
  someValue
};
```

When you import a module using the `require()` method, what you're actually doing is importing the `module.exports` object from the respective file. Once you've done that, you can access that object's properties

```jsx
// index.js

const utils = require('./utils');

const someFunction = utils.someFunction;
const someValue = utils.someValue;
```

```jsx
// index.js

const { someFunction, someValue } = require('./utils');
```