# BEM (Block, Element, Modifier)

#css #bem

## Naming rules

`block-name__elem-name_mod-name_mod-val`

-   Names are written in lowercase Latin letters.
    
-   Words are separated by a hyphen (`-`).
    
-   The block name defines the [namespace](https://en.wikipedia.org/wiki/Namespace) for its elements and modifiers.
    
-   The element name is separated from the block name by a double underscore (`__`).
    
-   The modifier name is separated from the block or element name by a single underscore (`_`).
    
-   The modifier value is separated from the modifier name by a single underscore (`_`).
    
-   For boolean modifiers, the value is not included in the name.

[Naming convention / Methodology / BEM](https://en.bem.info/methodology/naming-convention/)

```html
<header class="header"> <!-- this is a block; the page header to be precise -->
  <a href="#" class="header__link">[Your name]</a>
</header>
```

### Modifiers
We use modifiers to denote the state or behavior of a block or element.
We can use the `active` modifier to indicate that the link is active.
```html
<nav class="menu">
  <a href="#" class="menu__link menu__link_active">First steps in HTML and CSS</a>
  <a href="#" class="menu__link">JavaScript Libraries</a>
  <a href="#" class="menu__link">Practice in HTML, CSS and JavaScript</a>
</nav>
```

##### Types of modifiers
**Boolean modifiers** 
are used when an element or a block can only have two states. For example, a menu item can have two states: default and active (for example, an underlined menu link to show that this is the page the user is on).
```html
<nav class="menu">
    <a href="index.html" class="menu__link menu__link_active">Main page</a>
    <a href="about.html" class="menu__link">About us</a>
  <a href="contacts.html" class="menu__link">Contacts</a>
</nav>
```

**Key-value modifiers**
are used when there are several options for an item's appearance, state, or behavior.
```html
<div class="solution-status solution-status_type_success"></div>
<div class="solution-status solution-status_type_error"></div>
<div class="solution-status solution-status_type_message"></div>
```

