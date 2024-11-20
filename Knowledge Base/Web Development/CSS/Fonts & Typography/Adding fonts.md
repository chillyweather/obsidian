# Adding fonts

There are two steps involved in adding a font:

1.  Declaring the font
2.  Applying the font to an element

### 1. Declaring the font

```css
@font-face {
    src: url(file path to the normal font);
    font-family: "Best Font Ever";
}
@font-face {
    src: url(file path to the italic font);
    font-family: "Best Font Ever";
    font-style: italic;
}
@font-face {
    src: url(file path to the semi-bold font);
    font-family: "Best Font Ever";
    font-weight: bold;
}
@font-face {
    src: url(file path to the semi-bold italic font);
    font-family: "Best Font Ever";
    font-style: italic;
    font-weight: bold;
}
```

### 2.Adding fonts
```css
body {
    /* if the font file doesn't load, the browser will use either Arial or Helvetica. 
	As a last resort, it will use whatever sans-serif font it can find on the user's device. */
    font-family: 'Best Font Ever', 'Arial', 'Helvetica', sans-serif;
    font-weight: bold;
    font-style: italic;
}
```

### Font formats
the best for web - .woff2, .woff
```css
@font-face {
    src: url(path to.woff2) format('woff2'),
         url(path to.woff) format('woff'),
         url(path to.ttf) format('truetype'),
         url(path to.eot) format('eot');
}
```

### Font weights

![[Pasted image 20210803122558.png]]