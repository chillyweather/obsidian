```js
/* names of illnesses are written in order of 
how patients have arrived. Let's sort them in alphabetical order. */


const diseases = [
    "Mysophobia",
    "Fear of missing out",
    "Erythrophobia"
];

diseases.sort(function(a, b) {
  a = a.toLowerCase();
  b = b.toLowerCase();

    if (a < b) return -1; // a will come before b
    if (b < a) return 1; // b will come before a

  return 0;
});

console.log(diseases);

/* ["Erythrophobia","Fear of missing out", "Mysophobia"] */
```