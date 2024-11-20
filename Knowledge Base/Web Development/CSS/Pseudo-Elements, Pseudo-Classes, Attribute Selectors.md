# Pseudo-Elements, Pseudo-Classes, Attribute Selectors

### Pseudo-Elements
```css
.selector::before {
    /* styles for the "before" pseudo-element */
}
.selector::after {
    /* styles for the "after" pseudo-element */
}
```

```html
<h1 class="title">for</h1>
```

```css
.title::before {
  content: "Lust ";
}

.title::after {
  content: " Life";
}
```
Result  - **Lust for Life**

### Pseudo-Classes

### Attribute Selectors
These selectors are used to select elements with specific attribute values. To do this, you need to write the attribute name followed by an equals sign and the desired value in quotes, all enclosed within square brackets.
```css
img[src="logo.png"] {
    border: 1px solid #0000ff;
}
```

To avoid confusion on behavior of `:last-of-type` pseudo-class, here's some extra info:  
This pseudo-class is designed to work with **element** selectors like p, a, div, li, and so on...  
`p:last-of-type {`  
`... your styles here`  
`}`  
But it can also be used with **class** selectors **only** when the element you're referring to is the `:last-of-type` by **element** as well. To clarify:  
When you have  
`<div>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`</div>`  
the following rule **will** work:  
`.text:last-of-type {`  
`... your styles here`  
`}`  
But it **will not** work when you have in your <div> some other <p> tag with different or no class. So, the above CSS rule will not work in these cases:  
`<div>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`<p>...</p>`  
`</div>`  
or  
`<div>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`<p class="any-other-class">...</p>`  
`</div>`  
Because here the last <p> tag with class="text" is not the last <p> tag overall. Which means if there're any other elements after the last <p> tag with class="text", and they are not <p> tags, the rule will still work:  
`<div>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`<span>...</span`  
`</div>`  
The difference between using `p:last-of-type` and `.text:last-of-type` is that the first rule will apply to last <p> tag of each block, while the second will apply for any last element with class="text" in each block. So, in this case:  
`<div>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`<p class="text">...</p>`  
`</div>`  
`<div>`  
`<ul>`  
`<li class="text">...</li>`  
`<li class="text">...</li>`  
`<li class="text">...</li>`  
`</ul>`  
`</div>`  
our CSS rule will apply both for the last <p> tag in the first block and the last <li> tag in the second block.  
But if you have this situation and you want the styles to apply to the last <p> tag only (for each block), you can simply use  
`p.text:last-of-type {`  
`... your styles here`  
`}`