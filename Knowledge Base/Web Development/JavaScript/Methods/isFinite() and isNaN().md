The `Number.isFinite()` method checks whether the value is finite. It returns finite values as `true`, and infinite ones as `false`.

```js
Number.isFinite(Infinity); // false
Number.isFinite(-Infinity); // false
Number.isFinite(1703); // true
```

`NaN` has a funny characteristic in that it isn't identical to anything, even itself:

```js
console.log(NaN === NaN); // false 
```

Because of this, it's impossible to check directly whether the result of a calculation is identical to `NaN`. To get around this problem, we have the `Number.isNaN()` method, which will return `true` if the result of a calculation returns `NaN`, and `false` if not.

```js
Number.isNaN(NaN); // true
console.log(Number.isNaN(0 / 0)); // true
```