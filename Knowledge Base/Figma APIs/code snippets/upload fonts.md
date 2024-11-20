```js
const loadFonts = async () => {
await figma.loadFontAsync({ family: "Inter", style: "Regular" });
await figma.loadFontAsync({ family: "Inter", style: "Bold" });
};

....

const compText = figma.createText();

loadFonts()
	.then(() => {
		compText.fontSize = 24;
		compText.fills = [{ type: "SOLID", color: { r: 1, g: 1, b: 1 } }];
		compText.characters = "draft";
		compText.textCase = "UPPER";
		compText.fontName = {
			family: "Inter",
			style: "Bold",
			};
	}).finally(() => figma.closePlugin())
```