# useRouteMatch() Hook

React Router provides us with a hook called `useRouteMatch()` that allows us to access the router's state. There are two properties we'll look at here: `url` and `path`.

The `url` property will allow us to build relative links to use inside of our `Link` components, while the `path` property will allow us to build relative paths for our `Route` components.

```jsx
import React from "react";
import { Route, Link, useRouteMatch } from "react-router-dom";
import MyStory from "./MyStory";
import Hobbies from "./Hobbies";
import Contact from "./Contact";
import "./AboutMe.css";

function AboutMe() {
  const { path, url } = useRouteMatch();

  return (
    // our new JSX inside of AboutMe.js

    <ul className="links">
    <li>
      <Link to={`${url}/my-story`}>My Story</Link>
    </li>
    <li>
      <Link to={`${url}/hobbies`}>Hobbies</Link>
    </li>
    <li>
      <Link to={`${url}/contact`}>My Contact Info</Link>
    </li>
    </ul>
    <Route path={`${path}/my-story`}>
        <MyStory />
    </Route>
    <Route path={`${path}/hobbies`}>
        <Hobbies />
    </Route>
    <Route path={`${path}/contact`}>
        <Contact />
    </Route>
  );
}

export default AboutMe;
```