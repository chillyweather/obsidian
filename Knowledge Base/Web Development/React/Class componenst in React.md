```jsx
// User class component
class User extends React.Component {
  constructor(props) {
    super(props);

    // starting values for component's state
    this.state = {
      rating: 0,
    };
  }

  /*
   * event handlers: change the state
   */
  handleLike = () => {
    this.setState({ rating: 1 });
  };

  handleDislike = () => {
    this.setState({ rating: -1 });
  };

  // render the JSX structure
  render() {
    return (
      <p>
        <img
          src={`https://code.s3.yandex.net/web-code/react/${this.props.id}.png`}
          width="75"
        />
        <br />
        <b>{this.props.name}</b>
        <div className="rating">
          <button onClick={this.handleLike}>👍</button>
          {this.state.rating}
          <button onClick={this.handleDislike}>👎</button>
        </div>
      </p>
    );
  }
}

// the main app code
ReactDOM.render(
  <>
    <h2>My Imaginary Friends:</h2>
    <User id="1" name="Gregory" />
    <User id="2" name="James" />
    <User id="3" name="Allison" />
  </>,
  document.querySelector("#root")
);
```

```jsx
class Switch extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      isActive: this.props.isActive,
    };
  }

  handleClick = () => {
    this.setState({ isActive: !this.state.isActive });
  };

  render() {
    // we're using JavaScript expressions to build up our CSS class
    const className = `switch ${this.props.color} ${this.state.isActive ? 'on' : 'off'}`;

    return (
      <div className={className}>
        <button className="img" onClick={this.handleClick} />
        <h3>{this.props.title}</h3>
      </div>
    );
  }
}

ReactDOM.render((
  <>
    <Switch title="Happy" color="blue" isActive={true} />
    <Switch title="Love" color="orange" isActive={false} />
    <Switch title="Taco" color="green" isActive={false} />
  </>
), document.querySelector('#root'));

```