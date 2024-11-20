# @media Queries

Media queries are used to build responsive websites as they allow you to define how elements look depending on the size of the browser window.

```css
@media (condition1) and (condition2) {
    selector {
        property: value;
    }
}
```

These are generally placed at the end of the CSS code. Every display mode gets its own media query. If you're going with a BEM layout, media queries will be written separately for each component at the end of its stylesheet. If your styles are all grouped by type, they should go at the end of the general .css file.

```css
@media screen and (max-width: 720px) {
    body {
        background-color: blue;
    }
}
```

```css
/* main code for a resolution of 1024px */
@media (min-width : 2560px) {
    /* styles for large monitors with a resolution of 4K */
}
@media (min-width : 1440px) {
    /* styles for large desktops and laptops */
}
@media screen and (max-width: 1024px) {
    /* styles for tablets in landscape orientation */
}
@media (max-width : 768px) {
    /* styles for tablets */
}
@media (max-width : 425px) {
    /* styles for large smartphones */
}
@media (max-width : 375px) {
    /* styles for medium-sized smartphones */
}
@media (max-width : 320px) {
    /* styles for small smartphones */
}
```

#### Write styles starting from the general to the specific, and from the large to the small

### Landscape mode
```css
@media screen and (max-width: 568px) and (max-height: 320px) {
    /* styles for iPhone 5 */
}
```

