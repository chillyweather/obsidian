# Checkbox, Radio button styling

1. Hide original checkbox
--> [[Clip]]

```css
.input[type="checkbox"] {
    position: absolute;
    width: 1px; /* if the element doesn't have any dimensions, some browsers will think that it doesn't exist at all */
    height: 1px;
    overflow: hidden; /* in most cases, everything will work without this property, but we don't want to take any chances. we'll study it in more detail later. for now, it's enough to say that it hides elements that go beyond the boundaries of their parents */
    clip: rect(0 0 0 0);
}
```

2. Once the checkbox is hidden, we need to create a new element next to it where we'll apply our styles. This element and its design will overlay the hidden checkbox:

```html
<label>
    <input type="checkbox" class="invisible-checkbox"> <!-- we've hidden this element -->
    <span class="visible-checkbox"></span> <!-- we'll apply styles to this one -->
</label>
```

3. Describe all checkbox states

```css
input[type="checkbox"]:disabled {} /* user can't select or edit the field */
input[type="checkbox"]:checked {} /* user has checked the checkbox */
input[type="checkbox"]:focus {} /* user has activated the field */
```

The problem here with this is that our checkbox is hidden. We need the appearance of our overlay element to be regulated by the state of the checkbox itself. Applying styles this way is a whole other kettle of fish requiring a new type of selector. Our real goal is select the element that comes immediately after our hidden checkbox. We can do this using the adjacent sibling combinator (`+`):

```css
input[type="checkbox"] + span {} /* this will select our span element 
as long as it immediately follows the checkbox, 
and both elements are children of the same parent */
```

[[styling radio buttons and checkboxes]]
# Placeholder

```css
input::placeholder {
    font-family: Arial;
}
```

For IE:

```css
input::-ms-input-placeholder {
    font-family: Arial;
}
```

For all browsers:

```css
input::-webkit-input-placeholder {color:#c0392b;}
input::-moz-placeholder          {color:#c0392b;}
input::-ms-input-placeholder     {color:#c0392b;}
input::placeholder               {color:#c0392b;}
```