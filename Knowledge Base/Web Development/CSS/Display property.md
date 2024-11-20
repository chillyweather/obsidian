#css 


# Display property

The way an element behaves is defined by the `display` property. Inline elements can become block elements, and vice versa:

Copy codeCSS

```css
a {
  display: block; /* the link now takes up the entire width of its parent and is located on a new line */
}

p {
  display: inline; /* the paragraph will take up exactly the dimensions that it needs for the content inside it and will show up on the same line as other inline elements */
}
```

When a block element becomes an inline element, we can't set its height and width. To make it act like an inline element without ignoring the `width` and `height` properties, we can use the `inline-block` value.

```css
p {
  display: inline-block; /* the paragraph appears on the same line as inline and inline-block elements, but we can set its height and width independently */
}
```