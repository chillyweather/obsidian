# Methods Involving Attributes
 
 There are four things you can do with HTML attributes by calling certain methods:

1.  Retrieve an attribute's value with the `getAttribute()` method.
2.  Check if an element has a certain attribute with the `hasAttribute()` method.
3.  Set the value of an attribute with the `setAttribute()` method.
4.  Remove an attribute with the `removeAttribute()` method.

### getAttribute()
This method takes the name of an attribute as an argument and returns its value
```js
/* this code will find the first DOM element
 corresponding to an <img> element on the page */ 

let imageOnPage = document.querySelector("img");

imageOnPage.getAttribute("src"); /* this will return the 
link specified as the value of the src 
attribute of the first image on the page 
as found by the querySelector() method*/
```

If the element doesn't have the attribute we passed as an argument, or the attribute doesn't exist, the method will return a value of `null`. If the attribute has been assigned, but it doesn't have a value (for example, the `disabled` attribute doesn't have a value), this will return an empty string

```html
<button id="big-red-button" onclick="alert('KABOOM!');" disabled>
    A big red button
</button>
```

```js
// search the button by ID and store it in the bigAndRed variable
let bigAndRed = document.querySelector("#big-red-button");

// inspecting the button element via the getAttribute() method
bigAndRed.getAttribute("lang"); // null
bigAndRed.getAttribute("a non-existent attribute"); // null
bigAndRed.getAttribute("disabled"); // ''
```

### hasAttribute()
This is a simple way of verifying whether or not an element contains a given attribute. If the element has the chosen attribute, the method will return `true`. If not, it'll return `false`.
```js
bigAndRed.hasAttribute("onclick"); // true
bigAndRed.hasAttribute("a non-existent attribute"); // false
bigAndRed.hasAttribute("disabled"); // true
```

### setAttribute()
This method takes two arguments as an input. These are the name of the attribute, and the value you want to give it. If the attribute already exists, you can use this method to change its value.
```js
bigAndRed.setAttribute("lang", "en");
сonsole.log(bigAndRed.hasAttribute("lang")); //true
```

```js
disabledCheckbox.setAttribute("disabled", true); // Deactivating the checkbox.
```

```js
someElement.setAttribute("style", "background-color: #000000");
```

##### Attributes Without Values
To disable a checkbox, you need to pass two parameters through the `setAttribute()` method. The first parameter is `"disabled"`, and the second one can be absolutely anything.
```js
disabledCheckbox.setAttribute("disabled", true);
disabledCheckbox.setAttribute("disabled", "The value of this argument does not matter"); 
disabledCheckbox.setAttribute("disabled", "We simply pass it to make the method work"); 
disabledCheckbox.setAttribute("disabled", false); // even this will work
```

### removeAttribute()
```js
bigAndRed.hasAttribute("disabled"); // true
bigAndRed.removeAttribute("disabled"); // removes the attribute from the element
bigAndRed.hasAttribute("disabled"); // false
```