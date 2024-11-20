## innerHTML
The `innerHTML` property stores a string as its value, which contains all of the HTML content inside an element, including the markup:
```js
document.body.innerHTML; 
/*If there is no HTML code in the 
document body, an empty string 
is returned.*/
```

```js
document.body.innerHTML = "<div>Let's add some HTML</div>"; 
/*Now the page has this div element 
and nothing else. If there's some 
other code in the document before 
using this property, this new code 
will replace it.*/
```

## textContent
The `textContent` property allows us to access or change the text content of an element. Note that this doesn't affect the HTML tags themselves.

```html
<p id="paragraph">This is the text inside the element.</p>
```

```js
let paragraph = document.getElementById("paragraph");
console.log(paragraph.textContent); 
// "This is the text inside the element."
paragraph.textContent = "And this is the new text."; 
// you can change the text content like this
```