# Introduction
useContext is a feature in React that allows components to access values from a context without using a context consumer. It provides a simple and direct way to access context values within functional components.

```jsx
import React, { useContext } from 'react';

// Create a context
const ThemeContext = React.createContext('light');

// A component that consumes the theme context
const ThemeDisplay = () => {
  const theme = useContext(ThemeContext);

  return <div>Current theme: {theme}</div>;
}

// A parent component that provides the theme context
const App = () => {
  return (
    <ThemeContext.Provider value="dark">
      <ThemeDisplay />
    </ThemeContext.Provider>
  );
}

// Render the app
ReactDOM.render(<App />, document.getElementById('root'));
```

<br>

## Passing data deeply into the tree
1. Place the `useContext` hook at the top level of your component to access and subscribe to the context.

```jsx
import { useContext } from 'react';

function Button() {
  const theme = useContext(ThemeContext);
  // ...
```

2. By calling `useContext`, you can retrieve the value of the context you provided. React will search the component tree and find the nearest context provider above the component to determine the context value.

3. To make the context available to the `Button` component, you need to wrap it or one of its parent components with the corresponding context provider.

```jsx
function MyPage() {
  return (
    <ThemeContext.Provider value="dark">
      <Form />
    </ThemeContext.Provider>
  );
}

function Form() {
  // ... renders buttons inside ...
}
```

4. It doesn't matter how many components are between the provider and the `Button`. Whenever a `Button` inside the `Form` component uses `useContext(ThemeContext)`, it will receive "dark" as the context value.

<br>

## Updating data passed via context 
To update the context value, you can combine it with state. Declare a state variable in the parent component and pass the current state as the context value to the provider.

```jsx
function MyPage() {
  const [theme, setTheme] = useState('dark');
  return (
    <ThemeContext.Provider value={theme}>
      <Form />
      <Button onClick={() => {
        setTheme('light');
      }}>
        Switch to light theme
      </Button>
    </ThemeContext.Provider>
  );
}
```

Now, any `Button` component inside the provider will receive the current value of the theme. When you call `setTheme` to update the theme value, all `Button` components will re-render with the new value of 'light'.

<br>

## Specifying a fallback default value 
If there are no providers of a specific context found in the parent tree, the context value returned by `useContext()` will be equal to the default value specified when creating the context:

```jsx
const ThemeContext = createContext(null);
```

Instead of using `null` as the default value, it's often preferable to use a more meaningful value, such as:

```jsx
const ThemeContext = createContext('light');
```

<br>

## Overriding context for a part of the tree 
To change the context for a specific portion of the component tree, you can wrap that portion with a provider that has a different value:

```jsx
<ThemeContext.Provider value="dark">
  {/* ... */}
  <ThemeContext.Provider value="light">
    <Footer />
  </ThemeContext.Provider>
  {/* ... */}
</ThemeContext.Provider>
```

You can nest and override providers multiple times according to your requirements.

<br>

## Reference
https://react.dev/reference/react/useContext
