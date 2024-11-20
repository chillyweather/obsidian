# Explicit Type Conversion

## Convert to String

```js
const numberToString = String(2); // "2"
const nanToString = String(NaN); // "NaN"
const undefinedToString = String(undefined); // "undefined"
const nullToString = String(null); // "null"
const booleanToString = String(true); // "true"
```

## Convert to Number

```js
const stringToNumber = Number("2"); // 2
const nullToNumber = Number(null); // 0
```

## Convert to Boolean

```js
Boolean(2) // true
Boolean(0) // false
Boolean("") // false
Boolean("any string that isn't empty"); 
// true
```

```js
Boolean("any string that isn't empty"); 
// true
Boolean(""); // false
Boolean(1); // true
Boolean(0); // false
Boolean(NaN); // false
Boolean(null); //false
Boolean(undefined); // false
Boolean({}); // true
Boolean([]); //true
```

## Double negation converts a value to the Boolean type:

```js
!!true; // true
!!"This is not an empty string"; // true
!!""; // false
!!1; // true
!!0; // false
```