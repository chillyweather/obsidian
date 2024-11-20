# Refs

Sometimes we may need a direct reference to a real DOM element. React provides a mechanism for this, and we call them refs. [The official React documentation](https://reactjs.org/docs/refs-and-the-dom.html) provides the following list of cases when using refs is justified:

-   Managing focus, text selection, or media playback
-   Triggering imperative animations
-   Integrating with third-party DOM libraries

For functional components, there's a special hook named `useRef()`. It returns an object, which we can assign to any element in our JSX code via the `ref` attribute. Doing this links that element to its corresponding DOM node, which we can then reference via the `current` field/property of the object.

```jsx
function VideoPlayer() {
  const videoRef = React.useRef(); // assigning the object returned by a hook to a variable

  function handleClick() {
    videoRef.current.play(); // calling the required method on the current property of the object
  }

  return (
    <>
      <video ref={videoRef} src="./clip.mp4" /> // pointed a ref attribute to the element => got direct access to the DOM element
      <button onClick={handleClick}>▶️</button> /* attached a handler to a button */
    </>
  );
}
```

For class components, it's similar, except that the ref is created/declared using the `React.createRef()` function, and the ref itself is usually written with `this`:

```jsx
class VideoPlayer extends React.Component {
  constructor() {
    super();
    this.videoRef = React.createRef(); // created a ref and assigned it to a variable - it will be a property of this
  }

  handleClick = () => {
    this.videoRef.current.play(); // similarly, we call the required method on the current field of the object
  };

  render() {
    return (
      <>
        <video ref={this.videoRef} src="./clip.mp4" /> //
        <button onClick={this.handleClick}>▶️</button> //
      </>
    );
  }
}
```

### Refs and local variables

Refs serve an additional purpose in functional components. Sometimes, you need to write some data inside a component, but state can't be used for this.

Let's say we want to keep a render counter in a function component. If we try to do this by using the `useState()` hook, then every time it's updated, the render will be called again and the counter will be updated. It'll turn into a vicious circle and the application will freeze.

```jsx
function MessageComposer() {
  const [value, setValue] = React.useState('');
  const counterRef = React.useRef(0);

  function handleChange(e) {
    setValue(e.target.value);
  }

  return (
    <>
      <input type="text" value={value} onChange={handleChange} />
      <h4>Renders: {++counterRef.current}</h4>
    </>
  );
}
```