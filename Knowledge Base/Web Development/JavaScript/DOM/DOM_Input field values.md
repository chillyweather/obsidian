# Input field values

All `input` fields have the `value` property, which returns the value entered to an input field.

![image](https://pictures.s3.yandex.net/resources/Frame_223_1585660514.png)

```js
/* script.js */

let inputs = document.querySelectorAll("input");

console.log(inputs[0].value); // "I'm Not In Love"
console.log(inputs[1].value); // "10cc"
```

###### Checkbox and radio button states — the `checked` property
Only checkboxes and radio buttons have this property. It returns `true` if a checkbox or radio button is checked, and `false` if not.
