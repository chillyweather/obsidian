# DOM

Each branch in a DOM tree ends in a node. A node appears where there's

-   an opening tag
-   text
-   an HTML comment

## `querySelector()` and `querySelectorAll()` 

```html
<!-- index.html -->

<main id="container">
    <div class="content">
        <div class="content__item"></div>
        <div class="content__item"></div>
        <div class="content__item"></div>
    </div>
</main>
```

```js
/* script.js */

// To select an element by its identifier
let container = document.querySelector("#container");

// By class name
let content = container.querySelector(".content");

/* Note that here we're searching for an element 
specifically inside another element rather 
than searching the entire DOM tree */ 
let contentItems = content.querySelectorAll(".content__item");
```

 `querySelector()` method returns the first element on the page with this class name.
 
 `querySelectorAll()` will return all matching element.
 
 ```js
 /* script.js */

let container = document.querySelector("#container");
let content = container.querySelector(".content");
let contentItem = content.querySelector(".content__item");

console.log(contentItem) // Will log: 
// <div class="content__item"></div>

let contentItems = content.querySelectorAll(".content__item");

console.log(contentItems); /* Will log all elements 
with the .content__item class */
 ```
 
 