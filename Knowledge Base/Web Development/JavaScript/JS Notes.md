The JavaScript engine automatically converts different data types to numbers before using comparison operators:

```js
null >= 1; // false
"451" < 452; // true
```

you can add a `+` sign right before a non-numerical value without any spaces, and that value will be converted to a number. When you use the `+` in this way, it's called the unary plus operator. For example, `+"33"` returns the number `33`, and `+"-77"` returns the number `-77`. The addition operator (or binary plus) and the unary plus operator do not interfere with one another:

```js
console.log(67 + +"33"); // 100
```

## onversion to String

Implicit conversion to a string type occurs when you add a different data type to a string:

```js
1 + ""; // "1"
undefined + ""; // "undefined"
```