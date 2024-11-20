### Mutations of Complex Objects

If we use arrays or objects with fields for the state, we need to avoid changing (mutating) the state directly. For this reason, we need to remember to always pass a new object to the setter. In these cases, it's convenient to use the spread operator `...` as this creates a modified copy of the source object. We can do this with arrays:

```jsx 
const [array, setArray] = React.useState(['One', 'Two', 'Three']);

// this is not the correct way!
array.push('Four');
setArray(array); 

// this is the right way
setArray([...array, 'Four']);
```


And here's how we can avoid mutating the state when using objects:


```jsx 
const [object, setObject] = React.useState({ name: 'James', surname: 'Wilson' });

// this is not the correct way!
object.name = 'Gregory';
setObject(object); 

// this is the right way
setObject({
  ...object,
  name: 'Gregory',
});
```


It's important to note that this rule does not only apply to hooks, but also to any state changes we might make when working with class components.

Due to the fact that the React engine compares the old and new values using the `===` operator, we can't pass the original object — otherwise, the check will always return `true`.