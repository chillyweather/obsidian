# Optimizing Fonts for Devices

### Smoothing
`-font-smoothing` is a CSS vendor (or browser) property that you can use to smooth custom fonts. Vendor properties work like other CSS declarations, but are non-standard and often new and experimental. They also require prefixes to specify which browsers you want to support.
```css
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
```

### Adjusting Text Size

This is also a vendor property, used to make sure that font sizes stay proportional when the page dimensions change. Not all browsers support it and the changes will vary based on the device, i.e. you are more likely to notice a difference using a supported mobile browser.

```css
-webkit-text-size-adjust: 100%;
-ms-text-size-adjust: 100%;
-moz-text-size-adjust: 100%;
```

### Rendering

This property can access some important tools that improve text readability, such as kerning and ligatures.

```css
text-rendering: optimizeLegibility;
```