# DOM_Built-in Properties

```html
<!-- Applying the href attribute to the <a> element -->
<a href="https://ya.com">Search</a>
```

```js
// Selecting the <a> element
let a = document.querySelector("a");

a.href; // https://ya.com — now the <a> 
//object has the href property
```

```js
a.href = "https://practicum.yandex.com/"
```

Properties and attributes are not the same thing. If you apply an attribute to an element that doesn't meet [W3C specifications](https://www.w3.org/), the object won't have the corresponding property. Nevertheless, we still can get the value of this attribute by calling the `getAttribute()` method:

```html
<!-- index.html -->
<div id="cat" catName="Garfield">Cat</div>
```

```js
/* script.js */
let cat = document.querySelector("#cat");
console.log(cat.catName); // undefined
console.log(cat.getAttribute("catName")); 
// Garfield
```

