# Misc notes

## console methods

**console.count**console.count outputs the number of times it's been called, if you don't put an argument inside `count()` it will show a default label.
```js
function myName(name) {
  console.count();
  console.log(name); 
}

myName('Sharon'); 
myName('Mike');
myName('Crystal'); 

/* This will output how many times we called the function to the console
default: 1
Sharon
default: 2
Mike
default: 3
Crystal
*/
```


But you can also use it to count how many times the same argument was called for:
```js
function myName(name) {
  console.count(name);
}

myName('Sharon');
myName('Sharon'); 
myName('Mike');
myName('Crystal');
myName('Sharon');

/* This will output how many times we called the function with the same name

Sharon: 1
Sharon: 2
Mike: 1
Crystal: 1
Sharon: 3

*/
```


**console.warn**This method outputs a colorful warning message to the console, imagine you're making a function and you want to warn the user if he/she are doing something wrong.  
Copy the code below to your console to see how it looks:  
```js
function myName(name) {
  if(name){
    console.log(name);
  } else {
      console.warn("You didn't put any name in, genius!");
    }
}
myName('Sharon'); // Will print "Sharon"
myName(); // Will print "You didn't put any name in, genius!"
```



**console.table**This one is can be used when you're working with arrays or objects, and it displays the data in a nice table that is easier to read.Take this array for example:
```js
const randomWords = ["town", "studio", "sector", "steak", "worker", "length", "confusion", "platform", "player"];
console.table(randomWords);
```


Watch the output in the image below or copy the code and try it yourself, this could be very useful when you're working with huge or complex nested arrays.console.table also works with objects

```js
const dude = {
    picture: "[http://placehold.it/32x32](http://placehold.it/32x32)",
    age: 34,
    eyeColor: "blue",
    name: "Curry Miles",
    gender: "male",
    company: "Google",
    email: "currymiles@google.com",
    phone: "+1 (936) 409-2919"
}
console.table(dude);
```



So as you can see, console is much more than just console.log(), it has other methods and they can be very handy. Enjoy!