# Project 3

- For texts, use Figma's free "Inter" font family
- The design shows how the website should look on various screen resolutions. It doesn't provide instructions as to which breakpoints to use in media queries. We recommend that you focus on five intervals:

	-   1280px and higher (standard laptops and beyond).
	-   From 1024px to 1280px (from a tablet in landscape to a standard laptop).
	-   From 768px to 1024px (from a tablet in portrait to a tablet in landscape).
	-   From 425px to 768px (from a large smartphone to a tablet in portrait).
	-   Up to 425px (mobile devices).

- Make sure that your elements don't "break" between breakpoints by checking what the layout looks like at intermediate resolutions such as 470px, 665px, 999px, and 1100px.

Keep the following in mind:

-   Font sizes and margins between elements often change.
-   In order to make your site responsive, you need to know how to replace absolute values such as pixels with relative ones like `%`, `vw`, `vh`, and `fr`.
-   If images take up 100% of the page's width, don't be afraid to use the `width: 100%` declaration for them. The height will be calculated automatically.
-   Use the CSS `calc()` function. This will help you with calculating the dimensions of your elements while also revising your arithmetic.
-   Specify values for the `line-height` property in decimals (for example, `line-height: 1.5`) in accordance with best practices.
-   Don't make things too complicated for yourself here. Set font sizes in pixels. Save your knowledge of `em` and `rem` for job interviews at companies with strict coding guidelines.
-   Don't forget to smooth the fonts.
-   Download the fonts to your project folder and connect them locally.
-   It's a good practice to use decimals when specifying line spacing.
-   If you notice that the scaling for images looks strange at breakpoints, try using the `object-fit` property. This helps a lot in such cases.
-   Don't forget to look at the Hover On and Hover Off frames in the Figma file. They'll show you how elements should react when the user hovers over certain links.

- Don't forget to [compress your images](https://tinypng.com/)

Plan:

1.  Start off by building the website only for the highest resolution in the brief: `1280px`.
    
2.  Remember to use percentage values, flexbox, or Grid. They make your layout responsive by default. The less hardcoded values you have in your CSS, the less work you'll need to put in later to make it fit other resolutions.
    
3.  Once you've coded you site for screen widths of `1280px`, test it with Chrome and Firefox, using their developer tools. Make sure that there aren't any horizontal scroll bars on your website.
    
4.  Next, check your website against the `1024px` layout and add media queries.
    
5.  Make sure your layout matches the Figma prototype using devtools in your browsers.
    
6.  Likewise, add media queries for the `768px` and `425px` breakpoints and check them in your browsers.
    
7.  Check values in between the breakpoints and look out for horizontal scroll bars: if one appears, then page elements need to be reduced/increased in smaller steps.
    
8.  Don't forget to use the `calc()` function in your CSS files.