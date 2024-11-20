

# Regular expressions in JavaScript

```js
let re1 = new RegExp("abc");
let re2 = /abc/;
```

## Flags
/g - global
/i - ignore character case
/m - for multiple line searches
/s - This flag enables "dotall" mode, which allows `.` to match newline characters: `\n`.
/u - search by unicode code
```jsx
const str = '& is an ampersand. Its Unicode value is 26';
const regex = /\u{26}/; // u flag is not set here
const regexUnicode = /\u{26}/u; // but here it is set

str.match(regex); // null
str.match(regexUnicode); // ['&']
```
/y -  adds the sticky property. It allows us to search for a string at a particular place in a text.
*First, as with the above flags, we set the `y` flag after the last slash when composing a regular expression. After this is in place, we add the `lastIndex` property to the regular expression.
For the value of this property, we need to set a number that will determine where the search should begin in our string.*
```jsx
const fuelUp = 'fuel up and go';
const regex = /go/y;

regex.lastIndex = 0; 
fuelUp.match(regex); 
// null. The first word is 'fuel', not 'go'

regex.lastIndex = 12;
fuelUp.match(regex); // [ 'go' ]

/* interestingly enough, different browsers display the info returned by string methods differently: some show the index only, while others show the original string and capturing groups */
```

## Methods
#### RegEx Methods:
- /regex/.test(string) ('remembers' previous search)
- /regex/.exec(string) - more or less the same as .match()
However when the `g` flag is set, the `RegExp.exec()` method behaves differently. It will return the first match and it will also add the matching character's index to the `lastIndex` property of the regular expression.
```jsx
const str = `I write, erase, rewrite
Erase again, and then
A poppy blooms.`;
let regex = /.+/g;

regex.exec(str); // ['I write, erase, rewrite']
regex.exec(str); // ['Erase again, and then']
regex.exec(str); // ['A poppy blooms.']
regex.exec(str); // null
```

#### String Methods:
- string.match(regex)
- string.replace(regex)
![[Pasted image 20211202211905.png]]
```jsx
const strObj = 'The space goes after the comma ,not before the comma.';
const regex = /\s,/g;

strObj.replace(regex, ', '); // 'The space goes after the comma, not before the comma.'
```
- string.search(regex)
```jsx
const regex = /\d{3,}/i;
const string = '12! equals 479001600';

string.search(regex); // 11
```
- string.split(regex)
```jsx
const regex = /\n/im;
const text = `I made myself a snowball
As perfect as could be.
I thought I'd keep it as a pet
And let it sleep with me.
I made it some pajamas
And a pillow for its head.
Then last night it ran away,
But first it wet the bed.`

const newText = text.split(regex);
console.log(newText); 

/* [
  'I made myself a snowball',
  'As perfect as could be.',
  'I thought I'd keep it as a pet',
  'And let it sleep with me.',
  'I made it some pajamas',
  'And a pillow for its head.',
  'Then last night it ran away,',
  'But first it wet the bed.'
] */
```
- 

### Test
```js
console.log(/abc/.test("abcde"));
// → true
console.log(/abc/.test("abxde"));
// → false
```

```js
console.log(/[0123456789]/.test("in 1992"));
// → true
console.log(/[0-9]/.test("in 1992"));
// → true
```

### Match
If you pass a regular expression without the `g` flag to the `String.match()` method, some additional properties will be defined on the array.
```jsx
const userList = 'Emma, Sean, Kate, Owen, Jane, Bartholomew, Luke';
const regex = /Bartholomew/;

userList.match(regex);  // [ 'Bartholomew' ]
//['Bartholomew', index: 30, input: 'Emma, Sean, Kate, Owen, Jane, Bartholomew, Luke', groups: undefined]
```

The `String.match()` method takes one argument, which should be a regular expression. If `String.match()` finds the string, it will then return an array with what it has found.