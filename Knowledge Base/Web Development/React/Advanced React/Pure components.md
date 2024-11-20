# Pure components

**A special type of component that's not rendered when its parent is, but only when its own props change.**

### Creating a pure functional component
To make a functional component pure, just wrap it in the special `React.memo()` function:
```jsx
const Chat = React.memo((props) => {
  return (
    <div className="chat">
      <img src={`img/${props.id}.png`} width="75" />
      <h2>{Math.random()}</h2>
      <div className="date">{props.lastMessageAt}</div>
    </div>
  );
});
```

### Creating a pure class component

Making a class component pure is even simpler. Just use inheritance from `React.PureComponent` instead of `React.Component`:
```jsx
class Chat extends React.PureComponent {
  render() {
    return (
      <div className="chat">
        <img src={`img/${this.props.id}.png`} width="75" />
        <h2>{Math.random()}</h2>
        <div className="date">{this.props.lastMessageAt}</div>
      </div>
    );
  };
}
```

Both `React.memo()` and `React.PureComponent` work on a similar principle: they cache the latest props that were passed and the result of the last rendering of their child component. The next time there's a render attempt, if the props haven't changed, they simply return the cached result. If the props have changed, the renderer is called, and after that, the new cache and the new props are saved.

We recommend always using pure components unless the components are supposed to be updated along with their parents.

