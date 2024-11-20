# Programmatic Navigation

## History

```jsx
import { useParams, useHistory } from 'react-router-dom';

const history = useHistory();

// our updated JSX inside of Friend.js

<div className="friend__card">
  <img className="friend__userpic" src={friend.profilePicLight} alt={friend.name}/>
  <div className="friend__details">
    <h3 className="friend__name">{friend.name}</h3>
    <p className="friend__location">Location: {friend.location}</p>
    <p className="friend__quantity">Number of birds: {friend.parrotsOwned.length}</p>
    <p className="friend__fav-quote">Favorite bird quotes: "{friend.favBirdQuote}"</p>
  </div>
</div>
<button className="button button_type_back" onClick={() => history.goBack()}></button>

```

Using the `history` object gives us more options besides `history.goBack()`:

-   We use `history.goForward()` to send users forward through their history stack. This is analogous to the browser's "forward" button.
-   We could use `history.push()` to create an entirely new entry on the history stack. This action corresponds to visiting a new page in the browser. The path to the page is passed to the method as a parameter, for example, `history.push('/register')`.

## Redirecting the User

`Redirect` will replace the current entry on the history stack with a different one, which will send the user to another page. This often happens in a web application after authorization is performed, for example, to check if a user is logged in.
In the following example, we use a ternary operator inside of our `Route`. We check the value of `loggedIn` to see if the user is logged in or not. If they are logged in, they will see their profile component, `UserProfile`. If they aren't logged in, a `Redirect` will send them off to the log in screen instead:

```jsx
<Route path="/my-profile">
  {loggedIn ? <UserProfile /> : <Redirect to="/log-in" />}
</Route>
```

## 404
```jsx

// our updated routes inside of App.js

<Switch>
  <Route exact path="/">
    <Dashboard />
  </Route>
  <Route path="/reviews">
    <Reviews />
  </Route>
  <Route path="/about-me">
    <AboutMe />
  </Route>
  <Route path="/about-us">
    <AboutUs />
  </Route>
  <Route path="*">
    <PageNotFound />
  </Route>
</Switch>
```