# Promises

```js
// create a promise
const newPromise = new Promise(function(resolve, reject) {
  // determine randomly whether the request has been processed or not
    const rand = Math.random() > 0.5 ? true : false;

    if (rand) {
        resolve("Request processed successfully");
    } else {
        reject("Request rejected");
    }
});

newPromise
  .then(function (value) { // executed if the promise has been resolved

    /* the value parameter stores the value passed to 
    the resolve() method when creating the promise, i.e. 
    the string "Request processed successfully" */

      console.log(value);
  })
  .catch(function (value) { // executed if the promise has been rejected

    /* in this case, the value parameter stores the value
    passed to the reject() method, i.e. 
    the string "Request rejected" */

      console.log(value + ". We are sorry for the inconvenience.");
  })
  .finally(function () { // executed in either case
      console.log("We promise we got your request");
  });
```

```js
const newPromise = new Promise(function (resolve, reject) {
    resolve("One Mississippi"); // immediately get the resolved promise
});

function firstAction(value) {
  /* the value parameter will receive what we passed 
  to the resolve() method when creating the promise, 
  i.e. the string "One Mississippi" */

    return `${value}, two Mississippi`;
}

function secondAction(value) {
  /* the value will be equal to the value returned 
  by the previous then() method, i.e. the string "One Mississippi, two Mississippi" */

    return `${value}, three Mississippi`;
}

function thirdAction(value) {
    console.log(value);
}

newPromise.then(firstAction).then(secondAction).then(thirdAction);

/* we'll see the following in the console: "One Mississippi, two Mississippi, three Mississippi" */
```

```js
function change() {
        return new Promise(function(resolve, reject) {
  
            // Setting 2000 ms time
            setTimeout(resolve, 2000);
        }).then(function() {
            console.log("Wrapped setTimeout after 2000ms");
        });
    }
```