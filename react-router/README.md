# React Router
React Router is a library that allows you to handle routing and navigation in your React applications. It provides components and APIs to define different routes in your application and navigate between them.

<br>

```jsx
import React from 'react';
import { BrowserRouter as Router, Switch, Route, Link } from 'react-router-dom';

// Components for different pages
const Home = () => <h2>Home Page</h2>;
const About = () => <h2>About Page</h2>;
const Contact = () => <h2>Contact Page</h2>;

const App = () => {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
            <li>
              <Link to="/contact">Contact</Link>
            </li>
          </ul>
        </nav>

        <Switch>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/contact">
            <Contact />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Switch>
      </div>
    </Router>
  );
};

export default App;
```

<br>

## Reference
https://reactrouter.com/en/main
