# DOM_CSS Classes

Every DOM element has the `className` property, which allows us to check or change the values of the `class` attribute:

```html
<div class="princess">Elizabeth</div>
```

```js
// selecting the element with the class name "princess" 
let rank = document.querySelector(".princess");
console.log(rank.className); // princess

rank.className = "queen"; /* Her Majesty 
has ascended to the throne, and the Princess
is now the Queen, so we've changed 
the class name to "queen"*/
console.log(rank.className); // queen
```

### Getting a list of classes with the **`classList` property**

```html
<!-- The manufacturers of Her Majesty's Cars are written in the class names -->
<div class="bentley rolls-royce">The Royal Garage</div>
```

```js
/* Let's get a list of Her Majesty's Cars by searching
for the corresponding element via the .bentley selector */

let garage = document.querySelector(".bentley");
console.log(`Her Majesty's Garage: ${garage.classList}`); // Her Majesty's Garage: bentley rolls-royce
```

#### Checking if an element has a class with the **`contains()`** method
```js
let garage = document.querySelector(".bentley");

garage.classList.contains("bentley"); // true — Her Majesty has a Bentley 
garage.classList.contains("jaguar"); // false — Her Majesty does not have a Jaguar
```

#### Assigning a class to an element with the **`add()` method**
```js
// a Jaguar has been delivered to The Royal Garage 
garage.classList.add("jaguar");

console.log(`Her Majesty's Garage: ${garage.classList}`); // bentley rolls-royce jaguar
```

#### Removing a class with the `remove()` method

```js
garage.classList.remove("jaguar"); // Her Majesty has grown tired of the Jaguar

console.log(`Her Majesty's Garage: ${garage.classList}`); // bentley rolls-royce
```

#### Toggling a class with the `toggle()` method
If an element doesn't have a class, the `toggle()` method operates like the `add()` method. If an element has a class, it works like the `remove()` method. In other words, this method changes, or toggles, the status of a class.
```html
<div class="bentley rolls-royce jaguar">The Royal Garage</div>
```

```js
// If there's a Jaguar, we must dispose of it
garage.classList.toggle("jaguar");

console.log(`Her Majesty's Garage: ${garage.classList}`); // bentley rolls-royce
```