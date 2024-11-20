```js
/* Create an array to record a gambler's wins and losses. */ 
const winsAndLosses = [190, 117, -381, -394, -36, 137, -473, 372, -383]; 
/* Let's calculate how much money the gambler will have left at the end of the night if they started out with $1,000. */ 
const total = winsAndLosses.reduce(function (previousValue, item) { return previousValue + item; }, 1000); 
// The initial value you want to set is passed through the reduce() method as the second argument. 
console.log(total); 
// 149. What did you expect? That's gambling for you.
```

```js
const order = ["apple", "banana", "orange", "banana", "apple", "banana"];

const result = order.reduce(function (prevVal, item) {
    if (!prevVal[item]) {
        // if an object doesn't have a key yet, it means it wasn't repeated before
        prevVal[item] = 1;
    } else {
        // increase the number of repetitions by 1
        prevVal[item] += 1;
    }

    // and return the changed object
    return prevVal;
}, {}); // The initial value is an empty object.

console.log(result); // { apple: 2, banana: 3, orange: 1 }
```