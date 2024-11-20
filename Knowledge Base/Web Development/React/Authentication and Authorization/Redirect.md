# Redirect

We can use this as the last component inside of our `Switch` component so that users will be sent to the right place depending on their authorization status. We'll first import the `Redirect` component from `react-router-dom`, then we'll place it inside of our `Route` component.

```jsx
// inside of App.js

<Route exact path="/">
  {this.state.loggedIn ? <Redirect to="/ducks" /> : <Redirect to="/login" />}
</Route>
```