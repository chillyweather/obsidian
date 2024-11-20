# Clip

The `clip()` function works for elements with absolute positioning and defines the area in which its content will be displayed.

```css
clip(X1, Y1, X2, Y2);
```

![[Pasted image 20210726082702.png]]

```css
.input[type="checkbox"] {
    position: absolute;
    width: 1px; /* if the element doesn't have any dimensions, some browsers will think that it doesn't exist at all */
    height: 1px;
    overflow: hidden; /* in most cases, everything will work without this property, but we don't want to take any chances. we'll study it in more detail later. for now, it's enough to say that it hides elements that go beyond the boundaries of their parents */
    clip: rect(0 0 0 0);
}
```