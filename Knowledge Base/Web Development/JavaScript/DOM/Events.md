# Events and Reacting to User Actions

### Event Listener

We can use the `addEventListener()` method to detect and react to any event.
```js
element.addEventListener(eventName, handler);
```

`element` is the variable that's going to "listen" out for an event.

`eventName` is the name of the event that will trigger a reaction. We pass through the argument in the form of a string, such as `"click"`, `"scroll"`, or `"mouseover"`.

`handler` is the function that will run when the event is triggered.

```js
let element = document.querySelector(".my-element");

function showClick() {
    console.log("You have clicked on the element");
}

element.addEventListener("click", showClick);
```

There is another way to code the handler function. It can be useful when you're not planning to call this function anywhere else in your code. In other words, you can use this approach if you're only going to run the function once:

```js
let element = document.querySelector(".my-element");

element.addEventListener("click", function () {
    console.log("You have clicked on the element");
});
```