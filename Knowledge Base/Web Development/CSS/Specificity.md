# Specificity

-   Due to the cascading nature of CSS, if two rules are applied to the same element, the one that comes last is the one that will be used.
-   CSS specificity is a set of rules that determine which style is applied to an element.
-   The weight system is one way of calculating the specificity of different selectors. Here's a summary of the weights:

```
Inline Styles                               - 1000
ID selectors                                -  100
Classes, Attributes and Pseudo-classes      -   10
Elements and Pseudo-elements                -    1 
```

-   `!important` overrides all other styles regardless of the specificity of the selector where it is used.