# Link

![[Pasted image 20211101123319.png]]

## NavLink
Only real difference is that the `NavLink` component has a property called `activeClassName`, whereas `Link` doesn't.
![[Pasted image 20211101123615.png]]
The `activeClassName` property takes a CSS class selector as its value, and we can choose any name we'd like here. Essentially, whenever the browser has a URL that matches the path we specified inside of our `NavLink` component, the class we assigned to `activeClassName` will be active. In the example above, if the user navigates to `/`, the CSS class `nav__link_active` will become active. This will let us apply our own custom styles on links for the currently active page. This can be extremely helpful in a navigation bar, as it can provide a visual cue to our users as to their current location within our application.