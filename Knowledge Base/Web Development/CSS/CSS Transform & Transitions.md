# CSS Transformations

A **transformation** is a method for modifying the shape or position of an element. In CSS, this is done with the `transform` property.

Any transformation can be written in general terms with the `matrix` value, which contains 6 parameters, each of which dictates how a certain aspect of the element should be modified.

1 is changing the horizontal scale (the element is doubled along the X axis).
2 is vertical skew (a positive value raises the left half of the element and lowers the right, and a negative value does the opposite).
3 is horizontal skew (a positive value tilts the element to the left, a negative value tilts it to the right).
4 is changing the vertical scale (the element is stretched 5 times along the Y axis).
5 is translation in the direction of the X axis, in pixels.
6 is translation in the direction of the Y axis, in pixels.

```css
div {
  transform: matrix(2, 3, 4, 5, 6, 7);
}
```

We can use a matrix to describe practically any change to an object's shape and position, but there are specific values for the most popular transformations, like `rotate()` or `skew()`.

```css
transform: translate(10px, 20px); /* moves the object 10 pixels to the right and 20 pixels down */  

transform: scale(1.5, 0.5); /* enlarges the object by a factor of 1.5 horizontally and halves it vertically */  

transform: rotate(30deg); /* rotates the object 30 degrees clockwise */  

transform: skew(30deg, 40deg); /* skews the top side of the object 30 degrees to the left, the bottom side 30 degrees to the right, the left side 40 degrees up, and the right side 40 degrees down */  
```

![[Pasted image 20210725074341.png]]

# CSS Transitions

The transition from one style to another should take place more smoothly. We can regulate how this happens with the `transition` property. Here are the main sub-properties we'll be dealing with:

-   `transition-property` describes which property is being changed.
-   `transition-duration` specifies the transition time in seconds.
-   `transition-timing-function` defines how the transition animation will behave (speed up, slow down, or move linearly).
-   `transition-delay` is the number of seconds between the change in the element's state and the start of the animation.

```css
div {
    background-color: black;
    transition-property: background-color;
    transition-duration: 1s;
    transition-timing-function: linear;
    transition-delay: 2s;
}

div:hover {
    background-color: white;
}
```

We can do the same thing using a shorthand syntax with the `transition` property. In order, we can assign the value of `transition-property`, `transition-duration`, `transition-timing-function`, and `transition-delay` to this single property:

```css
div {
    background-color: black;
    transition: background-color 1s linear 2s;
}

div:hover {
    background-color: white;
}
```

Тайминг с помощью кривых Безье
https://cubic-bezier.com/
```css
transition-timing-function: cubic-bezier(1,.2,.52,.46);
```

**One thing to keep in mind about the transition property is that it performs best when applied directly to the element's rule rather than to its* :hover* rule.**

Проще говоря - в ховере прописывается ЧТО изменится (изначальное состояние), в оригинальном классе - насколько и каким образом.