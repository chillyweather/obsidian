# insertAdjacentHTML() and insertAdjacentText()

The `insertAdjacentHTML()` and `insertAdjacentText()` methods allow us to add new elements or text to the HTML code without losing any of the old elements.

We can add the tiger to the zoo using the `insertAdjacentHTML()` method as follows:
```js
zoo.insertAdjacentHTML('beforeend', '<div class="tiger"></div>');
```

The `"beforeend"` argument tell us that this new HTML code will go at the end of the specified element, i.e. before the closing tag of the `<div>` element with the `zoo` class. You can also pass through the following arguments:

-   `"beforebegin"` — insert before the opening tag
-   `"afterbegin"` — insert after the opening tag
-   `"afterend"` — insert after the closing tag

```html
<!-- "beforebegin" -->
<div>
    <!-- "afterbegin" -->

    <!-- some HTML code that is already present -->

    <!-- "beforeend" -->
</div>
<!-- "afterend" -->
```