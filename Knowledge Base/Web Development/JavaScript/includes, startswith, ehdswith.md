The `indexOf()` method can take any character as an argument and will return the index, or location, of that character within the string on which it's called

```js
"Practicum by Yandex".indexOf("P"); // 0
```

Thanks to the ES6 specification, we have the purpose-built `includes()` method, which provides a much tidier and efficient way of checking the contents of a string

```js
"Harry Potter and the Prisoner of Azkaban".includes("Harry Potter"); // true
"Teamwork".includes("I"); // false
```

The `startsWith()` and `endsWith()` methods work according to the same principle as `indexOf()`, except that they're more specific.

The `startsWith()` method checks whether the string passed through it matched the beginning of the string on which the method is called. If it's a match, the method returns `true`, if not, it'll return `false`

```js
"Vendetta".startsWith("V"); // true
"The perfect date".startsWith("Dinner and a movie"); // false
```

The `endsWith()` method works exactly the same way as `startsWith()`, except that it checks the end of the string for the specified characters:

```js
const theRealEnd = "This is not the end";

theRealEnd.endsWith("end"); // true
```
