## Extracting Part of a String with the `slice()` Method
The `slice()` method returns a section of a string and takes two arguments. The first argument specifies at which index the slicing should begin, while the second argument tells it where to stop. The index of the first argument is included in the slice, while the second one isn't

```js
"Believe".slice(2, 5); // "lie"
```