# Gradients

##  Linear Gradient

```css
div {
    background-image: linear-gradient(#6be454, #57d9ba);
}
```

![[Pasted image 20210725113549.png]]

or degrees:
```css
div {
  background-image: linear-gradient(90deg, #0078FF, #C2E3E3);
}
```

To build more complex gradients, we can use more than two colors:

#### Multiply colors
```css
div {
    background-image: linear-gradient(#0B2337, #126DDC, #76C2E0, #D1DC9D, #F09174);
}

```

After setting each color, you can set the interval at which the colors should be applied. The first value is the starting point of the direction you've set, and the second is the final point.

```css
div {
  width: 300px;
  height: 300px;
  background-image: linear-gradient(#0078FF 0px 100px, #B4DEEF 100px 200px, #FF5A0A 200px 300px);
}
```

as percentages:
```css
div:first-of-type {
  width: 300px;
  height: 300px;
  background-image: linear-gradient(#0078FF 20%, #C2E3E3 100%);
}

div:last-of-type {
  width: 300px;
  height: 300px;
  background-image: linear-gradient(#0078FF 80%, #C2E3E3 100%);
}
```

## Radial Gradient

basic:
```css
div { background-image: radial-gradient(#0078FF, #C2E3E3); }
```

с выбором положения центральной точки:
```css
div {
  width: 300px;
  height: 300px;
  background-image: radial-gradient(at 40px 50px, #0078FF, #C2E3E3);
}
```

несколько цветов:
```css
div {
  width: 300px;
  height: 300px;
  background-image: radial-gradient(#002918 10%, #B4DEEF 20%, #FFFFFF 50%, #FF5831 100%);
}
```

для жестких переходов указываем по два конкретных значения:
```css
div {
  width: 300px;
  height: 300px;
  background-image: radial-gradient(#002918 10%, #B4DEEF 20%, #FFFFFF 50%, #FF5831 100%);
}
```