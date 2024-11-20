# JSX syntax rules

### Parentheses

At first, it might look a little odd to see HTML code mixed with "real" JavaScript. In order to better separate code and layout, and to provide a cleaner look visually, we recommend wrapping JSX with parentheses:

Copy codeJSX

`ReactDOM.render((
  <h2>
    Can I stay here?
  </h2>
), document.querySelector('#root'));` 

Of course, the code will also be valid without parentheses:

Copy codeJSX

`ReactDOM.render(
  <h2>
    What am I doing here?
  </h2>,
  document.querySelector('#root')
);` 

### Conditional Logic

One of the most common tasks when dealing with dynamic interfaces (and programming in general) is the implementation of conditional logic. In the previous lesson, we looked at an example where our interface changed based on the values of a JavaScript variable.

Inside of our JSX, we can write any JavaScript expression, which means that it's also possible for us to use the `?:` and `&&` operators.

The ternary operator `?:` is a shorthand version of an `if...else` statement:

Copy codeJSX

`ReactDOM.render((
  <div>
    {isDaylight ? (
      <h2>Good morning!</h2>
    ) : (
      <h2>Good evening!</h2>
    )}
  </div>
), document.querySelector('#root'));` 

The `&&` operator is functionally analogous to an `if` statement (without `else`), although visually, the syntax is quite different. We can use `&&` if we only want to display some JSX when a certain condition has been met, and likewise, prevent that JSX from displaying when the condition isn't met:

Copy codeJSX

`ReactDOM.render((
  <div>
    {isLunchTime && <h2>Time for lunch!</h2>}
  </div>
), document.querySelector('#root'));` 

Similar to `?:`, the `&&` operator can have compound conditions:

Copy codeJSX

`ReactDOM.render((
  <div>
    {isThursday && isRaining && <h2>Welcome to New York!</h2>}
  </div>
), document.querySelector('#root'));` 

Copy codeJSX

`ReactDOM.render((
  <div>
    {(isSummer && isSun) ? (
      <h2>It's a wonderful day!</h2>
    ) : (
      <h2>An ordinary day.</h2>
    )}
  </div>
), document.querySelector('#root'));` 

### Class Conflicts

JSX is visually very similar to HTML, but there are a few differences that are worth remembering. For example, when assigning CSS classes, we must use the `className` attribute instead of `class`, because `class` is a reserved keyword in JavaScript:

Copy codeJSX

`ReactDOM.render((
  <div>
    <div className="math">
      The Pythagorean theorem, also known as Pythagoras' theorem, is a
      fundamental relation in Euclidean geometry among the three sides of a
      right triangle. It states that the area of the square whose side is the
      hypotenuse (the side opposite the right angle) is equal to the sum of the
      areas of the squares on the other two sides.
    </div>
    <div className="literature">
      But outer Space,
      At least this far,
      For all the fuss
      Of the populace
      Stays more popular
      Than populous.
      Robert Frost.
    </div>
  </div>
), document.querySelector('#root'));` 

### Styles

Another cool little feature of JSX is the ability to set styles right inside JavaScript objects. However, when setting CSS styles with objects, instead of using kebab-case_,_ we'll name the CSS styles inside our objects using camelCase. So, in JSX, we'll need to write `border-radius` as `borderRadius`:

Copy codeJSX

`const cssRules = {
    width: 6792,
    height: 6752,
    borderRadius: '50%',
    background: '#934838',
    color: 'black',
};

ReactDOM.render((
    <div style={cssRules}>What planet am I?</div>
), document.querySelector('#root'));` 

If we set the styles inline instead of passing an object, we'll need to use double curly braces here, like so: `{{...}}`. The external brackets tell our JSX to substitute the values, while the interior ones hold the syntax to actually set the styles:

Copy codeJSX

`ReactDOM.render((
    <div style={{
        width: 3475,
        height: 3472,
        borderRadius: '50%',
        background: '#d0d5d2',
        color: '#444444',
    }}>
        I want to be a planet, too!
    </div>
), document.querySelector('#root'));` 

There's no need to specify our values in pixels — take a look at `width` and `height`. There is no trailing `px` inside this value. React takes care of this for us. Thanks, React!

### Fragments

In React, we sometimes use special components called fragments instead of standard `<div>` elements. Before we explain why, here's what the syntax looks like:

Copy codeJSX

`import React from 'react'; // remember to import!

ReactDOM.render((
  <React.Fragment>
    <button type="submit">Click me!</button>
    <div>Was it clicked?</div>
    <div>Yes, it was clicked!</div>
  </React.Fragment>
), document.querySelector('#root'));` 

What's going on here? As a rule, a block of JSX code should have only one exterior element. The code above features two adjacent `<div>` elements and one `<button>` element. In order to make this JSX work properly, we've wrapped these three elements inside a `React.Fragment` component. If we were to remove this wrapper, we would instead have three outermost elements, breaking the rule we just mentioned, and resulting in an error.

So, if all we're doing is making sure that our JSX only has one exterior element, why not just use `<div>` elements? What's the deal with `React.Fragment`? There's actually a good reason to use it!

Whenever we use a `<div>` element inside of our JSX, corresponding elements are added to the DOM. We want to avoid this whenever possible, as an application containing a large amount of unnecessary `<div>` elements can waste resources, or cause other unintended side effects. As we have access to fragments, using extra `<div>` tags with the sole intent of wrapping our JSX elements so they function properly isn't good practice.

Thankfully, there's a special shorthand we can use for React fragments:

Copy codeJSX

`ReactDOM.render((
  <>
    <button type="submit">Click me!</button>
    <div>Was it clicked?</div>
    <div>Yes, it was clicked!</div>
    <div>It was clicked!</div>
  </>
), document.querySelector('#root'));` 

The example above is much more concise than the first example, but the code is functionally equivalent. Utilizing these "empty tags" allow us to avoid an import statement, while still providing us the full benefits of the `Fragment` component.

### Self-Closing Tags

Some HTML elements such as `<img>`, `<br>`, `<hr>`, `<input>`, `<meta>`, or `<link>` don't have closing tags. In JSX they must be written with a trailing slash: `<img />`, `<br />`, `<hr />`, `<input />`, `<meta />`, `<link />`.

In addition, if elements that do have closing tags like `<div>` don't have content inside of them, they can also be shortened using the self-closing syntax. So, instead of `<div></div>`, we just end up with `<div />`:

