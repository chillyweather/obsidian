# Order in CSS

As a general guideline, we recommend writing your CSS code in the following order:

1.  The most general rules first, such as for the `<body>` element. (Remember that in such cases you should still only use class selectors. Even if there is only one `<body>` element on each page, you should assign a class to this element and apply the styles to the class.)
2.  Styles for supplementary blocks (for example, those used only for a mix).
3.  Styles for the first block in the HTML code.
4.  Any modifiers for this block.
5.  The first element of this block.
6.  Any modifiers for this element.