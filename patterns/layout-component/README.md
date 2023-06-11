# Layout Component
The Layout Component is a React pattern that helps in structuring and organizing the layout of a web page or application. It acts as a wrapper component that defines the common layout structure and contains the shared components or elements that are present on every page.

<br>

```jsx
// Layout.js
import React from 'react';
import Header from './Header';
import Footer from './Footer';

const Layout = ({ children }) => {
  return (
    <div>
      <Header />
      <main>{children}</main>
      <Footer />
    </div>
  );
};

export default Layout;
```

```jsx
// App.js
import React from 'react';
import Layout from './Layout';
import Home from './pages/Home';

const App = () => {
  return (
    <Layout>
      <Home />
      {/* Other components */}
    </Layout>
  );
};

export default App;
```
