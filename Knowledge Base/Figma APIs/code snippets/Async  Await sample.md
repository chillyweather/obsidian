
```js
async function test() {

// const fontData = await figma.listAvailableFontsAsync();

console.log("aand");

const fonts = await figma.listAvailableFontsAsync();

console.log("yep");

console.log("fonts.length :>> ", fonts.length);

figma.closePlugin("something was done");

}

  

test();
```