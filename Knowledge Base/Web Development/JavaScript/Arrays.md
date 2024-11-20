# Arrays

### splice
```js
var arr = [];
arr[0] = "Jani";
arr[1] = "Hege";
arr[2] = "Stale";
arr[3] = "Kai Jim";
arr[4] = "Borge";

console.log(arr.join()); // Jani,Hege,Stale,Kai Jim,Borge
arr.splice(2, 0, "Lene");
console.log(arr.join()); // Jani,Hege,Lene,Stale,Kai Jim,Borge
```

## Iterating Through an Array with the `forEach()` Method

The `forEach()` method executes a function for each element in an array. The function that you want to call for each element is passed through the method as an argument, like so:
```js
const how = ["harder", "better", "faster", "stronger"];

how.forEach(function (item) {
    console.log(item + ".");
}); 
/* pay close attention to the use of 
parentheses here - notice that the whole 
function, including the body, 
is contained within the parentheses 
of the forEach() method*/

/*
    harder.
    better.
    faster.
    stronger.  
*/
```

### map()
```js
const characters = [

 'Luke Skywalker',

 'Obi-Wan',

 'Chewbacca',

 'Anakin Skywalker',

 'Han Solo',

 'Palpatine',

];

  

const newCharacters = characters.map((character) => {

 if (character === 'Anakin Skywalker') {

 // eslint-disable-next-line no-param-reassign

 character = 'Darth Vader';

 }

 return character;

});

  

console.log(newCharacters);
```

## Callback Functions and their Arguments

```js
const kings = [
    "Louis I the Fair",
    "Louis II the Stammerer",
    "Louis III",
    "Louis IV Transmarinus",
    "Louis V the Do-Nothing"
];

const kingsIndexed = kings.map(function (item, index, array) {
    const currentIndex = `(${(index + 1)} of ${array.length})`;
    return `${item} ${currentIndex}`;
});

console.log(kingsIndexed);

/*
[
    "Louis I the Fair (1 of 5)",
    "Louis II the Stammerer (2 of 5)",
    "Louis III (3 of 5)",
    "Louis IV Transmarinus (4 of 5)",
    "Louis V the Do-Nothing (5 of 5)"
]
*/
```

## Filter

```js
const a = [1, 9, 2, 2, 3, 4, 1, 7, 8, 0, 9, 0, 1, 5, 3];

const b = a.filter(function (item, index, array) {
    return array.lastIndexOf(item) === index; // this will return the unique elements
});

console.log(a); // [1, 9, 2, 2, 3, 4, 1, 7, 8, 0, 9, 0, 1, 5, 3]
console.log(b); // [2, 4, 7, 8, 9, 0, 1, 5, 3]
```

```js
const movies = [

 'Titanic (1997)',

 'Black Panther (2018)',

 'Isle of Dogs (2018)',

 'The Hateful Eight (2015)',

];

  

const moviesFiltered = movies.filter((item) => item.includes('2018'));

  

console.log(moviesFiltered);
```

