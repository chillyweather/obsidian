# Dynamic Routes

```jsx
// App.js

import React from "react";
import "./App.css";

import { BrowserRouter, NavLink, Route, Switch } from "react-router-dom";
// importing the necessary components
import Friends from "./Friends";
import Friend from "./Friend";
import Dashboard from "./Dashboard";
import serverData from "../serverData"; // this is the JSON we created before

function App() {
  return (
    <BrowserRouter>
      <div className="App">
        <header className="header">
          <NavLink to="/" className="header__logo">
            Parrot Friendship Society
          </NavLink>
          <nav className="menu">
            <ul className="menu__list">
              <li className="menu__list-item">
                <NavLink className="menu__link" to="/friends">
                  Friends
                </NavLink>
              </li>
            </ul>
          </nav>
        </header>
        <Switch>
          <Route exact path="/">
            <Dashboard />
          </Route>
          <Route exact path="/friends">
            <Friends serverData={serverData} />
          </Route>
          <Route path="/friends/:id">
            <Friend serverData={serverData} />
          </Route>
        </Switch>
      </div>
    </BrowserRouter>
  );
}

export default App;
```

## URL Parameters

When working with a `Route` component, if we include `:` in our `path`, the text following the colon will have a special meaning.

Specifically, the text following the colon will denote the name of a URL parameter. We can then access any value of this parameter as a variable inside the component that this route will render. The actual value of this parameter will be determined by whatever URL the user is currently visiting inside of the browser.
We can actually pass something from the URL right into our components!

```jsx
<Route path='/my-birds/:favoriteParrot'>
  <Friend serverData={serverData} />
</Route>

<p>{favoriteParrot}</p>
```

## useParams() Hook

However, in order to get these values, we'll first need to utilize another React hook: `useParams()`.

![[Pasted image 20211102134301.png]]

