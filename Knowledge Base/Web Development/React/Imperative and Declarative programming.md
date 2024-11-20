# Imperative and Declarative programming

- The imperative approach in programming implies describing the sequence of instructions for manipulating the DOM.

- The declarative approach in programming implies describing all possible interface states using state variables and conditional logic.

- The declarative approach allows making an interface responsive to user actions, not by making direct changes to the DOM, but instead changing variables responsible for the markup.


 In imperative programming, for every element, the developer describes a sequence of changes that should take place whenever a certain event occurs.
 
 ```jsx
 const element = document.querySelector('#myElement');

element.addEventListener('click', () => {
    const element2 = document.querySelector('#myAnotherElement');
    element2.classList.add('active');

    const element3 = document.querySelector('#myText');
    element3.innerHTML = 'It was clicked!';
});
 ```
 
```html
<div id="myElement">Click me!</div>

<div id="myAnotherElement">
    <div id="myText">
        Waiting for click...
    </div>
</div>
```

A declarative programming style allows us to approach this task from a different perspective. When an event occurs, we could simply change the value of some variable. Then, what if, for all other elements, we describe the possible states for any value of this variable in advance?
```jsx
const element = document.querySelector('#myElement');
let isClicked = false;

element.addEventListener('click', () => {
    isClicked = true;
});
```
HTML could depend upon variables inside of our JavaScript:
```jsx
<div id="myElement">Click me!</div>

<div id="myAnotherElement" className={isClicked ? 'active' : ''}>
    <div id="myText">
        {isClicked ? 'It was clicked!' : 'Waiting for click...'}
    </div>
</div>
```
