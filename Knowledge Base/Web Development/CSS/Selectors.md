#css
# Selectors
[CSS Diner - Where we feast on CSS Selectors! (flukeout.github.io)](https://flukeout.github.io/)


Nested selectors reference specific elements based on their parent elements and their location in the document
```css

/* all instances of a p element inside a div */ 
div p { color: red; } 
/* all elements with my-class inside a div */ 
div .my-class { color: red; }

```

Sometimes we need to select a very particular element. For example, if we want to only select links with a certain class or an element with two specific classes, we can use compound selectors:
```css
/* a link with the class my-link */ 
a.my-link { color: red; } 
/* any element with both the my-button and my-button_large classes */ 
.my-button.my-button_large { color: red; }
```


### Adjacent Sibling Selector
**p + .intro** selects every element with **class="intro"** that directly follows a p
**div + a** selects every a element that directly follows a div


### General Sibling Selector
 Select elements that follows another element
 **A ~ B** selects all **B** that follow a **A**
 
 ### Misc
 
 ```css
 .form__item[type="radio"][value="two-columns"] {
  margin-left: 25px;
}
 ```