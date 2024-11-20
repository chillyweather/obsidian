# Using Context Api

First, we'll create a new file named `AppContext.js`, which we'll put in the `/components` directory:

```jsx
// AppContext.js

import React from 'react';

export const AppContext = React.createContext();
```

Next, we'll import this file into `App.js` by adding the following line to our imports: `import { AppContext } from './AppContext';`

We'll then wrap our components with the provider component, and we'll have no need to pass down our state or methods, as we can do this inside the provider:

```jsx
<AppContext.Provider value={{state: this.state, handleLogin: this.handleLogin}}>
  <Switch>
    <ProtectedRoute path="/ducks" component={Ducks} />
    <ProtectedRoute path="/my-profile" component={MyProfile} />
    <Route path="/login">
      <div className="loginContainer">
        <Login />
      </div>
    </Route>
    <Route path="/register">
      <div className="registerContainer">
        <Register />
      </div>
    </Route>
    <Route>
      {this.state.loggedIn ? <Redirect to="/ducks" /> : <Redirect to="/login" />}
    </Route>
  </Switch>
</ AppContext.Provider>
```

## Subscribing to Context

We'll now have to update our `ProtectedRoute` and `Login` components accordingly so that they will be subscribed to this context. Let's look at our `ProtectedRoute` component first. This is a functional component so it will be easy to make this change using a `React.useContext()` hook:

```jsx
// ProtectedRoute.js

import React from 'react';
import { Route, Redirect } from 'react-router-dom';
import { AppContext } from './AppContext.js'; // importing the context

const ProtectedRoute = ({ component: Component, ...props }) => {
  const value = React.useContext(AppContext); // getting the values
  return (
    <Route>
      {
        () => value.state.loggedIn === true ? <Component {...props} userData={value.state.userData} /> : <Redirect to="./login" />
      }
    </Route>
)}

export default ProtectedRoute;
```

Note that we're putting the context inside of `value`, getting the value of `loggedIn`, and we're also passing down the `userData` object so that the `MyProfile` component can access this.

The `Login` class component will use the `handleLogin()` method, so we'll set it up like so:

```jsx
// Login.js

import React from 'react';
import { Link, withRouter } from 'react-router-dom';
import Logo from './Logo.js';
import * as auth from '../auth.js';
import { AppContext } from './AppContext.js'; // added here
import './styles/Login.css';

class Login extends React.Component {
  static contextType = AppContext;
  constructor(props){
    super(props);
    this.state = {
      username: '',
      password: '',
      message: ''
    }
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
   
  }
  handleChange(e) {
    const {name, value} = e.target;
    this.setState({
      [name]: value 
    });
  }
  handleSubmit(e){
    const value = this.context; //refer to the context
    e.preventDefault();
    if (!this.state.username || !this.state.password){
      return;
    }
    auth.authorize(this.state.username, this.state.password)
    .then((data) => {
      if (!data){
        return this.setState({
          message: 'Something went wrong!'
        });
      }
      if (data.jwt){
        this.setState({email: '', password: '', message: ''} ,() => {
          value.handleLogin(); //update our code
          this.props.history.push('/ducks');
          return;
        })
      }
    })
    .catch(err => console.log(err));
  }
  render(){
    return(
      <div onSubmit={this.handleSubmit} className="login">
        <Logo title={'CryptoDucks'}/>
        <p className="login__welcome">
          This app contains highly sensitive information. Please sign in or register to access CryptoDucks.
        </p>
        <p className="login__error">
          {this.state.message}
        </p>
        <form className="login__form">
          <label for="username">
            Username:
          </label>
          <input id="username" required name="username" type="text" value={this.state.username} onChange={this.handleChange} />
          <label for="password">
            Password:
          </label>
          <input id="password" required name="password" type="password" value={this.state.password} onChange={this.handleChange} />
          <div className="login__button-container">
            <button type="submit" className="login__link">Log in</button>
          </div>
        </form>

        <div className="login__signup">
          <p>Not a member yet?</p>
          <Link to="/register" className="signup__link">Sign up here</Link>
        </div>
      </div>
    )
  }
}

export default withRouter(Login);
```

The changes to the code are very minor, so it might be easy to miss them. We're just importing the context and adding `static contextType = AppContext;` after the opening curly brace inside the class component. Inside of the `handleSubmit()` method, we're getting the value of the context and using it to call `value.handleLogin()` instead of `this.props.handleLogin()` as we were previously doing.