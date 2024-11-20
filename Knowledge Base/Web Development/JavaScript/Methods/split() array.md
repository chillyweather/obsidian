The `split()` method takes one parameter — the separator. A separator can be any string — most commonly a space `(" ")` which `split()` will use to break strings up into array elements.

```js
"I came. I saw. I conquered.".split(" "); 
// [ 'I', 'came.', 'I', 'saw.', 'I', 'conquered.' ] 
"I came. I saw. I conquered.".split(". "); 
// [ 'I came', 'I saw', 'I conquered.' ]
```