# Objects

Objects are made up of key-value pairs. Values are the data stored in an object. A value can be a string, a number, a Boolean, an array, another object, or a function.

Keys are unique names given to the corresponding values. Keys serve the same purpose as variable names. You can access a value by its key.

```js
let myObject = {
    stringKey: 'value',
    numberKey: 4,
    booleanKey: true,
    methodKey: function consoleKitten() {
        console.log('kitten!');
    }
};
```

There are two types of key-value pairs: object properties and object methods.

If a value is a function, it's called a method.

If a value is not a function, i.e. it's a string, number, Boolean, array or object, it's called a property.

```js
let myObject = {
    stringKey: 'value', // property
    numberKey: 4, // also a property
    booleanKey: true, // yet another property
    methodKey: function consoleKitten() { // and here we have a method
        console.log('kitten!');
    }
};
```

After you create an object, you can fill it up with properties and methods. You can then use them by calling the methods and accessing the properties.
```js
myObject.stringKey;
```

```js
myObject["numberKey"];
```