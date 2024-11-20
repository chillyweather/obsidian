# The 'children' Prop

```jsx
function WrapperComponent(props) {
  console.log(props.children);
  return (
    <div>
      <h1>Hello Children!</h1>
      {props.children}
    </div>
  );
}
```

we use this component as a wrapper for some additional elements, it will look like this:

```jsx
/* the rest of the JSX */

<WrapperComponent>
  <div>
    <span>Here's content!</span>
  </div>
</WrapperComponent>

/* the rest of the JSX */
```

```jsx
function ConfirmationDialog(props) {
  return (
    <div class="dialog">
      <div class="dialog__body">{props.children}</div>
      <button onClick={props.onConfirm}>Confirm</button>
      <button onClick={props.onCancel}>Cancel</button>
    </div>
  );
}

export default function App() {
  return (
    <ConfirmationDialog
      onConfirm={() => alert("Order confirmed!")}
      onCancel={() => alert("Order cancelled!")}
    >
      Do you really want to place this order? {/* ← This is props.children */}
    </ConfirmationDialog>
  );
}
```