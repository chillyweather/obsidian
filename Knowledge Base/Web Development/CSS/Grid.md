# CSS Grid

A grid container consists of a set of horizontal and vertical grid lines inside which grid items are placed, with each item being a direct child of the grid container.

- display: grid;
- display: inline-grid; (its width equals the total width of its child elements)

### Grid-template-columns/rows
These properties can have multiple values separated by a space, each of which specifies the size of a row or column.

```css
.container {
    display: grid;
    grid-template-columns: 100px 100px 150px;
    grid-template-rows: 150px 150px 100px;
    grid-gap: 10px;
}
```

 We use the `grid-column-gap` property for columns and `grid-row-gap` for rows:
 
 ### Gap
 
 ```css
 .container {
    display: grid;
    grid-template-columns: 100px 100px 150px;
    grid-template-rows: 150px 150px 100px;
    grid-column-gap: 20px;
    grid-row-gap: 10px;
}
 ```
 
 Alternatively, you can specify values for both using the `grid-gap` property, and writing them on one line like this:
 ```css
 grid-gap: 10px 20px;
 ```
 
 ### Repeat
 
 ```css
 /* instead of this: */
grid-template-columns: 20% 20% 20% 20% 20%;
/* you can write this: */
grid-template-columns: repeat(5, 20%);

grid-template-columns: repeat(5, auto) 200px;
 ```
 
 ### Fractions
 ```css
 grid-template-columns: repeat(6, 1fr);
 ```
 
 ### Grid-column-start/end
 
 ```css
 .block_size_big {
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start: 1;
    grid-row-end: 6;
}
 ```
 
 ![[Pasted image 20210731184229.png]]
 
 Grid lines can also have negative numbers.
 
 ![[Pasted image 20210731184503.png]]
 
 ```css
 .block_size_big {
    grid-column-start: -1;
    grid-column-end: -3;
    grid-row-start: 1;
    grid-row-end: 6;
}
 ```
 
 ![[Pasted image 20210731184548.png]]
 
 #### shortcut
 
 ```css
 .block {
    grid-row: 1;
    grid-column: 2/4;
}
 ```
 
 ### Name row/column
 
 ```css
 grid-template-rows: [aside-start] 300px [aside-end];
 ```
 
 ```css
 grid-row: aside-start / 4;
 ```
 
 ### Span
 
 ```css
 .block {
    grid-column-start: 2;
    grid-column-end: span 2;
    grid-row-start: span 2;
    grid-row-end: 3;
}
 ```
 
 ## Grig Areas
 
 ```css
 .container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(4, 1fr);
    grid-template-areas:
    "header header header"
    "news news aside"
    "promo promo aside"
    ". footer footer";
}
 ```
 
 The `grid-template-areas` property won't work unless every grid cell has a name. You can name an area whatever you want, but we advise choosing names that describe what the cell will contain. If you want a cell to be empty, put a period instead of a name.

You can then control the area's appearance with the `grid-area` property, which is applied to the grid item, and specifies where it should be placed.

```css
.header {
    grid-area: header;
}
```