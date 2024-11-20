# Functions
```js
function functionName() {
    // body
}
```

```js
function consoleKitten() {
    let a = '  Λ _ Λ';
    let b = ' (=චᆽච=)==∫';
    let c = '  ˉ ˉ ˉ ˉ';

    console.log(a); 
    console.log(b); 
    console.log(c);
}
```

### Parameters
```js
function keepScore(ours, theirs) {
    // Let's check whether our team has scored more goals:
    if (ours > theirs) {
        console.log("We won! 😃 The score was " + ours + "-" + theirs);

        // If we didn't score more goals than they did,
        // maybe we scored the same amount? Check it:
    } else if (ours === theirs) {
        console.log("It's a draw. 😐 The score was " + ours + "-" + theirs);

        // If neither of the previous two conditions were met,
        // it must mean that we scored fewer goals :(
    } else {
        console.log("We lost... 😢 The score was " + ours + "-" + theirs);
    }
}
```

```js
keepScore(10, 8);
// the keepScore function will use 10 for the ours variable,
// and 8 for theirs. Then, it will perform all the checks and print the result:
// "We won! 😃 The score was 10-8"
```