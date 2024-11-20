Let's imagine that we want to make an app which will allow users to customize their cursor. We'll place a checkbox on the page so that users can switch on this feature, and then we'll add a component with a picture that will follow the movement of the mouse.

For this app, two components will be required: a root `App` component with a checkbox, and inside of it, a `NeonCursor` component that will be mounted only when the checkbox is checked.

```jsx
// the app's root component 
class App extends React.Component {
  constructor(props) {
    super(props);

    this.state = { isCustomCursor: false };
  }

  handleChange = () => {
    this.setState({
      isCustomCursor: !this.state.isCustomCursor,
    });
  };

  render() {
    return (
      <>
        <label>
          <input type="checkbox" onChange={this.handleChange} />
          Turn on the neon cursor
        </label>
        {this.state.isCustomCursor && <NeonCursor />}
      </>
    );
  }
}
```

```jsx
// the component responsible for the custom component
class NeonCursor extends React.Component {
  constructor(props) {
    super(props);

    this.state = { top: 0, left: 0 };
  }
  // this method will be called right after mounting: we're creating effects
  componentDidMount() {
    document.addEventListener('mousemove', this.handleMouseMove);
    document.documentElement.classList.add('no-cursor');
  }
    // this method will be called just before unmounting: we're removing some effects
  componentWillUnmount() {
    document.documentElement.classList.remove('no-cursor');
    document.removeEventListener('mousemove', this.handleMouseMove);
  }

  handleMouseMove = (event) => {
    this.setState({
      top: event.pageY,
      left: event.pageX,
    });
  };

  render() {
    return (
      <img
        src="./cursor.png"
        width="30"
        style={{
          position: 'absolute',
          top: this.state.top,
          left: this.state.left,
          pointerEvents: 'none',
        }}
      />
    );
  }
}
```